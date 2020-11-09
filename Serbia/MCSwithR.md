
#### Kevin O'Brien 

* Main Job: Forestry Data Scientist (mainly works with R).
* Formerly a university teacher in the West of Ireland.
* Also I worked in Arts and Events Sector in Ireland.
* Involved in R, Python and Julia Community organizations.
    Why R? Foundation, Forwards, Python Ireland, JuliaCon 

-----------------------------------------------------------------
#### Method Comparison

Prevalence in Clinical Science

Method comparison measures the closeness of agreement between the measured values of two methods.
Note: The term method is used as a generic term and can include different measurement procedures, measurement systems, laboratories, or any other variable that you want to if there are differences between measurements.

-----------------------------------------------------------------

#### Method Comparison



* In some situations accurate measurements are easily obtained.
* In other situations athere is some cost or overhead associated with accuracy.

Example: Body Mass Index

-----------------------------------------------------------------

#### Method Comparison

Two questions being asked:

Agreement: Do two methods of measurement consistently give the same measurements for each item?

Interchangeability: Can one method of measurement be substituted for another, with a loss of measuremnt accuracy that is within acceptable levels?

-----------------------------------------------------------------

#### Experimental Design

* Same sample of items / samples / patients
* Simultaneous measurements

Experimental Designs may be 
1. Single measurements or 
2. Replicate measurements.

-----------------------------------------------------------------

#### Application of Well-known approaches

* Correlation, Paired t-tests, Regression
* 

-----------------------------------------------------------------

#### Agreement Criteria (for Replicate Measurements)

* No inter-method Bias
* Within-item variability / a.k.a. Repeatability
* Between-item variability 


(Barnhart et al / Roy 2009)


-----------------------------------------------------------------

#### Intermethod Bias 

- One device systematically over-estimates or underestimates the measurements .
- Easy to detect 
    Mean of Case-wise differences, Paired t-test, Bland-Altman plot 
- Simple Recalibration


-----------------------------------------------------------------

#### The Bland-Altman Plot

* Mean-Difference Plot (Tukey)

#### Limits of agreement (LoA)
Limits of agreement estimate the interval within which a proportion of the differences between measurements lie.



-----------------------------------------------------------------

#### Construction

* Simple Construction
* Scatterplot of the case-wise averages vs the case-wise differences
* ``plot(A,D)``

-----------------------------------------------------------------

#### Prevalence of the Bland Altman plot

47284 Citations of Bland-Altman 1986 (Scholar.google.com)


-----------------------------------------------------------------
#### "Modified Bland-Altman Plot"
https://stats.stackexchange.com/questions/280917/proper-name-for-modified-bland-altman-plot


-----------------------------------------------------------------
#### Technology Acceptance Model

* The technology acceptance model proposes that perceived ease of use and usefulness of a technological tool determines the extent of consumer acceptance.




-----------------------------------------------------------------
#### Technology Acceptance Model
Davis (1989) proposes the TAM model, which suggests an hypothesis as to why users may adopt particular technologies, and not others. 
According to this theory, when users are presented with a new 
technology, two important factors will influence their decision about how and when they will adopt it.


* **Perceived usefulness (PU)** - This was defined by Fred Davis as "the degree to which a person believes that using a particular system would enhance their job performance".
* **Perceived ease-of-use (PEOU)** - Davis defined this as "the degree to which a person believes that using a particular system would be free from effort" 

-----------------------------------------------------------------
#### Technology Acceptance Model
Davis's explanations of these term can be rephrased for application to statistical analysis. 
Perceived Use could refer to the degree to which an user would deem a particular statistical method would properly establish the results of an analaysis. In the case of method comparison studies, proper indication of agreement, or lack thereof.

-----------------------------------------------------------------
#### Technology Acceptance Model

Perceived ease-of-use requires only applying the context of a satistical problem. A very modest statistical skill set is the only prerequistive for constructing a Bland-Altman plot, and computing limits of agreement. The main building blocks 
are simple descriptive, statistics and a knowledge of the normal distribution. These are topics that feature in almost every undergraduate statistics courses.


-----------------------------------------------------------------

#### Deming Regression

(Twitter)
https://twitter.com/NoahHaber/status/1304784136960454658/photo/1
https://twitter.com/moultano/status/1304826377414221830/photo/1

-----------------------------------------------------------------

#### Linear Mixed Effects Models (LME)


-----------------------------------------------------------------
#### Implementation of LME Models

* R programming: {nlme} and {lme4}

* SAS: PROC MIXED

* Julia: MixedModels.jl


-----------------------------------------------------------------
#### Previously Proposed Frameworks

* Carstensen et al (2004-2010)
* Anuradha Roy (2009)

-----------------------------------------------------------------
#### Critique of Between-item Criterion

-----------------------------------------------------------------

#### LME Models with Nested Random Effects



-----------------------------------------------------------------

####  Graphical Approaches

Mountain Plot
 - Folded ECDF Plot
 - Implementation with ggplot2

Mean Centred

-----------------------------------------------------------------

#### Influence Analysis

* Cook's Distance
* DFBetas, DFFIts


