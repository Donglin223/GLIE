# Global-to-Local Modeling for Pedestrian Detection

## Introduction

Pedestrian detection is a classic problem in computer vision, which aims at locating the pedestrian position from the given image or video. Current state-of-the-art methods concentrate on capturing human body contexts from the local view, which however remain challenging in extracting the complex shape and variable proportions of the human body information. In this paper, we advocate to encode the complementary pedestrian contexts and adaptive fuse closely related features at the global level. We also design a local feature extraction module to handle the complex body shape and aggregate different resolution features. Moreover, most existing methods consider generating detection results from a single resolution information, disregarding the diversity of features. Motivated by this, we present a novel detection module that captures various cues from multiresolution features to obtain satisfactory pedestrian contexts. Empirical results demonstrate that our model outperforms state-ofthe-art pedestrian detection methods on four benchmark datasets, including PASCAL VOC2012, CityPersons, WiderPerson, and Crowdhuman datasets. Our code is released at https://github.com/Donglin223/GLIE.

## Dependencies

```
Python: 3.9
Pytorch: 1.13.1
cuda:11.6
```

## Datasets

We use four pedestrian detection benchmark datasets, including PASCAL VOC2012, CityPersons, WiderPerson, and Crowdhuman datasets, to evaluate GLIE.

PASCAL VOC2012：http://host.robots.ox.ac.uk/pascal/VOC/voc2012/

CityPersons：https://opendatalab.com/OpenDataLab/CityPersons

WiderPerson：http://www.cbsr.ia.ac.cn/users/sfzhang/WiderPerson/

Crowdhuman ：https://www.crowdhuman.org/

## Train

