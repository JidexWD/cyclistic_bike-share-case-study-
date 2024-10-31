```python
pip install pandas matplotlib seaborn

```

    Requirement already satisfied: pandas in c:\users\jiderificent\anaconda3\lib\site-packages (2.2.2)
    Requirement already satisfied: matplotlib in c:\users\jiderificent\anaconda3\lib\site-packages (3.8.4)
    Requirement already satisfied: seaborn in c:\users\jiderificent\anaconda3\lib\site-packages (0.13.2)
    Requirement already satisfied: numpy>=1.26.0 in c:\users\jiderificent\anaconda3\lib\site-packages (from pandas) (1.26.4)
    Requirement already satisfied: python-dateutil>=2.8.2 in c:\users\jiderificent\anaconda3\lib\site-packages (from pandas) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in c:\users\jiderificent\anaconda3\lib\site-packages (from pandas) (2024.1)
    Requirement already satisfied: tzdata>=2022.7 in c:\users\jiderificent\anaconda3\lib\site-packages (from pandas) (2023.3)
    Requirement already satisfied: contourpy>=1.0.1 in c:\users\jiderificent\anaconda3\lib\site-packages (from matplotlib) (1.2.0)
    Requirement already satisfied: cycler>=0.10 in c:\users\jiderificent\anaconda3\lib\site-packages (from matplotlib) (0.11.0)
    Requirement already satisfied: fonttools>=4.22.0 in c:\users\jiderificent\anaconda3\lib\site-packages (from matplotlib) (4.51.0)
    Requirement already satisfied: kiwisolver>=1.3.1 in c:\users\jiderificent\anaconda3\lib\site-packages (from matplotlib) (1.4.4)
    Requirement already satisfied: packaging>=20.0 in c:\users\jiderificent\anaconda3\lib\site-packages (from matplotlib) (23.2)
    Requirement already satisfied: pillow>=8 in c:\users\jiderificent\anaconda3\lib\site-packages (from matplotlib) (10.3.0)
    Requirement already satisfied: pyparsing>=2.3.1 in c:\users\jiderificent\anaconda3\lib\site-packages (from matplotlib) (3.0.9)
    Requirement already satisfied: six>=1.5 in c:\users\jiderificent\anaconda3\lib\site-packages (from python-dateutil>=2.8.2->pandas) (1.16.0)
    Note: you may need to restart the kernel to use updated packages.
    


```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
data_files = [f for f in os.listdir() if f.endswith('.csv')]
```


```python
# Load all files into a single DataFramedata_files]
df_list = [pd.read_csv(file) for file in data_files]
df = pd.concat(df_list, ignore_index=True)

```


```python

```

    <class 'pandas.core.frame.DataFrame'>
    Index: 4332069 entries, 0 to 5719876
    Data columns (total 13 columns):
     #   Column              Dtype  
    ---  ------              -----  
     0   ride_id             object 
     1   rideable_type       object 
     2   started_at          object 
     3   ended_at            object 
     4   start_station_name  object 
     5   start_station_id    object 
     6   end_station_name    object 
     7   end_station_id      object 
     8   start_lat           float64
     9   start_lng           float64
     10  end_lat             float64
     11  end_lng             float64
     12  member_casual       object 
    dtypes: float64(4), object(9)
    memory usage: 462.7+ MB
    


