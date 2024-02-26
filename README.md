# Competition-AICUP2022-CropStatusMonitoringByImageRecognition

Source code from 2022 AI CUP Competition on Crop Status Monitoring by Image Recognition.
競賽網站：https://aidea-web.tw/topic/5f632f38-7213-4d4d-bea3-117ff13c1afb

1. 請使用 Anaconda 安裝 Python 3.9.15，並安裝 JupyterLab 或 JupyterNotebook
	Anaconda: https://www.anaconda.com/products/distribution

2. 需額外安裝的套件及函式庫：
    - CUDA 11.7：https://developer.nvidia.com/cuda-11-7-0-download-archive
    - PyTorch 1.13：https://pytorch.org/get-started/locally/
    - 使用pip安裝：numpy, tqdm, pillow, scikit-learn, tensorboard, pandas

3. 資料前處理方法：
    1. 先將影像資料放至 dataset\jpg\ [training, test_public, test_private]
    2. 使用 crop_images_training.ipynb 與 crop_images_test.ipynb 將影像進行裁切並輸出，檔案會存在後綴為 cropped 的資料夾
    3. 在 dataset\training.json 已有切分成 train/valid 的資料，可直接執行 make_npz_training.ipynb 來製作 training_cropped_480x480.npz，
       如有需要也能執行 split_train_valid.ipynb 來重新切分資料
    4. 執行 make_npz_test.ipynb 來製作 test_public_cropped_480x480.npz 與 test_private_cropped_480x480.npz

4. 訓練方法：
    1. 訓練程式位於 experiments\efficientnetv2_s.ipynb
    2. 從第 1 儲存格直接執行到第 9 儲存格並開始訓練，過程中會繪製 Accuracy/Loss 曲線，以及保存 best_acc, best_loss 與 last 的權重
    3. 訓練完成後，執行下方儲存格來保存模型
    4. 可使用第 11~13 儲存格來測試在 validation 資料的性能
    5. 執行第 14 儲存格可以查看 Accuracy/Loss 曲線

5. 測試方法：
    1. 測試程式位於 experiments\test_on_test_dataset.ipynb
    2. 從第 1 儲存格開始執行，在第 5 儲存格的 model_name 要改成欲測試的模型名稱