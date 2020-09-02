# K-Means Algorithm in Hadoop and Spark

The work, part of the Cloud Computing course, consists in implementing a distributed
MapReduce application that implements the well known K-Means Clustering algorithm.
The implementation must be carried out in Apache Hadoop and then in Apache Spark, both
running on a cluster of 4 virtual machines provided by the University of Pisa.
See the full documentation for more details.

### How to use: Hadoop ###

First of all the jar file of the Hadoop project must be placed in the home directory of the
hadoop-namenode. Then, the HDFS must have a Resources directory containing Input and
Output subdirectories. In the Input subdirectory we will put the input files for points and
clusters. In the Output subdirectory we will find the output file containing the centroids at
the end of the execution.
The input files must be named in the following manner:
 Resources/Input/points_nxd.txt, where n is the number of points and d is the
dimension.
 Resources/Input/centroids_nxd.txt, where n is the number of centroids and d is
the dimension.
The points file must contain a list of double or float coordinates separated by a whitespace,
one point per line. The centorids file must contain the coordinates of the centroids
and the unique IDs of the centroids as follows (example of a 3d centroid): ID. x y z
The ID must be separated from the coordinates by a tab.
After setting up the HDFS, the application can be launched (from the hadoop-namenode)
with the following command:
hadoop jar jar_file package_name.mainClass k n d
where the parameters are:
- package_name.mainClass, in our case, was it.unipi.hadoop.KMeans
- k is the number of clusters
- n is the number of points
- d is the dimensionality of points
At the end of the execution the output can be found in Resources/Output/part-r-00000.

### How to use: Spark ###

Given the input files configuration explained in the previous section, the Spark program can
be launched with the following command:

**spark-submit python_file –input "Resources/Input/points_nxd.txt"
–output "Resources/Output/Spark_param_test" –dimension d –num_k k
–iterations iter –threshold thr –seed s –master yarn**

where the parameters are:
- python_file, in our case, was k-means.py
- k is the number of clusters
- n is the number of points
- d is the dimensionality of points
- iter is the maximum number of iterations (10 in our case)
- thr is the stopping threshold (0.03 in our case)
- s is the seed used in the selection of initial centroids (for repeatability)
- –master specifies whether we want to run the program locally (local) or on the cluster
of nodes (yarn)

### Credits ###
This project was developed in collaboration with R. Polini, A. De Roberto and S. Pampaloni for the Cloud Computing course (MsC in Artificial Intelligence & Data Engineering @ University of Pisa).
