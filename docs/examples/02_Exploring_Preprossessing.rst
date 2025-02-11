02 - Exploring Preprocessing
============================

Data preprocessing is a set of activities performed to prepare data for
future analysis and data mining activities.

Load data from file
-------------------

The dataset used in this tutorial is GeoLife GPS Trajectories. Available
in https://www.microsoft.com/en-us/download/details.aspx?id=52367

.. code:: ipython3

    from pymove import read_csv

.. code:: ipython3

    df_move = read_csv('geolife_sample.csv')

.. code:: ipython3

    df_move.show_trajectories_info()
    df_move.head()


.. parsed-literal::


    ====================== INFORMATION ABOUT DATASET ======================

    Number of Points: 217653

    Number of IDs objects: 2

    Start Date:2008-10-23 05:53:05     End Date:2009-03-19 05:46:37

    Bounding Box:(22.147577, 113.548843, 41.132062, 121.156224)


    =======================================================================





.. raw:: html

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
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>id</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>1</td>
        </tr>
        <tr>
          <th>1</th>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>1</td>
        </tr>
        <tr>
          <th>2</th>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>1</td>
        </tr>
        <tr>
          <th>3</th>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>1</td>
        </tr>
        <tr>
          <th>4</th>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>1</td>
        </tr>
      </tbody>
    </table>
    </div>



Filtering
---------

The filters module provides functions to perform different types of data
filtering.

Importing the module:

.. code:: ipython3

    from pymove import filters

A bounding box (usually shortened to bbox) is an area defined by two
longitudes and two latitudes. The function by_bbox, filters points of
the trajectories according to a chosen bounding box.

.. code:: ipython3

    bbox = (22.147577, 113.54884299999999, 41.132062, 121.156224)
    filt_df = filters.by_bbox(df_move, bbox)
    filt_df.head()




.. raw:: html

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
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>id</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>1</td>
        </tr>
        <tr>
          <th>1</th>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>1</td>
        </tr>
        <tr>
          <th>2</th>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>1</td>
        </tr>
        <tr>
          <th>3</th>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>1</td>
        </tr>
        <tr>
          <th>4</th>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>1</td>
        </tr>
      </tbody>
    </table>
    </div>



by_datetime function filters point trajectories according to the time
specified by the parameters: start_datetime and end_datetime.

.. code:: ipython3

    filters.by_datetime(df_move, start_datetime = "2009-03-19 05:45:37", end_datetime = "2009-03-19 05:46:17")




.. raw:: html

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
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>id</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>217643</th>
          <td>40.000205</td>
          <td>116.327173</td>
          <td>2009-03-19 05:45:37</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217644</th>
          <td>40.000128</td>
          <td>116.327171</td>
          <td>2009-03-19 05:45:42</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217645</th>
          <td>40.000069</td>
          <td>116.327179</td>
          <td>2009-03-19 05:45:47</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217646</th>
          <td>40.000001</td>
          <td>116.327219</td>
          <td>2009-03-19 05:45:52</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217647</th>
          <td>39.999919</td>
          <td>116.327211</td>
          <td>2009-03-19 05:45:57</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217648</th>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>5</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>5</td>
        </tr>
      </tbody>
    </table>
    </div>



by label function filters trajectories points according to specified
value and column label, set by value and label_name respectively.

.. code:: ipython3

    filters.by_label(df_move, value = 116.327219, label_name = "lon").head()




.. raw:: html

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
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>id</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>3066</th>
          <td>39.979160</td>
          <td>116.327219</td>
          <td>2008-10-24 06:34:27</td>
          <td>1</td>
        </tr>
        <tr>
          <th>13911</th>
          <td>39.975424</td>
          <td>116.327219</td>
          <td>2008-10-26 08:18:06</td>
          <td>1</td>
        </tr>
        <tr>
          <th>16396</th>
          <td>39.980411</td>
          <td>116.327219</td>
          <td>2008-10-27 00:30:47</td>
          <td>1</td>
        </tr>
        <tr>
          <th>33935</th>
          <td>39.975832</td>
          <td>116.327219</td>
          <td>2008-11-05 11:04:04</td>
          <td>1</td>
        </tr>
        <tr>
          <th>41636</th>
          <td>39.976990</td>
          <td>116.327219</td>
          <td>2008-11-07 10:34:41</td>
          <td>1</td>
        </tr>
      </tbody>
    </table>
    </div>



