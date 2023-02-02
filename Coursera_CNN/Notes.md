# Notes

## Week1
### Edge Detection
* Vertical edges
    * example: kernal (filter)
        * <img src="https://media5.datahacker.rs/2018/10/multiplication_slicice.png"  width="440" height="200">
        * <img src="https://miro.medium.com/max/1004/1*jXhh2a0jApKbRuHaCFKynA.png"  width="440" height="200">
        * this kernal can be parameters to train
        
* Horizontal edge
    * example: kernal (filter) (filter is used to extract features)
        * 
* Padding
    * <img src="https://i.stack.imgur.com/IceQw.png"  width="440" height="200">
    * Valid padding: 
        * n * n X f * f => (n-f-1) * (n-f-1)
    * Same padding:
        * Pad so that output size is the same as the input size
        * so padding size = (f - 1) / 2 
            * f is size of filter, f is usually odd, 3*3, 5*5, 7*7 are very common
* Strided convolution
    * instead of shift 1 step, shift n steps for both row and column
    * n * n matrix, padding p, filter f * f, stride s, then the output size is floor((n + 2p - f)/s + 1) * floor((n + 2p - f)/s + 1)
    * convolution in math textbook: cross-correlation
* Layer of CNN
   * example of 1 layer in CNN (summarize feature)
      * ![image](https://user-images.githubusercontent.com/16402963/212436497-2d64aa74-8b84-4a01-a819-661c10b1f6e5.png)
      * n * n X f * f -> Relu(output + bias) -> part of layer, with both virtical and horizontal -> 1 layer. (we can also have more than 2 filters)
   * ![image](https://user-images.githubusercontent.com/16402963/212437874-c4f65425-7f9e-4cde-9500-997d56e267a7.png)
* Example of CNN
   * ![image](https://user-images.githubusercontent.com/16402963/212438387-ce465dfd-8508-48b2-843e-da3e581ba97c.png)
* Type of CNN layers  
   * Convolution
   * Pooling: to reduce the size of representation, speed the computation, make some of the features that detects more robust.
   * Fully Connected  
* Pooling Layers (no parameter tunning)
   * hyperparameters:
      * f: filter size
      * s: stride
      * max or average pooling 
   * Max pooling: 
      * ![image](https://user-images.githubusercontent.com/16402963/212438906-fcfe21af-135d-44e5-b8f5-51eca089e82f.png) 
   * Average pooling: more often than max pooling
* CNN Example
   * ![image](https://user-images.githubusercontent.com/16402963/212440107-2a88f837-684b-4c5f-a679-fbc534af0e98.png)
*  Why convolutions:
   * Parameter sharing: a feature detector (such as a vertical edge detector) that's useful in one part of the image is probably useful in another part of the image
   * Sparsity of connections: in each layer, each output value depends only on a small number of input     

## Week2
### Case Study
* Classic Networks:
   * LeNet-5
   * AlexNet
   * VGG-16
* ResNet
   * ![image](https://user-images.githubusercontent.com/16402963/213066003-fb5f64e3-0769-4c34-b348-dc96d1dc0b85.png)
   * ![image](https://user-images.githubusercontent.com/16402963/213066075-3407c004-4de7-4cbd-8783-befd7e802f68.png)
* 1 * 1 convolution
   * it alows to shrink the number of channels in your volumes or keep it the same or even increase it if you want.
   * it can be used to help build up to the inception network.
   *  ![image](https://user-images.githubusercontent.com/16402963/213067212-68c02f52-7cf2-4141-93ec-4581d116ef25.png)
* inception network
   * ![image](https://user-images.githubusercontent.com/16402963/213069734-58be0b0c-c906-48c3-a7b0-f2ab6f32fe89.png)
   * ![image](https://user-images.githubusercontent.com/16402963/213070033-00b6394a-7fec-4b2e-817e-3cbc7800cd12.png)
* MobileNet
   *  low computational cost at deployment/ useful for mobile and embedded vision application
   *  key idea: normal vs. depthwise-separable convolutions
   * ![image](https://user-images.githubusercontent.com/16402963/213071046-4b3f6c75-1e95-4e7e-aec4-5623164dbafa.png)
   * ![image](https://user-images.githubusercontent.com/16402963/213071146-7cfa32fb-38f9-4c0f-89f5-88e5941be86d.png)
   * ![image](https://user-images.githubusercontent.com/16402963/213071914-04b8e84a-2247-4ba7-a8e9-4a61db33aaf7.png)
   * ![image](https://user-images.githubusercontent.com/16402963/213072205-bd16b95b-b231-441b-8d65-7be44a5e9cc8.png)
   * ![image](https://user-images.githubusercontent.com/16402963/213072461-13259c0d-73cb-4555-97a2-a57bf1e9011e.png)
* MobileNett v2
   * ![image](https://user-images.githubusercontent.com/16402963/213074538-45e5d54c-ed40-4770-a2c4-46df4dce0701.png)
   * ![image](https://user-images.githubusercontent.com/16402963/213074867-17ebdfe0-a3c3-4bfc-b2b8-55211586dee9.png)
### Practical
* Data Augmentation
   * mirroring
   * random cropping 
      * rotation
      * shearing
      * local warping
      * ![image](https://user-images.githubusercontent.com/16402963/213591165-a7f6ecc6-50ee-4eb2-97b9-d92e480a9667.png)
   * color shifting 
      * ![image](https://user-images.githubusercontent.com/16402963/213591733-a139a7ae-ee3e-4971-b142-35a47d179fc5.png)
* Tips for doing well on benchmarks/winning competition (however, those are not recommended for production system)
   * emsembling: train several networks independently and average their outputs (this usually not using iin real production, more in experiment or competition)
   * multi-crop at test time: run classifier on multiple versions of test images and average results (this is for more actual production system)
   
## Week3
### Object localization
* ![image](https://user-images.githubusercontent.com/16402963/215236469-55c5cc82-c3eb-454a-adbe-f95bad493409.png)
* targett label: ![image](https://user-images.githubusercontent.com/16402963/215236496-b5f9cc01-bf56-400e-932c-2c34f82c39f6.png)
### Landmark detection
* ![image](https://user-images.githubusercontent.com/16402963/215236546-da932432-5216-4819-bdf5-d12525f74070.png)
### object detection
* sliding window detection
### Convolutional implementation of sliding windows
* turnring FC (fully connected layers into convolutional layers):
   * ![image](https://user-images.githubusercontent.com/16402963/215236658-7703272e-a3f9-49ba-97f4-2a19de4e3e63.png) 
* ![image](https://user-images.githubusercontent.com/16402963/215236708-9ec1f554-6206-4c58-89f5-77557493dfff.png)
### Bounding Box Prediction (YOLO algorithm)
* to check if middle point of object is in grid cell
* ![image](https://user-images.githubusercontent.com/16402963/215236807-3c2c11ec-d06c-4885-90df-64250dba5ebf.png)
* ![image](https://user-images.githubusercontent.com/16402963/215236843-4cebfd51-2e77-4d0a-9967-0fbbb671b764.png)
### Ubtersection Over Union
* evaluating object localization
* ![image](https://user-images.githubusercontent.com/16402963/215236900-33eaa8ee-c6eb-45fd-a081-30b76c279703.png)
### Non-max Suppression
* to make sure target only in 1 grid cell
* ![image](https://user-images.githubusercontent.com/16402963/215236958-c4e936de-4fb0-43ce-8b7c-6f1f92c19ea6.png)
### Anchor Boxes
* there can be multiple anchor boxes in every picture
* each object in training image is assigned to grid cell that contains object's midpoint and anchor box for the grid cell with highest IoU
* ![image](https://user-images.githubusercontent.com/16402963/215237000-b338dfca-cfc1-4559-be33-c5b6c02f3d19.png)
* ![image](https://user-images.githubusercontent.com/16402963/215237059-737b67c1-b053-4df1-849c-482850959fce.png)
### YOLO (You Only Look Once)
* ![image](https://user-images.githubusercontent.com/16402963/215237139-bc9728d1-727c-44d4-94d0-390fe14c2503.png)
### Sementic Segmentation with U-net
* ![image](https://user-images.githubusercontent.com/16402963/215237172-ae31abca-1c09-482e-82b1-b7c07e2fcc66.png)
* ![image](https://user-images.githubusercontent.com/16402963/215237336-85979272-f672-4d03-8542-749baf023b3b.png)
* ![image](https://user-images.githubusercontent.com/16402963/215237353-ef78ba99-773f-45ad-ac66-8c40456ae962.png)
   * final output: h * x * n_classes
### Transpose convolutions
* ![image](https://user-images.githubusercontent.com/16402963/215237246-f40643f2-09c7-4030-a83a-83b0bd90b7e4.png)

## Week4
### Face Recognition
* One Shot Learning
   * One-shot Learning (performance is not good): 
      * Learning from one example to recognize the person again (image -> CNN -> O(softmax multiple classification multiple probability)   
   * Learning a similary function
      * d(img1, img2) = degree of difference between images 
* Siamese Network
   * ![image](https://user-images.githubusercontent.com/16402963/215910193-16d484c4-ccb9-4094-82a2-2423c97b3545.png)
   * ![image](https://user-images.githubusercontent.com/16402963/215910366-1c13b355-44c0-4646-976a-a0114e1f1acc.png) 
* Triplet Loss
   * difference between object and positive - difference between object and negative + margin <= 0 
   * ![image](https://user-images.githubusercontent.com/16402963/215910950-e48c6747-e819-45e3-9e45-ed9922996fd1.png)
   * should choose triplets that are hard to train on, otherwise, if we randomly choose A, P, N, then d(A,P)+alpha<=d(A,N) is easilly satisfied, then gradient descent won't update with valueable information
* Face Verification and Binary Classification
   * ![image](https://user-images.githubusercontent.com/16402963/215913597-f6aaba66-ea92-49fb-81d2-1f4b9b78447e.png)
   * encoding of picture can precompute
 
### Neural Style Transfer
* What are deep ConvNets learning?
   *  different layers can capture different information from image
   *  ![image](https://user-images.githubusercontent.com/16402963/216193308-e5dd6b37-5e34-4258-b414-29a876eb5a37.png)
   * ![image](https://user-images.githubusercontent.com/16402963/216193349-004efeff-cbef-4b5a-acdf-3cd9f92b3c02.png)
* cost function
   * Neural style transfer cost function: 
      * C: content, S: stype, G: generated image
      * J(G) = alpha * J_content(C, G) + beta * J_style(S,G) -> how difference between content and generated + how difference between style and generated, alpha and beta are weight
   * Find the generated image G
      * initiate G randomly: G: 100 * 100 * 3
      * Use gradient descent to minimize J(G)
         * G = G - derivative of cost function
         * ![image](https://user-images.githubusercontent.com/16402963/216194270-7dba6080-db27-47a0-8b03-382d7a9f88c1.png)
         * this updating the pixel values of image G
* content cost function
   *  ![image](https://user-images.githubusercontent.com/16402963/216195426-de559f1f-2b01-4d30-9e92-48a227eff143.png)
* style cost function
   *  ![image](https://user-images.githubusercontent.com/16402963/216196547-016fb13e-189f-409e-aae4-e600823d50f1.png)
   *  ![image](https://user-images.githubusercontent.com/16402963/216196863-a3a7019b-eb1c-4bd1-94e2-8026df38e4ed.png)

* 1D and 3D generalizations
   * ![image](https://user-images.githubusercontent.com/16402963/216199658-9a337c37-d0fc-4da2-9d01-e05b7e43683d.png)
      * for most 1D data problem, mostly we use RNN, but CNN can also be applied
   
 
