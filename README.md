# Classification of Bad Type of Semiconductor Wafer Processing Using Deep learning model


![KakaoTalk_20210713_032822609](https://user-images.githubusercontent.com/66030601/125386248-eb974d00-e3d6-11eb-924e-c0cbdf21154a.jpg)

I conducted an industry-academic cooperation project with Hyundai Mobis Vander Shinhan Precision Industry Co., Ltd.

My name is Mingyo Kim. I am an industrial management engineer and have experience in researching in the industrial intelligence lab.

Let me start my research presentation.
#
![KakaoTalk_20210713_032822609_01](https://user-images.githubusercontent.com/66030601/125428505-d2f0efbe-21a9-493d-8115-484df554c387.jpg)

COVID19 has affected semiconductor production by semiconductor manufacturers.

After the decline in semiconductor production became a fait accompli, semiconductor manufacturers are focusing on producing high-end semiconductors with higher unit prices among high-end semiconductors and low-cost semiconductors they used to be produced.

As a result of focusing on producing high-end semiconductors, a few months later, there has been a shortage of low-cost semiconductors, and an issue of lack of supply of semiconductors for vehicles, a type of low-cost semiconductor, has occurred.

In addition, the automotive industry is changing from internal combustion engine cars to electric car manufacturing.

This chain of semiconductor shortages has expanded around the world, and Taiwan's TSMC has announced that it will increase the supply of semiconductors for vehicles, but it is unclear at the moment.
#
![KakaoTalk_20210713_032822609_02](https://user-images.githubusercontent.com/66030601/125432588-5e4ca39c-b4ce-4db8-b4c2-16e17d2903d6.jpg)

This is the recent issue of responding to the lack of supply of automotive semiconductors. Companies around the world, including Hyundai Motor, have taken measures to cut production.

If I cooperate with Hyundai Mobis Vander Shinhan Precision Industrial Co., Ltd. to present a solution to the semiconductor industry, I will be able to solve the problem of lack of supply of semiconductors both domestically and globally. 

Also, I conducted research activities to attract new customers using the service of Shinhan Precision Industry Co., Ltd.
#
![KakaoTalk_20210713_032822609_03](https://user-images.githubusercontent.com/66030601/125436478-1ac91efd-2de6-4200-aba3-3e82014f9e00.jpg)

The effect of determining defective types of semiconductor wafers using artificial intelligence can be identified by identifying defective types of semiconductors and identifying the ratio of defective types to each type, and thus increasing yields can be expected.

The yield is calculated by multiplying the actual number of normal chips by 100 by the maximum number of chips designed.
#
![KakaoTalk_20210713_032822609_04](https://user-images.githubusercontent.com/66030601/125436861-90e6d1a2-dd98-40a0-9c58-a46eb7569063.jpg)

The utilization data is WM-811K wafer map and the data has 811,457 sets of data. 

Contains information such as wafer map, wafer die size, lot name, wafer index, etc.
#
![KakaoTalk_20210713_032822609_05](https://user-images.githubusercontent.com/66030601/125436929-d95313ce-acc5-4d91-ab7e-9030322ad6cf.jpg)

If you look at the data, you can see that it also contains data that is not labeled.
#
![KakaoTalk_20210713_032822609_06](https://user-images.githubusercontent.com/66030601/125437165-8cb3376d-757d-45ec-9115-89ed2051a917.jpg)

I will use the labeled data except for the unlabeled data. The data are unbalanced.
#
![kmg_SVM_model ipynb - Colaboratory - Chrome 2021-07-13 19-50-25 mp4_20210713_195237](https://user-images.githubusercontent.com/66030601/125442466-f5e529b3-63cd-4d80-81e8-a974434cc9a8.gif)

It's part of the result of visualizing the data.
#
![KakaoTalk_20210713_032822609_08](https://user-images.githubusercontent.com/66030601/125443803-971149f5-1f0a-4c25-9c9f-aa0981380695.jpg)

The data has a total of eight bad types: Center, Donut, Edge-Loc, Edge-Ring, Loc, Random, Scratch, Near-full.
#
![3가지 성능비교](https://user-images.githubusercontent.com/66030601/125623346-b92b9856-cdd4-4b78-b7de-cc7cf2d60656.JPG)

I will compare the performance of SVM, CNN, and RF models.
# 
# ▶Support vector machine
![SVM캡쳐](https://user-images.githubusercontent.com/66030601/125451049-aaa19545-065f-4b3b-8c18-2e3f7088406e.JPG)

I will use the support vector machine to classify defect types. 

Based on a given dataset, the SVM algorithm creates a non-probable binary linear classification model that determines which category the new data will fall into.
#
![파이썬 강좌 1](https://user-images.githubusercontent.com/66030601/125452255-0d1b77e6-53b3-4e44-8666-36ad9c36e6e3.JPG)

The created classification model is represented by boundaries in the space where data is thought, and the SVM algorithm is the algorithm that finds boundaries with the largest width of them.

In addition to linear classification, SVMs can also be used in nonlinear classification.

In order to classify non-linearly, it is necessary to think of the given data as a high-dimensional feature space, and in this study, the curvilinear integral was carried out using radon conversion.
#
![KakaoTalk_20210713_032822609_09](https://user-images.githubusercontent.com/66030601/125444385-d8a7dc88-7f2b-4fee-9ca5-0ae485d87144.jpg)

The wafer map was divided into 13 parts and the defect density was calculated accordingly.
#
![KakaoTalk_20210713_032822609_10](https://user-images.githubusercontent.com/66030601/125452504-c9828b5e-6a77-4477-b0f8-362cd0d335e3.jpg)

This chart is the density information for eight failure types, which shows the partial density of wafers divided by 13.

At this time, we will use radon conversion, a method used mainly for CT scans in hospitals, as a way to eliminate noise.
#
![KakaoTalk_20210713_032822609_11](https://user-images.githubusercontent.com/66030601/125452745-2457cb6b-7bad-48d0-8b6d-59b115773208.jpg)

Radon conversion is one of the image processing techniques used to convert tomography data into two-dimensional images in medical and geological fields.

If you want to find a particular shape or pattern on a dimension image, it is a method that adds some additional processing, applying radon conversion and inverse conversion techniques to the image data.

Calculates the integral value of the image's pixels along a vertical line and a line that leads to a position at a certain angle and distance from the origin of the two-dimensional image. That means combining all the pixel values on the line.
#
![KakaoTalk_20210713_032822609_12](https://user-images.githubusercontent.com/66030601/125453045-8c873d32-7987-48ec-8416-2d56a7aa4ae8.jpg)

This figure shows the results of the radon conversion for eight types of failures.

However, this conversion result is not immediately available because the wafer map size is different.
#
![KakaoTalk_20210713_032822609_13](https://user-images.githubusercontent.com/66030601/125453185-a623ac8a-4542-48f6-833f-e6c0fd51b518.jpg)

In the next step, you will obtain fixed dimension geometry values for row means and row standard deviations in the radon transformation.

Dimensions are fixed at 20.

A total of 40 dimensions are extracted from radon-based features.
#
![KakaoTalk_20210713_032822609_14](https://user-images.githubusercontent.com/66030601/125455184-8cf5b51a-7772-4b7e-aca3-cd89e3af747c.jpg)

The figure on the left is a radon-based feature based on the row mean and the figure on the right is a radon-based feature separated from the row standard deviation.
#
![KakaoTalk_20210713_032822609_15](https://user-images.githubusercontent.com/66030601/125455461-834b3e36-7e15-4db0-ac94-14fc3a8a87d9.jpg)

Using radon-based geometry, the most prominent area identification utilized noise filtering.

The region-labeling algorithm was used, and the maximum region was selected as the most prominent region.

Based on prominent regions, we aimed to extract geometric features such as area, perimeter, length of main axis, length of secondary axis, robustness, and eccentricity.
#
![KakaoTalk_20210713_032822609_16](https://user-images.githubusercontent.com/66030601/125455735-1942f093-f26a-490a-9cee-ec07e3afb205.jpg)

I implemented multi-class and multi-label learning algorithms with SVM, and the ACC is 82%.
#
## ▶Convolutional neural network
![CNN](https://user-images.githubusercontent.com/66030601/125468296-69a17639-cccc-45a3-8b34-f1200d3abe85.jpg)

Convolutional neural networks are a type of multi-layer feed-forward artificial neural network used to analyze visual images.

It is classified as a deep neural network in deep learning, and is mainly used for visual image analysis.

It is applied to image and video recognition, recommendation system, image classification, medical image analysis, and natural language processing.

In feedforward neural networks, passing through the hidden layer means that the input of the hidden layer is weighted and then biased to become the input of the activation function.
#
![KakaoTalk_20210713_032822609_17](https://user-images.githubusercontent.com/66030601/125476555-46127c74-29af-4977-a696-47ad0c6af57a.jpg)

We confirmed that there are 8 types of defective types: center, donut, edgelock, edgering, rock, random, scratch, and near-pool.
#
![KakaoTalk_20210713_032822609_18](https://user-images.githubusercontent.com/66030601/125476635-110de9ec-1b84-40b0-b4d9-5b587763fdcb.jpg)

As seen in the data description section, the data we currently use has an imbalance problem.

Therefore, we will proceed with data augmentation to solve the problem of data imbalance.
#
![KakaoTalk_20210713_032822609_19](https://user-images.githubusercontent.com/66030601/125476842-88adbeed-74c5-4dfd-8fdd-dfdd22e2c1d5.jpg)

When expanding data, I thought about GAN and autoencoder.

Although GAN was created by an autoencoder, it focused on the characteristics of increasing the number of learning data that Autoencoder lacks more effectively, and selected Autoencoder.

We will use a 2D convolutional autoencoder that extends dimensions.
#
![KakaoTalk_20210713_032822609_20](https://user-images.githubusercontent.com/66030601/125477077-c1365d3e-db6e-43b9-aef4-9933f0db7957.jpg)

An encoder model and a decoder model were created as part of the autoencoder model layer.

This is to add noise.

Add noise to encoded defective wafer vectors.
#
![KakaoTalk_20210713_032822609_21](https://user-images.githubusercontent.com/66030601/125477326-43c23741-57ff-4c51-9c12-8c84f5d2786c.jpg)

Wafer data reconstructed by adding new noise wafer data to the original faulty wafer data.

Through this process, we increased 2000 data for each defective type.

This solved the problem of data imbalance.
#
![KakaoTalk_20210713_032822609_22](https://user-images.githubusercontent.com/66030601/125477511-9523bd07-a600-468d-b887-1320ed125366.jpg)

The step to define a model generation function and validate the model through cross-validation.

For the cross-validation model, K Fold Cross validation method was used.

K Fold is a method of making k-folds and proceeding with verification by the specified number of ks.

The reason for using Kfold is that accuracy can be improved for datasets with a small total number of data.

In our model, we designated it as k=3, and the score was 97%.
#
![KakaoTalk_20210713_032822609_23](https://user-images.githubusercontent.com/66030601/125477872-38ac34d7-ad43-423f-a18d-f6da0c7ae436.jpg)

This is the result of  CNN model.

The accuracy of the CNN model was 99% and, as shown in the table on the right, ACC is increasingly increasing, converging to 1, and Loss converging to zero.
#
## ▶Random forest 
![KakaoTalk_20210713_032822609_24](https://user-images.githubusercontent.com/66030601/125478390-59a9f8fc-12fb-4391-88c6-a721bfbd11eb.jpg)

The third model we proceeded with is Random Forest.

Random forest is an algorithm that is often used in the field due to its simplified principles and better performance than most design trees.

We conducted a random forest to compare the performance of the two models that we proceeded before.
#
![KakaoTalk_20210713_032822609_25](https://user-images.githubusercontent.com/66030601/125478689-8e3a60eb-68ae-460f-bbc8-cd11a95c8864.jpg)

Deep learning was performed using theano library and keras.

I separated the training set and the test set.
#
![KakaoTalk_20210713_032822609_26](https://user-images.githubusercontent.com/66030601/125479345-c3feb7c1-96ee-42c8-9630-dc8ead00cb68.jpg)

Accuracy was predicted using the accuracy_score module.

Set the last node count of the decision tree differently to 2 and 50.

You can see the percentage of all predicted targets that you classify correctly.

When predicted using random forests, we could see that it was predicted with approximately 89% accuracy and that it had better performance than the decision tree.
#
![KakaoTalk_20210713_032822609_27](https://user-images.githubusercontent.com/66030601/125480592-9688ad05-f697-431c-a5a4-198607f4c778.jpg)

In the next step, we checked with confusion matrix to see if Random Forest is the right model.
#
![KakaoTalk_20210713_032822609_28](https://user-images.githubusercontent.com/66030601/125480825-04a07968-3f1e-457b-a491-1b1245f974c1.jpg)

You can see that the 'Near-full' defect labeled number 7 is the most predictive.
#
## ▶Conclusion◀
![KakaoTalk_20210713_032822609_29](https://user-images.githubusercontent.com/66030601/125482531-423107cf-896d-436a-879a-cb1728a06fdd.jpg)

Accuracy of SVM, CNN, and Random Forest.

CNN showed the highest accuracy with 99%, followed by Random Forest with 89%, and SVM 82%.
#
![KakaoTalk_20210713_032825993](https://user-images.githubusercontent.com/66030601/125482892-690d3d3d-464c-43cc-bba4-9c677fe2e0a5.jpg)

Let me announce the results of the study. First, we promoted the increase in yield by identifying the type of defect.

High yields are the most important in the semiconductor industry, so among the defective types that lower yields, those that need process improvement can be improved.

The second is the improvement of the existing defect classification method.

We have derived meaningful research results by adding deep learning to the defect type classification method that was previously used by the company.

For CNN, we built a model that was 99% accurate and applicable directly to the company's system.
#
![KakaoTalk_20210713_032825993_01](https://user-images.githubusercontent.com/66030601/125483276-168faff4-8d4d-4dca-bc67-a7af20592f3b.jpg)

Third, it is easier to identify the location extraction that causes the wafer map to fail.

Since it is divided into 13 zones, it is easy to identify the defect location.

Fourth, it is to secure practicality by applying various fields.

As it is applicable to various processes where imbalance exists, it is highly likely to be practical and can be expected to be applicable to other areas other than manufacturing processes.
#
![KakaoTalk_20210713_032825993_02](https://user-images.githubusercontent.com/66030601/125483574-780c577f-3b39-4484-a2aa-49845e8c2643.jpg)

Hyundai Mobis Vander Shinhan Precision Industrial Co., Ltd. has expressed its position on the results of the study.
#
![KakaoTalk_20210713_032825993_03](https://user-images.githubusercontent.com/66030601/125483752-00fbb09b-4e46-4b78-a35b-0a0c5c69c7d0.jpg)

