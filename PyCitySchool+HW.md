

```python
import csv
import pandas as pd
import numpy as np
```


```python
file_school = "schools_complete.csv"
file_stu = "students_complete.csv"

file_school_pd = pd.read_csv(file_school)
file_stu_pd = pd.read_csv(file_stu)
```


```python
file_stu_pd.head(10)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Bryan Miranda</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Sheena Carter</td>
      <td>F</td>
      <td>11th</td>
      <td>Huang High School</td>
      <td>82</td>
      <td>80</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Nicole Baker</td>
      <td>F</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>96</td>
      <td>69</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Michael Roth</td>
      <td>M</td>
      <td>10th</td>
      <td>Huang High School</td>
      <td>95</td>
      <td>87</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Matthew Greene</td>
      <td>M</td>
      <td>10th</td>
      <td>Huang High School</td>
      <td>96</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
file_school_pd.head(15)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
</div>




```python
schoolcount = file_school_pd["School ID"].count()
stucount = file_stu_pd["Student ID"].count()
totalbudget = file_school_pd["budget"].sum()
avgmathscore = file_stu_pd["math_score"].mean()
avgreadscore = file_stu_pd["reading_score"].mean()

pass_math = file_stu_pd.loc[file_stu_pd["math_score"] > 70,:]
pass_math_count = pass_math["name"].count()
perc_mathpass = pass_math_count / stucount *100

pass_read = file_stu_pd.loc[file_stu_pd["reading_score"] > 70,:]
pass_read_count = pass_read["name"].count()
perc_readpass = pass_read_count / stucount *100

overall_passrate = (perc_mathpass + perc_readpass) / 2

summary_data = pd.DataFrame({"Total Schools":[schoolcount],
                          "Total Students":[stucount],
                          "Total Budget": "$ "+ str(totalbudget),
                          "Average Math Score":[avgmathscore],
                          "Average Reading Score":[avgreadscore],
                          "Average Reading Score":[avgreadscore],
                          "% Passing Math":[perc_mathpass],
                          "% Passing Reading":[perc_readpass],
                          "% Overall Passing Rate":[overall_passrate]
                          })

summary_data
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>% Overall Passing Rate</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Total Budget</th>
      <th>Total Schools</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>77.681899</td>
      <td>72.392137</td>
      <td>82.971662</td>
      <td>78.985371</td>
      <td>81.87784</td>
      <td>$ 24649428</td>
      <td>15</td>
      <td>39170</td>
    </tr>
  </tbody>
</table>
</div>