```python
# Preview the first few rows
df.head()
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
      <th>ride_id</th>
      <th>rideable_type</th>
      <th>started_at</th>
      <th>ended_at</th>
      <th>start_station_name</th>
      <th>start_station_id</th>
      <th>end_station_name</th>
      <th>end_station_id</th>
      <th>start_lat</th>
      <th>start_lng</th>
      <th>end_lat</th>
      <th>end_lng</th>
      <th>member_casual</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>F96D5A74A3E41399</td>
      <td>electric_bike</td>
      <td>2023-01-21 20:05:42</td>
      <td>2023-01-21 20:16:33</td>
      <td>Lincoln Ave &amp; Fullerton Ave</td>
      <td>TA1309000058</td>
      <td>Hampden Ct &amp; Diversey Ave</td>
      <td>202480.0</td>
      <td>41.924074</td>
      <td>-87.646278</td>
      <td>41.930000</td>
      <td>-87.640000</td>
      <td>member</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13CB7EB698CEDB88</td>
      <td>classic_bike</td>
      <td>2023-01-10 15:37:36</td>
      <td>2023-01-10 15:46:05</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BD88A2E670661CE5</td>
      <td>electric_bike</td>
      <td>2023-01-02 07:51:57</td>
      <td>2023-01-02 08:05:11</td>
      <td>Western Ave &amp; Lunt Ave</td>
      <td>RP-005</td>
      <td>Valli Produce - Evanston Plaza</td>
      <td>599</td>
      <td>42.008571</td>
      <td>-87.690483</td>
      <td>42.039742</td>
      <td>-87.699413</td>
      <td>casual</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C90792D034FED968</td>
      <td>classic_bike</td>
      <td>2023-01-22 10:52:58</td>
      <td>2023-01-22 11:01:44</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3397017529188E8A</td>
      <td>classic_bike</td>
      <td>2023-01-12 13:58:01</td>
      <td>2023-01-12 14:13:20</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Remove rows with missing values in essential columns
df = df.dropna(subset=['ride_id', 'start_station_name', 'end_station_name', 'started_at', 'ended_at'])
```


