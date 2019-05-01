
Assignment 1B:

# What are Channels and Kernels (according to EVA)?

- Featues are the ingredients i.e. the small individual components in order to build complex things. Say for an image, we have 
**edges & gradients** which gives **textures**,then **patterns** then **parts of objects** then **objects** and if objects are
combined it gives **scene**. 


- Kernels are features extractors and a set of similar features_bags / information are the channels.


- Kernel is also called filters, a feature extractors or a 3x3 matrix (convolution matrix or mask ).

Below, we have 3x3 kernel convolved over 4x4 input image. The output 2x2 is  a feature map or a channel. This can be a very basic channel say consists of all edges.So an arc can contain many similar edges. Remember that the arc might be not be fundamental channel however by combining may arc and angle there would exist complex channel which contextually makes sense.

![conv](https://raw.githubusercontent.com/Mutum/conv_arithmetic/master/gif/no_padding_no_strides.gif)

# Why should we only (well mostly) use 3x3 Kernels?

- Kernel size are odd as it gives  advantage of its symmetry around the origin. 


- Any odd size (bigger than 3x3) kernel can be expressed as a multiple convolution operation of 3x3 kernel. In below figure, an input 5x5 image can be convolved by 5x5 kernel to reach 1x1 yet convolving on the same input by 3x3 kernel twice gives the same result. 


- Less parameter and computationally efficient : Refering from the second point above, in case of 5x5 kernel we have 2x5=25 parameters/weights to learn. Yet for 3x3 kernel convolving twice, it is   18 (3x3 + 3x3) parameters.Hence with less parameters,3x3 kernel is more computationally efficient than 5x5 or other higher odd kernels. Moreover, lesser kernel contribute more layers which in turn learn more complex non-linear features by the network.


- As such 3x3 kernel is heavily optimized and accelerated by most of the graphic card manufactures like Nvidia,Intel etc

![receptive_field](https://mlblr.com/images/receptive_field.gif)

# How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)

By rough calculation , we can quickly show 199/2 = 99.5 ie 99 or 100 layers will be there. Below is the details reduction in size in each layers. When convolved by 3x3 kernel on an input size without padding and stride of 1, the feature map size would be 2 less than input size.

- layer 0: 199 x 199
- layer 1: 197 X 197
- layer 2: 195 X 195
- layer 3: 193 X 193
- layer 4: 191 X 191
- layer 5: 189 X 189
- layer 6: 187 X 187
- layer 7: 185 X 185
- layer 8: 183 X 183
- layer 9: 181 X 181
- layer 10: 179 X 179
- layer 11: 177 X 177
- layer 12: 175 X 175
- layer 13: 173 X 173
- layer 14: 171 X 171
- layer 15: 169 X 169
- layer 16: 167 X 167
- layer 17: 165 X 165
- layer 18: 163 X 163
- layer 19: 161 X 161
- layer 20: 159 X 159
- layer 21: 157 X 157
- layer 22: 155 X 155
- layer 23: 153 X 153
- layer 24: 151 X 151
- layer 25: 149 X 149
- layer 26: 147 X 147
- layer 27: 145 X 145
- layer 28: 143 X 143
- layer 29: 141 X 141
- layer 30: 139 X 139
- layer 31: 137 X 137
- layer 32: 135 X 135
- layer 33: 133 X 133
- layer 34: 131 X 131
- layer 35: 129 X 129
- layer 36: 127 X 127
- layer 37: 125 X 125
- layer 38: 123 X 123
- layer 39: 121 X 121
- layer 40: 119 X 119
- layer 41: 117 X 117
- layer 42: 115 X 115
- layer 43: 113 X 113
- layer 44: 111 X 111
- layer 45: 109 X 109
- layer 46: 107 X 107
- layer 47: 105 X 105
- layer 48: 103 X 103
- layer 49: 101 X 101
- layer 50: 99 X 99
- layer 51: 97 X 97
- layer 52: 95 X 95
- layer 53: 93 X 93
- layer 54: 91 X 91
- layer 55: 89 X 89
- layer 56: 87 X 87
- layer 57: 85 X 85
- layer 58: 83 X 83
- layer 59: 81 X 81
- layer 60: 79 X 79
- layer 61: 77 X 77
- layer 62: 75 X 75
- layer 63: 73 X 73
- layer 64: 71 X 71
- layer 65: 69 X 69
- layer 66: 67 X 67
- layer 67: 65 X 65
- layer 68: 63 X 63
- layer 69: 61 X 61
- layer 70: 59 X 59
- layer 71: 57 X 57
- layer 72: 55 X 55
- layer 73: 53 X 53
- layer 74: 51 X 51
- layer 75: 49 X 49
- layer 76: 47 X 47
- layer 77: 45 X 45
- layer 78: 43 X 43
- layer 79: 41 X 41
- layer 80: 39 X 39
- layer 81: 37 X 37
- layer 82: 35 X 35
- layer 83: 33 X 33
- layer 84: 31 X 31
- layer 85: 29 X 29
- layer 86: 27 X 27
- layer 87: 25 X 25
- layer 88: 23 X 23
- layer 89: 21 X 21
- layer 90: 19 X 19
- layer 91: 17 X 17
- layer 92: 15 X 15
- layer 93: 13 X 13
- layer 94: 11 X 11
- layer 95: 9 X 9
- layer 96: 7 X 7
- layer 97: 5 X 5
- layer 98: 3 X 3
- layer 99: 1 X 1



### General formula feature map (output volume): 
    
                (W−F+2P)/S+1
        
        where W = input size
              F = kernel size
              P = padding
              S = stride  
              
In above example , we have
             W = 199 ,
             F = 3 ,
             P = 0 ,
             S = 1
              
    output volume size =  (W−F+2P)/S+1
                       =  (199-3+2*0)/1 + 1 
                       =  196 + 1
                       =  197
                       
Hence in our example above ,in each layer, size of the feature maps will reduce by 2 pixel.


```python

```
