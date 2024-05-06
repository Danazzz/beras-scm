FORECASTING BERAS JABAR

Produksi Beras:
https://jabar.bps.go.id/indicator/53/713/1/produksi-beras-menurut-kabupaten-kota.html
Tingkat Konsumsi:
https://jabar.bps.go.id/publication/2020/10/21/fb790745cfb78cd438910f5f/analisis-statistik-komoditas-beras-provinsi-jawa-barat-2019.html
Jumlah Penduduk di jawa barat:
https://jabar.bps.go.id/indicator/12/731/1/jumlah-penduduk-hasil-proyeksi-interim-di-provinsi-jawa-barat-menurut-kabupaten-kota-dan-jenis-kelamin.html
UMP:
https://www.detik.com/jabar/berita/d-7048595/menengok-besaran-ump-jabar-5-tahun-terakhir
Harga Beras: 
https://www.bi.go.id/hargapangan/TabelHarga/PasarTradisionalKomoditas
Data Supply:
https://panelharga.badanpangan.go.id/harga-produsen

=======================================================================

Random Forest (durasi agak lama sedikit)

Memakai GridSearchCV untuk hyperparameter
Pembagian data actual:data testing = 80:20

# Initialize the RandomForestRegressor
rf = RandomForestRegressor(random_state=42)
# Setup GridSearchCV
grid_search = GridSearchCV(estimator=rf, param_grid=param_grid, cv=5, scoring='neg_mean_squared_error', verbose=1)

best_model = RandomForestRegressor(max_depth=10, n_estimators=50, random_state=42)
best_score = -63894.20518210005
best_params = ’max_depth': 10, 'min_samples_split': 2, 'n_estimators': 50

Semua fitur:
RMSE: 1176.80
MAE: 958.96
r2 =  -1.8949
MSE: 1384875.01
Fitur Importance:
Harga Beras Penggilingan
GKP Tingkat Penggilingan
Produksi Beras

ex. GKP Tingkat Penggilingan:
RMSE: 1170.33
MAE: 953.13
r2: -1.8632
MSE: 1369686.40
Fitur Importance:
Harga Beras Penggilingan
Tingkat Konsumsi
UMP

ex. GKG Tingkat Penggilingan:
RMSE: 1191.16
MAE: 970.56
r2: -1.9660
MSE: 1418885.49
Fitur Importance:
Harga Beras Penggilingan
GKP TIngkat Penggilingan
Tingkat Konsumsi

ex. GKP Tingkat Petani:
RMSE: 1173.58
MAE: 955.95
r2: -1.8791
MSE: 1377290.47
Fitur Importance:
Harga Beras Penggilingan
GKP Tingkat Penggilingan
UMP

ex. GKP Tingkat Petani, GKG Tingkat Penggilingan, GKP Tingkat Penggilingan:
RMSE: 1186.76
MAE: 966.56
r2: -1.9441
MSE: 1408403.17
Fitur Importance:
Harga Beras Penggilingan
UMP
Month

ex. GKG Tingkat Penggilingan, GKP Tingkat Penggilingan:
RMSE: 1191.09
MAE: 970.77
r2: -1.9657
MSE: 1418716.99
Fitur Importance:
Harga Beras Penggilingan
Year
UMP

ex. GKP Tingkat Petani, GKP Tingkat Penggilingan:
RMSE: 1161.56
MAE: 945.73
r2: -1.8204
MSE: 1349233.19
Fitur Importance:
Harga Beras Penggilingan
Month
Year

ex. GKP Tingkat Petani, GKG Tingkat Penggilingan:
RMSE: 1188.72
MAE: 968.42
r2: -1.9539
MSE: 1413078.03
Fitur Importance:
Harga Beras Peggilingan
GKP Tingkat Penggilingan
Year

=======================================================================

XGBoost (Extreme Gradient Boosting): (durasi cepat)

Memakai GridSearchCV untuk hyperparameter
Pembagian data actual:data testing = 80:20

# Initialize XGBRegressor
xgb = XGBRegressor(random_state=42)
# Setup GridSearchCV
grid_search = GridSearchCV(estimator=xgb, param_grid=param_grid, cv=5, scoring='neg_mean_squared_error', verbose=1)

best_model: XGBRegressor(base_score=None, booster=None, callbacks=None,
              colsample_bylevel=None, colsample_bynode=None,
              colsample_bytree=None, device=None, early_stopping_rounds=None,
              enable_categorical=False, eval_metric=None, feature_types=None,
              gamma=None, grow_policy=None, importance_type=None,
              interaction_constraints=None, learning_rate=0.05, max_bin=None,
              max_cat_threshold=None, max_cat_to_onehot=None,
              max_delta_step=None, max_depth=3, max_leaves=None,
              min_child_weight=None, missing=nan, monotone_constraints=None,
              multi_strategy=None, n_estimators=100, n_jobs=None,
              num_parallel_tree=None, random_state=42, ...)
