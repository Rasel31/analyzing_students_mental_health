![Illustration of silhouetted heads](mentalhealth.jpg)

Does going to university in a different country affect your mental health? A Japanese international university surveyed its students in 2018 and published a study the following year that was approved by several ethical and regulatory boards.

The study found that international students have a higher risk of mental health difficulties than the general population, and that social connectedness (belonging to a social group) and acculturative stress (stress associated with joining a new culture) are predictive of depression.


Explore the `students` data using PostgreSQL to find out if you would come to a similar conclusion for international students and see if the length of stay is a contributing factor.

Here is a data description of the columns you may find helpful.

Explore and analyze the students data to see how the length of stay (stay) impacts the average mental health diagnostic scores of the international students present in the study.

| Field Name    | Description                                      |
| ------------- | ------------------------------------------------ |
| `inter_dom`     | Types of students (international or domestic)   |
| `japanese_cate` | Japanese language proficiency                    |
| `english_cate`  | English language proficiency                     |
| `academic`      | Current academic level (undergraduate or graduate) |
| `age`           | Current age of student                           |
| `stay`          | Current length of stay in years                  |
| `todep`         | Total score of depression (PHQ-9 test)           |
| `tosc`          | Total score of social connectedness (SCS test)   |
| `toas`          | Total score of acculturative stress (ASISS test) |


```python
-- Run this code to view the data in students
SELECT * 
FROM students;
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>inter_dom</th>
      <th>region</th>
      <th>gender</th>
      <th>academic</th>
      <th>age</th>
      <th>age_cate</th>
      <th>stay</th>
      <th>stay_cate</th>
      <th>japanese</th>
      <th>japanese_cate</th>
      <th>english</th>
      <th>english_cate</th>
      <th>intimate</th>
      <th>religion</th>
      <th>suicide</th>
      <th>dep</th>
      <th>deptype</th>
      <th>todep</th>
      <th>depsev</th>
      <th>tosc</th>
      <th>apd</th>
      <th>ahome</th>
      <th>aph</th>
      <th>afear</th>
      <th>acs</th>
      <th>aguilt</th>
      <th>amiscell</th>
      <th>toas</th>
      <th>partner</th>
      <th>friends</th>
      <th>parents</th>
      <th>relative</th>
      <th>profess</th>
      <th>phone</th>
      <th>doctor</th>
      <th>reli</th>
      <th>alone</th>
      <th>others</th>
      <th>internet</th>
      <th>partner_bi</th>
      <th>friends_bi</th>
      <th>parents_bi</th>
      <th>relative_bi</th>
      <th>professional_bi</th>
      <th>phone_bi</th>
      <th>doctor_bi</th>
      <th>religion_bi</th>
      <th>alone_bi</th>
      <th>others_bi</th>
      <th>internet_bi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Inter</td>
      <td>SEA</td>
      <td>Male</td>
      <td>Grad</td>
      <td>24.0</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>Long</td>
      <td>3.0</td>
      <td>Average</td>
      <td>5.0</td>
      <td>High</td>
      <td></td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>0.0</td>
      <td>Min</td>
      <td>34.0</td>
      <td>23.0</td>
      <td>9.0</td>
      <td>11.0</td>
      <td>8.0</td>
      <td>11.0</td>
      <td>2.0</td>
      <td>27.0</td>
      <td>91.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>6.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Inter</td>
      <td>SEA</td>
      <td>Male</td>
      <td>Grad</td>
      <td>28.0</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>Short</td>
      <td>4.0</td>
      <td>High</td>
      <td>4.0</td>
      <td>High</td>
      <td></td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>2.0</td>
      <td>Min</td>
      <td>48.0</td>
      <td>8.0</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>10.0</td>
      <td>39.0</td>
      <td>7.0</td>
      <td>7.0</td>
      <td>7.0</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Inter</td>
      <td>SEA</td>
      <td>Male</td>
      <td>Grad</td>
      <td>25.0</td>
      <td>4.0</td>
      <td>6.0</td>
      <td>Long</td>
      <td>4.0</td>
      <td>High</td>
      <td>4.0</td>
      <td>High</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>2.0</td>
      <td>Min</td>
      <td>41.0</td>
      <td>13.0</td>
      <td>4.0</td>
      <td>7.0</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>14.0</td>
      <td>51.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Inter</td>
      <td>EA</td>
      <td>Female</td>
      <td>Grad</td>
      <td>29.0</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>Short</td>
      <td>2.0</td>
      <td>Low</td>
      <td>3.0</td>
      <td>Average</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>3.0</td>
      <td>Min</td>
      <td>37.0</td>
      <td>16.0</td>
      <td>10.0</td>
      <td>10.0</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>21.0</td>
      <td>75.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Inter</td>
      <td>EA</td>
      <td>Female</td>
      <td>Grad</td>
      <td>28.0</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>Short</td>
      <td>1.0</td>
      <td>Low</td>
      <td>3.0</td>
      <td>Average</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>3.0</td>
      <td>Min</td>
      <td>37.0</td>
      <td>15.0</td>
      <td>12.0</td>
      <td>5.0</td>
      <td>8.0</td>
      <td>7.0</td>
      <td>4.0</td>
      <td>31.0</td>
      <td>82.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>281</th>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>128</td>
      <td>140</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>282</th>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>137</td>
      <td>131</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>283</th>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>66</td>
      <td>202</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>284</th>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>61</td>
      <td>207</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>285</th>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>NaN</td>
      <td></td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30</td>
      <td>238</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
<p>286 rows × 50 columns</p>
</div>


Return a table with nine rows and five columns.

The five columns should be aliased as: stay, count_int, average_phq, average_scs, and average_as, in that order.

The average columns should contain the average of the todep (PHQ-9 test), tosc (SCS test), and toas (ASISS test) columns for each length of stay, rounded to two decimal places.

The count_int column should be the number of international students for each length of stay.

Sort the results by the length of stay in descending order.

```python
-- Start coding here...
SELECT stay, COUNT(*) AS count_int, ROUND(AVG(todep), 2) AS average_phq, ROUND(AVG(tosc), 2) AS average_scs, ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE stay >= 1 AND inter_dom = 'Inter'
GROUP BY 1
ORDER BY 1 DESC;
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stay</th>
      <th>count_int</th>
      <th>average_phq</th>
      <th>average_scs</th>
      <th>average_as</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>1</td>
      <td>13.00</td>
      <td>32.00</td>
      <td>50.00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8</td>
      <td>1</td>
      <td>10.00</td>
      <td>44.00</td>
      <td>65.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>1</td>
      <td>4.00</td>
      <td>48.00</td>
      <td>45.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6</td>
      <td>3</td>
      <td>6.00</td>
      <td>38.00</td>
      <td>58.67</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>1</td>
      <td>0.00</td>
      <td>34.00</td>
      <td>91.00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>4</td>
      <td>14</td>
      <td>8.57</td>
      <td>33.93</td>
      <td>87.71</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>46</td>
      <td>9.09</td>
      <td>37.13</td>
      <td>78.00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>39</td>
      <td>8.28</td>
      <td>37.08</td>
      <td>77.67</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>95</td>
      <td>7.48</td>
      <td>38.11</td>
      <td>72.80</td>
    </tr>
  </tbody>
