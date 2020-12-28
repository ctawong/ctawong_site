---
layout: post
title: A Comparison of COVID-19 vaccines 
categories: biotechnology
permalink: articles/covid19-vaccines.html
excerpt: My notes on COVID-19 vaccines currently approved by FDA for emergence use.
author: Andrew Wong
comments: true
---

My notes on COVID-19 vaccines currently approved by FDA for emergence use.

**Table of Contents**
* TOC
{:toc}

# Summary

|     | Pfizer/BioNTech | Moderna |
| --- | --- | --- |
| Name | BNT162b2 | mRNA-1273 |
| Core technology | mRNA | mRNA |
| target | Optimized SARS-CoV-2 full-length spike glycoprotein |  Stabilized prefusion SARS-CoV-2 spike protein   |
| dosage | two doses, 3 weeks apart, 30 ug each | two doses, 3 weeks apart, 100 ug each |
| Storage technology |  [Lipid nanoparticles](https://www.technologyreview.com/2020/12/09/1013538/what-are-the-ingredients-of-pfizers-covid-19-vaccine/)   | Lipid nanoparticles, modified nuceltoides(?)[^m1] |
| Storage temperature | -80C | -20C |
| minimium order | 975 | 100 |
| Manufacturing capacity | 100 million doses by the end of 2020. 1.3 billion doses by the end of 2021 |  20 million doses by the end of 2020. 500 million in 2021    |
| Funding | Private | Public |
| Clincal trail ID | [NCT04368728](https://clinicaltrials.gov/ct2/show/NCT04368728) |  [NCT04470427](https://clinicaltrials.gov/ct2/show/NCT04470427)   |
| Safety |  Look for severe allgeric reaction to ingradient. [CDC Guideline](https://www.cdc.gov/coronavirus/2019-ncov/vaccines/recommendations/underlying-conditions.html)   | Look for severe allgeric reaction to ingradient. [CDC Guideline](https://www.cdc.gov/coronavirus/2019-ncov/vaccines/recommendations/underlying-conditions.html). [Severe allgeric reaction](https://thehill.com/homenews/state-watch/531710-boston-doctor-with-history-of-allergies-has-severe-reaction-to-moderna) in a patient with existing allergy condition |
| Efficacy | 95% @ 3 months | 95% @ 3 months |
| How long does it last| At least 3 months | At least 3 months |

Additional Source:  
- [Pfizer press release](https://www.pfizer.com/news/press-release/press-release-detail/pfizer-and-biontech-choose-lead-mrna-vaccine-candidate-0)  
- [CDC - Grading of Recommendations, Assessment, Development, and Evaluation (GRADE): Pfizer-BioNTech COVID-19 Vaccine](https://www.cdc.gov/vaccines/acip/recs/grade/covid-19-pfizer-biontech-vaccine.html)

[^m1]: [PNR News](https://www.npr.org/sections/health-shots/2020/11/17/935563377/why-does-pfizers-covid-19-vaccine-need-to-be-kept-colder-than-antarctic). Usage of modified nucleotide not comfirmed by Moderna.

The two vaccines are remarkably similar. Both are mRNA vaccines instead of traditional vaccines that are made from dead viruses. Both target the same spike protein. And unsurprisingly, the two have similar effectiveness. Both use lipid nanoparticle technology to stabilize the mRNA. For the difference in storage condition (-20C for Moderna vs -80C for BioNTech), it is unclear if Moderna has better lipid nanoparticle technology, or simply becasue BioNTech has not completed the temperature stability test to claim higher temperature.

# Efficacy

According to Moderna vaccine's Phase 3 clinical trial [design](https://clinicaltrials.gov/ct2/show/NCT04470427) and [result](https://www.nih.gov/news-events/news-releases/promising-interim-results-clinical-trial-nih-moderna-covid-19-vaccine): 
- 30,000 participants
    - 37% are from racial and ethnic minorities.
    - Healthy adults with high risks of contracting COVID19
- 95 cases of symptomatic COVID-19. 90 of the cases occurred in the placebo group and 5 occurred in the vaccinated group.
- 11 cases of severe COVID-19 out of the 95 total, all of which occurred in the placebo group.

Efficacy rate calcuation (Asumming equal split between vaccine and placebo groups):
- Vaccine attack rate (people who took the vaccine and got sick) = 5/15,000
- Unvaccined attack rate (pople who took the placebo and got sick) = 90/15,000
- Efficacy = (90-5)/90=94.4%

For the rest of people who do not show sympton, they could be
- uninfected
- infected but did not show symptom

So from this data, we cannot say how severe Covid-19 is.

From the calculation above, the efficacy can be interpreted as percentage of infection would have prevented if people are vaccinated. Note that it does not include the effect of herd immunity, where enough population is immune causing infection not be effectively transmitted.

# How long does it last

Moderna's Avian flu mRNA was shown to be effective [up to 6 months](https://www.sciencedirect.com/science/article/pii/S0264410X19305626) based on antibody persistence test. It is unclear if the test correlates perfectly with immune response to the virus, but is a good data point. From published data, Moderna's COVID-19 vaccine showed good antibody persistence up to [3 months](https://www.nejm.org/doi/full/10.1056/NEJMc2032195?query=RP), though the persistence dropped off faster for older people. To sum up, we have data to say it is the vaccine is at least good for 3 months, and is likely less effective in older people.

# Basic concepts
Below are some basic concepts to understand the biomedical literature.

## Binding vs neutralizing antibody

Binding antibody binds to virus but does not inactivating it. Neutralizing antibody binds to functional module of the virus and inactivates it.

## Pseudovirus neutralization assay

### Pseudovirus

> Compared with natural virus, the pseudovirus can only infect cells in a single round, has broad host range, high titer, and is not easily inactivated by serum complement. ([source](https://www.creative-diagnostics.com/sars-cov-2-pseudovirus-neutralization-assay.htm))

### Pseudovirus luciferase assay
Pseudovirus luciferase assay is used to measure antibody's ability to inhibit the virus's entry to the cell. Pseudovirus is engineered to express luciferase, a light emitting protein. If pseudovirus successfully enters a cell, we will see the interior of the cell lights up. The intensity is a proxy measure of the amount of virus entered a cell.

$ID_{50}$: is the fold of dilution of antibody that causes 50% reduction of the light signal in pseudovirus luciferase assay. It is a measure of antibody concentration in linear scale. The higher $ID_{50}$ value, the higher the antibody concentration.

**GMT**: [Geometric mean](https://en.wikipedia.org/wiki/Geometric_mean) [titer](#titer) is a measure of average concentration in titer of a group of samples.

### Titer

Titer is a measurement of concentration. It is used to measure an analyst together with a test that yields only positive and negative results. Titer is defined as the last fold of dilution that the test result is still positive. For example, titer of sample A is 8 and sample B is 4 below. The higher the titer, the higher the concentration.

| Serial Dilution | 1   | 2   | 3   | 4   |
| --- | --- | --- | --- | --- |
| concentration (fraction of original) | 1/2 | 1/4 | 1/8 | 1/16 |
| fold of diluton | 2   | 4   | 8   | 16  |
| Test result for sample A | Positive | Positive | **Positive** | Negative |
| Test result for sample B | Positive | **Positive** | Negative | Negative |

## Immunogen

An antigen that can induce immune response.

# Footnotes