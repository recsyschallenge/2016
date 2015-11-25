RecSys Challenge 2016
=====================

About: Job Recommendations (preliminary description)
--------------------------

**In short:** given a XING user, the goal is to predict those job postings that a user will click on. 

**In Detail:** XING is a social network for business. People use XING, for example, to find a job and 
recruiters use XING to find the right candidate for a job. At the moment, XING has more than 15 Million 
users and around 1 Million job postings on the platform. Given a user, the goal of the job 
recommendation system is to predict those job postings that are likely to be relevant to the user. 
In order to fulfill this task, various data sources can be exploited as listed below. 


Datasets (preliminary description)
---------

A more detailed description will follow soon.  

### Types of data sources

- **impressions** - which items were shown to which user at which point in time?
- **interactions** of the users - clicks on job postings
  + ID of the user (anonymized) who clicked
  + ID of the item (anonymized)
  + timestamp (Unix timestamp, rounded to 5 min)
- **details about users** (including details about social network size, work experience): 
  + ID of the user (anonymized)
  + jobrole ID 
  + career level ID (e.g. beginner, experienced, manager)
  + industry ID (IDs represent industries such as "Internet", "Automotive", "Finance")
  + discipline ID (IDs represent disciplines such as "Consulting", "HR", "Engineering & Technical")
  + number of contacts (ranges such as less than 10, 10-50)
  + estimated years of experience (ranges such as 2-5 years)
  + educational background ID (classes such as: no university degree, Bsc/Msc, doctor)
- **details about job postings** such as: 
  + ID of the job posting (anonymized)
  + jobrole ID (IDs represent job roles such as "Java Software Developer", "Account Manager", etc.)
  + tag IDs (also from full-text description) (IDs represent, for example, skills such as "Java", "Data mining", "Leadership", etc. but may also represent jobroles or other concepts that are mentioned in the text)
  + career level ID (e.g. beginner, experienced, manager) 
  + industry ID (IDs represent industries such as "Internet", "Automotive", "Finance")
  + discipline ID (IDs represent disciplines such as "Consulting", "HR", "Engineering & Technical")
  + location ID (city-level; IDs will follow a postal-code logic so that distances can be estimated)

### Sampling and Anonymization

The data that is provided is a sample of XING's dataset. XING users will be splitted into two groups A and B. 
The interactions and anonymized demographics about those users will be released. The dataset will moreover 
be enriched with a small percentage of fake users. Anonymization of profiles will be done by mapping 
jobroles, etc. into a numeric space and by using ranges for fields such as the number of contacts or years 
of experience. 

### Training data

**Current plan:** One large dataset that covers more than 20 Million interactions (possibly from a time period of around 6 months), 
more than 1 Million anonymized users and more than 500k job postings will be released for analysis and training. 


Procedure (preliminary description) 
-----------

We would like to do a mix of _"offline evaluation"_ and _"online evaluation"_. Details will follow soon. 


Organizers
-----------

- [Fabian Abel](http://fabianabel.de), [XING AG](https://xing.com)
- [Daniel Kohlsdorf](https://www.xing.com/profile/Daniel_Kohlsdorf), [XING AG](https://xing.com)
- [Martha Larson](http://homepage.tudelft.nl/q22t4/), [TU Delft](http://mmc.tudelft.nl/)
- ...