All the training sets are defined in [train.py](https://github.com/Donglin223/GLIE/blob/master/train.py) ,If you want to modify other profile settings you can enter the [default.yaml](https://github.com/Donglin223/GLIE/blob/master/ultralytics/cfg/default.yaml). We use following commands to train on different datasets and representations.

```python
python train.py
```

## **Evalution and visualize results**

+ evaluate our model:

  ```
  python val.py
  ```

+ visualize the results: 

  + visualize the bounding box:

    ```
    python plot_result.py
    ```

  + visualize the heat map:

  ```
  python heatmap.py
  ```

## Results

**PASCAL VOC2012**

|                     | AP(%)    | AP~50~(%) | AP~75~(%) | AP~S~(%) | AP~M~(%) | AP~L~(%) |
| :-----------------: | -------- | --------- | --------- | -------- | -------- | -------- |
|    Faster R-CNN     | 61.2     | 88.1      | 68.7      | 36.6     | 55.2     | 69.8     |
|      RetinaNet      | 63.8     | 89.5      | 70.6      | 35.6     | 58.4     | 72.5     |
|    Cascade R-CNN    | 65.1     | 88.8      | 72.4      | 40.2     | 59.3     | 74.1     |
|   DH Faster R-CNN   | 64.7     | 89.7      | 71.7      | 39.9     | 58.6     | 73.5     |
| Libra Faster  R-CNN | 63.3     | 89.6      | 72.1      | 41.4     | 59.0     | 70.4     |
|        YOLOf        | 66.6     | 90.7      | 74.3      | 35.8     | 60.5     | 75.7     |
|      Vfnet(ms)      | 70.0     | 91.3      | **77.3**  | 44.2     | 64.5     | 78.0     |
|  Sparse R-CNN(ms)   | 66.1     | 89.3      | 73.2      | 37.6     | 58.6     | 77.3     |
|      TOOD(ms)       | 68.4     | 89.3      | 75.4      | 44.1     | 64.5     | 75.7     |
|        PVDet        | 69.9     | 91.3      | 76.9      | 41.2     | 63.9     | 78.4     |
|      YOLOv5-s       | 57.5     | 79.5      | 50.1      | 41.6     | 61.0     | 72.6     |
|      **GLIE**       | **72.6** | **96.3**  | 75.9      | **56.7** | **74.0** | **86.7** |

![PASCALVOC20122](assets/PASCALVOC20122.png)

**widerPerson**

|                       |    F1    | mAP~50~(%) | mAP~50：95~(%) | GFLOPS   | Params    | FPS    |
| :-------------------: | :------: | ---------- | -------------- | -------- | --------- | ------ |
|        YOLOv7         |   0.72   | 76.7       | 45.6           | 106.3    | 37.6M     | **81** |
|  YOLOv7+Multi-Scale   |   0.74   | 78.9       | 48.1           | 119.5    | 37.8M     | 65     |
|  Previous+2×BTDetect  |   0.76   | 79.6       | 49.4           | 119      | 38.0M     | 68     |
| RT-YOLO(Previous+NAM) |   0.78   | 80.1       | 49.6           | 119.1    | 39.6M     | 67     |
|     YOLOv5s+G^2^      |    /     | 76.9       | 48.3           | **13.7** | /         | /      |
|       **GLIE**        | **0.80** | **84.0**   | **57.2**       | 89.8     | **36.1M** | 70     |

![widerPerson](assets/widerPerson.png)

**Cityperson**

|              | mAP~50~(%) | AP(%)    | Precision(%) | Recall(%) |
| :----------: | ---------- | -------- | ------------ | --------- |
| Faster R-CNN | /          | 67.4     | 69.4         | 63.6      |
|     SSD      | /          | 59.8     | 61.7         | 56.8      |
|    YOLOv4    | /          | 68.4     | 70.9         | 67.2      |
|  YOLOv4+TP   | /          | **72.9** | 73.7         | **69.4**  |
|  SE-YOLOv4   | /          | 71.3     | /            | /         |
|   YOLOv5-s   | 72.6       | 69       | 77.3         | 63.7      |
|   **GLIE**   | **75.9**   | **72.9** | **80.4**     | 67        |

![Cityperson](assets/Cityperson.png)

**crowdhuman**

|              |  Params   |  GFLOPS  | mAP~50~(%) | mAP~50：95~(%) |  FPS   |
| :----------: | :-------: | :------: | :--------: | :------------: | :----: |
|     SSD      | **34.3M** |  386.2   |    69.6    |      35.5      |   41   |
|  RetinaNet   |   45.7M   |  218.3   |    76.1    |      45.7      |   50   |
| Faster R-CNN |   41.5M   |  207.1   |    79.3    |      46.6      |   52   |
|   SOLIDER    |   43.9M   |  259.5   |    82.2    |       /        |   19   |
|   YOLOv5-l   |   46.5M   |  109.1   |    80.2    |      50.4      |   71   |
|   YOLOvX-l   |   54.2M   |  155.6   |    81.0    |      49.0      |   45   |
|    YOLOv7    |   37.6M   |  106.5   |    83.1    |      52.3      | **81** |
|   YOLOv8-l   |   43.7M   |  165.2   |    86.3    |      56.5      |   68   |
|   RT-Yolo    |   39.6M   |  119.1   |    86.9    |      57.2      |   67   |
|   **GLIE**   |   36.1M   | **89.8** |  **87.0**  |    **58.3**    |   70   |

![crowdhuman](assets/crowdhuman.png)

voc_data:https://github.com/Donglin223/GLIE/blob/master/images/PASCAL%20VOC2012-data.png

voc:https://github.com/Donglin223/GLIE/blob/master/images/PASCALVOC20122.png

widerperson_data:https://github.com/Donglin223/GLIE/blob/master/images/widerPerson-data.png

widerperson:https://github.com/Donglin223/GLIE/blob/master/images/widerPerson.png

cityperson_data:https://github.com/Donglin223/GLIE/blob/master/images/Cityperson-data.png

cityperson:https://github.com/Donglin223/GLIE/blob/master/images/Cityperson.png

crowdhuman_data:https://github.com/Donglin223/GLIE/blob/master/images/crowdhuman-data.png

crowdhuman:https://github.com/Donglin223/GLIE/blob/master/images/crowdhuman.png
