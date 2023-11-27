******
Steps:
******

CSV:        Original dataset is 'resale_price_2017_onwards.csv'
⬇
Jupyter:    In 'get2023_location.ipynb', get latitudes and longitudes, only save data in 2023
⬇
CSV:        '2023_resale_price_with_geolocation.csv' has lat & lng
⬇
TXT:        'primary_phase2B.txt' + 'primary_phase2C.txt', copied from website https://elite.com.sg/primary-schools
⬇
CSV:        'top60_primary_without_duplication.csv', manually generated
⬇
Jupyter:    'new_feature_mrt.ipynb' + 'new_feature_primary_school.ipynb', get new features related to famours primary school & MRT, incoporate with main dataset
⬇
CSV:        Finally we get '2023_resale_price_with_geolocation___minMrt_w_t___minPrimary_w_t.csv'
⬇
Jupyter:    'persqm_insights.ipynb', calculate per sqm, get insights from plots & covariance matrix, generate train sets & test sets


# all new features of a certain row are generated only use data from this row


