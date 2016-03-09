# Computing The Really Optimal Tour Across The USA On The Cloud With Python

## Author: [Jean-François Puget](https://www.ibm.com/developerworks/community/blogs/jfp/?lang=en)

This is a follow up on Randy Olson work on solving TSPs in Python: [Computing the optimal road trip across the U.S.](http://www.randalolson.com/2015/03/08/computing-the-optimal-road-trip-across-the-u-s/). The code below is commented at length in my blog entry on [Computing The Really Optimal Tour Across The USA On The Cloud With Python](https://www.ibm.com/developerworks/community/blogs/jfp/entry/computing_the_really_optimal_tour_acrosss_the_usa_on_the_cloud_with_python)

Some of the code is a derivative work of Randy Olson's code, namely the list of points to visits, and the html template used for rendering the tour on Google Map.

Can we do better than Randy, i.e. can we compute the shortest tour visiting each one of the 50 landmarks he has selected? 

The answer is yes.  I will use these tools to compute it.
    
### Google Maps
No need to present this, is it?  We will use it for gathering data and rendering the result on a map.
    
### Concorde
[Concorde](http://www.math.uwaterloo.ca/tsp/concorde.html) is the best known algorithm to solve TSPs, see my [post](http://www.randalolson.com/2015/03/08/computing-the-optimal-road-trip-across-the-u-s/) for more background on it.
    
### CPLEX
We use [CPLEX](http://www.ibm.com/software/commerce/optimization/cplex-optimizer/) indirectly as Concorde is built on top of it.  In all fairness, Concorde can also be used with an alternative solver called QSopt.  Using CPLEX is faster, but the difference becomes noticeable only for very large TSPs.  For a 50 city TSP lke Randy Olson's tour, using CPLEX or QSopt is similar.  Let's admit that I have a strong bias towards CPLEX in general!
    
### NEOS
This is what makes Concorde and CPLEX easy to consume in Python.  NEOS is a server delivering  Software as a Service (SaaS).  Actually, we could say that NEOS delivers Solvers as a Service because it provides quite a few optimization solvers.  In particular, Concorde on NEOS is available at: http://neos.mcs.anl.gov/neos/solvers/co:concorde/TSP.html
