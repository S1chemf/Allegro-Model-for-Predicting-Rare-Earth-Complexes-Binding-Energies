# Building an Allegro Model to Predict Binding Energies of Rare-Earth Metal Complexes

This repository contains instructions and configuration examples for training, evaluating, and analyzing an Allegro machine learning potential to predict binding energies of rare-earth metal complexes.

---

## Requirements

### 1. Install Allegro 

Follow the installation guide in the official Allegro repository: https://github.com/mir-group/allegro

**Tip:** Run on **GPU** to improve performance

### 2. Provided Files
- **Training config:** `train.yaml`  
- **Evaluation config:** `check_models.yaml`
- **Metrics config:** `metric_config.yaml`

These YAML files contain parameters needed for model training and evaluation.

---

## Datasets

1. Datasets must be in **extended XYZ (.xyz)** format.
2. The dataset used in this study is accessible via the link in the Data Availability Statement (full data will be available when paper is published)
3. Update dataset paths in your YAML configuration files accordingly.

---

## Training

Once Allegro is installed, train your model using: 

`nequip-train train.yaml`

### YAML Configuration (train.yaml) 

Edit the following parameters before training:

| Parameter                      | Description                               |
| -------------------------------| ----------------------------------------- |
| `dataset_file_name`            | Path to the **training dataset**          |
| `validation_dataset_file_name` | Path to the **validation dataset**        |
| `n_train`                      | Number of training datapoints             |
| `n_val`                        | Number of validation datapoints           |
| `root`                         | Directory for saving **training results** |
| `run_name`                     | Name of this training run                 |
| `wandb_project`                | Project name for Weights & Biases logging |

### Key hyperparameters to modify:
- edge_eng_mlp_latent_dimensions: [16]
- env_embed_multiplicity: 2 / 4
- l_max: 2
- latent_mlp_latent_dimensions: [8, 16, 32, 64]
- num_layers: 2
- two_body_latent_mlp_latent_dimensions: [8, 16, 32, 64]

---

## Evaluation

To test your trained model on your test set, run:

`nequip-evaluate --train-dir ./training_results_directory --dataset-config check_models.yaml --batch-size 10 --output name_tested.xyz --metrics-config metric_config.yaml`

### YAML Configuration (check_models.yaml) 

Set:

`dataset_file_name` → path to your test dataset

---

## Citation

If you use this workflow in your research, please cite:

[**A. Gupta, C. V. Hetherington and W.A. de Jong**, *Toward Accelerating Rare-Earth Metal Extraction Using Equivariant Neural Networks* 2025](https://chemrxiv.org/engage/chemrxiv/article-details/684279d91a8f9bdab53e29b9)