by_id function filters trajectories points according to selected
trajectory id.

.. code:: ipython3

    filters.by_id(df_move, id_=5).head()




.. raw:: html

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
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>id</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>108607</th>
          <td>40.004155</td>
          <td>116.321337</td>
          <td>2008-10-24 04:12:30</td>
          <td>5</td>
        </tr>
        <tr>
          <th>108608</th>
          <td>40.003834</td>
          <td>116.321462</td>
          <td>2008-10-24 04:12:35</td>
          <td>5</td>
        </tr>
        <tr>
          <th>108609</th>
          <td>40.003783</td>
          <td>116.321431</td>
          <td>2008-10-24 04:12:40</td>
          <td>5</td>
        </tr>
        <tr>
          <th>108610</th>
          <td>40.003690</td>
          <td>116.321429</td>
          <td>2008-10-24 04:12:45</td>
          <td>5</td>
        </tr>
        <tr>
          <th>108611</th>
          <td>40.003589</td>
          <td>116.321427</td>
          <td>2008-10-24 04:12:50</td>
          <td>5</td>
        </tr>
      </tbody>
    </table>
    </div>



A tid is the result of concatenation between the id and date of a
trajectory. The by_tid function filters trajectory points according to
the tid specified by the tid\_ parameter.

.. code:: ipython3

    df_move.generate_tid_based_on_id_datetime()
    filters.by_tid(df_move, "12008102305").head()




.. raw:: html

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
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>id</th>
          <th>tid</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>1</th>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>2</th>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>3</th>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>4</th>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
      </tbody>
    </table>
    </div>



clean_consecutive_duplicates function removes consecutives duplicate
rows of the Dataframe. Optionally only certaind columns can be consider,
this is defined by the parameter subset, in this example only the lat
column is considered.

.. code:: ipython3

    filtered_df = filters.clean_consecutive_duplicates(df_move, subset = ["lat"])
    len(filtered_df)




.. parsed-literal::

    196142



clean_gps_jumps_by_distance function removes from the dataframe the
trajectories points that are outliers.

.. code:: ipython3

    filters.clean_gps_jumps_by_distance(df_move)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>dist_to_next</th>
          <th>dist_prev_to_next</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>13.690153</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>7.403788</td>
          <td>20.223428</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>1.821083</td>
          <td>5.888579</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>2.889671</td>
          <td>1.873356</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>66.555997</td>
          <td>68.727260</td>
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
        </tr>
        <tr>
          <th>217648</th>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.291709</td>
          <td>12.214590</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>6.241949</td>
          <td>10.400206</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>8.462920</td>
          <td>14.628012</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>4.713399</td>
          <td>6.713456</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>NaN</td>
          <td>NaN</td>
        </tr>
      </tbody>
    </table>
    <p>217270 rows × 8 columns</p>
    </div>



clean_gps_nearby_points_by_distances function removes points from the
trajectories when the distance between them and the point before is
smaller than the parameter radius_area.

