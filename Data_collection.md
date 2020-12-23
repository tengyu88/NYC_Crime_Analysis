## Data collection


```python
import numpy as np
import types
import pandas as pd
from botocore.client import Config
import ibm_boto3

def __iter__(self): return 0

# @hidden_cell
# The following code accesses a file in your IBM Cloud Object Storage. It includes your credentials.
# You might want to remove those credentials before you share the notebook.
client_0d5ade0e1ec140c58bab5879c61d1360 = ibm_boto3.client(service_name='s3',
    ibm_api_key_id='MtNUSluFjvSGvegbym7xro3VlYrUW-SNYij5jT1hmbwR',
    ibm_auth_endpoint="https://iam.cloud.ibm.com/oidc/token",
    config=Config(signature_version='oauth'),
    endpoint_url='https://s3-api.us-geo.objectstorage.service.networklayer.com')

body = client_0d5ade0e1ec140c58bab5879c61d1360.get_object(Bucket='nyccrimeanalysis-donotdelete-pr-hixueakb9xdfua',Key='NYPD_Complaint_Data_Historic.csv')['Body']
# add missing __iter__ method, so pandas accepts body as file-like object
if not hasattr(body, "__iter__"): body.__iter__ = types.MethodType( __iter__, body )

df_data_1 = pd.read_csv(body)
df_data_1.head()
```

    /opt/conda/envs/Python-3.7-main/lib/python3.7/site-packages/IPython/core/interactiveshell.py:3063: DtypeWarning: Columns (18,20) have mixed types.Specify dtype option on import or set low_memory=False.
      interactivity=interactivity, compiler=compiler, result=result)





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
      <th>CMPLNT_NUM</th>
      <th>CMPLNT_FR_DT</th>
      <th>CMPLNT_FR_TM</th>
      <th>CMPLNT_TO_DT</th>
      <th>CMPLNT_TO_TM</th>
      <th>ADDR_PCT_CD</th>
      <th>RPT_DT</th>
      <th>KY_CD</th>
      <th>OFNS_DESC</th>
      <th>PD_CD</th>
      <th>...</th>
      <th>SUSP_SEX</th>
      <th>TRANSIT_DISTRICT</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Lat_Lon</th>
      <th>PATROL_BORO</th>
      <th>STATION_NAME</th>
      <th>VIC_AGE_GROUP</th>
      <th>VIC_RACE</th>
      <th>VIC_SEX</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>325341655</td>
      <td>02/11/2015</td>
      <td>15:00:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>73.0</td>
      <td>02/11/2015</td>
      <td>359</td>
      <td>OFFENSES AGAINST PUBLIC ADMINI</td>
      <td>749.0</td>
      <td>...</td>
      <td>M</td>
      <td>NaN</td>
      <td>40.664239</td>
      <td>-73.908425</td>
      <td>(40.664239422, -73.908425011)</td>
      <td>PATROL BORO BKLYN NORTH</td>
      <td>NaN</td>
      <td>&lt;18</td>
      <td>BLACK</td>
      <td>M</td>
    </tr>
    <tr>
      <th>1</th>
      <td>393816841</td>
      <td>03/17/2012</td>
      <td>10:30:00</td>
      <td>03/17/2012</td>
      <td>11:00:00</td>
      <td>69.0</td>
      <td>03/17/2012</td>
      <td>344</td>
      <td>ASSAULT 3 &amp; RELATED OFFENSES</td>
      <td>114.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>40.644590</td>
      <td>-73.892672</td>
      <td>(40.644589618, -73.892672426)</td>
      <td>PATROL BORO BKLYN SOUTH</td>
      <td>NaN</td>
      <td>45-64</td>
      <td>BLACK</td>
      <td>F</td>
    </tr>
    <tr>
      <th>2</th>
      <td>802896158</td>
      <td>10/27/2016</td>
      <td>13:48:00</td>
      <td>11/03/2016</td>
      <td>13:49:00</td>
      <td>71.0</td>
      <td>11/03/2016</td>
      <td>578</td>
      <td>HARRASSMENT 2</td>
      <td>638.0</td>
      <td>...</td>
      <td>M</td>
      <td>NaN</td>
      <td>40.658758</td>
      <td>-73.942435</td>
      <td>(40.658758183, -73.942434788)</td>
      <td>PATROL BORO BKLYN SOUTH</td>
      <td>NaN</td>
      <td>18-24</td>
      <td>BLACK</td>
      <td>M</td>
    </tr>
    <tr>
      <th>3</th>
      <td>633812343</td>
      <td>11/27/2014</td>
      <td>19:00:00</td>
      <td>11/27/2014</td>
      <td>22:30:00</td>
      <td>112.0</td>
      <td>11/28/2014</td>
      <td>104</td>
      <td>RAPE</td>
      <td>157.0</td>
      <td>...</td>
      <td>M</td>
      <td>NaN</td>
      <td>40.722364</td>
      <td>-73.851474</td>
      <td>(40.722363687, -73.851473894)</td>
      <td>PATROL BORO QUEENS NORTH</td>
      <td>NaN</td>
      <td>25-44</td>
      <td>WHITE</td>
      <td>F</td>
    </tr>
    <tr>
      <th>4</th>
      <td>300349533</td>
      <td>12/11/2013</td>
      <td>13:30:00</td>
      <td>12/11/2013</td>
      <td>14:15:00</td>
      <td>24.0</td>
      <td>12/12/2013</td>
      <td>109</td>
      <td>GRAND LARCENY</td>
      <td>438.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>40.793465</td>
      <td>-73.968950</td>
      <td>(40.793464597, -73.968949638)</td>
      <td>PATROL BORO MAN NORTH</td>
      <td>NaN</td>
      <td>45-64</td>
      <td>WHITE</td>
      <td>F</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 35 columns</p>
