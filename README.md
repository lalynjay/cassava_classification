
![](https://github.com/lalynjay/cassava_classification/blob/main/images/cassava-1.jpg)


# Cassava Leaf Disease Detection


### Using Neural Networks to Identify Diseased Plants


#### Lynn Anderson


# Overview



The objective of this project was to build a neural network classification model to identify diseased cassava plants. Cassava roots are an important source of calories and nutrition for many people, especially in sub-Saharan Africa. As the human population increases, it is increasingly important to prioritize crop health, as fertile land is finite and precious. Identifying diseased plants and appropriately treating them in a timely manner is important to ensure adequate yields. A pretrained Resnet50 model was able to correctly classify images 85% of the time. 



# Business Understanding

An agricultural company specializing in treating plant diseases is seeking to implement a model to identify diseased Cassava plants. It is important they can accurately identify plants in need of treatment and determine the best solutions for their customers. However, it is time consuming for the team of plant experts to manually go through images from farmers, and would be much more time efficient to automate the process of identifying diseased cassava plants. 


# Data 

The data for this project was sourced  from the Kaggle Cassava Disease dataset- https://www.kaggle.com/c/cassava-disease/overview. 

The data consisted of leaf images for the cassava plant belonging to one of 5 classes- healthy or four disease
conditions- Cassava Mosaic Disease (CMD), Cassava Bacterial Blight (CBB), Cassava Greem Mite (CGM), and Cassava Brown Streak Disease (CBSD). There were a total of 5,656 labelled images in the dataset. The number of images per class were heavily unbalanced, with two disease classes- CMD and CBSD- representing 72% of the images, and healthy plants only made up 5% of the dataset.

Due to challenges with very poor performance and long run times and resource usage when training models with the full dataset, a smaller dataset consisting of 1,200 images (300 from each class) was initially used, with the most performant models then investigated on the full dataset. Images were split into training and test sets to validate model performance. 


![](https://github.com/lalynjay/cassava_classification/blob/main/images/bar_chart_1.png)

Even after data manipulation, the diseased class still comprised 80% of the dataset.

# Modeling and Evaluation


Initially, multiclass classification models were investigated, with the aim of accurately classifying images into one of 5 classes- either as healthy or identifying the specific disease condition. Due to poor model performance, a binary classification system was then used to classify plants as either healthy or diseased. A basic neural network was the baseline model, with models consisting of different numbers of hidden layers, and different regularization techniques examined. CNN models and Pre-trained networks were then trained and evaluated, since the basic neural network models were all unsatisfactory.  


For this situation, minimizing false negatives is important, since a plant labelled as healthy when it is actually diseased would be detrimental to the customer, since their diseased plants going untreated would be the worst case scenario. Thus, recall and F-1 score were taken into consideration when evaluating model performance.


![](https://github.com/lalynjay/cassava_classification/blob/main/images/model_scores.png)


Summary of model scores for every model investigated. A pretrained Resnet50V2 model for binary classification had by far the best performance on the initial dataset. The Resnet model was then trained and evaluated on the entire dataset, with sub-par results. A multiclass model on the smaller dataset was the best model among the multiclass models; however one trained on the entire dataset performed extremely poorly.



![](https://github.com/lalynjay/cassava_classification/blob/main/images/all_cnf.png) 

Confusion matrices for the multiclass Resnet model trained on the smaller dataset (left), the Resnet binary classification model (center), and the Resnet binary classification model trained on the entire dataset (right). For the Resnet binary classification model trained on the entire dataset, there were more false negatives than true negatives, indicating that model could not be trusted to adequately classify the images.



## Visualization 


### Correctly vs incorrectly predicted images

In order to gain insight on where the model may be going right and wrong, it is helpful to take a look at some images that were both corrctly and incorrectly predicted. This next section demonstrates a sample of such images and their predicted and actual class. An inspection of some images incorrectly predicted as healthy show that those may not demonstrate quite as much yellowing as the correctly identified diseased plants. 

![](https://github.com/lalynjay/cassava_classification/blob/main/images/predictions.png)


Examples of a correct and incorrect prediction for each class. When compared to the images correctly predicted, it is evident that in many cases the incorrect images display a different lighting/background, do not contain the center of the plant or show a diferent angle, and/or generally show less obvious yellowing. The rightmost image also has a different perspective, showing a few leaves but not the center of the plant. This suggests the need for consistency among images.  


### LIME library to view focus areas

The LIME library is used to reveal which pixels of an image were most important in the model's prediction. It should be expected that the model would be paying most attention to the leaves of the plant and not the parts of the image that are not vegetation. It appears this is mostly the case, with the model paying most attention to the leaf ends and center of the plant.


![](https://github.com/lalynjay/cassava_classification/blob/main/images/lime_plant.png)


Since the center of the plant and leaves appear to be important in the model's predictions, the model's accuracy would likely be improved if there was more consistency among the images.


# Recommendations


   * Start with the smaller Resnet model, but have an expert verify
   
   
   * Focus on center of plant and large leaves
   

   * Instruct the farmer on how to properly collect images- lighting, parts of plant, etc 
   
   


# Conclusions


   * Simple neural network models were inadequate for accurately classifying the Cassava images
   

   * The pretrained Resnet model was far better than any others in correctly classifying images
   
    
   * A model trained and evaluated on the full dataset had room for improvement, likely due to challanges with the extreme dataset imbalance.
   
   
   * There is a need for more specific standards on capturing images
   
  

# Next Steps and Limitations: 
   
    
   * Gather more images of the underrepresented classes
   
   
   * Set a more specific standard for images before beginning the modeling process
   
    
   * Further investigate other pre-trained models
   

   * The image size for modeling was 128 x 128 pixels. Attempts at larger image sizes resulted in errors and crashes. Recreate the modeling process using a more powerful machine that can handle a much larger dataset size. 



# For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/lalynjay/cassava_classification/blob/main/final_notebook.ipynb) or review [this presentation](https://github.com/lalynjay/cassava_classification/blob/main/cassava_presentation.pdf)

For additional info, contact Lynn Anderson at lalynjay@gmail.com

Repository Structure

├── data 

├── images

├── README.md

├── cassava_presentation.pdf

|── final_notebook.ipynb

|── all_models.ipynb

|── activation_layers.ipynb

|── requirements.txt


# References

[Interpreting Image Classification Model with LIME](https://towardsdatascience.com/interpreting-image-classification-model-with-lime-1e7064a2f2e5)

[The Annotated ResNet-50](https://towardsdatascience.com/the-annotated-resnet-50-a6c536034758)



