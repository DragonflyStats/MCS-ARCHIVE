
Kevin O'Brien 

* Main Job: Forestry Data Scientist (mainly works with R).
* Formerly a University lecturer in the West of Ireland.
* Also I worked in Arts and Events Sector in Ireland.
* Involved in R, Python and Julia Community organizations.

1. Who am I

Forestry 
Former University Lecturer

Why R? Foundation
Python Ireland
JuliaCon 



-----------------------------------------------------------------

Method Comparison

In some situations accurate measurements are easily obtained.
In other situations athere is some cost or overhead associated with accuracy.

Example: Body Mass Index

-----------------------------------------------------------------
Experimental Design

Same item / sample / patient
Simultaneous Measurements
-----------------------------------------------------------------
Two questions being asked:

Agreement

Interchangeability

-----------------------------------------------------------------
Application of Well-known approaches

* Correlation, Paired t-tests, Regression
* 

-----------------------------------------------------------------
The Bland-Altman Plot

* Mean-Difference Plot (Tukey)


-----------------------------------------------------------------
Construction

* Scatterplot of the case-wise averages vs the case-wise differences
* ``plot(A,D)``

-----------------------------------------------------------------
Prevalence of the Bland Altman plot




-----------------------------------------------------------------
Technology Acceptance Model


-----------------------------------------------------------------

Linear Mixed Effects Models (LME)


-----------------------------------------------------------------

R programming:

SAS: PROC MIXED

Julia:


-----------------------------------------------------------------

--------------------------------------


--------------------------------------

Agreement Criteria (for Replicate Measurements)

* No inter-method Bias
* Repeatability
* Between-item Covariances


(Barnhart et al / Roy 2009)

--------------------------------------
Intermethod Bias 
- One device systematically over-estimates or underestimates the measurements .
- Easy to detect 
- Simple Recalibration

---------------------------------------

Technology Acceptance Model


The technology acceptance model proposes that perceived ease of use and usefulness of a technological tool determines the extent of consumer acceptance.
----------------------------------------

Mountain Plot
 - Folded ECDF Plot
 - Implementation with ggplot2
 
----------------------------------------
---------------------------------------------

2. The Method Comparison Problem

Prevalence in Clinical Science
The Bland Altman Plot
Other Measurements and Technqiues
Simplicity of Construction
Technology Acceptance Model
Ubiquity of The Bland Altman Plots
Limits of Agreement 
Tolerance Intervals

-----------------------------------------------

3. Systolic Blood Pressure 

Replicate Measurements

-----------------------------------------------

4. Model Based Approach

Simple Linear Regression
Deming Regression

------------------------------------------------
5. Linear Mixed Effects Models

lme4 R package
nested random effects

------------------------------------------------

6. Graphical Approaches

Mountain Plots

------------------------------------------------

7. Influence Analysis

Cook's Distance
-------------------------------------------------
