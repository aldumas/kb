#todo 

Different Java versions
`strictp`??? Or is it `strictfp`??
What's JDK17 do for this?

Turns out floating point math is hard because some machines have registers that have 80 bit registers but some have 64 (to allow for intermediate results to contain more significant figures). Turning on strictfp enforces calculations to only use 64 bits.