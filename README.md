# Bond-risk-premiums

# NN 저자 code 고려
Google Colab
MC = 2, AVG = 1, epoch 500 
R2 OOS and p-values:
             xr24      xr36      xr48      xr60      xr84     xr120
R2_oos   0.061935 -0.060574 -0.319362 -0.036126 -0.140257 -0.137511
p_value  0.003060  0.099353  0.524112  0.082373  0.063736  0.518650

# NN 내가 혼자 짜본거. 저자 code 고려 안함
Google Colab
single model (learning_rate=0.001, batch_size=32, validation_split=0.15, loss='mse'), epoch 500 
       xr24      xr36      xr48      xr60      xr84     xr120
0 -0.870831 -0.818162 -0.849705 -0.837254 -0.810891 -0.803931
