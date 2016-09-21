.. _intro_R:


*****************
Introduction to R 
*****************

.. _install_Rstudio:

Rstudio and R
=============

Hopefully, you have downloaded R and Rstudio already. If you do not have chance
for it yet. You can now download R from `R <https://cran.rstudio.com/>`_ and 
Rstudio from  `Rstudio <https://www.rstudio.com/products/rstudio/download3/>`_.
Please check your Operation System before downloading. R is one of the best softwares 
for statistical analysis. You can find all the implementations of the methods you've
learned in STAT 135. Rstudio is said to be the best platform for R.


.. _R_basics:

R basics
--------

- Assignment

  The most straight forward way to store a list of numbers is through an
  assignment using the c command. (c stands for "combine.") The idea is
  that a list of numbers is stored under a given name, and the name is
  used to refer to the data. A list is specified with the c command, and
  assignment is specified with the "<-" symbols. Another term used to
  describe the list of numbers is to call it a "vector."

  The numbers within the c command are separated by commas. As an example,
  we can create a new variable, called "bubba" which will contain the numbers
  3, 5, 7, and 9::

    > bubba <- c(3, 5, 7, 9)

  When you enter this command you should not see any output except a new
  command line. The command creates a list of numbers called "bubba." To
  see what numbers is included in bubba type “bubba” and press the enter key::

    > bubba
    [1] 3 5 7 9

  If you wish to work with one of the numbers you can get access to it
  using the variable and then square brackets indicating which number::

    > bubba[2]
    [1] 5
    > bubba[1]
    [1] 3
    > bubba[0]
    numeric(0)
    > bubba[3]
    [1] 7
    > bubba[4]
    [1] 9

  Notice that the first entry is referred to as the number 1 entry, and
  the zero entry can be used to indicate how the computer will treat the
  data. You can store strings using both single and double quotes, and
  you can store real numbers.

  
- Operation

  R's basic operation like "+", "-", "*", "/", "^", are the same as those of
  other languages such as Python, C, C++ and so on. There are also
  basic math function like "log", "sin"::

     > 2^5
     [1] 32
     > log(2)
     [1] 0.6931472
     > sin(pi)
     [1] 1.224647e-16
     > cos(pi)
     [1] -1

     
- Read Data from a CSV file

  Please download the data from `bcourse <https://bcourses.berkeley.edu/courses/1453788/files/folder/Data>`_.
  Now I store it in "~/Desktop/temp" (You can store it in anywhere you like). Then we
  read this file by::

    xom <- read.csv("~/Desktop/temp/sp500Historical.csv")

  The data file is in the format called "comma separated values" (csv).
  That is, each line contains a row of values which can be numbers or
  letters, and each value is separated by a comma. We also assume that
  the very first row contains a list of labels. The idea is that the labels
  in the top row are used to refer to the different columns of values. We
  can use a command to take a look at the data or, a good thing for Rstudio,
  is that you can just click::

    View(xom)

  The data is a 252 by 7 matrix. The first 5 rows look like:

  .. table::

    +----------+---------+---------+--------+--------+-----------+--------------+
    |    Date  |   Open  |   High  |   Low  |  Close | Adj.Close |   Volume     |
    +==========+=========+=========+========+========+===========+==============+
    | 12-Sep-16| 2,120.86| 2,150.76|2,119.12|2,148.10| 2,148.10  | 321,471,413  |
    +----------+---------+---------+--------+--------+-----------+--------------+
    |  9-Sep-16| 2,169.08| 2,169.08|2,127.81|2,127.81| 2,127.81  | 4,233,960,000|
    +----------+---------+---------+--------+--------+-----------+--------------+
    |  8-Sep-16| 2,182.76| 2,184.94|2,177.49|2,181.30| 2,181.30  | 3,727,840,000|
    +----------+---------+---------+--------+--------+-----------+--------------+
    |  7-Sep-16| 2,185.17| 2,187.87|2,179.07|2,186.16| 2,186.16  | 3,319,420,000|
    +----------+---------+---------+--------+--------+-----------+--------------+
    |  6-Sep-16| 2,181.61| 2,186.57|2,175.10|2,186.48| 2,186.48  | 3,447,650,000|
    +----------+---------+---------+--------+--------+-----------+--------------+

 For more details and more advanced knowledge, please refer to `R Tutorial <http://www.cyclismo.org/tutorial/R/index.html>`_.
 This is a course tutorial by Kelly Black in University of Georiga.

     
	   
  
  

  

  

  


  
  








   