```python
df
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
      <th>ride_id</th>
      <th>rideable_type</th>
      <th>started_at</th>
      <th>ended_at</th>
      <th>start_station_name</th>
      <th>start_station_id</th>
      <th>end_station_name</th>
      <th>end_station_id</th>
      <th>start_lat</th>
      <th>start_lng</th>
      <th>end_lat</th>
      <th>end_lng</th>
      <th>member_casual</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>F96D5A74A3E41399</td>
      <td>electric_bike</td>
      <td>2023-01-21 20:05:42</td>
      <td>2023-01-21 20:16:33</td>
      <td>Lincoln Ave &amp; Fullerton Ave</td>
      <td>TA1309000058</td>
      <td>Hampden Ct &amp; Diversey Ave</td>
      <td>202480.0</td>
      <td>41.924074</td>
      <td>-87.646278</td>
      <td>41.930000</td>
      <td>-87.640000</td>
      <td>member</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13CB7EB698CEDB88</td>
      <td>classic_bike</td>
      <td>2023-01-10 15:37:36</td>
      <td>2023-01-10 15:46:05</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BD88A2E670661CE5</td>
      <td>electric_bike</td>
      <td>2023-01-02 07:51:57</td>
      <td>2023-01-02 08:05:11</td>
      <td>Western Ave &amp; Lunt Ave</td>
      <td>RP-005</td>
      <td>Valli Produce - Evanston Plaza</td>
      <td>599</td>
      <td>42.008571</td>
      <td>-87.690483</td>
      <td>42.039742</td>
      <td>-87.699413</td>
      <td>casual</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C90792D034FED968</td>
      <td>classic_bike</td>
      <td>2023-01-22 10:52:58</td>
      <td>2023-01-22 11:01:44</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3397017529188E8A</td>
      <td>classic_bike</td>
      <td>2023-01-12 13:58:01</td>
      <td>2023-01-12 14:13:20</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
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
    </tr>
    <tr>
      <th>5719872</th>
      <td>F74DF9549B504A6B</td>
      <td>electric_bike</td>
      <td>2023-12-07 13:15:24</td>
      <td>2023-12-07 13:17:37</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874702</td>
      <td>-87.649804</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
    </tr>
    <tr>
      <th>5719873</th>
      <td>BCDA66E761CC1029</td>
      <td>classic_bike</td>
      <td>2023-12-08 18:42:21</td>
      <td>2023-12-08 18:45:56</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
    </tr>
    <tr>
      <th>5719874</th>
      <td>D2CF330F9C266683</td>
      <td>classic_bike</td>
      <td>2023-12-05 14:09:11</td>
      <td>2023-12-05 14:13:01</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
    </tr>
    <tr>
      <th>5719875</th>
      <td>3829A0D1E00EE970</td>
      <td>electric_bike</td>
      <td>2023-12-02 21:36:07</td>
      <td>2023-12-02 21:53:45</td>
      <td>Damen Ave &amp; Madison St</td>
      <td>13134</td>
      <td>Morgan St &amp; Lake St*</td>
      <td>chargingstx4</td>
      <td>41.881396</td>
      <td>-87.674984</td>
      <td>41.885492</td>
      <td>-87.652289</td>
      <td>casual</td>
    </tr>
    <tr>
      <th>5719876</th>
      <td>A373F5B447AEA508</td>
      <td>classic_bike</td>
      <td>2023-12-11 13:07:46</td>
      <td>2023-12-11 13:11:24</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
    </tr>
  </tbody>
</table>
<p>4332069 rows × 13 columns</p>
</div>




```python
# Convert 'started_at' and 'ended_at' columns to datetime format
df['started_at'] = pd.to_datetime(df['started_at'])
df['ended_at'] = pd.to_datetime(df['ended_at'])
```


```python
df.describe()
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
      <th>started_at</th>
      <th>ended_at</th>
      <th>start_lat</th>
      <th>start_lng</th>
      <th>end_lat</th>
      <th>end_lng</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>5719877</td>
      <td>5719877</td>
      <td>5.719877e+06</td>
      <td>5.719877e+06</td>
      <td>5.712887e+06</td>
      <td>5.712887e+06</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2023-07-16 10:27:50.017874688</td>
      <td>2023-07-16 10:46:00.177127168</td>
      <td>4.190288e+01</td>
      <td>-8.764704e+01</td>
      <td>4.190322e+01</td>
      <td>-8.764720e+01</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2023-01-01 00:01:58</td>
      <td>2023-01-01 00:02:41</td>
      <td>4.163000e+01</td>
      <td>-8.794000e+01</td>
      <td>0.000000e+00</td>
      <td>-8.816000e+01</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2023-05-21 12:50:44</td>
      <td>2023-05-21 13:14:09</td>
      <td>4.188096e+01</td>
      <td>-8.766000e+01</td>
      <td>4.188103e+01</td>
      <td>-8.766027e+01</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2023-07-20 18:02:50</td>
      <td>2023-07-20 18:19:47</td>
      <td>4.189902e+01</td>
      <td>-8.764403e+01</td>
      <td>4.190000e+01</td>
      <td>-8.764410e+01</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2023-09-16 20:08:49</td>
      <td>2023-09-16 20:28:10</td>
      <td>4.193000e+01</td>
      <td>-8.762991e+01</td>
      <td>4.193000e+01</td>
      <td>-8.763000e+01</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2023-12-31 23:59:38</td>
      <td>2024-01-01 23:50:51</td>
      <td>4.207000e+01</td>
      <td>-8.746000e+01</td>
      <td>4.218000e+01</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.505556e-02</td>
      <td>2.733412e-02</td>
      <td>5.444371e-02</td>
      <td>6.919621e-02</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 5719877 entries, 0 to 5719876
    Data columns (total 13 columns):
     #   Column              Dtype         
    ---  ------              -----         
     0   ride_id             object        
     1   rideable_type       object        
     2   started_at          datetime64[ns]
     3   ended_at            datetime64[ns]
     4   start_station_name  object        
     5   start_station_id    object        
     6   end_station_name    object        
     7   end_station_id      object        
     8   start_lat           float64       
     9   start_lng           float64       
     10  end_lat             float64       
     11  end_lng             float64       
     12  member_casual       object        
    dtypes: datetime64[ns](2), float64(4), object(7)
    memory usage: 567.3+ MB
    


