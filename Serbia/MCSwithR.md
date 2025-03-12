
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

Roy’s Tests (Roy 2009)
=============================
Roy 2009 devised an LME based Testing approach to the MCS problem, based on earlier work by Hamlett et al. 
Roy 2009 presents a series of three formal hypothesis tests for assessing agreement between two methods of measurement.
Roy also alludes to some of the current shortcomings of the approach.

### Components of Test

Comparing different model specifications with LRT tests

---

## Variability Tests
- Three tests are implemented using R’s **NLME** package:
  1. **Between-Subject Variability**: Comparing variability between two methods.
  2. **Within-Subject Variability**: Assessing consistency within individuals across methods.
  3. **Overall Variability**: Computing coefficients of repeatability for both methods.

### R Implementation
- Use the `anova()` function in R for variability testing.
- Variance components from the computer output directly generate limits of agreement and measures of repeatability.

### Papers:
- Roy 2007
- Roy 2009
- Hamlett et al.
- Roy Leiva 2011

-----------------------------------------------------------------------------------
# Limits of Agreement

## Calculation of LMEs (Linear Mixed Effects Models)

### Established Methodologies for Method Comparison Studies
- Graphical methods such as Bland and Altman's difference plot and scatterplot are widely used.
- **Classical Approach**:
  - Limits of agreement are calculated using Bland and Altman’s approach.
  - Alternative computation methods include prediction intervals (BXC 2008).

**BXC 2008** states:  
*"Limits of Agreement can only be interpreted as prediction limits for the difference between means of a series of measurements by both methods, which is not normally relevant."* (BXC 2008, pg. 3)

---

### Use of LME Models
- Commenting on **BXC**, the adoption of computer-based approaches to method comparison studies is now necessary, moving away from traditional pen-and-paper methods.
- Linear mixed effects models are highly suitable for method comparison studies (MCS).

#### What is an LME Model?
- Provides a precise definition of replicate measurements, incorporating:
  - BXC’s definition.
  - Bland and Altman’s definition.
- Replicate measurements are an additional source of variance.  
  **Hamlett** provides guidelines on handling replicate measurements.

#### Formatting Data for Analysis
- Both **Roy** and **Carstensen** emphasize formatting method comparison data using four variables:
  - Example: `meth`, `repl`, `item`, etc.
- **BXC** advises specific variable names to simplify the process for users not proficient in R.

---

### Blood JSR Data Set
- Introduced by Bland and Altman (1999).
- **Roy** demonstrates the use of this dataset to apply their model.



#### Example
- **BXC 2008, pg. 4**:
  - Variation between items is specified by \( m^2 \).
  - Variation within items is specified by \( m^2 \).

---

## Case Study: Carstensen’s "Oximetry" Data Set
- BXC computes Limits of Agreement (LoAs) for two cases:
  - With additional interaction term: **(-9.87, 14.81)**.
  - Without additional interaction term: **(-12.18, 17.12)**.

---

## Repeatability
- Requires multiple measurements from both methods.
- Based on residual standard deviation:  
  \( 2 \times 2m = 2.83m \).

---

## Expansion to Three-Method Case
- Consider Variance-Covariance (VC) structure:
  - Compound symmetric: \( x^2 = y^2 = z^2 \).
  - Symmetric structure.

When two of the three methods are considered equal, further adjustments are necessary.

---

## Types of Residuals in Linear Models
**Three Basic Types**:
1. **Marginal Residuals**: Difference between observed data and estimated marginal mean.
2. **Model-Specified Residuals**: Based on generalized least-squares (GLS) solutions.
3. **Full Conditional Residuals**: Difference between observed data and predicted value.

### Case Deletion Diagnostics
- Efficient methods for parameter estimation and model refitting.
- Desirable properties of residuals include:
  - Diagnostic influence (Schabenberger, 2004).
  - Subsets and singletons.

Here's your content polished and organized into Markdown format, making it easier to read while retaining the details:

```markdown
# Bland-Altman Plot Function (R Code Example)

```r
# Set seed for replicability
set.seed(42)
x = rnorm(50)
y = x + rnorm(50)