</div>




```python

```


```python
# convert date to pandas datetime type
df_data_1['CMPLNT_DATE'] = pd.to_datetime(df_data_1['CMPLNT_FR_DT'], errors = 'coerce')
df_data_1.dropna(subset=['CMPLNT_DATE'], inplace=True)
df_data_1.head()
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
      <th>CMPLNT_NUM</th>
      <th>CMPLNT_FR_DT</th>
      <th>CMPLNT_FR_TM</th>
      <th>CMPLNT_TO_DT</th>
      <th>CMPLNT_TO_TM</th>
      <th>ADDR_PCT_CD</th>
      <th>RPT_DT</th>
      <th>KY_CD</th>
      <th>OFNS_DESC</th>
      <th>PD_CD</th>
      <th>...</th>
      <th>TRANSIT_DISTRICT</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Lat_Lon</th>
      <th>PATROL_BORO</th>
      <th>STATION_NAME</th>
      <th>VIC_AGE_GROUP</th>
      <th>VIC_RACE</th>
      <th>VIC_SEX</th>
      <th>CMPLNT_DATE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>325341655</td>
      <td>02/11/2015</td>
      <td>15:00:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>73.0</td>
      <td>02/11/2015</td>
      <td>359</td>
      <td>OFFENSES AGAINST PUBLIC ADMINI</td>
      <td>749.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>40.664239</td>
      <td>-73.908425</td>
      <td>(40.664239422, -73.908425011)</td>
      <td>PATROL BORO BKLYN NORTH</td>
      <td>NaN</td>
      <td>&lt;18</td>
      <td>BLACK</td>
      <td>M</td>
      <td>2015-02-11</td>
    </tr>
    <tr>
      <th>1</th>
      <td>393816841</td>
      <td>03/17/2012</td>
      <td>10:30:00</td>
      <td>03/17/2012</td>
      <td>11:00:00</td>
      <td>69.0</td>
      <td>03/17/2012</td>
      <td>344</td>
      <td>ASSAULT 3 &amp; RELATED OFFENSES</td>
      <td>114.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>40.644590</td>
      <td>-73.892672</td>
      <td>(40.644589618, -73.892672426)</td>
      <td>PATROL BORO BKLYN SOUTH</td>
      <td>NaN</td>
      <td>45-64</td>
      <td>BLACK</td>
      <td>F</td>
      <td>2012-03-17</td>
    </tr>
    <tr>
      <th>2</th>
      <td>802896158</td>
      <td>10/27/2016</td>
      <td>13:48:00</td>
      <td>11/03/2016</td>
      <td>13:49:00</td>
      <td>71.0</td>
      <td>11/03/2016</td>
      <td>578</td>
      <td>HARRASSMENT 2</td>
      <td>638.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>40.658758</td>
      <td>-73.942435</td>
      <td>(40.658758183, -73.942434788)</td>
      <td>PATROL BORO BKLYN SOUTH</td>
      <td>NaN</td>
      <td>18-24</td>
      <td>BLACK</td>
      <td>M</td>
      <td>2016-10-27</td>
    </tr>
    <tr>
      <th>3</th>
      <td>633812343</td>
      <td>11/27/2014</td>
      <td>19:00:00</td>
      <td>11/27/2014</td>
      <td>22:30:00</td>
      <td>112.0</td>
      <td>11/28/2014</td>
      <td>104</td>
      <td>RAPE</td>
      <td>157.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>40.722364</td>
      <td>-73.851474</td>
      <td>(40.722363687, -73.851473894)</td>
      <td>PATROL BORO QUEENS NORTH</td>
      <td>NaN</td>
      <td>25-44</td>
      <td>WHITE</td>
      <td>F</td>
      <td>2014-11-27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>300349533</td>
      <td>12/11/2013</td>
      <td>13:30:00</td>
      <td>12/11/2013</td>
      <td>14:15:00</td>
      <td>24.0</td>
      <td>12/12/2013</td>
      <td>109</td>
      <td>GRAND LARCENY</td>
      <td>438.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>40.793465</td>
      <td>-73.968950</td>
      <td>(40.793464597, -73.968949638)</td>
      <td>PATROL BORO MAN NORTH</td>
      <td>NaN</td>
      <td>45-64</td>
      <td>WHITE</td>
      <td>F</td>
      <td>2013-12-11</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 36 columns</p>
</div>




```python
df_data_1.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 6982397 entries, 0 to 6983206
    Data columns (total 36 columns):
     #   Column             Dtype         
    ---  ------             -----         
     0   CMPLNT_NUM         int64         
     1   CMPLNT_FR_DT       object        
     2   CMPLNT_FR_TM       object        
     3   CMPLNT_TO_DT       object        
     4   CMPLNT_TO_TM       object        
     5   ADDR_PCT_CD        float64       
     6   RPT_DT             object        
     7   KY_CD              int64         
     8   OFNS_DESC          object        
     9   PD_CD              float64       
     10  PD_DESC            object        
     11  CRM_ATPT_CPTD_CD   object        
     12  LAW_CAT_CD         object        
     13  BORO_NM            object        
     14  LOC_OF_OCCUR_DESC  object        
     15  PREM_TYP_DESC      object        
     16  JURIS_DESC         object        
     17  JURISDICTION_CODE  float64       
     18  PARKS_NM           object        
     19  HADEVELOPT         object        
     20  HOUSING_PSA        object        
     21  X_COORD_CD         float64       
     22  Y_COORD_CD         float64       
     23  SUSP_AGE_GROUP     object        
     24  SUSP_RACE          object        
     25  SUSP_SEX           object        
     26  TRANSIT_DISTRICT   float64       
     27  Latitude           float64       
     28  Longitude          float64       
     29  Lat_Lon            object        
     30  PATROL_BORO        object        
     31  STATION_NAME       object        
     32  VIC_AGE_GROUP      object        
     33  VIC_RACE           object        
     34  VIC_SEX            object        
     35  CMPLNT_DATE        datetime64[ns]
    dtypes: datetime64[ns](1), float64(8), int64(2), object(25)
    memory usage: 1.9+ GB