```python
#pass rates
file_stu_pd['Math_Pass'] = np.where(file_stu_pd['math_score'] >= 70, 1, 0)
file_stu_pd['Reading_Pass'] = np.where(file_stu_pd['reading_score'] >= 70, 1, 0)

#read and math score grades and average pass rates
score_df = pd.DataFrame(file_stu_pd.groupby("school")["reading_score","math_score", "Reading_Pass","Math_Pass"].mean())

score_df.reset_index(inplace=True)

score_df["Overall Pass Rate"] = ( score_df["Reading_Pass"] + score_df["Math_Pass"] ) /2

score_df.columns = ['name', 'Avg Reading Score', 'Avg Math Score', 'Reading Pass Rate', 'Math Pass Rate','Overall Pass Rate']


#school infos
file_school_pd["Per Student Budget"] = file_school_pd["budget"]/file_school_pd["size"]

#merge
summary_merge_df = pd.merge(file_school_pd,score_df,  on="name")

del summary_merge_df['School ID']

summary_merge_df = summary_merge_df.set_index("name")

del summary_merge_df.index.name

summary_merge_df['Reading Pass Rate'] = summary_merge_df['Reading Pass Rate']*100
summary_merge_df['Math Pass Rate'] = summary_merge_df['Math Pass Rate']*100
summary_merge_df['Overall Pass Rate'] = summary_merge_df['Overall Pass Rate']*100

summary_merge_df.columns = ['School Type','Total Students', 'Total School Budget', 'Per Student Budget',
                            'Average Reading Score', 'Average Math Score', '% Passing Reading',
                            '% Passing Math','% Overall Passing Rate']

summary_merge_df.head(10)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Reading Score</th>
      <th>Average Math Score</th>
      <th>% Passing Reading</th>
      <th>% Passing Math</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>81.316421</td>
      <td>65.683922</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>80.739234</td>
      <td>65.988471</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>95.854628</td>
      <td>93.867121</td>
      <td>94.860875</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>80.862999</td>
      <td>66.752967</td>
      <td>73.807983</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>97.138965</td>
      <td>93.392371</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>96.539641</td>
      <td>93.867718</td>
      <td>95.203679</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>97.039828</td>
      <td>94.133477</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>81.933280</td>
      <td>66.680064</td>
      <td>74.306672</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>96.252927</td>
      <td>92.505855</td>
      <td>94.379391</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>95.945946</td>
      <td>94.594595</td>
      <td>95.270270</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Top 5 Schools
summary_merge_df = summary_merge_df.sort_values(["% Overall Passing Rate"], ascending=False)
summary_merge_df.head(5)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Reading Score</th>
      <th>Average Math Score</th>
      <th>% Passing Reading</th>
      <th>% Passing Math</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>97.039828</td>
      <td>94.133477</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>97.308869</td>
      <td>93.272171</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>95.945946</td>
      <td>94.594595</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>97.138965</td>
      <td>93.392371</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>96.539641</td>
      <td>93.867718</td>
      <td>95.203679</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Bottom 5 Schools
summary_merge_df = summary_merge_df.sort_values(["% Overall Passing Rate"], ascending=True)
summary_merge_df.head(5)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Reading Score</th>
      <th>Average Math Score</th>
      <th>% Passing Reading</th>
      <th>% Passing Math</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>80.220055</td>
      <td>66.366592</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>80.739234</td>
      <td>65.988471</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>81.316421</td>
      <td>65.683922</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>81.222432</td>
      <td>66.057551</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>79.299014</td>
      <td>68.309602</td>
      <td>73.804308</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Read Scores by Grade
read_table = pd.pivot_table(file_stu_pd, values='reading_score', index=['school'],columns=['grade'], aggfunc=np.mean)

del read_table.index.name

read_table.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>grade</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
      <th>9th</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
      <td>81.303155</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
      <td>83.676136</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
      <td>81.198598</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
      <td>80.632653</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
      <td>83.369193</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Math Scores by Grade
math_table = pd.pivot_table(file_stu_pd, values='math_score', index=['school'],columns=['grade'], aggfunc=np.mean)

del math_table.index.name

math_table.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>grade</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
      <th>9th</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
      <td>77.083676</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
      <td>83.094697</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
      <td>76.403037</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
      <td>77.361345</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
      <td>82.044010</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Binning Spendings

spend_bins = [0,500000, 1000000, 2000000, 4000000]
spend_bins_label = ['< 500k','< 1m', '< 2m', '< 4m']

pd.cut(file_school_pd ["budget"],spend_bins,labels=spend_bins_label)

file_school_pd ['BudgetBin'] = pd.cut(file_school_pd["budget"],spend_bins,labels=spend_bins_label)

merged_data = pd.merge(file_stu_pd,file_school_pd, left_on = 'school', right_on ='name')

spending_summary_df = pd.DataFrame(merged_data.groupby("BudgetBin")["reading_score","math_score", "Reading_Pass","Math_Pass"].mean())

spending_summary_df.reset_index(inplace=True)

spending_summary_df["Overall Pass Rate"] = (spending_summary_df["Reading_Pass"] + spending_summary_df["Math_Pass"] ) /2

spending_summary_df.columns = ['name', 'Avg Reading Score', 'Avg Math Score', 'Reading Pass Rate', 'Math Pass Rate','Overall Pass Rate']

spending_summary_df = spending_summary_df.set_index("name")

del spending_summary_df.index.name

spending_summary_df['Reading Pass Rate'] = spending_summary_df['Reading Pass Rate']*100
spending_summary_df['Math Pass Rate'] = spending_summary_df['Math Pass Rate']*100
spending_summary_df['Overall Pass Rate'] = spending_summary_df['Overall Pass Rate']*100

spending_summary_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avg Reading Score</th>
      <th>Avg Math Score</th>
      <th>Reading Pass Rate</th>
      <th>Math Pass Rate</th>
      <th>Overall Pass Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt; 500k</th>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>96.252927</td>
      <td>92.505855</td>
      <td>94.379391</td>
    </tr>
    <tr>
      <th>&lt; 1m</th>
      <td>83.906996</td>
      <td>83.544856</td>
      <td>96.666667</td>
      <td>93.868313</td>
      <td>95.267490</td>
    </tr>
    <tr>
      <th>&lt; 2m</th>
      <td>82.529094</td>
      <td>80.213577</td>
      <td>88.897559</td>
      <td>80.721213</td>
      <td>84.809386</td>
    </tr>
    <tr>
      <th>&lt; 4m</th>
      <td>80.928365</td>
      <td>77.070764</td>
      <td>81.106091</td>
      <td>66.468891</td>
      <td>73.787491</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Binning Size

size_bins = [0,1000, 2500, 5000]
size_bins_label = ['< 1000','< 2500', '< 5000']

pd.cut(merged_data["size"],size_bins,labels=size_bins_label)

merged_data['SizeBin'] = pd.cut(merged_data["size"],size_bins,labels=size_bins_label)

size_summary_df = pd.DataFrame(merged_data.groupby("SizeBin")["reading_score","math_score", "Reading_Pass","Math_Pass"].mean())

size_summary_df.reset_index(inplace=True)

size_summary_df["Overall Pass Rate"] = (size_summary_df["Reading_Pass"] + size_summary_df["Math_Pass"] ) /2

size_summary_df.columns = ['name', 'Avg Reading Score', 'Avg Math Score', 'Reading Pass Rate', 'Math Pass Rate','Overall Pass Rate']

size_summary_df = size_summary_df.set_index("name")

del size_summary_df.index.name

size_summary_df['Reading Pass Rate'] = size_summary_df['Reading Pass Rate']*100
size_summary_df['Math Pass Rate'] = size_summary_df['Math Pass Rate']*100
size_summary_df['Overall Pass Rate'] = size_summary_df['Overall Pass Rate']*100

size_summary_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avg Reading Score</th>
      <th>Avg Math Score</th>
      <th>Reading Pass Rate</th>
      <th>Math Pass Rate</th>
      <th>Overall Pass Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt; 1000</th>
      <td>83.974082</td>
      <td>83.828654</td>
      <td>96.040317</td>
      <td>93.952484</td>
      <td>94.996400</td>
    </tr>
    <tr>
      <th>&lt; 2500</th>
      <td>83.893660</td>
      <td>83.351874</td>
      <td>96.723739</td>
      <td>93.669597</td>
      <td>95.196668</td>
    </tr>
    <tr>
      <th>&lt; 5000</th>
      <td>80.962485</td>
      <td>76.987026</td>
      <td>80.905249</td>
      <td>66.518387</td>
      <td>73.711818</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Grouping Type

type_summary_df = pd.DataFrame(merged_data.groupby("type")["reading_score","math_score", "Reading_Pass","Math_Pass"].mean())

type_summary_df.reset_index(inplace=True)

type_summary_df["Overall Pass Rate"] = (type_summary_df["Reading_Pass"] + type_summary_df["Math_Pass"] ) /2

type_summary_df.columns = ['name', 'Avg Reading Score', 'Avg Math Score', 'Reading Pass Rate', 'Math Pass Rate','Overall Pass Rate']

type_summary_df = type_summary_df.set_index("name")

del type_summary_df.index.name

type_summary_df['Reading Pass Rate'] = type_summary_df['Reading Pass Rate']*100
type_summary_df['Math Pass Rate'] = type_summary_df['Math Pass Rate']*100
type_summary_df['Overall Pass Rate'] = type_summary_df['Overall Pass Rate']*100

type_summary_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avg Reading Score</th>
      <th>Avg Math Score</th>
      <th>Reading Pass Rate</th>
      <th>Math Pass Rate</th>
      <th>Overall Pass Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>83.902821</td>
      <td>83.406183</td>
      <td>96.645891</td>
      <td>93.701821</td>
      <td>95.173856</td>
    </tr>
    <tr>
      <th>District</th>
      <td>80.962485</td>
      <td>76.987026</td>
      <td>80.905249</td>
      <td>66.518387</td>
      <td>73.711818</td>
    </tr>
  </tbody>
</table>
</div>