```python
# Calculate ride length in minutes
df['ride_length'] = (df['ended_at'] - df['started_at']).dt.total_seconds() / 60
```


```python
df
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
      <th>ride_id</th>
      <th>rideable_type</th>
      <th>started_at</th>
      <th>ended_at</th>
      <th>start_station_name</th>
      <th>start_station_id</th>
      <th>end_station_name</th>
      <th>end_station_id</th>
      <th>start_lat</th>
      <th>start_lng</th>
      <th>end_lat</th>
      <th>end_lng</th>
      <th>member_casual</th>
      <th>ride_length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>F96D5A74A3E41399</td>
      <td>electric_bike</td>
      <td>2023-01-21 20:05:42</td>
      <td>2023-01-21 20:16:33</td>
      <td>Lincoln Ave &amp; Fullerton Ave</td>
      <td>TA1309000058</td>
      <td>Hampden Ct &amp; Diversey Ave</td>
      <td>202480.0</td>
      <td>41.924074</td>
      <td>-87.646278</td>
      <td>41.930000</td>
      <td>-87.640000</td>
      <td>member</td>
      <td>10.850000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13CB7EB698CEDB88</td>
      <td>classic_bike</td>
      <td>2023-01-10 15:37:36</td>
      <td>2023-01-10 15:46:05</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>8.483333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BD88A2E670661CE5</td>
      <td>electric_bike</td>
      <td>2023-01-02 07:51:57</td>
      <td>2023-01-02 08:05:11</td>
      <td>Western Ave &amp; Lunt Ave</td>
      <td>RP-005</td>
      <td>Valli Produce - Evanston Plaza</td>
      <td>599</td>
      <td>42.008571</td>
      <td>-87.690483</td>
      <td>42.039742</td>
      <td>-87.699413</td>
      <td>casual</td>
      <td>13.233333</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C90792D034FED968</td>
      <td>classic_bike</td>
      <td>2023-01-22 10:52:58</td>
      <td>2023-01-22 11:01:44</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>8.766667</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3397017529188E8A</td>
      <td>classic_bike</td>
      <td>2023-01-12 13:58:01</td>
      <td>2023-01-12 14:13:20</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>15.316667</td>
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
    </tr>
    <tr>
      <th>5719872</th>
      <td>F74DF9549B504A6B</td>
      <td>electric_bike</td>
      <td>2023-12-07 13:15:24</td>
      <td>2023-12-07 13:17:37</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874702</td>
      <td>-87.649804</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
      <td>2.216667</td>
    </tr>
    <tr>
      <th>5719873</th>
      <td>BCDA66E761CC1029</td>
      <td>classic_bike</td>
      <td>2023-12-08 18:42:21</td>
      <td>2023-12-08 18:45:56</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
      <td>3.583333</td>
    </tr>
    <tr>
      <th>5719874</th>
      <td>D2CF330F9C266683</td>
      <td>classic_bike</td>
      <td>2023-12-05 14:09:11</td>
      <td>2023-12-05 14:13:01</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
      <td>3.833333</td>
    </tr>
    <tr>
      <th>5719875</th>
      <td>3829A0D1E00EE970</td>
      <td>electric_bike</td>
      <td>2023-12-02 21:36:07</td>
      <td>2023-12-02 21:53:45</td>
      <td>Damen Ave &amp; Madison St</td>
      <td>13134</td>
      <td>Morgan St &amp; Lake St*</td>
      <td>chargingstx4</td>
      <td>41.881396</td>
      <td>-87.674984</td>
      <td>41.885492</td>
      <td>-87.652289</td>
      <td>casual</td>
      <td>17.633333</td>
    </tr>
    <tr>
      <th>5719876</th>
      <td>A373F5B447AEA508</td>
      <td>classic_bike</td>
      <td>2023-12-11 13:07:46</td>
      <td>2023-12-11 13:11:24</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
      <td>3.633333</td>
    </tr>
  </tbody>
</table>
<p>5719877 rows × 14 columns</p>
</div>




```python
# Create day_of_week column based on started_at
df['day_of_week'] = df['started_at'].dt.day_name()
```


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 5719877 entries, 0 to 5719876
    Data columns (total 15 columns):
     #   Column              Dtype         
    ---  ------              -----         
     0   ride_id             object        
     1   rideable_type       object        
     2   started_at          datetime64[ns]
     3   ended_at            datetime64[ns]
     4   start_station_name  object        
     5   start_station_id    object        
     6   end_station_name    object        
     7   end_station_id      object        
     8   start_lat           float64       
     9   start_lng           float64       
     10  end_lat             float64       
     11  end_lng             float64       
     12  member_casual       object        
     13  ride_length         float64       
     14  day_of_week         object        
    dtypes: datetime64[ns](2), float64(5), object(8)
    memory usage: 654.6+ MB
    


```python
df
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
      <th>ride_id</th>
      <th>rideable_type</th>
      <th>started_at</th>
      <th>ended_at</th>
      <th>start_station_name</th>
      <th>start_station_id</th>
      <th>end_station_name</th>
      <th>end_station_id</th>
      <th>start_lat</th>
      <th>start_lng</th>
      <th>end_lat</th>
      <th>end_lng</th>
      <th>member_casual</th>
      <th>ride_length</th>
      <th>day_of_week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>F96D5A74A3E41399</td>
      <td>electric_bike</td>
      <td>2023-01-21 20:05:42</td>
      <td>2023-01-21 20:16:33</td>
      <td>Lincoln Ave &amp; Fullerton Ave</td>
      <td>TA1309000058</td>
      <td>Hampden Ct &amp; Diversey Ave</td>
      <td>202480.0</td>
      <td>41.924074</td>
      <td>-87.646278</td>
      <td>41.930000</td>
      <td>-87.640000</td>
      <td>member</td>
      <td>10.850000</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13CB7EB698CEDB88</td>
      <td>classic_bike</td>
      <td>2023-01-10 15:37:36</td>
      <td>2023-01-10 15:46:05</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>8.483333</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BD88A2E670661CE5</td>
      <td>electric_bike</td>
      <td>2023-01-02 07:51:57</td>
      <td>2023-01-02 08:05:11</td>
      <td>Western Ave &amp; Lunt Ave</td>
      <td>RP-005</td>
      <td>Valli Produce - Evanston Plaza</td>
      <td>599</td>
      <td>42.008571</td>
      <td>-87.690483</td>
      <td>42.039742</td>
      <td>-87.699413</td>
      <td>casual</td>
      <td>13.233333</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C90792D034FED968</td>
      <td>classic_bike</td>
      <td>2023-01-22 10:52:58</td>
      <td>2023-01-22 11:01:44</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>8.766667</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3397017529188E8A</td>
      <td>classic_bike</td>
      <td>2023-01-12 13:58:01</td>
      <td>2023-01-12 14:13:20</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>15.316667</td>
      <td>Thursday</td>
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
    </tr>
    <tr>
      <th>5719872</th>
      <td>F74DF9549B504A6B</td>
      <td>electric_bike</td>
      <td>2023-12-07 13:15:24</td>
      <td>2023-12-07 13:17:37</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874702</td>
      <td>-87.649804</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
      <td>2.216667</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>5719873</th>
      <td>BCDA66E761CC1029</td>
      <td>classic_bike</td>
      <td>2023-12-08 18:42:21</td>
      <td>2023-12-08 18:45:56</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
      <td>3.583333</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>5719874</th>
      <td>D2CF330F9C266683</td>
      <td>classic_bike</td>
      <td>2023-12-05 14:09:11</td>
      <td>2023-12-05 14:13:01</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
      <td>3.833333</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>5719875</th>
      <td>3829A0D1E00EE970</td>
      <td>electric_bike</td>
      <td>2023-12-02 21:36:07</td>
      <td>2023-12-02 21:53:45</td>
      <td>Damen Ave &amp; Madison St</td>
      <td>13134</td>
      <td>Morgan St &amp; Lake St*</td>
      <td>chargingstx4</td>
      <td>41.881396</td>
      <td>-87.674984</td>
      <td>41.885492</td>
      <td>-87.652289</td>
      <td>casual</td>
      <td>17.633333</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>5719876</th>
      <td>A373F5B447AEA508</td>
      <td>classic_bike</td>
      <td>2023-12-11 13:07:46</td>
      <td>2023-12-11 13:11:24</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
      <td>3.633333</td>
      <td>Monday</td>
    </tr>
  </tbody>