```python
# get the year and month info for further use
df_data_1['CMPLNT_YEAR']=df_data_1['CMPLNT_DATE'].map(lambda x:x.strftime('%Y')).astype(int)
df_data_1['CMPLNT_MONTH']=df_data_1['CMPLNT_DATE'].map(lambda x:x.strftime('%m')).astype(int)
df_data_1.head()
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
      <th>CMPLNT_NUM</th>
      <th>CMPLNT_FR_DT</th>
      <th>CMPLNT_FR_TM</th>
      <th>CMPLNT_TO_DT</th>
      <th>CMPLNT_TO_TM</th>
      <th>ADDR_PCT_CD</th>
      <th>RPT_DT</th>
      <th>KY_CD</th>
      <th>OFNS_DESC</th>
      <th>PD_CD</th>
      <th>...</th>
      <th>Longitude</th>
      <th>Lat_Lon</th>
      <th>PATROL_BORO</th>
      <th>STATION_NAME</th>
      <th>VIC_AGE_GROUP</th>
      <th>VIC_RACE</th>
      <th>VIC_SEX</th>
      <th>CMPLNT_DATE</th>
      <th>CMPLNT_YEAR</th>
      <th>CMPLNT_MONTH</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>325341655</td>
      <td>02/11/2015</td>
      <td>15:00:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>73.0</td>
      <td>02/11/2015</td>
      <td>359</td>
      <td>OFFENSES AGAINST PUBLIC ADMINI</td>
      <td>749.0</td>
      <td>...</td>
      <td>-73.908425</td>
      <td>(40.664239422, -73.908425011)</td>
      <td>PATROL BORO BKLYN NORTH</td>
      <td>NaN</td>
      <td>&lt;18</td>
      <td>BLACK</td>
      <td>M</td>
      <td>2015-02-11</td>
      <td>2015</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>393816841</td>
      <td>03/17/2012</td>
      <td>10:30:00</td>
      <td>03/17/2012</td>
      <td>11:00:00</td>
      <td>69.0</td>
      <td>03/17/2012</td>
      <td>344</td>
      <td>ASSAULT 3 &amp; RELATED OFFENSES</td>
      <td>114.0</td>
      <td>...</td>
      <td>-73.892672</td>
      <td>(40.644589618, -73.892672426)</td>
      <td>PATROL BORO BKLYN SOUTH</td>
      <td>NaN</td>
      <td>45-64</td>
      <td>BLACK</td>
      <td>F</td>
      <td>2012-03-17</td>
      <td>2012</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>802896158</td>
      <td>10/27/2016</td>
      <td>13:48:00</td>
      <td>11/03/2016</td>
      <td>13:49:00</td>
      <td>71.0</td>
      <td>11/03/2016</td>
      <td>578</td>
      <td>HARRASSMENT 2</td>
      <td>638.0</td>
      <td>...</td>
      <td>-73.942435</td>
      <td>(40.658758183, -73.942434788)</td>
      <td>PATROL BORO BKLYN SOUTH</td>
      <td>NaN</td>
      <td>18-24</td>
      <td>BLACK</td>
      <td>M</td>
      <td>2016-10-27</td>
      <td>2016</td>
      <td>10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>633812343</td>
      <td>11/27/2014</td>
      <td>19:00:00</td>
      <td>11/27/2014</td>
      <td>22:30:00</td>
      <td>112.0</td>
      <td>11/28/2014</td>
      <td>104</td>
      <td>RAPE</td>
      <td>157.0</td>
      <td>...</td>
      <td>-73.851474</td>
      <td>(40.722363687, -73.851473894)</td>
      <td>PATROL BORO QUEENS NORTH</td>
      <td>NaN</td>
      <td>25-44</td>
      <td>WHITE</td>
      <td>F</td>
      <td>2014-11-27</td>
      <td>2014</td>
      <td>11</td>
    </tr>
    <tr>
      <th>4</th>
      <td>300349533</td>
      <td>12/11/2013</td>
      <td>13:30:00</td>
      <td>12/11/2013</td>
      <td>14:15:00</td>
      <td>24.0</td>
      <td>12/12/2013</td>
      <td>109</td>
      <td>GRAND LARCENY</td>
      <td>438.0</td>
      <td>...</td>
      <td>-73.968950</td>
      <td>(40.793464597, -73.968949638)</td>
      <td>PATROL BORO MAN NORTH</td>
      <td>NaN</td>
      <td>45-64</td>
      <td>WHITE</td>
      <td>F</td>
      <td>2013-12-11</td>
      <td>2013</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 38 columns</p>
</div>




```python
# creat the dateframe which only contains the information we need
df_data = df_data_1[['CMPLNT_NUM', 'CMPLNT_DATE', 'CMPLNT_YEAR', 'CMPLNT_MONTH', 'OFNS_DESC', 'LAW_CAT_CD', 'BORO_NM', 'Latitude', 'Longitude', 'Lat_Lon']]
df_data.head()
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
      <th>CMPLNT_NUM</th>
      <th>CMPLNT_DATE</th>
      <th>CMPLNT_YEAR</th>
      <th>CMPLNT_MONTH</th>
      <th>OFNS_DESC</th>
      <th>LAW_CAT_CD</th>
      <th>BORO_NM</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Lat_Lon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>325341655</td>
      <td>2015-02-11</td>
      <td>2015</td>
      <td>2</td>
      <td>OFFENSES AGAINST PUBLIC ADMINI</td>
      <td>MISDEMEANOR</td>
      <td>BROOKLYN</td>
      <td>40.664239</td>
      <td>-73.908425</td>
      <td>(40.664239422, -73.908425011)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>393816841</td>
      <td>2012-03-17</td>
      <td>2012</td>
      <td>3</td>
      <td>ASSAULT 3 &amp; RELATED OFFENSES</td>
      <td>MISDEMEANOR</td>
      <td>BROOKLYN</td>
      <td>40.644590</td>
      <td>-73.892672</td>
      <td>(40.644589618, -73.892672426)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>802896158</td>
      <td>2016-10-27</td>
      <td>2016</td>
      <td>10</td>
      <td>HARRASSMENT 2</td>
      <td>VIOLATION</td>
      <td>BROOKLYN</td>
      <td>40.658758</td>
      <td>-73.942435</td>
      <td>(40.658758183, -73.942434788)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>633812343</td>
      <td>2014-11-27</td>
      <td>2014</td>
      <td>11</td>
      <td>RAPE</td>
      <td>FELONY</td>
      <td>QUEENS</td>
      <td>40.722364</td>
      <td>-73.851474</td>
      <td>(40.722363687, -73.851473894)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>300349533</td>
      <td>2013-12-11</td>
      <td>2013</td>
      <td>12</td>
      <td>GRAND LARCENY</td>
      <td>FELONY</td>
      <td>MANHATTAN</td>
      <td>40.793465</td>
      <td>-73.968950</td>
      <td>(40.793464597, -73.968949638)</td>
    </tr>
  </tbody>
