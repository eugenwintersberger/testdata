==========
Motivation
==========

In many cases testing applications (in particular scientific ones) requires the
generation of test data. There are several naiv approaches how to generate this
data. The two most often used are 

#. use a single, known numeric value (even for arrays)
#. generate uniformly distributed random values. 

Both approaches have their applications however, in many cases this is not 
really what we want. 
Using a single, known, constant value for everything is a dangerous thing
as a test may pass accidentaly since your code works, for whatever reason, 
for this particular value. 
A simple uniform random distribution for an input value is not always what 
a program will face in the real world. 

*libtestdata* provides the facilities to generate more realistic test data 
for your unit and program acceptance tests. 
