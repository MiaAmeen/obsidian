[[Lecture25.pdf]]

- used for edge detection
- convolution layers: kernels ($f\times f$), padding($p$), stride($s$)
	- input size: (h x w)
	- output size: $[\frac{h + 2p − f}{s} + 1] \times [\frac{w + 2p − f}{s} + 1]$
	- kernel depth = input channels, output channels = no of kernels.
	- **valid convolution**: no padding. **same convolution**:  image is padded such that output size equals image size!![[Screenshot 2025-04-22 at 11.44.37 PM.png]]
	- Parameters per kernel = $(f \times f \times inputChannels) + 1$
	- Parameters per layer = $((f \times f \times inputChannels) + 1) \times numKernels$
- Pooling Layers: max/avg. No parameters needed.
- Loss
	- MSE: $\frac{1}{m} \sum_{i=1}^m (y_i - \hat{y_i})^2$
	- Cross Entropy for classification: $-\frac{1}{m} \sum_{i=1}^m \sum_{j=1}^k (y_{ij} - \hat{y_{ij}})^2$