.. code:: ipython3

    filters.clean_gps_nearby_points_by_distances(df_move, radius_area=10)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>dist_to_next</th>
          <th>dist_prev_to_next</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>13.690153</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>7.403788</td>
          <td>20.223428</td>
        </tr>
        <tr>
          <th>5</th>
          <td>1</td>
          <td>39.984710</td>
          <td>116.319865</td>
          <td>2008-10-23 05:53:23</td>
          <td>12008102305</td>
          <td>66.555997</td>
          <td>6.162987</td>
          <td>60.622358</td>
        </tr>
        <tr>
          <th>14</th>
          <td>1</td>
          <td>39.984959</td>
          <td>116.319969</td>
          <td>2008-10-23 05:54:03</td>
          <td>12008102305</td>
          <td>40.672170</td>
          <td>11.324767</td>
          <td>51.291054</td>
        </tr>
        <tr>
          <th>15</th>
          <td>1</td>
          <td>39.985036</td>
          <td>116.320056</td>
          <td>2008-10-23 05:54:04</td>
          <td>12008102305</td>
          <td>11.324767</td>
          <td>32.842422</td>
          <td>24.923216</td>
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
        </tr>
        <tr>
          <th>217563</th>
          <td>5</td>
          <td>40.001185</td>
          <td>116.321791</td>
          <td>2009-03-19 05:39:02</td>
          <td>52009031905</td>
          <td>11.604029</td>
          <td>6.915583</td>
          <td>17.245027</td>
        </tr>
        <tr>
          <th>217637</th>
          <td>5</td>
          <td>40.000759</td>
          <td>116.327088</td>
          <td>2009-03-19 05:45:07</td>
          <td>52009031905</td>
          <td>28.946922</td>
          <td>18.331999</td>
          <td>47.148573</td>
        </tr>
        <tr>
          <th>217638</th>
          <td>5</td>
          <td>40.000595</td>
          <td>116.327066</td>
          <td>2009-03-19 05:45:12</td>
          <td>52009031905</td>
          <td>18.331999</td>
          <td>9.926875</td>
          <td>27.905967</td>
        </tr>
        <tr>
          <th>217641</th>
          <td>5</td>
          <td>40.000368</td>
          <td>116.327072</td>
          <td>2009-03-19 05:45:27</td>
          <td>52009031905</td>
          <td>10.877438</td>
          <td>8.887992</td>
          <td>19.705708</td>
        </tr>
        <tr>
          <th>217643</th>
          <td>5</td>
          <td>40.000205</td>
          <td>116.327173</td>
          <td>2009-03-19 05:45:37</td>
          <td>52009031905</td>
          <td>11.406650</td>
          <td>8.563704</td>
          <td>19.107146</td>
        </tr>
      </tbody>
    </table>
    <p>79969 rows × 8 columns</p>
    </div>



clean_gps_nearby_points_by_speed function removes points from the
trajectories when the speed of travel between them and the point before
is smaller than the value set by the parameter speed_radius.

.. code:: ipython3

    filters.clean_gps_nearby_points_by_speed(df_move, speed_radius=40.0)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>time_to_prev</th>
          <th>speed_to_prev</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>149</th>
          <td>1</td>
          <td>39.977648</td>
          <td>116.326925</td>
          <td>2008-10-23 10:33:00</td>
          <td>12008102310</td>
          <td>1470.641291</td>
          <td>7.0</td>
          <td>210.091613</td>
        </tr>
        <tr>
          <th>560</th>
          <td>1</td>
          <td>40.009802</td>
          <td>116.313247</td>
          <td>2008-10-23 10:56:54</td>
          <td>12008102310</td>
          <td>47.020950</td>
          <td>1.0</td>
          <td>47.020950</td>
        </tr>
        <tr>
          <th>561</th>
          <td>1</td>
          <td>40.009262</td>
          <td>116.312948</td>
          <td>2008-10-23 10:56:55</td>
          <td>12008102310</td>
          <td>65.222058</td>
          <td>1.0</td>
          <td>65.222058</td>
        </tr>
        <tr>
          <th>1369</th>
          <td>1</td>
          <td>39.990659</td>
          <td>116.326345</td>
          <td>2008-10-24 00:04:29</td>
          <td>12008102400</td>
          <td>40.942759</td>
          <td>1.0</td>
          <td>40.942759</td>
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
        </tr>
        <tr>
          <th>216382</th>
          <td>5</td>
          <td>40.000185</td>
          <td>116.327286</td>
          <td>2009-02-28 03:52:45</td>
          <td>52009022803</td>
          <td>333.656648</td>
          <td>5.0</td>
          <td>66.731330</td>
        </tr>
        <tr>
          <th>217458</th>
          <td>5</td>
          <td>39.999918</td>
          <td>116.320057</td>
          <td>2009-03-19 04:36:02</td>
          <td>52009031904</td>
          <td>556.947064</td>
          <td>5.0</td>
          <td>111.389413</td>
        </tr>
        <tr>
          <th>217459</th>
          <td>5</td>
          <td>39.999077</td>
          <td>116.317156</td>
          <td>2009-03-19 04:36:07</td>
          <td>52009031904</td>
          <td>264.212540</td>
          <td>5.0</td>
          <td>52.842508</td>
        </tr>
        <tr>
          <th>217463</th>
          <td>5</td>
          <td>40.001122</td>
          <td>116.320879</td>
          <td>2009-03-19 04:40:52</td>
          <td>52009031904</td>
          <td>267.350055</td>
          <td>5.0</td>
          <td>53.470011</td>
        </tr>
        <tr>
          <th>217476</th>
          <td>5</td>
          <td>40.005903</td>
          <td>116.318669</td>
          <td>2009-03-19 04:49:47</td>
          <td>52009031904</td>
          <td>436.405009</td>
          <td>5.0</td>
          <td>87.281002</td>
        </tr>
      </tbody>
    </table>
    <p>281 rows × 8 columns</p>
    </div>



