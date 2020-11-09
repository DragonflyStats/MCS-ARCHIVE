
#### Kevin O'Brien 

* Main Job: Forestry Data Scientist (mainly works with R).
* Formerly a university teacher in the West of Ireland.
* Also I worked in Arts and Events Sector in Ireland.
* Involved in R, Python and Julia Community organizations.
    Why R? Foundation, Forwards, Python Ireland, JuliaCon 

-----------------------------------------------------------------

#### Method Comparison

Prevalence in Clinical Science

* In some situations accurate measurements are easily obtained.
* In other situations athere is some cost or overhead associated with accuracy.

Example: Body Mass Index

-----------------------------------------------------------------

#### Method Comparison

Two questions being asked:

Agreement

Interchangeability

-----------------------------------------------------------------

#### Experimental Design

* Same item / sample / patient
* Simultaneous Measurements


-----------------------------------------------------------------

#### Agreement Criteria (for Replicate Measurements)

* No inter-method Bias
* Repeatability
* Between-item Covariances


(Barnhart et al / Roy 2009)


-----------------------------------------------------------------

#### Intermethod Bias 

- One device systematically over-estimates or underestimates the measurements .
- Easy to detect 
- Simple Recalibration

-----------------------------------------------------------------

#### Application of Well-known approaches

* Correlation, Paired t-tests, Regression
* 

-----------------------------------------------------------------

#### The Bland-Altman Plot

* Mean-Difference Plot (Tukey)


Limits of Agreement 
Tolerance Intervals


-----------------------------------------------------------------

#### Construction

* Scatterplot of the case-wise averages vs the case-wise differences
* ``plot(A,D)``

-----------------------------------------------------------------

#### Prevalence of the Bland Altman plot




-----------------------------------------------------------------
#### Technology Acceptance Model

* The technology acceptance model proposes that perceived ease of use and usefulness of a technological tool determines the extent of consumer acceptance.



-----------------------------------------------------------------

#### Deming Regression

(Twitter)

-----------------------------------------------------------------

#### Linear Mixed Effects Models (LME)


-----------------------------------------------------------------
#### Implementation of LME Models

* R programming: {nlme} and {lme4}

* SAS: PROC MIXED

* Julia: MixedModels.jl

-----------------------------------------------------------------

#### LME Models with Nested Random Effects

-----------------------------------------------------------------

####  Graphical Approaches

Mountain Plot
 - Folded ECDF Plot
 - Implementation with ggplot2


-----------------------------------------------------------------

#### Influence Analysis

* Cook's Distance
* DFBetas, DFFIts


