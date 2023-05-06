---
title: "Unsupervised Map Registration Estimation From Multiple Point Clouds"
excerpt: "This project was part of 16833: Robot Localization and Mapping<br/><img src='/images/architecture.png'>"
collection: portfolio
---

Advances in deep learning have led to many state-of-theart methods for semantic computer vision tasks. Despite those successes, their compelling improvements on the geometric aspects of computer vision are yet to be fully demonstrated especially for registration and mapping. Several works attempt to integrate deep learning methods into geometric vision problems like mapping and registration asociated with point clouds. Currenrlty State of the Art (SOTA) programs achive this point cloud registration can using pairwise local approaches like [Iterative Closest Point (ICP)](https://cs.gmu.edu/~kosecka/cs685/cs685-icp.pdf) appraoch or global apparoaches involving fearture detectors like [NARF](http://ais.informatik.uni-freiburg.de/publications/papers/steder10irosws.pdf). However, for fusing information from multiple point clouds, these algorithms are used iteratively for each sensor reading,thereby accumulating the registration error which leads to incorrect cloud registration and iomahe mapping. To mitigate this, [DeepMapping](https://github.com/ai4ce/DeepMapping/tree/master/script), a novel registration framework using deep neural networks (DNNs) as auxiliary functions to align multiple point clouds from scratch to a globally consistent frame is porposed. While Deepmapping achieves  results, there is still scope for improvement through addition of ICP as a warm start for the DNN and using PointNet feature extractor as a replacmenet for the convolutional neural network (CNN) based feature extractor.

![](/images/architecture.png)
*DeepMapping Pipeline*

The localization is perfomed using a Localization Network (L-net) which involves extracting features from individual light Detection and Ranging (LiDAR) outputs, transforming them to global coordinates, and performing point cloud registration while fusing multiple sensors.The L-Net consists of a latent feature extraction module followed by a multi-layer perceptron (MLP) that outputs a sensor pose. For organised point cloud convolutional neural network (CNN) to extract
the feature vector of point cloud followed by a global pooling layer to aggregate local features to a global one. On the otherhand, for unorganized point cloud data, point clouds are extracted using PointNet. A combination of MLP and global pooling layer is used to aggregate all the features and output a final feature vector with a dimension equal to the sensor’s degree of freedom. To associate points between each point cloud, Chamfer distance is used as minimized this improves the pairwise alignment. The point cloud registration output is then fed to another MLP network for generating an occupancy grip mapby assigning probabilities to each cell optimized using Binary Cross Entropy (BCE) loss. Furthermore, All of our experiments were performed on the 2D synthetic dataset and the 3D Active Vision dataset  and evaluated usingAbsolute Trajectory Error(ATE) as a metric similar to DeepMapping. 

<img width ='400' height='400' src='/images/deep mapping 2d.jpg'>

<img width ='400' height='400' src='/images/deep mapping avd.jpg'>

*Point cloud registration using DeepMapping for 2D and AVD dataset* 

Me and my team conducted several experiments with potential to improve upon DeepMapping and reduce Absolute Trajectory Error (ATE): 

* The original Deep Mapping model was trained on the 2D synthetic dataset and the 3D Active Vision dataset. This was repeated using the Iterative Closest Point(ICP) Algorithm. Two diffreent variants of ICP were used especially point-to-point and point-to-plane variations to perform comparative analysis. The general observation was that DeepMapping outperformed both variants of ICP by a large margin. In general registration with Point-to-point ICP gave an ATE value 12 times the ATE value of DeepMapping. Simultaneously, registration with Point-to-plane ICP gave an ATE value 3.18 times the value of DeepMapping. 


<img src='/images/ICP 2D.jpg'>
*Point cloud registration using ICP point-to-point and point-to-plane*

<img src='/images/ICP AVD.jpg'>
*Point cloud registration using ICP point-to-point and point-to-plane*

* Generally, Random initialization will cause the Deep Learning model to take a longer time to converge.A possible method to reduce this convergence time was using the results from Incremental ICP to act as a coarse initialization starting point. With such a warm start, our model will converge faster also more stable than starting from scratch. We observed that this warm start method produced a ATE value 27% less than baseline ATE value proving our hypothesis right.

![](/images/ICP+deepmapping.jpg)
*Point cloud registration using ICP as warmstart for 2D and AVD datasets*

* Given the recent success of PointNet with global feature extraction for point cloud classification and segmentation and achieving permutation invariance while feature extraction of the point cloud, we hyopothesized that it would be worthwhile to experiment by replacing the Localization Network’s(L_Net’s) feature extractor of the Deep Mapping pipeline with the PointNet feature extractor while keeping the rest of the training pipeline same. This experiment was able to achieve an Absolute Trajectory Error of 19.305 and a BCE+CH loss of 0.0316 after 3000 epochs of training, these results are comparable to the results we got using the ICP Point-to-Place implementation. While according to our hypothesis, our method should perform better, it instead resulted in an ATE value which was 2.74 % larger than baseline ATE value.

![](/images/m_net_slam.jpg)
*Point cloud registration when M_net is replaced by traditional SLAM methods*



