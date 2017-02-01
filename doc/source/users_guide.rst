===========
Users guide
===========

Random variables
================

Simply speaking `random variables`_ are numeric values which change their 
value over time following a particular statistical distribution. 

.. code-block:: cpp

   namespace desy{
   namespace testdata {
        
        template<
                 typename DTYPE,
                 typename GTYPE
                >
        class random_variable
        {
            public:
                using value_type = ....;
                
                value_type operator()();
                value_type current_value() const;
        
        };
   
   } // end of namespace testdata
   } // end of namespace desy
   
 
This class template heavily relies on the random number code which has 
become standard since C++11 (see `random numbers in C++11`_ for more 
details).
It must be mentioned that random number generators provided by the STL may not
good enough for security applications or advances mathematical methods 
like Monte-Carlo simulations. However, they are certainly good enougth to 
create test data for programs.
 
.. _random numbers in C++11: http://en.cppreference.com/w/cpp/numeric/random  
.. _random variables: https://en.wikipedia.org/wiki/Random_variable
.. _multivariate random variable: https://en.wikipedia.org/wiki/Multivariate_random_variable

Create a random variable
------------------------


There are some default implementations available to make life a bit easier. 
For noise one could use the :cpp:class:`uniform_random_var` template. 

.. code-block:: cpp

    namespace td = desy::testdata;

    auto var = td::uniform_random_var<int8_t>(-5,5);
    
    for(size_t index=0;index<1025;++index)
        std::cout<<index<<"\t"<<var()<<std::endl;

The constructor arguments are the minimum and maximum value of the closed 
interval :math:`[a,b]` from which the values are drawn.        
The above example would produce the following output

.. todo:: 

    Add image here from gnuplot with the output
    
The second important distribution is the the Gauss- or normal-distribution 
defined as 

.. math::

    f(x;\mu,\sigma)=\frac{1}{\sigma\sqrt{2\pi}}
                    \exp\left(-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2\right)
                    
A random variable with a gaussian distribution can be defined with

.. code-block:: cpp

    namspace td = std::testdata;
    
    auto var = td::gaussian_random_var<double>(10,0.5);
    
The first argument of the constructor is the mean value (:math:`\mu`) and the
second one the standard deviation (:math:`\sigma`).

.. todo::

    Show here some plots of such a series of numbers along with a histogram.
    


Using random variables
----------------------

The simplest application for a random number is to be used as a generator

.. code-block:: cpp

    std::vector<double > data(1024);
    
    auto lambda = create_random_var(generator,distribution);
    
    std::generate(data.begin(),data.end(),lambda);
    
Sochastic Process
=================

A `stochastic process`_ can be considered as a function of random variables. 
In our particular implementation, 
    
.. _stochastic process: https://en.wikipedia.org/wiki/Stochastic_process

Concept of a stochastic process 

.. code-block:: cpp

    template<typename T>
    class stochastic_process
    {
        public:
        
            void  
    
    };
    
