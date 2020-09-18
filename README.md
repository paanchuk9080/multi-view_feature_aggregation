# multi-view_feature_aggregation
This repository is built for our paper Multi-view Feature Aggregation for Facade Parsing. The source code and more details will be released in the near future.

## Data augmentation
   In order to make the model to be capable of leveraging information from multi-views, we synthesize occlusions with randomly block at each view in the training stage. The block area of occlusion is a factor that directly determines the model. We experiment under seven block areas: 0.0, 0.025, 0.05, 0.075, 0.1, 0.125, 0.15.  The block area is fixed at 0.075 in the experiments.
    ![Example](https://github.com/wohaiyo/multi-view_feature_aggregation/blob/master/data_aug.png)

## Model training
   To train the proposed model, we adopt the standard cross-entropy loss to evaluate its prediction, i.e., the label map of the target view. The loss is defined as
   
   ![CE](https://github.com/wohaiyo/multi-view_feature_aggregation/blob/master/ce.png)
   
where M is the total number of category and N is the total number of pixels in the output label map, and c is the index of categories and i is the index of pixels. y c,i and p c,i are the ground truth label and the predicted one of pixel i.
    Since each input view can be treated as the target view, we use multi-view losses to train the overall architecture. The total loss is defined as
    
   ![ALL_CE](https://github.com/wohaiyo/multi-view_feature_aggregation/blob/master/all_ce.png)
   
where V is the number of input view.
