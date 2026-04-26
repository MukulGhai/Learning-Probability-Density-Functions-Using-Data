````md
# Learning Probability Density Functions using GAN (NO2 Dataset)

## Project Overview

This project learns an unknown probability density function (PDF) of a transformed random variable using a Generative Adversarial Network (GAN).

The original feature used is NO2 concentration from the India Air Quality dataset. Each value is transformed into a new variable `z` using a nonlinear transformation, and then a GAN is trained only on samples of `z` to learn its distribution.

---

## Dataset

- **Dataset Name:** India Air Quality Data  
- **Source:** Kaggle  
- **Link:** https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data

- **Feature Used:** NO2 concentration

---

## Objective

To estimate the probability density function of transformed variable `z` without assuming any analytical distribution such as Gaussian, Exponential, etc.

The GAN learns only from data samples.

---

## Transformation Function

```math
z = x + a_r \sin(b_r x)
````

Where:

* `a_r = 0.5 × (r mod 7)`
* `b_r = 0.3 × ((r mod 5) + 1)`

`r` = University Roll Number

---

## Used Roll Number

`102303463`

### Computed Parameters

* `a_r = 0.5`
* `b_r = 1.2`

---

## GAN Architecture

### Generator

Input: Random noise from Normal Distribution N(0,1)

Layers:

* Dense (16 neurons, ReLU)
* Dense (32 neurons, ReLU)
* Dense (1 neuron output)

### Discriminator

Input: Real/Fake sample

Layers:

* Dense (32 neurons, ReLU)
* Dense (16 neurons, ReLU)
* Dense (1 neuron, Sigmoid)

---

## Training Process

The GAN is trained using two networks:

### Discriminator learns to classify:

* Real transformed samples `z`
* Fake generated samples `z_f`

### Generator learns to fool the discriminator by producing realistic samples.

---

## PDF Approximation

After training:

1. Generate thousands of fake samples using Generator
2. Apply Kernel Density Estimation (KDE)
3. Plot learned probability density function

---

## Libraries Used

* Python
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* SciPy
* TensorFlow / Keras

---

## Output

The final graph compares:

* Histogram of real transformed data
* GAN learned PDF curve

---

## Observations

### Mode Coverage

GAN captures major peaks of the real distribution.

### Training Stability

GAN loss may fluctuate during training, which is normal.

### Quality of Generated Distribution

Generated samples closely follow transformed NO2 distribution.

---

## How to Run

```bash
pip install numpy pandas matplotlib scikit-learn scipy tensorflow
```

Then run:

```python
python main.py
```

---

## Future Improvements

* Use WGAN for better stability
* Deeper Generator network
* Hyperparameter tuning
* Compare KDE vs Histogram PDF

---

## Author

Machine Learning Assignment
Probability Density Estimation using GAN

```
```