</table>
</div>




```python
# reduce the amount of data, get data after year 2012

df_data.sort_values(by=['CMPLNT_DATE'], inplace=True)
df_data.reset_index(drop=True)
```

    /opt/conda/envs/Python-3.7-main/lib/python3.7/site-packages/ipykernel/__main__.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      if __name__ == '__main__':





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
      <th>CMPLNT_NUM</th>
      <th>CMPLNT_DATE</th>
      <th>CMPLNT_YEAR</th>
      <th>CMPLNT_MONTH</th>
      <th>OFNS_DESC</th>
      <th>LAW_CAT_CD</th>
      <th>BORO_NM</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Lat_Lon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>944477711</td>
      <td>1900-03-10</td>
      <td>1900</td>
      <td>3</td>
      <td>BURGLARY</td>
      <td>FELONY</td>
      <td>BROOKLYN</td>
      <td>40.646130</td>
      <td>-73.973227</td>
      <td>(40.646129746, -73.973227133)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>857331711</td>
      <td>1900-05-08</td>
      <td>1900</td>
      <td>5</td>
      <td>ASSAULT 3 &amp; RELATED OFFENSES</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.788861</td>
      <td>-73.952004</td>
      <td>(40.788861361, -73.95200411)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>346351111</td>
      <td>1900-08-06</td>
      <td>1900</td>
      <td>8</td>
      <td>FRAUDS</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.774602</td>
      <td>-73.945017</td>
      <td>(40.774602082, -73.94501725)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>130320181</td>
      <td>1900-08-07</td>
      <td>1900</td>
      <td>8</td>
      <td>BURGLARY</td>
      <td>FELONY</td>
      <td>BROOKLYN</td>
      <td>40.603887</td>
      <td>-73.942543</td>
      <td>(40.603887149, -73.942543318)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>667928187</td>
      <td>1900-11-26</td>
      <td>1900</td>
      <td>11</td>
      <td>HARRASSMENT 2</td>
      <td>VIOLATION</td>
      <td>MANHATTAN</td>
      <td>40.735323</td>
      <td>-73.984240</td>
      <td>(40.735323079, -73.984240111)</td>
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
    </tr>
    <tr>
      <th>6982392</th>
      <td>523951474</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>PETIT LARCENY</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.757396</td>
      <td>-73.969623</td>
      <td>(40.757396174000064, -73.96962338999998)</td>
    </tr>
    <tr>
      <th>6982393</th>
      <td>113819683</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>PETIT LARCENY</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.744173</td>
      <td>-73.993740</td>
      <td>(40.744173068000066, -73.99374010399998)</td>
    </tr>
    <tr>
      <th>6982394</th>
      <td>769376585</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>CRIMINAL MISCHIEF &amp; RELATED OF</td>
      <td>MISDEMEANOR</td>
      <td>QUEENS</td>
      <td>40.744057</td>
      <td>-73.891805</td>
      <td>(40.74405654700007, -73.89180486099997)</td>
    </tr>
    <tr>
      <th>6982395</th>
      <td>115473641</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>PETIT LARCENY</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.816801</td>
      <td>-73.947240</td>
      <td>(40.816800597000054, -73.94724037699996)</td>
    </tr>
    <tr>
      <th>6982396</th>
      <td>659647494</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>ASSAULT 3 &amp; RELATED OFFENSES</td>
      <td>MISDEMEANOR</td>
      <td>BRONX</td>
      <td>40.883125</td>
      <td>-73.879775</td>
      <td>(40.88312524200006, -73.87977465099993)</td>
    </tr>
  </tbody>
