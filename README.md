# RLAP: Remote Learning Affect and Physiologic dataset  

The Remote Learning Affect and Physiologic (RLAP) dataset is a dataset applied to remote learning affect and engagement, which contains learners' blood volume pulse (BVP) signals that are highly synchronized. This dataset is suitable for training neural rPPG algorithms.  

## Efficient remote physiological sensing training set  

In recent years, remote physiological sensing has received increasing attention, especially the algorithms using neural networks. However, training a model for extracting physiological signals is not easy. The lack of high-quality datasets limits the development of advanced algorithms, and many models have to add some modules to fight against the "noise" in the dataset. The main noises are: offset caused by no strict synchronization between cameras and physiological signal sensors; data loss during video compression due to device's unsupported or incorrect settings. The RLAP dataset is collected using PhysRecorder to minimize any adverse factors for model training as much as possible. According to PhysBench's experimental results, this is known as the best training set so far.

## PhysRecorder recording tool
If you want to learn about the details of data collection and hardware & software equipment, or collect your own dataset using the same method, please visit https://github.com/KegangWangCCNU/PhysRecorder

## RLAP dataset  

The RLAP dataset includes videos of 58 student participants involved in a series of tasks, collected using PhysRecorder software with Logitech C930c webcam and Contec CMS50E pulse oximeter, released as an ISO image.

## Samples  

|1|2|3|4|5|6|7|8|9|
|-|-|-|-|-|-|-|-|-|  
|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/1_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/2_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/3_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/4_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/5_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/6_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/7_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/8_.jpg?raw=true)|![image](https://github.com/KegangWangCCNU/PICS/blob/main/examples/9_.jpg?raw=true)|

## Experiment procedure  

|Step|Label|Task|Duration(S)|  
|-|-|-|-|  
|1|R1|Relaxed|120|  
|2|R2|Relaxed (dark)|120|  
|3|R3|Play a game|120|    
|4|R4|Read an article|120|  
|5|E1|Watch natural sceneries|120|  
|6|E2|Watch a puzzle game|180|  
|7|E3|Watch a comedy|120|  
|8|E4|Watch an illusion picture|20|  
|9|E5|Watch an academic paper|60|  
|10|E6|Watch yawn videos|60|  
|11|T1|Video-based learning|240|  
|12|T2|Textbook-based learning|480|  
|13|T3|Watch a public class|420|  

## File structure  

```
RLAP.iso
├── p001
    ├── R1                          # Relaxed.
        ├── pictures_ZIP_RAW_RGB    # Raw RGB video.
            ├── 00000000.png        # PNG lossless format.
            ├── 00000001.png
            ├── ...
        ├── video_ZIP_H264.mp4      # H264 format.
        ├── video_ZIP_MJPG.avi      # MJPG format.
        ├── BVP.csv                 # BVP wavefrom with UNIX timestamps.
        ├── frames_timestamp.csv    # UNIX timestamps for each frame.
        ├── info.txt                # Information related to video recording.
        ├── missed_frames.csv       # If all frames are written correctly to the file, it is empty. 
    ├── ... 
    ├── E1
    ├── ... 
    ├── T3
├── ...
├── p058
├── EEQ_Emotion ···.csv             # Self-emotion report form for each participant.
├── participants.csv                # Basic information of each participant, without involving privacy.
├── EEQ.mp4                         # Video materials for guiding spontaneous emotional expression.
```

## Dataset Partition  
Please download the `Dataset Nutrition Label.ods`, which includes the division of each sample. Fold 0 and fold 4 are used for validation and testing, while folds 1, 2, and 3 are used for training.  

**A small amount of excluded data is marked as -1 fold.**  

## Request and download RLAP dataset  
If you wish to obtain the RLAP dataset, please send an email to kegangwang@mails.ccnu.edu.cn and cc yantaowei@ccnu.edu.cn, with the [Data Usage Agreement](https://github.com/KegangWangCCNU/RLAP-dataset/blob/main/RLAP%20Data%20Usage%20Agreement.pdf) attached. 
Once you obtain the permission, you will receive a signed link. The signature is valid for 14 days, please download as soon as possible.  
`wget -c https://dataport.kegang.wang/RLAP.iso?auth=<your_sign> -O RLAP.iso`  
`SHA256: b67813294cc08d8b9b55604d9a88caff9d1d09921a96c4e872088997f45ccd46`  
The entire file is approximately 642GB, supports resumable downloads, and if the download is interrupted, re-entering the above command will continue downloading from where it left off.  

## Mount RLAP dataset  
For Windows users, simply open RLAP.iso with File Explorer to automatically mount it.  
For Linux users, please create an empty folder for mounting.  
```
sudo mkdir ./RLAP 
sudo mount ./RLAP.iso ./RLAP -o loop
cd RLAP
```
It is not recommended to use software like 7-zip to extract files.

## Training framework  

It is recommended to use the PhysBench framework for training, which supports the RLAP dataset and multiple public datasets.  
https://github.com/KegangWangCCNU/PhysBench

## Citation  

If you use PLAP dataset, please cite the following <a href="https://github.com/KegangWangCCNU/PICS/raw/main/PhysBench.pdf" target="_blank">paper</a>
```
@misc{wang2024camerabasedhrvpredictionremote,
      title={Camera-Based HRV Prediction for Remote Learning Environments}, 
      author={Kegang Wang and Yantao Wei and Jiankai Tang and Yuntao Wang and Mingwen Tong and Jie Gao and Yujian Ma and Zhongjin Zhao},
      year={2024},
      eprint={2305.04161},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2305.04161}, 
}
```
