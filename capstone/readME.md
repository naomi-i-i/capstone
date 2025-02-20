Data is collected by Amazon Mechanical Turk, aiming to predict if their drivers would accept a coupon offered to them while they were driving. 
A survey was conducted, to determine the driving conditions when the coupon was offered, personal information about the driver, and whether the coupon was accepted.  
Machine learning models were trained on this data to predict if the coupon will be accepted.

Preprocessing
The column ‘car’ was dropped as only 108 out of 1284 rows filled.
Rows with empty values were dropped, reducing the number of rows from 1284 to 12079.
The column ‘toCouponGEQ5min’ was dropped as it had only one unique value.
The column ‘direction_opp’ was dropped as it was a duplicate of 'direction_same'. Both columns are binary, and were the inverse of each other. For example a value was 0 in 'direction_opp' but 1 in 'direction_same'.
The column occupation had 25 subcategories. Categories with under 1000 entries were merged into one category, producing 5 categories. 

EDA

According to the survey, 57% of drivers accept the coupon.
The data has 6 numerical columns (excluding the target). 5 are binary, and the last has 3 integer values. 
The data has 17 categorical columns.

The correlation between accepting a coupon and the numerical features ranged from -0.1 to 0.057. The strongest correlation was with toCouponGEQ25mins (-0.1)
The type of restaurant the coupon is for affects the target, notably for ‘Carry out or Take away’ (0.74) and ‘Bar’ (0.41). 

Fitting
5 models were fit with the data, and all performed better than chance. The 2 best performing models were tuned as one had a better accuracy and precision but the other had better recall. Both performed very similarly on test data, with accuracy 0.757(XGBoost) and 0.756(RF), and precision 0.769(XGBoost) and 0.756(RF). Recal for the second model (RF) was higher, 0.838 compared to 0.816, as expected.
