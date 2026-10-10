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
Fine - tuning:             0.775      448.91s            8398858

## Conclusion
If the frozen backbone were left in train() mode, its BatchNorm running statistics would continue updating on the new dataset, changing the frozen features (which goes against the point).

Fine tuning works slightly better on this dataset (with 10 epoch and a seed of 1), reaching a validation accuracy of 0.775 compared to 0.760 for feature extraction.

With feature extraction, the pretrained backbone remained frozen, so only the new classification head could learn from CIFAR10. Fine tuning on the other hand, allowed the whole last block of the backbone to update, which let the model adjust its pretrained features to better fit the new dataset.

This extra adjustment likely produced the small increase in validation accuracy, however, it came at the cost of requiring more training time and far more trainable parameters.

## Known limitations
One limitation that I know of is that my laptop isn't the best and running off of the CPU. The results may have differed if I was using a more powerful PC with a GPU.

With more time I could try testing different numbers of epochs, different seeds, different datasets / subsets of CIFAR10, and different learning rates.