</table>
</div>



# Analytical Findings
Impact of Length of Stay on PHQ-9 Scores (Depression)

High PHQ-9 Scores: The highest PHQ-9 scores are observed for students with a length of stay of 10 years (13.00) and 8 years (10.00). This suggests that students who stay for longer periods may experience higher levels of depression.
Low PHQ-9 Scores: Conversely, students with shorter stays, such as 1 year (7.48) and 2 years (8.28), tend to have lower average PHQ-9 scores. This may indicate that shorter stays are associated with lower levels of depression.

Social Connectedness (SCS Scores)

The Social Connectedness Scale (SCS) scores vary across different lengths of stay. Notably, students with a stay of 7 years have the highest SCS scores (48.00), indicating a strong sense of belonging to social groups. On the other hand, students with a stay of 10 years have the lowest SCS scores (32.00), suggesting weaker social connections.

Acculturative Stress (ASISS Scores)

High ASISS Scores: Acculturative stress is highest for students with a stay of 5 years (91.00) and 4 years (87.71). This suggests that students in this mid-range length of stay may experience significant stress related to adapting to a new culture.

Lower ASISS Scores: Students with a stay of 1 year (72.80) and 7 years (45.00) have lower ASISS scores, indicating lower levels of acculturative stress.

Count of International Students

Higher Counts for Short Stays: The count of international students is highest for shorter stays, with 95 students for a stay of 1 year and 46 students for a stay of 3 years. This indicates that a larger number of students tend to stay for shorter periods.

Lower Counts for Longer Stays: The count of students decreases as the length of stay increases, with only 1 student each for stays of 10, 8, 7, and 5 years. This suggests that fewer students opt for longer stays.
# Key Interpretations
Increased Risk of Mental Health Difficulties: The data aligns with the study's conclusion that international students have a higher risk of mental health difficulties, with longer stays potentially exacerbating symptoms of depression.

Social Connectedness: Social connectedness varies significantly with the length of stay. Strong social connections appear to develop at specific intervals (e.g., 7 years), while weaker connections are observed for very long stays (e.g., 10 years).

Acculturative Stress: Acculturative stress is notably higher for students with mid-range stays (4-5 years), indicating that this period may be particularly challenging for adapting to a new culture.
# Recommendations
Support Systems: Universities should implement support systems to help international students build strong social connections, especially for those with longer stays.

Mental Health Resources: Providing accessible mental health resources and counseling services can help mitigate the risk of depression among international students.

Cultural Adaptation Programs: Introducing cultural adaptation programs for students in the mid-range stay period (4-5 years) could help reduce acculturative stress and improve overall well-being.

```python

```
