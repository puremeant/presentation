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

# script
The original paper uses high-performance computing and parallelizes the estimation of the **100 neural networks** at each forecast date and uses model averaging to reduce sensitivity to random initialization. In my extension, I first replicate this forecasting design to report **simpler single-model results as a robustness check**. **A naive single feedforward NN without model averaging performs poorly.** This is why the original paper relies on regularization, validation-based selection, and forecast averaging. Averaging the top-performing networks is a reasonable ensemble strategy, but it may also introduce validation-selection risk. 
Because fully flexible deep architectures are computationally expensive and may overfit, my extension focuses not on making the static network deeper, but on changing the information structure: I allow the model to use historical yield-curve paths through an RNN.

# RNN
RNN seed 0, 1, 2, 3, 4 정도만 돌려서 R2 분포 확인
The improvement should be interpreted as evidence that **historical yield-curve paths contain additional predictive information**. The authors’ best one-layer NN benchmark for the 10-year maturity achieves an out-of-sample R^2 of 26.4%, despite using a top-10 ensemble over 100 neural networks. In my preliminary results, a single RNN trained under the same yield-only forecasting setting produces a higher R^2_{OOS}. This suggests that the historical path of the yield curve may contain information not fully captured by static feedforward neural networks.
