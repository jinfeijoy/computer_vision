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
   