clean_gps_speed_max_radius function recursively removes trajectories
points with speed higher than the value set by the user.

.. code:: ipython3

    filters.clean_gps_speed_max_radius(df_move)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>time_to_prev</th>
          <th>speed_to_prev</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>1.0</td>
          <td>13.690153</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>5.0</td>
          <td>1.480758</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>5.0</td>
          <td>0.364217</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>5.0</td>
          <td>0.577934</td>
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
        </tr>
        <tr>
          <th>217648</th>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.0</td>
          <td>1.439771</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>5.0</td>
          <td>1.058342</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>5.0</td>
          <td>1.248390</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>5.0</td>
          <td>1.692584</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>20.0</td>
          <td>0.235670</td>
        </tr>
      </tbody>
    </table>
    <p>217304 rows × 8 columns</p>
    </div>



clean_trajectories_with_few_points function removes from the given
dataframe, trajectories with fewer points than was specified by the
parameter min_points_per_trajectory.

.. code:: ipython3

    filters.clean_trajectories_with_few_points(df_move)




.. raw:: html

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
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>id</th>
          <th>tid</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>1</th>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>2</th>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>3</th>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>4</th>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>1</td>
          <td>12008102305</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>217648</th>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>5</td>
          <td>52009031905</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>5</td>
          <td>52009031905</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>5</td>
          <td>52009031905</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>5</td>
          <td>52009031905</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>5</td>
          <td>52009031905</td>
        </tr>
      </tbody>
    </table>
    <p>217649 rows × 5 columns</p>
    </div>



Segmentation
------------

The segmentation module are used to segment trajectories based on
different parameters.

Importing the module:

.. code:: ipython3

    from pymove import segmentation

bbox_split function splits the bounding box in grids of the same size.
The number of grids is defined by the parameter number_grids.

.. code:: ipython3

    bbox = (22.147577, 113.54884299999999, 41.132062, 121.156224)
    segmentation.bbox_split(bbox, number_grids=4)




.. raw:: html

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
          <th>lat_min</th>
          <th>lon_min</th>
          <th>lat_max</th>
          <th>lon_max</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>22.147577</td>
          <td>113.548843</td>
          <td>41.132062</td>
          <td>115.450688</td>
        </tr>
        <tr>
          <th>1</th>
          <td>22.147577</td>
          <td>115.450688</td>
          <td>41.132062</td>
          <td>117.352533</td>
        </tr>
        <tr>
          <th>2</th>
          <td>22.147577</td>
          <td>117.352533</td>
          <td>41.132062</td>
          <td>119.254379</td>
        </tr>
        <tr>
          <th>3</th>
          <td>22.147577</td>
          <td>119.254379</td>
          <td>41.132062</td>
          <td>121.156224</td>
        </tr>
      </tbody>
    </table>
    </div>



by_dist_time_speed functions segments the trajectories into clusters
based on distance, time and speed.

.. code:: ipython3

    segmentation.by_dist_time_speed(
        df_move,
        max_dist_between_adj_points=5000,
        max_time_between_adj_points=800,
        max_speed_between_adj_points=60.0
    )



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>time_to_prev</th>
          <th>speed_to_prev</th>
          <th>tid_part</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>1</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>1.0</td>
          <td>13.690153</td>
          <td>1</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>5.0</td>
          <td>1.480758</td>
          <td>1</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>5.0</td>
          <td>0.364217</td>
          <td>1</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>5.0</td>
          <td>0.577934</td>
          <td>1</td>
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
        </tr>
        <tr>
          <th>217648</th>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.0</td>
          <td>1.439771</td>
          <td>515</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>5.0</td>
          <td>1.058342</td>
          <td>515</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>5.0</td>
          <td>1.248390</td>
          <td>515</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>5.0</td>
          <td>1.692584</td>
          <td>515</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>20.0</td>
          <td>0.235670</td>
          <td>515</td>
        </tr>
      </tbody>
    </table>
    <p>217653 rows × 9 columns</p>
    </div>



