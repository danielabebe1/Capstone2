# Predict lung function decline (pulmonary fibrosis)
Pulmonary fibrosis is a lung disease that occurs when lung tissue becomes damaged and scarred. The word “pulmonary” means lung and the word “fibrosis” means scar tissue— similar to scars that you may have on your skin from an old injury or surgery.The scar tissue thickened, stiff tissue makes it more difficult for the lungs to work properly as shown in Fig 1. As pulmonary fibrosis worsens, it becomes progressively more short of breath. As of now pulmonary fibrosis has no treatment but some medications and therapies help to improve quality of life. 
[![normal-and-impaired-gas-exchange.png](https://i.postimg.cc/mrwQfKN6/normal-and-impaired-gas-exchange.png)](https://postimg.cc/Z9W967Qr)
Illustration of lugs with and without pulmonary fibrosis ([source](www.pulmonaryfibrosis.org/))

### About the Dataset
The dataset used in this project is acquired from kaggle where uploaded for competition by OSIC (Open Source Imaging Consortium) [dataset](https://www.kaggle.com/c/osic-pulmonary-fibrosis-progression/data). The dataset contains a baseline chest CT scan and associated clinical information for a set of patients. A patient has an image acquired at time Week = 0 and has numerous follow up visits over the course of approximately 1-2 years, at which time their FVC is measured.

### Target
The aim of the project is to predict a patient’s severity of decline in lung function based on a CT scan of their lungs and determine lung function based on output from a spirometer, which measures the volume of air inhaled and exhaled. Using machine learning techniques to make a prediction with the image, metadata, and baseline FVC as input.

### Evaluation Metrics

Predictions are evaluated with a modified version of the Laplace Log Likelihood. For each sample in test set, an `FVC` and a `Confidence` measure (standard deviation σ) has to be predicted.

`Confidence` values smaller than 70 are clipped.
<img src="https://latex.codecogs.com/svg.latex?\Large&space;x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" title="\large \Delta = min ( |FVC_{true} - FVC_{predicted}|, 1000 )>

\begin{equation*}
P(E)   = {n \choose k} p^k (1-p)^{ n-k} 
\end{equation*}

Errors greater than 1000 are also clipped in order to avoid large errors.

$\large \Delta = min ( |FVC_{true} - FVC_{predicted}|, 1000 ),$

The metric is defined as:

$\Large metric = -   \frac{\sqrt{2} \Delta}{\sigma_{clipped}} - \ln ( \sqrt{2} \sigma_{clipped} ).$
