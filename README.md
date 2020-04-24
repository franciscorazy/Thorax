# Thorax
[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org)

Provides Python code to reproduce model training, predictions, and heatmaps from the [CheXNet paper](https://arxiv.org/pdf/1711.05225) that predicted 14 common diagnoses using convolutional neural networks in over 100,000 NIH chest x-rays.

![Illustration](illustration.png?raw=true "Illustration")


## Getting Started:
Click on the `launch binder` button at the top of this `README` to launch a remote instance in your browser using [binder](https://mybinder.org/). This requires no local configuration and lets you get started immediately. Open `Explore_Predictions.ipynb`, run all cells, and follow the instructions provided to review a selection of included [chest x-rays from NIH](https://arxiv.org/pdf/1705.02315.pdf).

To configure your own local instance (assumes [Anaconda is installed](https://www.anaconda.com/download/); can be run on Amazon EC2 p2.xlarge instance if you do not have a GPU):

```git clone https://github.com/franciscorazy/Thorax.git
cd Thorax
conda env create -f environment.yml
source postBuild
source activate Thorax
```

## Replicated results:
This reproduction achieved average test set AUC 0.836 across 14 findings compared to 0.841 reported in original paper:

<div>
<table border="0" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>retrained auc</th>
      <th>chexnet auc</th>
    </tr>
    <tr>
      <th>label</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Atelectasis</th>
      <td>0.8161</td>
      <td>0.8094</td>
    </tr>
    <tr>
      <th>Cardiomegaly</th>
      <td>0.9105</td>
      <td>0.9248</td>
    </tr>
    <tr>
      <th>Consolidation</th>
      <td>0.8008</td>
      <td>0.7901</td>
    </tr>
    <tr>
      <th>Edema</th>
      <td>0.8979</td>
      <td>0.8878</td>
    </tr>
    <tr>
      <th>Effusion</th>
      <td>0.8839</td>
      <td>0.8638</td>
    </tr>
    <tr>
      <th>Emphysema</th>
      <td>0.9227</td>
      <td>0.9371</td>
    </tr>
    <tr>
      <th>Fibrosis</th>
      <td>0.8293</td>
      <td>0.8047</td>
    </tr>
    <tr>
      <th>Hernia</th>
      <td>0.9010</td>
      <td>0.9164</td>
    </tr>
    <tr>
      <th>Infiltration</th>
      <td>0.7077</td>
      <td>0.7345</td>
    </tr>
    <tr>
      <th>Mass</th>
      <td>0.8308</td>
      <td>0.8676</td>
    </tr>
    <tr>
      <th>Nodule</th>
      <td>0.7748</td>
      <td>0.7802</td>
    </tr>
    <tr>
      <th>Pleural_Thickening</th>
      <td>0.7860</td>
      <td>0.8062</td>
    </tr>
    <tr>
      <th>Pneumonia</th>
      <td>0.7651</td>
      <td>0.7680</td>
    </tr>
    <tr>
      <th>Pneumothorax</th>
      <td>0.8739</td>
      <td>0.8887</td>
    </tr>
  </tbody>
</table>
</div>

## Results available in pretrained folder:
- `aucs.csv`: test AUCs of retrained model vs original ChexNet reported results
- `checkpoint`: saved model checkpoint
- `log_train`: log of train and val loss by epoch
- `preds.csv`: individual probabilities for each finding in each test set image predicted by retrained model

## NIH Dataset
To explore the full dataset, [download images from NIH (large, ~40gb compressed)](https://nihcc.app.box.com/v/ChestXray-NIHCC),
extract all `tar.gz` files to a single folder, and provide path as needed in code.

## Note on data
A sample of 621 test NIH chest x-rays enriched for positive pathology is included with the repo to faciliate immediate use and exploration in the `Explore Predictions.ipynb` notebook. The [full NIH dataset](https://nihcc.app.box.com/v/ChestXray-NIHCC) is required for model retraining.

