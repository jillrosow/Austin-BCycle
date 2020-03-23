<h1>Austin BCycle Station Analysis</h1>
    <p> Data is pulled from data.world in March 2020, and collected from weatherunderground and AustinBcycle in April-May 2016</p>
    <h2>Primary Goal</h2>
    <p>A cycle station can either be categorized as <b>active</b> or <b>inactive</b> depending on the number of bikes or docks available at a given time. When a station is considered INACTIVE, it is in one of two possible states:</p>
        <ol>
            <li>The station has no available bikes to check out (cannot start a ride).</li>
            <li>The station has no available docks to return a bike to (cannot end a ride)</li>
    </ol>
    <p>If neither of these conditions are true, the station is considered ACTIVE.
    </p>
    <p> In order to maximize customer satisfaction, inactive stations should be minimized as much as possible. To accomplish this goal, we need to identify stations which become inactive most frequently, and make suggestions to mitigate this effect.</p> 
    
<h2>Part 1 ‑ Data Cleaning & Exploratory data analysis</h2>

<h3>Objectives<br></h3>
<p>The Bcycle data was originally collected every 5 minutes from the Austin Bcycle website. I aggregated these bike and dock counts based on daily and 1 hour time intervals, and then visualize and describe the resulting station activity. Next, I reported and illustrated important features of the activity, such as individual station location variability and weather patterns. As interesting patterns emerged, statistical tests were done to investigate correlations. </p>
</div>

<h2>Part 2 ‑ Predictive Modeling</h2>

<h3>Objectives<br></h3>
<p>I will first need to collect of the the features to be modeled into one dataframe. After this, some feature engineering is done to add month, day, and time columns, as well as convert categorical varibles to dummy variables. Since station_id should have no correlation with the target variable, it was removed. Additionally, since "bikes", "docks", "empty", and "full" all predict the target variable perfectly, these were removed. Finally, the weather variables which included three variations such as min, mean and max were reduced to include just the mean measurements.</p>
<p> Initially, seven different classifiers are tested to determine which baseline model performed the best. After cross validation using auc as the scoring parameter, a best performing classifier is chosen to further undergo hyperparameter tuning. Once sufficiently tuned, the most important features which are predictive of a bicycle station becoming "inactive" are identified and presented visually. </p>
</div>

<div class = 'alert alert-info'> 
    <h1> Conclusions</h1>
    <h3>Results summary:</h3>
    <ul>
<li> I began by testing seven different classifiers in order to diversify my options, but found that the gradient boosting classifier performed best at baseline. </li>
<li> My original models all seemed to perform well in terms of accuracy, with the best model having an accuracy of 93%. However, after looking into the classification report, I found the model had poor recall and f-1 scores. </li>
<li> After extensive hyperparameter tuning, not only did the model increase accuracy up to 99% (6% improvement), but the recall and f-1 statistics dramatically improved. </li>
<li> Additionally, the tuned gradient boosting classifier increased the area under the curve from 0.793 to 0.995, a 0.202 increase. </li>
<li> Evaluating the feature importances showed that the hour of day and location of the station are the most powerful predictors of inactivity. I would suggest that Austin Bcycle refill stations at the most inactive time of day, as well as look into adding additional or larger stations in highly inactive locations.</li>
    </ul>
<h3> Future directions:</h3>
<ul>
<li> Adding data from months other than April and May could introduce month as a more important predicting feature; The same could be said for year, since all of the data came from 2016.</li> 
<li> Collecting data on average ride time would be valuable in understanding if stations become inactive more frequently when rider's embark on longer routes. It would also be interesting to know if some stations are correlated with a higher average ride time than others, leading to the need for a higher station capacity in a particular location.</li>
<li> Hyperparamter tuning should be done on other high performing baseline models, but was not done here due to time constraints. </li>
<li> Further hyperparameter tuning by grid search should be done, but was not done here due to hardware limitations.</li>
    </ul>
</div>