best_score: -109167.54564287179
best_params: 'learning_rate': 0.05, 'max_depth': 3, 'n_estimators': 100

Semua Fitur:
RMSE: 1178.81
MAE: 961.11
r2: -1.9048
MSE: 1389609.34
Fitur Importance:
Harga Beras Penggilingan
GKG Tingkat Penggilingan
GKP TIngkat Penggilingan

ex. GKP Tingkat Penggilingan:
RMSE: 1147.69
MAE: 935.73
r2: -1.7535
MSE: 1317208.88
Fitur Importance:
Harga Beras Penggilingan
Produksi Beras
GKG Tingkat Penggilingan

ex. GKG Tingkat Penggilingan:
RMSE: 1211.05
MAE: 988.24
r2: -2.0659
MSE: 1466653.93
Fitur Importance:
Harga Beras Penggilingan
Produksi Beras
Month

ex. GKP Tingkat Petani:
RMSE: 1190.42
MAE: 971.84
r2: -1.9623
MSE: 1417110.25
Fitur Importance:
Harga Beras Penggilingan
Produksi Beras
Month

ex. GKP Tingkat Petani, GKG Tingkat Penggilingan, GKP Tingkat Penggilingan:
RMSE: 1158.34
MAE: 941.58
r2: -1.8048
MSE: 1341755.00
Fitur Importance:
UMP
Harga Beras Penggilingan
Produksi Beras

ex. GKG Tingkat Penggilingan, GKP Tingkat Penggilingan:
RMSE: 1167.45
MAE: 954.09
r2: -1.8491
MSE: 1362945.40
Fitur Importance:
Harga Beras Penggilingan
UMP
Produksi Beras

ex. GKP Tingkat Petani, GKP Tingkat Penggilingan:
RMSE: 1142.65
MAE: 930.90
r2: -1.7294
MSE: 1305668.81
Fitur Importance:
Harga Beras Penggilingan
Produksi Beras
Month

ex. GKP Tingkat Petani, GKG Tingkat Penggilingan:
RMSE: 1203.84
MAE: 983.18
r2: -2.0295
MSE: 1449252.15
Fitur Importance:
Harga Beras Penggilingan
Produksi Beras
UMP

========================================================================

GBM (Gradient Boosting Machines): (Cepat juga)

Memakai GridSearchCV untuk hyperparameter
Pembagian data actual:data testing = 80:20

# Initialize GradientBoostingRegressor
gbm = GradientBoostingRegressor(random_state=42)
# Setup GridSearchCV
grid_search = GridSearchCV(estimator=gbm, param_grid=param_grid, cv=5, scoring='neg_mean_squared_error', verbose=1)

best_model: GradientBoostingRegressor(learning_rate=0.2, random_state=42)
best_score:  -65602.10279055897
best_params: 'learning_rate': 0.2, 'max_depth': 3, 'n_estimators': 100

Semua Fitur: 
RMSE: 1186.09
MAE: 971.82
r2: -1.9408
MSE: 1406810.24
Fitur Importance:
Harga Beras Penggilingan
GKP Tingkat Penggilingan
GKG TIngkat Penggilingan

ex. GKP TIngkat Penggilingan:
RMSE: 1172.65
MAE: 958.81
r2: -1.8746
MSE: 1375124.90
FItur Importance:
Harga Beras Penggilingan
GKG TIngkat Penggilngan
Month

ex. GKG Tingkat Pengggilingan:
RMSE: 1241.58
MAE: 1016.47
r2: -2.2224
MSE: 1541539.45
Fitur Importance:
Harga Beras Penggilingan
GKP Tingkat Penggilingan
Month

ex. GKP Tingkat Petani:
RMSE: 1133.45
MAE: 924.53
r2: -1.6856
MSE: 1284728.50
FItur Importance:
Harga Beras Penggilingan
GKG TIngkat Penggilingan
GKP TIngkat Penggilingan

ex. GKP Tingkat Petani, GKG Tingkat Penggilingan, GKP Tingkat Penggilingan:
RMSE: 1164.85
MAE: 948.87
r2: -1.8365
MSE: 1356896.73
Fitur Importance:
Harga Beras Penggilingan
Month
Year

ex. GKG Tingkat Penggilingan, GKP Tingkat Penggilingan:
RMSE: 1174.33
MAE: 960.52
r2: -1.8828
MSE: 1379066.77
Fitur Importance:
Harga Beras Penggilingan
Month
Produksi Beras

ex. GKP Tingkat Petani, GKP Tingkat Penggilingan:
RMSE: 1111.00
MAE: 903.20
r2: -1.5803
MSE: 1234342.76
Fitur Importance:
Harga Beras Penggilingan
GKG Tingkat Penggilingan
Month

ex. GKP Tingkat Petani, GKG Tingkat Penggilingan:
RMSE: 1247.49
MAE: 1022.76
r2: -2.2531
MSE: 1556232.13
Fitur Importance:
Harga Beras Penggilingan
GKP TIngkat Penggilingan
Month