</table>
<p>5719877 rows × 15 columns</p>
</div>




```python
# Separate casual riders and annual members
casual_riders = df[df['member_casual'] == 'casual']
annual_members = df[df['member_casual'] == 'member']
```


```python
df
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
      <th>ride_id</th>
      <th>rideable_type</th>
      <th>started_at</th>
      <th>ended_at</th>
      <th>start_station_name</th>
      <th>start_station_id</th>
      <th>end_station_name</th>
      <th>end_station_id</th>
      <th>start_lat</th>
      <th>start_lng</th>
      <th>end_lat</th>
      <th>end_lng</th>
      <th>member_casual</th>
      <th>ride_length</th>
      <th>day_of_week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>F96D5A74A3E41399</td>
      <td>electric_bike</td>
      <td>2023-01-21 20:05:42</td>
      <td>2023-01-21 20:16:33</td>
      <td>Lincoln Ave &amp; Fullerton Ave</td>
      <td>TA1309000058</td>
      <td>Hampden Ct &amp; Diversey Ave</td>
      <td>202480.0</td>
      <td>41.924074</td>
      <td>-87.646278</td>
      <td>41.930000</td>
      <td>-87.640000</td>
      <td>member</td>
      <td>10.850000</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13CB7EB698CEDB88</td>
      <td>classic_bike</td>
      <td>2023-01-10 15:37:36</td>
      <td>2023-01-10 15:46:05</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>8.483333</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BD88A2E670661CE5</td>
      <td>electric_bike</td>
      <td>2023-01-02 07:51:57</td>
      <td>2023-01-02 08:05:11</td>
      <td>Western Ave &amp; Lunt Ave</td>
      <td>RP-005</td>
      <td>Valli Produce - Evanston Plaza</td>
      <td>599</td>
      <td>42.008571</td>
      <td>-87.690483</td>
      <td>42.039742</td>
      <td>-87.699413</td>
      <td>casual</td>
      <td>13.233333</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C90792D034FED968</td>
      <td>classic_bike</td>
      <td>2023-01-22 10:52:58</td>
      <td>2023-01-22 11:01:44</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>8.766667</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3397017529188E8A</td>
      <td>classic_bike</td>
      <td>2023-01-12 13:58:01</td>
      <td>2023-01-12 14:13:20</td>
      <td>Kimbark Ave &amp; 53rd St</td>
      <td>TA1309000037</td>
      <td>Greenwood Ave &amp; 47th St</td>
      <td>TA1308000002</td>
      <td>41.799568</td>
      <td>-87.594747</td>
      <td>41.809835</td>
      <td>-87.599383</td>
      <td>member</td>
      <td>15.316667</td>
      <td>Thursday</td>
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
    </tr>
    <tr>
      <th>5719872</th>
      <td>F74DF9549B504A6B</td>
      <td>electric_bike</td>
      <td>2023-12-07 13:15:24</td>
      <td>2023-12-07 13:17:37</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874702</td>
      <td>-87.649804</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
      <td>2.216667</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>5719873</th>
      <td>BCDA66E761CC1029</td>
      <td>classic_bike</td>
      <td>2023-12-08 18:42:21</td>
      <td>2023-12-08 18:45:56</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>casual</td>
      <td>3.583333</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>5719874</th>
      <td>D2CF330F9C266683</td>
      <td>classic_bike</td>
      <td>2023-12-05 14:09:11</td>
      <td>2023-12-05 14:13:01</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
      <td>3.833333</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>5719875</th>
      <td>3829A0D1E00EE970</td>
      <td>electric_bike</td>
      <td>2023-12-02 21:36:07</td>
      <td>2023-12-02 21:53:45</td>
      <td>Damen Ave &amp; Madison St</td>
      <td>13134</td>
      <td>Morgan St &amp; Lake St*</td>
      <td>chargingstx4</td>
      <td>41.881396</td>
      <td>-87.674984</td>
      <td>41.885492</td>
      <td>-87.652289</td>
      <td>casual</td>
      <td>17.633333</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>5719876</th>
      <td>A373F5B447AEA508</td>
      <td>classic_bike</td>
      <td>2023-12-11 13:07:46</td>
      <td>2023-12-11 13:11:24</td>
      <td>900 W Harrison St</td>
      <td>13028</td>
      <td>Racine Ave &amp; Congress Pkwy</td>
      <td>TA1306000025</td>
      <td>41.874754</td>
      <td>-87.649807</td>
      <td>41.874640</td>
      <td>-87.657030</td>
      <td>member</td>
      <td>3.633333</td>
      <td>Monday</td>
    </tr>
  </tbody>
</table>
<p>5719877 rows × 15 columns</p>
</div>




```python
# Calculate the average ride length for both groups
avg_ride_length_casual = casual_riders['ride_length'].mean()
avg_ride_length_member = annual_members['ride_length'].mean()


