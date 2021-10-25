# Fully-Convolutional-Networks-for-Semantic-Segmentation
A Keras implementation of the Fully Convolutional Networks (FCN-32s, FCN-8s) set up by [Shelmar et al.](https://arxiv.org/abs/1605.06211)  and dedicated for the task of semantic segmentation on PASCAL VOC dataset. For more details regarding the task of semantic segmentation, Methodology, datasets, internals of the networks, results, and discussion, please see the [detailed report](https://github.com/Eslam-Zaher/Fully-Convolutional-Networks-for-Semantic-Segmentation/blob/main/Detailed%20Report.pdf).


Image semantic segmentation is the task of grouping pixels that belong to the same class in one group or class, a dense predection/classification task on the levels of pixels. The following example shows an image and its semantically segmented version.

![alt text](https://github.com/Eslam-Zaher/Fully-Convolutional-Networks-for-Semantic-Segmentation/blob/main/examples/sem_seg.PNG)


# Networks
Fully Convolutional Networks are encoder-decoder based architectures in which an encoder network performs subregion classification over the shallow-level feature maps. The decoder architecture, based on upsampling/deconvolutional layers, performs pixel-wise dense predictions. Results are enhanced in FCN-8s by fusing the outputs from shallower layers (rich with location information) with the ones from deeper layers to produce more enhanced and boundary-preserving predictions. The following triplet shows an image, its FCN-32s, and FCN-8s (boosted with skip connections) respectively.

![alt text](https://github.com/Eslam-Zaher/Fully-Convolutional-Networks-for-Semantic-Segmentation/blob/main/examples/resut.PNG)


# Data
[Pascal  VOC  2012  dataset](http://host.robots.ox.ac.uk/pascal/VOC/voc2012/) is used and augmented with  the [Berkeley Segmentation Boundaries Dataset (SBD)](http://home.bharathh.info/pubs/codes/SBD/download.html) , whichcontains  11,355  labelled  images  (8,498  training,  2,857  vali-dation).  For  training,  the  676  unique  images  from  the  PascalVOC  dataset  were  augmented  with  both  the  training  set  andthe last 1,657 images (out of 2,857 total) in the validation setof Berkeley SBD. The first 1,200 images of the SBD validationset for was for validating our models. Refer to the report and code file for details and links for preprocessed and augmented dataset.

# Drawbacks and Future Work
The relative small margin (~2-3%) in mean Intersection Over Unioun (IOU) between our models and the original ones by [Shelmar et al.](https://arxiv.org/abs/1605.06211) is believed to be due to the differences in framework, optimization, and dataset augmentation. Our implementation is Keras-based while the original networks were built and trained using Caffe. The authors benefited from their augmented dataset, GPU resources, and the wrapping around network layers to assign different learning rates for different layers, resulting in better fine tuning, but at the cost of training time (3 days). Future work will investigate data augmentation, utilization of GPU-resources, and other optimizers. 

* The following repos were helpful for the prepartion of this projects
- https://github.com/shelhamer/fcn.berkeleyvision.org
- https://github.com/fmahoudeau/FCN-Segmentation-TensorFlow
- https://github.com/kevinddchen/Keras-FCN
- https://github.com/sagieppel/Fully-convolutional-neural-network-FCN-for-semantic-segmentation-Tensorflow-implementation