baplot = function(x, y) {
  xstd = (x - mean(x)) / sd(x)
  ystd = (y - mean(y)) / sd(y)

  bamean = (xstd + ystd) / 2
  badiff = (ystd - xstd)

  plot(badiff ~ bamean, pch = 20, xlab = "Mean", ylab = "Difference")

  # Construct the title dynamically
  title(main = paste("Bland-Altman plot of x and y\n",
    deparse(substitute(x)), "and", deparse(substitute(y)),
    "standardized"), adj = ".5")

  # Draw reference lines dynamically
  abline(h = c(mean(badiff), 
               mean(badiff) + 1.96 * sd(badiff),
               mean(badiff) - 1.96 * sd(badiff)), lty = 2)
}

baplot(x, y)
```

---

# Limits of Agreement and Linear Mixed-Effects (LME) Models

## Objectives of the Paper
This paper proposes and demonstrates the implementation of a method comparison study (MCS) using R, based on Linear Mixed-Effects models. The methodology aims to achieve the following:

1. Compute the inter-method bias between two methods of measurement.
2. Compute the limits of agreement.
3. Assess the between-subject variability of both methods.
4. Assess the within-subject variability of both methods.
5. Evaluate the overall variability of both methods.
6. Determine the coefficient of repeatability.

The methodology integrates two existing approaches:
1. **Bendix Carstensen et al.**: Tasks 1, 2, and 6.
2. **Anuradha Roy**: Tasks 1, 3, 4, 5, and 6.

---

## Sampling Protocols
### Types of Sampling
- **Paired tests**
- **No matching**
- **Linked replicates**
- **Unlinked replicates**

**Carstensen Sampling**: Describes the sampling method used in the "Fat" dataset.

---

## Linear Mixed-Effects (LME) Models

### Statement of an LME Model
An LME model satisfies the structure defined by **Laird and Ware (1982)**:

$$
y_i = X_i\beta + Z_i b_i + \epsilon_i
$$

- \( b_i \sim N(0, D) \)
- \( \epsilon_i \sim N(0, R_i) \)

Where:
- \( D \): Variance-covariance matrix of random effects.
- \( R_i \): Variance-covariance of residuals at time points.

### Carstensen's LME Model
Carstensen specifies the model as:

$$
y_{mir} = \mu + m_i + c_{mi} + \epsilon_{mir}
$$

- \( \mu + m_i \): Fixed effects.
- \( c_{mi} + \epsilon_{mir} \): Random effects (interaction and measurement error).

### Limits of Agreement (LoA)
The Limits of Agreement can be calculated using the formula:

$$
1 - 2 \cdot 1.96 \cdot \sigma + \sigma_1^2 + \sigma_2^2
$$

---

## Case Studies
1. **Fat Dataset** (Carstensen's case study).
2. **Oximetry Dataset**:
   - LoAs with an interaction term: **(-9.87, 14.81)**.
   - LoAs without an interaction term: **(-12.18, 17.12)**.

---

## Variability Tests
Proposed by **Roy (2009)** and implemented in R using the `anova()` function in the **NLME** package. Three primary tests are included:

1. **Between-Subject Variability**: Compares variability across individuals.
2. **Within-Subject Variability**: Assesses consistency within individuals.
3. **Overall Variability**: Computes the coefficient of repeatability for both methods.

---

## Expansion to Three-Method Case
When expanding from two to three methods, consider the variance-covariance (VC) structure:

- **Compound Symmetric**: \( x^2 = y^2 = z^2 \)
- **Symmetric**: More general variance specification.

---

## Residuals in LME Models
Three types of residuals are defined:
1. **Marginal Residuals**: Difference between observed data and estimated marginal means.
2. **Model-Specified Residuals**: Based on GLS solutions.
3. **Full Conditional Residuals**: Difference between observed data and predicted observations.

### Case Deletion Diagnostics
- Efficient methods for refitting LME models.
- Desirable properties of residuals include diagnostic influence measures for subsets and single observations (**Schabenberger, 2004**).



## Citations
1. Bland, J. M., & Altman, D. G. (1999). Limits of Agreement.
2. BXC (2008). Prediction Intervals for Method Comparison Studies.
3. Hamlett, A. (Advisory on Handling Replicate Measurements).
4. Roy, A. (Variability Tests and LME Models for Method Comparison).
5. Carstensen, B. (Oximetry Data Set Study).
6. Schabenberger, O. (2004). Influence Diagnostics in Residuals.
```

This markdown format organizes the content systematically while maintaining clarity. The citations are consolidated at the end for ease of reference. Let me know if you’d like more refinements!


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


