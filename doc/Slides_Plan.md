# Presentation Slides Organization

## 1. Introduction
It's an honor to be here and present this pilot study on GIS-based Multi-Criteria Decision Analysis for Deploying Electric Vehicle Supply Equipment in Philadelphia. 
My name is Emily and I am a first year Masters in City Planning student studying smart cities at University of Pennsylvania's graduate school of design. 

## 2. Motivations
I would like to start by talking about the motivations behind this work and GIS for smart cities planning in general. 
Philadelphia 


- Philadelphia has a number of initiatives to reduce emissions from vehicles and expand EV charging options. However, we still see a mismatch between the number of EVs and EV chargers available. 
- Philadelphia’s Office of Innovation and Technology is grappling with how to equitably roll out and maintain Electric Vehicle Supply Equipment (EVSE). But there are a lot of concerns to address: 
- A city is not a smart city if the technology only serves some of its residents. How do we ensure that our solution benefits residents outside of the primary economic hubs in the city. Are there ways we can deploy EVSE so they do more and serve more people? How do we ensure that chargers stay functional all the time? How do we minimize the cost and maximize the benefits? How do we prioritize where to implement EVSEs first?

Because the issue we are facing is complicated, with a lot of conflicting/competing interests at stake, and is geographic in nature, we adopted a GIS-based multi-criteria decision analysis to evaluate the suitablity of potential evse sites. 

## 3. Data
In this pilot study, our model considers key criteria ranging from socio-demographic indicators (population density, driving-age population, current ev owernship), existing infrastructure (spatial distribution of existing evse and accessibility), environment (available parking spaces, neighborhood safety, zoning restrictions), energy (power supply). These data were obtaiend from American Community Survey, Department of Energy, OpenStreetMap, and PECO...In the real world scenario, the inclusion of criteria is determined through stake holders meetings. 


## 4. Workflow
Specifically, we implemented our study in R and developed a five-step solution approach for this problem that considers geographic data models, spatial dimensions of the criteria and decision alternatives, and statistic models 

- create a fishnet for Philadelphia as the spatial unit for analysis and remove any water features. 
- preprocess the criteria. In particular, we computed the spatial accessibility of EVSEs using 2SFCA and distance to parking lots using k-nearest neighbor, etc. 
- transform criteria into this standard geographic unit. This include: aggregate or dissolve for nested relationship, area-weighted re-aggregation for un-nested relationship, count points within polygons. 
- transform criteria data into standard measuring unit. 
- prioritize the criteria using AHP and self-assigned weights. 
- ranking the potential sites using WSM, PROMETHEE, and TOPSIS. 

## 5. MCDA Method Used 
We have conducted the following analyses: 
- Self-assign weights directly and then use WSM, TOPSIS, and PROMETHEE to rank alternatives and compare the results. 
- Assign weights directly or use AHP to conduct pair-wise comparison across criteria and then use TOPSIS to rank the results. 

## 6. Weighted Sum Method 
The weighted sum method is the simplest and widely used method where each alternative is evaluated based on the sum of its weighted criteria scores. 

Our results shows that....

## 7. Classical TOPSIS Method
TOPSIS is based on the idea that the best alternative should have the shortest euclidean distance from the ideal solution and the farthest euclidean distance from the negative-ideal solution. For each alternative, relative closeness is measured as the degree of its closeness to the ideal solutions relative to the negtive ideal solution. 

Out resutls shows that....

## 8. PROMETHEE Method
The PROMETHEE is an outranking method that compares alternatives pairwise based on a set of criteria, considering the decision-maker's preferences with respect three metrics: a preference function, a preference threshold, and an indifference threshold. 

Our results shows that...

## 9. AHP Method 
The AHP method involves making pairwise comparisons between groups of criterias, using a scale to express relative importance. It then synthesize these individual weights to produce a overall weight for each criteria. 

Our results shows that....

## 10. Comparison - Ranking

