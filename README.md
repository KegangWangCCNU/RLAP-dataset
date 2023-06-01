# RLAP: Remote Learning Affect and Physiologic dataset  

The Remote Learning Affect and Physiologic (RLAP) dataset is a dataset applied to remote learning affect and engagement, which contains learners' blood volume pulse (BVP) signals that are highly synchronized. This dataset is suitable for training neural rPPG algorithms.  

## Efficient remote physiological sensing training set  

In recent years, remote physiological sensing has received increasing attention, especially the algorithms using neural networks. However, training a model for extracting physiological signals is not easy. The lack of high-quality datasets limits the development of advanced algorithms, and many models have to add some modules to fight against the "noise" in the dataset. The main noises are: offset caused by no strict synchronization between cameras and physiological signal sensors; data loss during video compression due to device's unsupported or incorrect settings. The RLAP dataset is collected using PhysRecorder to minimize any adverse factors for model training as much as possible. According to PhysBench's experimental results, this is known as the best training set so far.

## RLAP dataset  

The RLAP dataset includes videos of 58 student participants involved in a series of tasks, collected using PhysRecorder software with Logitech C930c webcam and Contec CMS50E pulse oximeter, released as an ISO image.

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

## FIle structure  

```
RLAP.iso
├── p001
    ├── R1                          # Relaxed.
        ├── pictures_ZIP_RAW_RGB    # Raw RGB video.
                  ├── 00000000.png  # PNG lossless format.
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
```
