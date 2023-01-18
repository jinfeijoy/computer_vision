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