</table>
<p>6982397 rows × 10 columns</p>
</div>




```python
df_data=df_data.loc[df_data['CMPLNT_DATE'] > '2012-01-01']
df_data.reset_index(drop=True)
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
      <th>CMPLNT_NUM</th>
      <th>CMPLNT_DATE</th>
      <th>CMPLNT_YEAR</th>
      <th>CMPLNT_MONTH</th>
      <th>OFNS_DESC</th>
      <th>LAW_CAT_CD</th>
      <th>BORO_NM</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Lat_Lon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>408450072</td>
      <td>2012-01-02</td>
      <td>2012</td>
      <td>1</td>
      <td>OFF. AGNST PUB ORD SENSBLTY &amp;</td>
      <td>MISDEMEANOR</td>
      <td>BROOKLYN</td>
      <td>40.597121</td>
      <td>-73.941249</td>
      <td>(40.597120566, -73.941249217)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>114547452</td>
      <td>2012-01-02</td>
      <td>2012</td>
      <td>1</td>
      <td>BURGLARY</td>
      <td>FELONY</td>
      <td>QUEENS</td>
      <td>40.762102</td>
      <td>-73.820334</td>
      <td>(40.762101814, -73.820333596)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>579666649</td>
      <td>2012-01-02</td>
      <td>2012</td>
      <td>1</td>
      <td>ARSON</td>
      <td>FELONY</td>
      <td>BRONX</td>
      <td>40.851316</td>
      <td>-73.902117</td>
      <td>(40.851316088, -73.902116523)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>228510203</td>
      <td>2012-01-02</td>
      <td>2012</td>
      <td>1</td>
      <td>PETIT LARCENY</td>
      <td>MISDEMEANOR</td>
      <td>QUEENS</td>
      <td>40.709501</td>
      <td>-73.786483</td>
      <td>(40.709501076, -73.78648323)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>329522444</td>
      <td>2012-01-02</td>
      <td>2012</td>
      <td>1</td>
      <td>BURGLARY</td>
      <td>FELONY</td>
      <td>BROOKLYN</td>
      <td>40.668598</td>
      <td>-73.889725</td>
      <td>(40.668598196, -73.889724755)</td>
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
    </tr>
    <tr>
      <th>3846483</th>
      <td>523951474</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>PETIT LARCENY</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.757396</td>
      <td>-73.969623</td>
      <td>(40.757396174000064, -73.96962338999998)</td>
    </tr>
    <tr>
      <th>3846484</th>
      <td>113819683</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>PETIT LARCENY</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.744173</td>
      <td>-73.993740</td>
      <td>(40.744173068000066, -73.99374010399998)</td>
    </tr>
    <tr>
      <th>3846485</th>
      <td>769376585</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>CRIMINAL MISCHIEF &amp; RELATED OF</td>
      <td>MISDEMEANOR</td>
      <td>QUEENS</td>
      <td>40.744057</td>
      <td>-73.891805</td>
      <td>(40.74405654700007, -73.89180486099997)</td>
    </tr>
    <tr>
      <th>3846486</th>
      <td>115473641</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>PETIT LARCENY</td>
      <td>MISDEMEANOR</td>
      <td>MANHATTAN</td>
      <td>40.816801</td>
      <td>-73.947240</td>
      <td>(40.816800597000054, -73.94724037699996)</td>
    </tr>
    <tr>
      <th>3846487</th>
      <td>659647494</td>
      <td>2019-12-31</td>
      <td>2019</td>
      <td>12</td>
      <td>ASSAULT 3 &amp; RELATED OFFENSES</td>
      <td>MISDEMEANOR</td>
      <td>BRONX</td>
      <td>40.883125</td>
      <td>-73.879775</td>
      <td>(40.88312524200006, -73.87977465099993)</td>
    </tr>
  </tbody>
</table>
<p>3846488 rows × 10 columns</p>
</div>




```python
# save processed data to csv

