# Student Grading Prediction

## Overview

Welcome to the *"Predicting Your Future Grade"* project! This model attempts to predict the grade of students based on their attendance, assignments, quiz scores, and other fun academic details. If you’ve ever wondered if you could predict your grade just from your *study hours per week* (or lack thereof), this is the project for you. Using a **Random Forest Classifier**, this model gives a non-judgmental glimpse into the future of your academic performance.

The project uses **SMOTE** (no, not the fun kind) to balance class distributions because life isn’t always fair, and sometimes, data isn't either. It’s a journey through data preprocessing, feature engineering, and a sprinkling of machine learning magic.

## Dataset

The dataset we’re using is the *Students_Grading_Dataset.csv*. This treasure trove includes the following columns:

- **Grade**: The grade the student receives (the thing we’re predicting).
- **Gender**: Gender of the student (because, well, it’s 2025, and it’s still relevant).
- **Department**: The department the student belongs to.
- **Extracurricular_Activities**: Whether the student is socially active or spending too much time studying.
- **Parent_Education_Level**: What’s your excuse for your grades? Just kidding—this measures the education level of the student’s parent.
- **Age**: Student’s age. Because, shockingly, older students might actually have better grades.
- **Attendance (%)**: How often the student showed up to class (spoiler: higher attendance usually helps).
- **Midterm_Score**: The dreaded midterm score.
- **Final_Score**: The final exam score, aka the "make or break" moment.
- **Assignments_Avg**: Average assignment score. Let’s hope you actually handed them in on time.
- **Quizzes_Avg**: Average quiz score. No pressure, but quizzes are important.
- **Participation_Score**: How much you talk in class. Or, if you're like me, how much you just pretend to listen.
- **Projects_Score**: The score based on projects. Remember those? The ones that eat up your weekends.
- **Study_Hours_per_Week**: The number of hours a student spends studying per week. Or the number of hours you wish you were studying.

## Data Preprocessing

The dataset was… not exactly perfect. We had to do some cleaning, like:
- **Missing Values**: Because, let’s face it, not everything in life is neatly filled in. So:
  - **Attendance (%)**: Filled with the mean (because that’s what everyone else is doing).
  - **Assignments_Avg**: Filled with the median (because the mean is *so* mainstream).
  - **Parent_Education_Level**: Filled with the mode (because apparently, there’s one “most popular” level).

- **Feature Selection**: The dataset got split into numerical and categorical features (because everything in life needs boundaries).

- **Scaling and Encoding**: 
  - Numerical features were standardized because who doesn’t love a good scale? 
  - Categorical features were encoded, turning words into numbers because computers don’t understand our human languages.

- **SMOTE**: Synthetic Minority Over-sampling Technique (SMOTE) was applied because the model was feeling a little lonely with some of the classes underrepresented. SMOTE creates fake data to keep things fair.

## Model Training and Evaluation

1. **Random Forest Classifier**: The model was trained using **Random Forest**. Why? Because trees are cool. Plus, the forest looks at lots of data points to make decisions, just like a really overthinking student.

2. **Evaluation Metrics**:
   - **Classification Report**: Gives you precision, recall, and F1-scores, so you can feel better about your model’s ability to distinguish between grades, even if it’s still unsure about that "B."
   - **ROC-AUC Score**: Measures the overall ability of the model to distinguish between classes. Spoiler alert: This one’s good, around 0.88. Nice, right?

### Sample Output

```bash
Classification Report: 
              precision    recall  f1-score   support

           A       0.67      0.61      0.64       299
           B       0.67      0.47      0.55       299
           C       0.62      0.68      0.65       299
           D       0.59      0.72      0.65       299
           F       0.63      0.69      0.66       299

    accuracy                           0.63      1495
   macro avg       0.64      0.63      0.63      1495
weighted avg       0.64      0.63      0.63      1495

ROC-AUC Score:  0.876
