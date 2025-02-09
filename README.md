![cover](https://user-images.githubusercontent.com/11289173/196726512-f1994677-141e-4d24-bdbe-887146d323b5.jpg)
# HW 2: Image of Buddha Classification using pre-trained CNN Models

Simple overview of use/purpose.

## Data Source
Collect image from google search 1,852 picture of image of budha for each day and split data using systematic ramdom using ranking of file name.

| Class |  Day  |  Thai name   |  Image  |   Train 60%  |  Validate 20% |  Test 20% |
|-------|-------|--------------|---------|--------------|---------------|-----------|
|0| Mon |ปางห้ามญาติ| ![image](https://user-images.githubusercontent.com/11289173/196733095-d78b9c54-7139-41da-a143-96bea98d7611.png)  |     115  |      37    |   39   |
|1| Tue |ปางไสยาสน์| ![image](https://user-images.githubusercontent.com/11289173/196733034-2cbeaa66-de22-4092-b816-47ec31877fc9.png)  |     113  |      37    |   39   |
|2| Wed (m) |ปางอุ้มบาตร|![image](https://user-images.githubusercontent.com/11289173/196732976-12ecf1b9-cf73-41c5-9aba-b3a330c837c9.png) |     112  |      38    |   39   |
|3| Wed (n) |ปางป่าเลไลยก์|![image](https://user-images.githubusercontent.com/11289173/196732933-e860abec-6c15-4d9e-bbcf-702a01f62c7a.png) |     112  |      39    |   38   |
|4| Thu |ปางสมาธิ|![image](https://user-images.githubusercontent.com/11289173/196732862-26045f14-9e69-4b38-a481-ff9118f39327.png)    |     125  |      42    |   40   |
|5| Fri |ปางรำพึง|![image](https://user-images.githubusercontent.com/11289173/196732785-7ab8ddef-6297-4d16-8d8b-8decee45eeff.png)   |     202  |      69    |   68   |
|6| Sat |ปางนาคปรก|![image](https://user-images.githubusercontent.com/11289173/196732737-b120c7bb-595c-40d1-a34d-3ea01b8840d1.png)    |     157  |      51    |   54   |
|7| Sun |ปางถวายเนตร|![image](https://user-images.githubusercontent.com/11289173/196732323-a4eebc69-7fef-4727-a8b8-d04f94bb6522.png) |     184  |      63    |   63   |


Source : see reference.xlsx


## Methodology
[Image of process flow]
0. set seed
 1111,2222,3333

1. Data Gathering and Labeling 
  1.1 Split data 60:20:20  Train Test validation
2. Image augmentation and standard preprocessing
  2.1 rescale (if there is no scaling action in model preprocessing)
  2.2 Image augmentation
        -RandomFlip("horizontal")
        -RandomRotation(0.1)
        -Normalization()
        -RandomFlip("horizontal")
        -RandomRotation(factor=0.1)
        -RandomContrast(factor=0.1)
        -RandomZoom(height_factor=0.2, width_factor=0.2)
  2.3 Apply standadard preprocessing for each model
  
3. Select 2 well-known CNN models, VGG16 and XXXXX with pre-trained imagenet  weight and remove classification layer set
  3.1 Select base model
    - VGG16 : Freeze all feature extraction layers
    - Xception : Freeze all feature extraction layers
  3.2 Added dense layers to perform clasification tasks
       - Dense512 relu -> dropout0.4-> Sense 128 relu -> dropout 0.4 -> Dense 64  Relu -> Dense 8  softmax
       - Optimizer = Adam
       - Loss function = categorical_crossentropy
       - Metric = Accuracy
       
![image](https://user-images.githubusercontent.com/11289173/196020339-00d0b629-ec92-4a18-ab36-70e4124f1ea4.png)

8. Train Model
  6.1 Image of Buddha
   - Image size vary by model
   - batch size vary by model
   - Epoch vary by model
   
   |   Model  | Image size | batch size | Epoch | Remark |
   |----------|------------|------------|-------|--------|
   | Xception |  299 * 299 |    16      |   300 |        |
   | VGG16    |  256 * 256 |    16      |   300 |        |
   
9. Evaluate model

### Result for each Model
Processor : Tesla T4


  |  Model | Dataset  | Records |   Lost   | Accuracy | Train Time (s) | Pretrained Accuracy |
  |--------|----------|---------|----------|----------|----------------|---------------------|
  | VGG16  | Train    |   1,112 |0.3363±0.04|0.8735±0.01|    1,019±8  |                      |
  | VGG16  | Validate |     368 |1.1404±0.06|0.7446±0.01|       N/A    |                     |
  | VGG16  | test     |     372 |1.2113±0.15|0.7301±0.01|       N/A    |                     | 


### Comparison



## Team Members

6410422014 (%)

6410422012 (%)

6410422019 (%) 

6410422023 (%)

6410422035 (%)

This project is a part of subject DADS7202. Data Analytics and Data Science. NIDA



## Acknowledgments

Inspiration, code snippets, etc.
* [Network Drawing tool](https://alexlenail.me/NN-SVG/AlexNet.html)
