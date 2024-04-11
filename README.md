# Global-to-Local Modeling for Pedestrian Detection

## Introduction

Pedestrian detection is a classic problem in computer vision, which aims at locating the pedestrian position from the given image or video. Current state-of-the-art methods concentrate on capturing human body contexts from the local view, which however remain challenging in extracting the complex shape and variable proportions of the human body information. In this paper, we advocate to encode the complementary pedestrian contexts and adaptive fuse closely related features at the global level. We also design a local feature extraction module to handle the complex body shape and aggregate different resolution features. Moreover, most existing methods consider generating detection results from a single resolution information, disregarding the diversity of features. Motivated by this, we present a novel detection module that captures various cues from multiresolution features to obtain satisfactory pedestrian contexts. Empirical results demonstrate that our model outperforms state-ofthe-art pedestrian detection methods on four benchmark datasets, including PASCAL VOC2012, CityPersons, WiderPerson, and Crowdhuman datasets. Our code is released at https://github.com/Donglin223/GLIE_Model.

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

**PASCALVOC**

![https://github.com/Donglin223/GLIE/blob/master/images/PASCAL VOC2012-data.png](https://github.com/Donglin223/GLIE/blob/master/images/PASCAL%20VOC2012-data.png)

![PASCALVOC](https://github.com/Donglin223/GLIE/blob/master/images/PASCALVOC2012.png)

**WiderPerson**


![assets/widerPerson.png](https://github.com/Donglin223/GLIE/blob/master/images/widerPerson-data.png)

![https://github.com/Donglin223/GLIE/blob/master/images/widerPerson-data.png](https://github.com/Donglin223/GLIE/blob/master/images/widerPerson.png)
**Cityperson**

![assets/crowdhuman.png](https://github.com/Donglin223/GLIE/blob/master/images/Cityperson-data.png)

![https://github.com/Donglin223/GLIE/blob/master/images/Cityperson-data.png](https://github.com/Donglin223/GLIE/blob/master/images/Cityperson.png)


**Crowdhuman**


![https://github.com/Donglin223/GLIE/blob/master/images/Cityperson-data.png](https://github.com/Donglin223/GLIE/blob/master/images/crowdhuman-data.png)

![https://github.com/Donglin223/GLIE/blob/master/images/Cityperson.png](https://github.com/Donglin223/GLIE/blob/master/images/crowdhuman.png)


**Heatmap**

![heatmap](https://github.com/Donglin223/GLIE/blob/master/images/heatmap.png)
