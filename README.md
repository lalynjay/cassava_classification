
# Cassava Leaf Disease Detection


## Using Neural Networks to Identify Diseased Plants


### Lynn Anderson

![](https://github.com/lalynjay/cassava_classification/blob/main/images/cassava-1.jpg)





The objective of this project was to build a neural network classification model to identify diseased cassava plants. Cassava roots are an important source of calories and nutrition for many people, especially in sub-Saharan Africa. As the human population increases, it is increasingly important to prioritize crop health, as fertile land is finite and precious. Identifying diseased plants and appropriately treating them in a timely manner is important to ensure adequate yields. A pretrained Resnet50 model was able to correctly classify images 85% of the time. 

# Overview

In this project, models were trained on labelled images and evaluated on a hold out test set. Initially, multiclass classification models were investigated, with the aim of the model being able to identify the specific disease condition if the plant was not healthy. However, model performance was very unreliable, thus a binary classification systems was used to identify a plant as either healthy or diseased. A basic neural network was the baseline model, with models consisting of different numbers of hidden layers, and different regularization techniques examined. CNN models and Pre-trained networks were then trained and evaluated, since the basic neural network models were all unsatisfactory. Precision, recall, and F-1 score of the test data used to evaluate overall model performance.


# Business Understanding

An agricultural company specializing in treating plant diseases is seeking to implement a model to identify diseased Cassava plants. It is important they can accurately identify plants in need of treatment and determine the best solutions for their customers. However, it is time consuming for the team of plant experts to manually go through images from farmers, and would be much more time efficient to automate the process of identifying diseased cassava plants. 


# Data 

The data for this project was sourced  from the Kaggle Cassava Disease dataset- https://www.kaggle.com/c/cassava-disease/overview. 

The data consisted of leaf images for the cassava plant belonging to one of 5 classes- healthy or four disease
conditions- Cassava Mosaic Disease (CMD), Cassava Bacterial Blight (CBB), Cassava Greem Mite (CGM), and Cassava Brown Streak Disease (CBSD). There were a total of 5,656 labelled images in the dataset. The number of images per class were heavily unbalanced, with two disease classes- CMD and CBSD- representing 72% of the images, and healthy plants only made up 5% of the dataset.

Due to challenges with very poor performance and long run times and resource usage when training models with the full dataset, a smaller dataset consisting of 1,200 images (300 from each class) was initially used, with the most performant models then investigated on the full dataset. Images were split into training and test sets to validate model performance. 


![](https://github.com/lalynjay/cassava_classification/blob/main/images/bar_chart_1.png)

# Modeling and Evaluation

Initially, multiclass classification models were investigated, with the aim of accurately classifying plants as either healthy or identifying the specific disease. Due to unsatisfactory model performance, a binary classification system was then used to classify plants as either healthy or diseased. 10 different models for each classification system were looked at in total, with a summary of the models and scores below. For the full analysis with with every model, see 
[this notebook](https://github.com/lalynjay/cassava_classification/blob/main/Time_series_analysis.ipynb)  


For this situation, minimizing false negatives is important, since a plant labelled as healthy when it is actually diseased would be detrimental to the customer, as their plants might go untreated would be the worst case. Thus, recall and F-1 score were used to evaluate model performance.

Again, baseline neural network models were investigated, followed by a CNN and Resnet model. Images of diseased plants consisted of 80% of the dataset, so it was still quite imbalanced. In many of the models, it appeared to indiscriminately classify plants as diseased. However, the pretrained model far outperformed all others. 

Pre-trained models are pre-built machine learning models that have already been trained on large datasets, such as ImageNet or COCO. Such datasets often contain millions of images, which allows the models to learn a wide range of features and patterns. This makes them highly accurate and effective for a variety of tasks. Moreover, training a machine learning model from scratch can be a time-consuming process and by using pre-trained models, and typically much time and resources cab be saved by starting with a model that has already been trained.

ResNet models were developed especially for image classification. ResNet-50 is a pretrained model Convolutional Neural Network(CNN) model. ResNet-50 is 50 layers deep and is trained on a million images of 1000 categories from the ImageNet database. 

After selecting the best performing model, a Resnet model was then trained and evaluated on the entire dataset. Initially, the Resnet model trained on the small dataset was evaluated on the full dataset, with extremely poor performance. A multiclass model on the entire dataset was trained and evaluated as well, again with sub-par results. The binary classification Resnet model trained and evaluated on the full dataset demonstrated some level of competency, although there is room for improvement. 



![](https://github.com/lalynjay/cassava_classification/blob/main/images/all_cnf.png) 



# Visualization 


The LIME library is used to reveal which pixels of an image were most important in the model's prediction. It should be expected that the model would be paying most attention to the leaves of the plant and not the parts of the image that are not vegetation. It appears this is mostly the case, with the model paying most attention to the leaf ends and center of the plant.


![](https://github.com/lalynjay/cassava_classification/blob/main/images/lime_plant.png)



# Conclusions


   * Simple neural network models were inadequate for accurately classifying the Cassava images
   

   * The pretrained Resnet model was far better than any others in correctly classifying images
   
    
   * A model trained and evaluated on the full dataset had room for improvement, likely due to challanges with the extreme dataset imbalance.
   
  

# Next Steps and Limitations: 


   * The image size for modeling was 128 x 128 pixels. Attempts at larger image sizes resulted in errors and crashes. Recreate the modeling process using a more powerful machine that can handle a much larger dataset size. 
    
   * Gather more images of the underrepresented classes
    
   * Further investigate other pre-trained models




# For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/lalynjay/cassava_classification/blob/main/final_notebook.ipynb) or review [this presentation](https://github.com/lalynjay/cassava_classification/blob/main/presentation.pdf)

For additional info, contact Lynn Anderson at lalynjay@gmail.com

Repository Structure

├── data 

├── images

├── README.md

├── cassava_presentation.pdf

└── final_notebook.ipynb

└── all_models.ipynb

└── activation_layers.ipynb


