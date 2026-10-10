# From Frozen Features to Fine-Tuning
Fine-tuning a pretrained vision backbone on CIFAR10, comparing feature extraction against fine-tuning.

## Setup
python -m venv .venv
source .venv/bin/activate # windows: .venv\scripts\activate
pip install -r requirements.txt

## Run
Run the lab03.ipynb notebook from start to finish

## Dataset
I used a 1000 image subset of the CIFAR10 dataset with 800 training images and 200 validation images.
The dataset consists of 32x32 image in 10 classes: Airplanes, Cars, Birds, Cats, Deer, Dogs, Frogs, Horses, Boats, and Trucks.

## Results
Stage               val accuracy   train time   trainable params
Feature extraction:        0.760      372.91s               5130
Fine - tuning:             0.XXX         X.Xs                  X

## Conclusion
which approach worked better on this dataset, and why, in terms of what fine-tuning changed that feature extraction could not.

## Known limitations
Anything you are aware of that does not work, or that you would improve with more time.