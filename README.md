# Speech_Recognition-PyTorch
## 一、作法說明
### 1.資料預處理
由於直接縮短音檔長度訓練會導致音檔與utterance不匹配，因此直接移除長度過長的訓練集以加快訓練速度。
### 2. 資料集切割
dataset_partition由@[Chen-Yen Chang BlackyYen](https://github.com/BlackyYen/Dataset_Partition)友情贊助！！  
切割訓練集與測試集9:1。
### 3. 特徵擷取
1. 固定所有訓練資料長度，避免記憶體用量忽高忽低。
2. MelSpectrogram擷取特徵(sample_rate=16000, n_mels=128, n_fft=400)，對訓練資料隨機加入時間與頻率遮罩以增加模型泛化能力。
## 二、模型架構
DeepSpeech2  
![DeepSpeech2](https://github.com/BlackyYen/Speech_Recognition-PyTorch/blob/Jack/images/deepspeech2(1).png?raw=true)  
## 三、實驗與結果
![lr](https://github.com/BlackyYen/Speech_Recognition-PyTorch/blob/Jack/images/rnn7-rnndim1024-drop0.1/train_learning_rate.jpeg?raw=true)
OneCycleLR每個mini batch更新學習率。
![Loss](https://github.com/BlackyYen/Speech_Recognition-PyTorch/blob/Jack/images/rnn7-rnndim1024-drop0.1/loss.jpg?raw=true)
![驗證WER驗證WER](https://github.com/BlackyYen/Speech_Recognition-PyTorch/blob/Jack/images/rnn7-rnndim1024-drop0.1/wer.jpg?raw=true)  
雖然以訓練驗證損失來看有明顯的overfitting發生，但在驗證的WER上卻還是逐漸價降，詳細實驗數據可至[comet](https://www.comet.ml/jerryjack121/speech/8d7af6e924ba4bf08086b225506f33c2?experiment-tab=chart&showOutliers=true&smoothing=0&transformY=smoothing&viewId=0Az4gwmjBfiXAHGwodKdCQqBg&xAxis=epoch)平台上查看。
## 四、Acknowledgements
1. ##### [Speech_Recognition-PyTorch](https://github.com/BlackyYen/Speech_Recognition-PyTorch) @[Chen-Yen Chang BlackyYen](https://github.com/BlackyYen)
2. ##### [pytorch載入語音類自定義資料集](https://www.it145.com/9/56376.html) @[sddin@qq.com]
3. ##### [利用 AssemblyAI 在 PyTorch 中建立端到端的語音識別模型](https://cloud.tencent.com/developer/article/1645492) @[Comet]
4. ##### [編輯距離WER/CER計算的一種python實現](https://blog.csdn.net/baobao3456810/article/details/107381052) @[zwglory](https://blog.csdn.net/baobao3456810)
5. ##### [HResults計算字錯率(WER)、句錯率(SER)](https://www.cnblogs.com/findyou/p/10646312.html)  @[Findyou](https://home.cnblogs.com/u/findyou/)
6. ##### [語音識別CER計算](https://zhuanlan.zhihu.com/p/114414797) @[Jack](https://www.zhihu.com/people/honher)
## 五、Reference
1. ##### [Deep Speech 2 : End-to-End Speech Recognition in English and Mandarin. Proceedings of The 33rd International Conference on Machine Learning, in PMLR 48:173-182](http://proceedings.mlr.press/v48/amodei16) @[Amodei, D., nanthanarayanan, S., Anubhai, R., Bai, J., Battenberg, E., Case, C., Casper, J., Catanzaro, B., Cheng, Q., Chen, G., Chen, J., Chen, J., Chen, Z., Chrzanowski, M., Coates, A., Diamos, G., Ding, K., Du, N., Elsen, E., Engel, J., Fang, W., Fan, L., Fougner, C., Gao, L., Gong, C., Hannun, A., Han, T., Johannes, L., Jiang, B., Ju, C., Jun, B., LeGresley, P., Lin, L., Liu, J., Liu, Y., Li, W., Li, X., Ma, D., Narang, S., Ng, A., Ozair, S., Peng, Y., Prenger, R., Qian, S., Quan, Z., Raiman, J., Rao, V., Satheesh, S., Seetapun, D., Sengupta, S., Srinet, K., Sriram, A., Tang, H., Tang, L., Wang, C., Wang, J., Wang, K., Wang, Y., Wang, Z., Wang, Z., Wu, S., Wei, L., Xiao, B., Xie, W., Xie, Y., Yogatama, D., Yuan, B., Zhan, J. and Zhu, Z.]

以上圖片部分是引用自網路，如有侵權請立即告知，會立即刪除。謝謝您！