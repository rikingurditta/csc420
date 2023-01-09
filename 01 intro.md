# Intro

## Digital images

- image is a matrix
  - pixel $(i, j)$ has intensity $I(i, j)$
  - greyscale or colour
    - $I \in \R^{m \times n}$ for greyscale
    - $I \in \R^{3 \times m \times n}$ for greyscale
  - usually unsigned 8 bit int

## Image filtering

- modify the pixels in image

### Linear filtering - correlation

#### Denoising

- could do with averaging filter
  - causes blurring
- could average with non-uniform weights (e.g. weight central pixels higher)
  - underlying assumption is that closer pixels are more important
  - causes less blurring

- (actual denoising done by stacking multiple images)

#### Correlation kernel

If we have a filter of size $s = 2k+1$, we can apply a linear filter $F \in \R^{s \times s}$ by applying the correlation operation
$$
J(i, j) = F \otimes I =  \sum_{u=-k}^k \sum_{v=-k}^k F(u, v) \cdot I(i + u, j + v)
$$
(in Python, can use `scipy.signal.convolve2d` for this)