by_max_dist function segments the trajectories into clusters based on
distance.

.. code:: ipython3

    segmentation.by_max_dist(df_move, max_dist_between_adj_points=4000)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>time_to_prev</th>
          <th>speed_to_prev</th>
          <th>tid_dist</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>1</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>1.0</td>
          <td>13.690153</td>
          <td>1</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>5.0</td>
          <td>1.480758</td>
          <td>1</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>5.0</td>
          <td>0.364217</td>
          <td>1</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>5.0</td>
          <td>0.577934</td>
          <td>1</td>
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
        </tr>
        <tr>
          <th>217648</th>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.0</td>
          <td>1.439771</td>
          <td>20</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>5.0</td>
          <td>1.058342</td>
          <td>20</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>5.0</td>
          <td>1.248390</td>
          <td>20</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>5.0</td>
          <td>1.692584</td>
          <td>20</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>20.0</td>
          <td>0.235670</td>
          <td>20</td>
        </tr>
      </tbody>
    </table>
    <p>217653 rows × 9 columns</p>
    </div>



by_max_time function segments the trajectories into clusters based on
time.

.. code:: ipython3

    segmentation.by_max_time(df_move, max_time_between_adj_points=1000)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>time_to_prev</th>
          <th>speed_to_prev</th>
          <th>tid_time</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>1</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>1.0</td>
          <td>13.690153</td>
          <td>1</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>5.0</td>
          <td>1.480758</td>
          <td>1</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>5.0</td>
          <td>0.364217</td>
          <td>1</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>5.0</td>
          <td>0.577934</td>
          <td>1</td>
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
        </tr>
        <tr>
          <th>217648</th>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.0</td>
          <td>1.439771</td>
          <td>353</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>5.0</td>
          <td>1.058342</td>
          <td>353</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>5.0</td>
          <td>1.248390</td>
          <td>353</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>5.0</td>
          <td>1.692584</td>
          <td>353</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>20.0</td>
          <td>0.235670</td>
          <td>353</td>
        </tr>
      </tbody>
    </table>
    <p>217653 rows × 9 columns</p>
    </div>



by_max_speed function segments the trajectories into clusters based on
speed.

.. code:: ipython3

    segmentation.by_max_speed(df_move, max_speed_between_adj_points=70.0)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>time_to_prev</th>
          <th>speed_to_prev</th>
          <th>tid_speed</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>1</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>1.0</td>
          <td>13.690153</td>
          <td>1</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>5.0</td>
          <td>1.480758</td>
          <td>1</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>5.0</td>
          <td>0.364217</td>
          <td>1</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>5.0</td>
          <td>0.577934</td>
          <td>1</td>
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
        </tr>
        <tr>
          <th>217648</th>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.0</td>
          <td>1.439771</td>
          <td>86</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>5.0</td>
          <td>1.058342</td>
          <td>86</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>5.0</td>
          <td>1.248390</td>
          <td>86</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>5.0</td>
          <td>1.692584</td>
          <td>86</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>20.0</td>
          <td>0.235670</td>
          <td>86</td>
        </tr>
      </tbody>
    </table>
    <p>217653 rows × 9 columns</p>
    </div>



Stay point detection
--------------------

A stay point is location where a moving object has stayed for a while
within a certain distance threshold. A stay point could stand different
places such: a restaurant, a school, a work place.

Importing the module:

.. code:: ipython3

    from pymove import stay_point_detection

create_or_update_move_stop_by_dist_time function creates or updates the
stay points of the trajectories, based on distance and time metrics.

.. code:: ipython3

    stay_point_detection.create_or_update_move_stop_by_dist_time(df_move, dist_radius=40, time_radius=1000)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=3512)))




.. raw:: html

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
          <th>segment_stop</th>
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>time_to_prev</th>
          <th>speed_to_prev</th>
          <th>stop</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>False</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>1.0</td>
          <td>13.690153</td>
          <td>False</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>5.0</td>
          <td>1.480758</td>
          <td>False</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>5.0</td>
          <td>0.364217</td>
          <td>False</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>5.0</td>
          <td>0.577934</td>
          <td>False</td>
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
          <th>217648</th>
          <td>3512</td>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.0</td>
          <td>1.439771</td>
          <td>False</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>3512</td>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>5.0</td>
          <td>1.058342</td>
          <td>False</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>3512</td>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>5.0</td>
          <td>1.248390</td>
          <td>False</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>3512</td>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>5.0</td>
          <td>1.692584</td>
          <td>False</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>3512</td>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>20.0</td>
          <td>0.235670</td>
          <td>False</td>
        </tr>
      </tbody>
    </table>
    <p>217653 rows × 10 columns</p>
    </div>