print(f"Average ride length (Casual riders): {avg_ride_length_casual} minutes")
print(f"Average ride length (Annual members): {avg_ride_length_member} minutes")
```

    Average ride length (Casual riders): 28.224530027096556 minutes
    Average ride length (Annual members): 12.513165786051365 minutes
    


```python
# Count rides by day of the week for both groups
rides_by_day_casual = casual_riders['day_of_week'].value_counts()
rides_by_day_member = annual_members['day_of_week'].value_counts()

print("Casual riders by day of the week:\n", rides_by_day_casual)
print("Members by day of the week:\n", rides_by_day_member)
```

    Casual riders by day of the week:
     day_of_week
    Saturday     410706
    Sunday       335718
    Friday       311925
    Thursday     270612
    Wednesday    249166
    Tuesday      246224
    Monday       234828
    Name: count, dtype: int64
    Members by day of the week:
     day_of_week
    Thursday     589590
    Wednesday    586459
    Tuesday      576754
    Friday       531599
    Monday       494576
    Saturday     472860
    Sunday       408860
    Name: count, dtype: int64
    


```python
# Extract the hour from 'started_at' to analyze peak times
df['hour'] = df['started_at'].dt.hour

# Group by hour for casual riders and members
rides_by_hour = df.groupby(['hour', 'member_casual']).size().unstack()

# Plot the number of rides by hour of the day
rides_by_hour.plot(kind='bar', stacked=True, figsize=(10,6))
plt.title("Rides by Hour of Day (Casual vs Member)")
plt.xlabel("Hour of the Day")
plt.ylabel("Number of Rides")
plt.show()
```


    
![png](output_20_0.png)
    



```python
# Number of Rides by Day of the Week
plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='day_of_week', hue='member_casual', order=['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'])
plt.title('Number of Rides by Day of the Week (Casual vs Member)')
plt.show()
```


    
![png](output_21_0.png)
    



```python
# Ride Length Distribution
plt.figure(figsize=(10, 6))
sns.histplot(data=df, x='ride_length', hue='member_casual', bins=50, kde=True)
plt.xlim(0, 60)  # Focus on rides less than 1 hour
plt.title('Ride Length Distribution (Casual vs Member)')
plt.show()
```


    
![png](output_22_0.png)
    



```python

```
