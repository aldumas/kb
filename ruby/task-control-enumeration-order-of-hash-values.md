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
1. Replace the receiver of the `each` message. The idea is this: instead of passing the `Hash` into `Job.perform_all`, we'll pass a different object whose `each` method will `yield` the `Job`s in order of priority. We'll explore a few different options.
2. Intercept the `each` message such that a different method runs rather than `Hash#each`. Here, we'll pass in the `Hash` but we will patch it so that a different method runs when `Job.perform_all` calls `each` on it.



1. Transform the `Hash` into an object that has an `each` method which will yield `Job`s in order of priority. (This is probably the most obvious solution (and not a bad one)).
2. Tweak our `jobs` hash to have an `each` method that yields `Job`s in order of priority.  
3. Create an enumerator that has an `each` method that yields `Job`s in order of priority. 
	a. By using Object#enum_for. 
	b. By defining a class which exposes an `each` method that yields `Job`s in order of priority.  
  
# Option 1: Transform the `Hash` into an object that has an `each` method which will yield `Job`s in order of priority.  
  
jobs_array = jobs_hash.values.sort_by(&:priority)  
  
Job.perform_all(jobs_array)  
  
=begin  
  
This works because:  
1. `Array#each` yields the elements in of the array in the order that they exist in the array.  
2. The elements of the array are `Job`s instead of key/value pairs.  
  
It's simple and it works great.  
  
=end  
  
# Option 2: Tweak our `jobs` hash to have an `each` method that yields `Job`s in order of priority.  
  
def jobs_hash.each(&proc)  
  values.sort_by(&:priority).each(&proc)  
end  
  
# Note: if you don't have to sort it, you can skip converting the hash to an array with `values` by using `each_value`  
# instead of `each`. The problem with having to sort it is that `sort_by` returns an array, and Array does not have  
# `each_value`. You would have to convert it back to a hash again, but then you would lose your ordering (and it's an  
# extra method call). The upshot is that if you don't care about ordering, each_value saves you from having to create  
# an array only to throw it away.  
  
Job.perform_all(jobs_hash)  
  
=begin  
  
This works by creating a method in the singleton class associated with this specific hash instance (i.e. no other hash)  
instances have access to this method.  
  
During method lookup, the singleton class associated with jobs_hash is looked at before Hash#each and our custom `each`  
method is found and used.  
  
# TODO discuss why this can make code hard to reason about.  
  
=end  
  
# Since we modified the singleton class object for `jobs_hash`, we need to clean up for the next example.  
class << jobs_hash  
  remove_method :each  
end  
  
# Option 3a: Create an enumerator that has an `each` method that yields `Job`s in order of priority by using Object#enum_for  
  
=begin  
  
In order to use `Object#enum_for` (or its synonym `Object#to_enum`), the object needs to have a method which does the  
iteration in the desired order. The benefit of this approach is that we don't need to redefine `each` so all other code  
continues to use the built-in `each`.  
  
In order to add the method to the hash, we can use the same trick as the previous option by defining a new singleton  
method with a new name. The only code which will use this method is the code which generates the enumerator.  
  
=end  
  
def jobs_hash.each_job_in_priority_order(&proc)  
  values.sort_by(&:priority).each(&proc)  
end  
  
# This creates an object whose `each` uses `each_job_in_priority_order` under the hood.  
jobs_in_priority_order = jobs_hash.enum_for(:each_job_in_priority_order)  
  
Job.perform_all(jobs_in_priority_order)  
  
# Clean up  
  
class << jobs_hash  
  remove_method :each_job_in_priority_order  
end  
  
# IMPORTANT: Since we removed :each_job_in_priority_order, calls to `jobs_in_priority_order#each` will no longer work.  
  
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

---
References:

