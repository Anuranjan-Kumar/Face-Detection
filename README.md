# Face and Facial features extraction using MTCNN 

Face detection is a computer vision problem that involves finding faces in photos.

It is a trivial problem for humans but indeed a challenging one for machines. More recently deep learning methods have achieved state-of-the-art results on standard benchmark face detection datasets. One such algorithm is the **Multi-task Cascade Convolutional Neural Network (MTCNN)**, described by Kaipeng Zhang, et al. in the 2016 paper titled [“Joint Face Detection and Alignment Using Multitask Cascaded Convolutional Networks.”](https://arxiv.org/abs/1604.02878)

MTCNN extracts face and other facial features including nose, mouth and eyes from any fiven picture or frames in a video with very high accuracy. It is a very popular and powerful technique used in pre-processing for Face Recognition tasks. MTCNN can also be used for Facial Landmark Detection.

Here, we will use on opensource implementation of MTCNN to extract the face, and other features and draw bounding boxed around them.

Some examples of outputs of the algorithm are as follows:

![Output](./images/vacation.png) ![Output](./images/school-children%20(1).png)

The model is called a multi-task network because each of the three models in the cascade **(P-Net, R-Net and O-Net)** are trained on three tasks, e.g. make three types of predictions; they are: face classification, bounding box regression, and facial landmark localization.

The three models are not connected directly; instead, outputs of the previous stage are fed as input to the next stage. This allows additional processing to be performed between stages; for example, non-maximum suppression (NMS) is used to filter the candidate bounding boxes proposed by the first-stage P-Net prior to providing them to the second stage R-Net model.

### Benchmarking Results 
The following tables shows the benchmark of this mtcnn implementation running on an Intel i7-3612QM CPU @ 2.10GHz, with a CPU-based Tensorflow 1.4.1. [Ref. 4]

#### Pictures containing single Face

|Image size      | Total pixels | Process time |
| :------------- | :----------: | -----------: |
|  460x259       | 119,140      | 	0.118 sec  |
| 667x1000	     | 667,000	    |   0.456 sec	 |
| 1920x1200      | 2,304,000    | 1.093 sec    |

#### Pictures containing ten Faces

|Image size      | Total pixels | Process time |
| :------------- | :----------: | -----------: |
|474x224	       | 106,176	    |0.185 sec     |	
|736x348	       | 256,128	    |0.290 sec     |	
|2100x994	       | 2,087,400	  |1.286 sec     |


### References:
1. https://arxiv.org/ftp/arxiv/papers/1604/1604.02878.pdf
2. https://machinelearningmastery.com/how-to-perform-face-detection-with-classical-and-deep-learning-methods-in-python-with-keras/
3. https://towardsdatascience.com/face-detection-using-mtcnn-a-guide-for-face-extraction-with-a-focus-on-speed-c6d59f82d49
4. https://github.com/ipazc/mtcnn#zhang2016
