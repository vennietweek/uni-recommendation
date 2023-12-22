# University Recommendation System using US College Scorecard Dataset

## Project Information

This was a school project done for my Fundamentals of Data Analytics course. We were tasked to use the US College Scorecard dataset.

I collaborated with @lmngxn on this project, who did a large portion of the data preprocessing, regression model selection and testing, and refinement of the recommendation system.

My main contributions:
* Ideating on how we would use the US College Scorecard dataset, coming up with the objectives and requirements of the recommendation system
* Formulating the 2-step model approach to work with how the data was structured. We first used an unsupervised classification model to predict schools a student can consider based on their profile, then used a regression model to predict earnings based on the aggregated feature vectors of the schools. More details are below.
* Helping with data preprocessing (including feature encoding and scaling) and exploratory data analysis (feature correlation analysis, data visualisations)
* Training the classification model and building the foundations for the recommendation system

Project report: [IT5006 Project Report.pdf](https://github.com/vennietweek/uni-recommendation/files/13748350/IT5006.Project.Report.pdf)

## Objective

Develop a recommendation engine to help students make better-informed decisions on their higher education options. 

## Outcomes

Our recommendation engine takes in a student’s profile, which includes their SAT scores, race, family income, desired field of study, desired region and desired locale, and provides a list of recommended universities that best fit their profiles, as well as their projected earnings from this selection of schools.

## Dataset

We used data from the College Scorecard dataset, which contains a wide range of information on colleges and universities in the United States. Their are two main datasets, the School and Student dataset. https://collegescorecard.ed.gov/

## Approach
Our main challenge was in matching the disparate 'School' and 'Student' datasets, as both contained different data fields.

1. **Train a regression model using university-specific data to predict earnings**: We first train a regression model using university-specific data i.e. the ‘School’ dataset, with earnings as the target. Features include Admission Rate, Average SAT score, Completion rate, Demographics (Percentage of each race in institution), Parents’ education, Full-time Faculty Rate, Expenditures per student, Faculty salary, Locale and Region. The regression model will thus be built based on all the colleges within the dataset.
2. **Train a classification model using student-specific data to find the most similar colleges based on a student’s profile**: We trained the K-Nearest Neighbours model using student-specific data such as SAT score, race, family income, parents’ education levels, desired field of study, desired region of study (e.g. Southwest, Northeast) and desired locale of study (e.g. City, Suburb). After filtering out schools that fit the student’s preferences (i.e. field, region and locale of study), the model will be trained using the remaining features i.e. the ‘Student’ dataset, and will provide a list of most similar schools based on the student’s profile.
3. **Combine the 2 models to predict earnings based on a student’s recommended colleges**: When a student provides their inputs, we first use the clustering model to provide a list of similar schools. From the list of schools, we then generate an aggregated feature vector that can be fitted into the regression model to predict the student’s projected earnings.
<img width="1172" alt="Screenshot 2023-10-12 at 8 44 40 PM" src="https://github.com/vennietweek/uni-recommendation/assets/19652161/a1f63545-5249-41b8-be0a-7b8e41d32ef6">