create_or_update_move_and_stop_by_radius function creates or updates the
stay points of the trajectories, based on distance.

.. code:: ipython3

    stay_point_detection.create_or_update_move_and_stop_by_radius(df_move, radius=2)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))




.. raw:: html

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
          <th>id</th>
          <th>lat</th>
          <th>lon</th>
          <th>datetime</th>
          <th>tid</th>
          <th>dist_to_prev</th>
          <th>dist_to_next</th>
          <th>dist_prev_to_next</th>
          <th>situation</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>39.984094</td>
          <td>116.319236</td>
          <td>2008-10-23 05:53:05</td>
          <td>12008102305</td>
          <td>NaN</td>
          <td>13.690153</td>
          <td>NaN</td>
          <td>nan</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>39.984198</td>
          <td>116.319322</td>
          <td>2008-10-23 05:53:06</td>
          <td>12008102305</td>
          <td>13.690153</td>
          <td>7.403788</td>
          <td>20.223428</td>
          <td>move</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>39.984224</td>
          <td>116.319402</td>
          <td>2008-10-23 05:53:11</td>
          <td>12008102305</td>
          <td>7.403788</td>
          <td>1.821083</td>
          <td>5.888579</td>
          <td>move</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1</td>
          <td>39.984211</td>
          <td>116.319389</td>
          <td>2008-10-23 05:53:16</td>
          <td>12008102305</td>
          <td>1.821083</td>
          <td>2.889671</td>
          <td>1.873356</td>
          <td>stop</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1</td>
          <td>39.984217</td>
          <td>116.319422</td>
          <td>2008-10-23 05:53:21</td>
          <td>12008102305</td>
          <td>2.889671</td>
          <td>66.555997</td>
          <td>68.727260</td>
          <td>move</td>
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
        </tr>
        <tr>
          <th>217648</th>
          <td>5</td>
          <td>39.999896</td>
          <td>116.327290</td>
          <td>2009-03-19 05:46:02</td>
          <td>52009031905</td>
          <td>7.198855</td>
          <td>5.291709</td>
          <td>12.214590</td>
          <td>move</td>
        </tr>
        <tr>
          <th>217649</th>
          <td>5</td>
          <td>39.999899</td>
          <td>116.327352</td>
          <td>2009-03-19 05:46:07</td>
          <td>52009031905</td>
          <td>5.291709</td>
          <td>6.241949</td>
          <td>10.400206</td>
          <td>move</td>
        </tr>
        <tr>
          <th>217650</th>
          <td>5</td>
          <td>39.999945</td>
          <td>116.327394</td>
          <td>2009-03-19 05:46:12</td>
          <td>52009031905</td>
          <td>6.241949</td>
          <td>8.462920</td>
          <td>14.628012</td>
          <td>move</td>
        </tr>
        <tr>
          <th>217651</th>
          <td>5</td>
          <td>40.000015</td>
          <td>116.327433</td>
          <td>2009-03-19 05:46:17</td>
          <td>52009031905</td>
          <td>8.462920</td>
          <td>4.713399</td>
          <td>6.713456</td>
          <td>move</td>
        </tr>
        <tr>
          <th>217652</th>
          <td>5</td>
          <td>39.999978</td>
          <td>116.327460</td>
          <td>2009-03-19 05:46:37</td>
          <td>52009031905</td>
          <td>4.713399</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>move</td>
        </tr>
      </tbody>
    </table>
    <p>217653 rows × 9 columns</p>
    </div>



Compression
-----------

Importing the module:

.. code:: ipython3

    from pymove import compression

The function below is used to reduce the size of the trajectory, the
stop points are used to make the compression.

.. code:: ipython3

    df_compressed = compression.compress_segment_stop_to_point(df_move)
    len(df_move), len(df_compressed)



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=2)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=4809)))



.. parsed-literal::

    VBox(children=(HTML(value=''), IntProgress(value=0, max=285)))




.. parsed-literal::

    (217653, 65620)
