---
created-at: 2023-08-21 20:15
tags: ruby
---
# Task: Control enumeration order of `Hash` values

When `each` is called on a `Hash` instance, the order of enumeration is not defined. This task explores ways to order enumeration for `Hash` objects.

# Setup

Suppose we have some jobs that have a name and priority. A job is run by calling its `perform` method. Suppose further that we have a method that accepts a collection of jobs and runs them all. In this case, we defined it directly in the  `Job` class, but it could be defined in a separate library, for example.  

```ruby
class Job  
  attr_reader :name, :priority  
  
  def initialize(name:, priority:)  
    @name = name  
    @priority = priority  
  end  
  
  # Run the job.  
  def perform  
    puts "Job #{@name} with priority #{@priority} has been run."  end  
  
  # Run all of the given jobs.  
  #  # Jobs are run in the order returned by `jobs.each`.  #  # @param jobs [Enumerable<Job>]  def self.perform_all(jobs)  
    jobs.each(&:perform)  
  end  
end
```
  
Suppose, further, that we have a Hash of jobs, indexed by job name. Why do have them in a hash? Let's just assume our code needs to do a lot of job lookups by name and so we decided to keep them in a hash for performance reasons. Or maybe we are receiving the jobs from a 3rd party library, and this is the structure it gives us the jobs in.  

```ruby
jobs_hash = (1..5).map { |i| Job.new(name: i, priority: rand(10)) }.to_h { |job| [job.name, job] }  
```
  
# Objective

Our task is to run all of the jobs in order of priority. We have 2 problems:  
1. `Job.perform_all` expects `jobs.each` to yield a Job to the block, but our Hash will yield the key/value pair.  
2. The ordering of elements returned by Hash maps is not defined, but we need them in order of priority.  
  
How do we run the jobs present in our Hash in order of priority?  

# Approaches

We'll explore two main approaches:
1. Change the receiver of the `each` message. The idea is this: instead of passing the `Hash` into `Job.perform_all`, we'll pass a different object whose `each` method will `yield` the `Job`s in order of priority. We'll explore a few different options.
2. Change the method that gets run when `jobs_hash` receives the `each` message. Here, we'll pass in the `Hash` but we will patch it so that a different method runs when `Job.perform_all` calls `each` on it.

## Approach 1: Change the receiver of the `each` message

### Option 1: Transform the `Hash` into an object that has an `each` method which will yield `Job`s in order of priority.  

```ruby
jobs_array = jobs_hash.values.sort_by(&:priority)  
  
Job.perform_all(jobs_array)  
```
  
This works because:  
1. `Array#each` yields the elements in of the array in the order that they exist in the array.  
2. The elements of the array are `Job`s instead of key/value pairs.  
  
It's simple and it works great.

### Option 2: Use `Object#enum_for` to create an enumerator with an `each` method which uses a custom method under the hood

In order to use `Object#enum_for` (or its synonym `Object#to_enum`), the object needs to have a method which does the iteration in the desired order. In order to add the method to the hash, we can define a new singleton method. The only code which will use this method is the code which generates the enumerator.  

```ruby
class << jobs_hash
	def each_job_in_priority_order(&proc)  
	  values.sort_by(&:priority).each(&proc)  
	end
end 
```

Now we use `Object#enum_for` to create an object whose `each` uses `each_job_in_priority_order` under the hood.

```ruby
jobs_in_priority_order = jobs_hash.enum_for(:each_job_in_priority_order)  
  
Job.perform_all(jobs_in_priority_order)  
```

`Object#enum_for` works best when you don't need to add special singleton methods, like we did here. If you're working with your own class, you can define different enumerator methods that you think will be generally useful, and then clients can either use those directly or, if they need to run code which relies on `each` they can use `Object#enum_for` to get an object whose `each` relies on the desired enumerator method.

## Approach 2: Change the method that gets run when `jobs_hash` receives the `each` message

### Option 1: Add an `each` singleton method

```ruby
class << jobs_hash
	def each(&proc)
		values.sort_by(&:priority).each(&proc)  
	end
end

Job.perform_all(jobs_hash)  
```

Because method resolution finds singleton methods before methods defined in the class, this new `each` singleton method will be used when `jobs_hash.each` is called.

The main drawback to this approach as that the new `each` behavior only applies to this specific `Hash` instance. If you recreate `jobs_hash` but don't add the singleton method, you won't get the new `each` behavior.


# Option 3b: Create an enumerator that has an `each` method that yields `Job`s in order of priority by defining a class which exposes an `each` method that yields `Job`s in order of priority.  
  
class HashValueEnumerator  
  def initialize(hash, order_by:)  
    @hash = hash  
    @order_by = order_by  
  end  
  
  def each(&block)  
    @hash.values.sort_by(&@order_by).each(&block)  
  end  
end  
  
jobs_in_priority_order = HashValueEnumerator.new(jobs_hash, order_by: :priority)  
  
Job.perform_all(jobs_in_priority_order)  
  
=begin  
  
HashValueEnumerator is general enough to put in a library. You could also make it more useful by having the `initialize`  
method accept a block which transforms the value to whatever the caller desires, and then use that transform in the  
implementation of `each` so the desired values are yielded.








More options to add:

```ruby

# Option X (change `each` method)

# class << jobs_hash  
#   def jobs_in_priority_order(&proc)  
#     values.sort_by(&:priority).each(&proc)  
#   end  
#  
#   alias :each :jobs_in_priority_order  
# end  
#  
# Job.perform_all(jobs_hash)  

# Option Y - change the `each` method

module HashJobOrdering  
  def each(&block)  
    values.sort_by(&:priority).each(&block)  
  end  
end  

class << jobs_hash  
  prepend HashJobOrdering  
end  
  
Job.perform_all(jobs_hash)
```

---
References:

