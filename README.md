# Plankton-Image-Classification
The laboratory from Algorithmic Machine Learning Course at EURECOM

This repository included the Music Recommendation System Laboratory from the Algorithmic Machine Learning Course at EURECOM, which was conducted in a group with DANG Ngoc-Vien (Ngoc-Vien.Dang@eurecom.fr).

Furthermore, the Algorithmic Machine Learning Course was offered by Prof. Pietro Michiardi at EURECOM. The details of the course can be retrieved in here https://github.com/DistributedSystemsGroup/Algorithmic-Machine-Learning

## Course Description
The goal of this course is mainly to offer data science projects to students to gain hands-on experience. It nicely merges the theoretical concepts students can learn in our courses on machine learning and statistical inference, and systems concepts we teach in distributed systems.

Notebooks require to address several challenges, that can be roughly classified in:
- Data preparation and cleaning
- Building descriptive statistics of the data
- Working on a selected algorithm, e.g., for building a statistical model
- Working on experimental validation

## The Laboratory Description
Plankton comprises all the organisms freely drifting with ocean currents. These life forms are a critically important piece of oceanic ecosystems, accounting for more than half the primary production on earth and nearly half the total carbon fixed in the global carbon cycle. They also form the foundation of aquatic food webs, including those of large, commercially important fisheries. Loss of plankton populations could result in ecological upheaval as well as negative societal impacts, particularly in indigenous cultures and the developing world. Plankton’s global significance makes their population levels an ideal measure of the health of the world’s oceans and ecosystems.

Traditional methods for measuring and monitoring plankton populations are time consuming and cannot scale to the granularity or scope necessary for large-scale studies. Improved approaches are needed. One such approach is through the use of underwater imagery sensors.

In this challenge, which was prepared in cooperation with the Laboratoire d’Océanographie de Villefranche, jointly run by Sorbonne Université and CNRS, plankton images were acquired in the bay of Villefranche, weekly since 2013 and manually engineered features were computed on each imaged object.

This challenge aims at developing solid approaches to plankton image classification. We will compare methods based on carefully (but manually) engineered features, with “Deep Learning” methods in which features will be learned from image data alone.

The purpose of this challenge is for you to learn about the commonly used paradigms when working with computer vision problems. This means you can choose one of the following paths:

Work directly with the provided images, e.g. using a (convolutional) neural network
Work with the supplied features extracted from the images (native or skimage or both of them)
Extract your own features from the provided images using a technique of your choice
You will find a detailed description about the image data and the features at the end of this text. In any case, the choice of the classifier that you decide to work with strongly depends on the choice of features.

Please bear in mind that the purpose of this challenge is not simply to find the best-performing model that was released on e.g. Kaggle for a similar problem. You should rather make sure to understand the dificulties that come with this computer vision task. Moreover, you should be able to justify your choice of features/model and be able to explain its advantages and disadvantages for the task.

### The Goals of this laboratory:
**1. Data Exploration**
The first broad component of your notebook should enable you to familiarise yourselves with the given data, an outline of which is given at the end of this challenge specification.

What is new in this challenge is that you will be working with image data. Therefore, you should have a look at example images located in the imgs.zip file (see description below). If you decide to work with the native or the skimage features, make sure to understand them!

Among others, this section should investigate:

- Distribution of the different image dimensions (including the number of channels)
- Distribution of the different labels that the images are assigned to
The image labels are organized in a taxonomy. We will measure the final model performance for the classification into the level2 categories. Make sure to understand the meaning of this label inside the taxonomy.

**2. Data Pre-processing**
The previous step should give you a better understanding of which pre-processing is required for the data based on your approach:

- If you decide to work with the provided features, some data cleaning may be required to make full use of all the data.
- If you decide to extract your own features from the images, you should explain your approach in this section.
- If you decide to work directly with the images themselves, preprocessing the images may improve your classification results. - In particular, if you work with a neural network the following should be of interest to you:
  - Due to the fully-connected layers (that usually come after the convolutional ones), the input needs to have a fixed dimension.
  - Data augmentation (image rotation, scaling, cropping, etc. of the existing images) can be used to increase the size of the training data set. This may improve performance especially when little data is available for a particular class.
  - Be aware of the computational cost! It might be worth rescaling the images to a smaller size!

All of the operations above are usually realized using a dataloader. This means that you do not need to create a modified version of the dataset and save it to disk. Instead, the dataloader processes the data "on the fly" and in-memory before passing it to the network.

NB: Although aligning image sizes is necessary to train CNNs, this will prevent your classifier from learning about different object sizes as a feature. Additional gains may be achieved when also taking object sizes into account.

**3. Model Selection**
Perhaps the most important segment of this challenge involves the selection of a model that can successfully handle the given data and yield sensible predictions. Instead of focusing exclusively on your final chosen model, it is also important to share your thought process in this notebook by additionally describing alternative candidate models.

The choice of your model is closely connected to the way you preprocessed the input data.

Furthermore, there are other factors which may influence your decision:

- What is the model's complexity?
- Is the model interpretable?
- Is the model capable of handling different data-types?
- Does the model return uncertainty estimates along with predictions?

**4. Parameter Optimisation**
Irrespective of your choice, it is highly likely that your model will have one or more (hyper-)parameters that require tuning. There are several techniques for carrying out such a procedure, including cross-validation, Bayesian optimisation, and several others. As before, an analysis into which parameter tuning technique best suits your model is expected before proceeding with the optimisation of your model.

If you use a neural network, the optimization of hyperparameters (learning rate, weight decay, etc.) can be a very time-consuming process. In this case, your may decide to carry out smaller experiments and to justify your choice on these preliminary tests.

**5. Model Evaluation**
Some form of pre-evaluation will inevitably be required in the preceding sections in order to both select an appropriate model and configure its parameters appropriately. In this final section, you may evaluate other aspects of the model such as:

- Assessing the running time of your model;
- Determining whether some aspects can be parallelised;
- Training the model with smaller subsets of the data.
- etc.
For the evaluation of the classification results, you should use the F1 measure (see Submission Instructions). Here the focus should be on level2 classification. A classification evaluation for other labels is optional.

Please note that you are responsible for creating a sensible train/validation/test split. There is no predefined held-out test data.
