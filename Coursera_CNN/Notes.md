# Notes

## Week1
### Edge Detection
* Vertical edges
    * example: kernal (filter)
        * <img src="https://media5.datahacker.rs/2018/10/multiplication_slicice.png"  width="440" height="200">
        * <img src="https://miro.medium.com/max/1004/1*jXhh2a0jApKbRuHaCFKynA.png"  width="440" height="200">
        * this kernal can be parameters to train
        
* Horizontal edge
    * example: kernal (filter)
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