Comparing the rank that each method give to the same grid, we found that:
- The differences in rank between weighted sum and promethee method is the smallest. 
- TOPSIS is leading to rank reversal issues for some parts of Philadelphia. In other word, a few grids that were ranked of lower priority in PROMETHEE and WSM are ranked of much high priority in TOPSIS and vice versa. Closer examination of these grids reveal that they are located in the outskirt of Philadelphia, mainly industrial areas that use a lot of electricty power. TOPSIS assumes that criteria are independent of each other. When a new alternative is introduced or an existing one is removed, the distance to the ideal and negative-ideal solutions can change. The presence of extreme values (very high or very low) can significantly influence the ideal and negative-ideal solutions. MCDA is sensitive to the quality of our data. 
- Assign weights directly has under-ranked several sites than using the AHP. 

## 11. Comparison - Method

WSM: easy to understand and implement, but assumes that criteria are independent of each other and ranking is highly dependent on the weights

TOPSIS: easy to understand and implement and is more comprehensive than the simple WSM, but it also assumes that criteria are independent of each other, is sensitive to rank reveral issues, and requires additional input froms stakeholders to decide upon the positive and negative ideal scenario. 

PROMETHEE: the most robust statistical mode, but requires careful selection of preference functions and preference function, indifference threshold 

AHP: breaks complex decisions into manageable part, but pairwise comparison can be subjective and biased  and that maintaining consistency in comparison can be challenging. 

## 12. Public Private Partnership

We decide to find places in Philadelphia that is consistently ranked as more suitable for new EVSE among all MCDA models. Through consulting the output of our  site visits, various stakeholder meetings, and budget considerations, we selected one of those sites in South Philadelphia and proposed a public-private partnership model between Philadelphia’s OIT and local grocery stores to install and maintain the EVSEs. We subsequently conducted financial analyses for the cost and revenue of breakdowns and designed a phased implementation of EVSE infrastructure given the current site conditions. 

## 13. Conclusions
 

- GIS-based MCDA is a robust criteria based methodology that support multiple criteria and statistical models at once, which allows for more in-depth decision making in the planning field. 

- Our study demonstrate a spatially informed starting point to identify potential areas for new EVSE that contribute to Philadelphia's sustainable transportation goals. 

- However, our study also highlighted several challenges in using MCDA. This includes agreeing on the input criteria, the weighting schemes, and various other inputs required for MCDA models. Considering the number of goals for this particular decision, equity,sustainable transportation, affordability, etc.,  what should be included and how important they are become important questions to consider and would significantly alter the result. 

- In addition, we would like to point out that there's no perfect decision making model. Methods that are more comprehensive and robust mathematically 1) requires more decision inputs, which is more time consuming, introduces more inconsistencies from stakeholders, and introduces more subjectivity 2) could be more computationally intensive, 3) less intuitive to non-experts. The best practice is to not rely on a single method in decision making. Beyond using MCDA models, it is essential to check the actual site condition before making final decisions. Note that there are things that spatial analysis cannot capture.

- Moreoever, our study have also highlighted several recurrent challenges in geospatial model for decision making. Specifically, the modifiable areal unit problem (MAUP) is a source of uncertainty, considering that out raw data all comes with different spatial unit and needs to be re-aggregated before proceed. In addition, ecological fallacy could be an issues as we are making inference about a small portion of the population using tract level statistics for the whole population.Moreover, errors and uncertainties may also arise when dealing with missing information, when we make assumptions/spatial interpolations about a neighboring grids' situation. 


## 14. Moving on

The use of a MCDM framework based on characterization of alternatives could inform short term choices considering known constraints and preferences. Moving forward, we would like to look for ways to bridge the gap between short term decision making and long-term planning in a context of rapidly changing projections regarding future states of EV usage/climate scenarios. We believe the innovation lies in developing a structured and replicable framework that can provide a model for other cities facing similar challenges. 



## 15. Acknowledgement

I would like to end by acknowlegde the support of Philadelphia's Office of Innovation Technology.....

## 16. End
List GitHub repository and email