from project_lib import Project
project = Project(project_id='ed0835f6-192e-41ad-a9c7-e66d5f9f9b68', project_access_token='p-32532cd1a9f2391e87790f9eb50d22c1d48f2275')
pc = project.project_context
project.save_data(data=df_data.to_csv(index=False),file_name='data1019.csv')
```


    ---------------------------------------------------------------------------

    KeyboardInterrupt                         Traceback (most recent call last)

    <ipython-input-8-1b67897710ca> in <module>
          4 project = Project(project_id='ed0835f6-192e-41ad-a9c7-e66d5f9f9b68', project_access_token='p-32532cd1a9f2391e87790f9eb50d22c1d48f2275')
          5 pc = project.project_context
    ----> 6 project.save_data(data=df_data.to_csv(index=False),file_name='data1019.csv')
    

    /opt/conda/envs/Python-3.7-main/lib/python3.7/site-packages/pandas/core/generic.py in to_csv(self, path_or_buf, sep, na_rep, float_format, columns, header, index, index_label, mode, encoding, compression, quoting, quotechar, line_terminator, chunksize, date_format, doublequote, escapechar, decimal)
       3202             decimal=decimal,
       3203         )
    -> 3204         formatter.save()
       3205 
       3206         if path_or_buf is None:


    /opt/conda/envs/Python-3.7-main/lib/python3.7/site-packages/pandas/io/formats/csvs.py in save(self)
        202             )
        203 
    --> 204             self._save()
        205 
        206         finally:


    /opt/conda/envs/Python-3.7-main/lib/python3.7/site-packages/pandas/io/formats/csvs.py in _save(self)
        323                 break
        324 
    --> 325             self._save_chunk(start_i, end_i)
        326 
        327     def _save_chunk(self, start_i: int, end_i: int) -> None:


    /opt/conda/envs/Python-3.7-main/lib/python3.7/site-packages/pandas/io/formats/csvs.py in _save_chunk(self, start_i, end_i)
        338                 decimal=self.decimal,
        339                 date_format=self.date_format,
    --> 340                 quoting=self.quoting,
        341             )
        342 


    /opt/conda/envs/Python-3.7-main/lib/python3.7/site-packages/pandas/core/internals/blocks.py in to_native_types(self, slicer, na_rep, date_format, quoting, **kwargs)
       2267             tz=getattr(self.values, "tz", None),
       2268             format=fmt,
    -> 2269             na_rep=na_rep,
       2270         ).reshape(i8values.shape)
       2271         return np.atleast_2d(result)


    pandas/_libs/tslib.pyx in pandas._libs.tslib.format_array_from_datetime()


    pandas/_libs/tslibs/timestamps.pyx in pandas._libs.tslibs.timestamps.Timestamp.__new__()


    pandas/_libs/tslibs/conversion.pyx in pandas._libs.tslibs.conversion.convert_to_tsobject()


    KeyboardInterrupt: 


------
