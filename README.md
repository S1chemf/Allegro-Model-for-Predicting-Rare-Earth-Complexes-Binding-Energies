# Building an Allegro Model to Predict Binding Energies of Rare-Earth Metal Complexes

This repository contains instructions and configuration examples for training, evaluating, and analyzing an Allegro machine learning potential to predict binding energies of rare-earth metal complexes.

---

## Requirements

### 1. Install Allegro 

Follow the installation guide in the official Allegro repository: https://github.com/mir-group/allegro

**Tip:** Run on **GPU** to improve performance

### 2. Provided Files
- **Training config:** `filename.yaml`  
- **Evaluation config:** `check_models.yaml`
- **Metrics config:** `metric_config.yaml`

These YAML files contain parameters needed for model training and evaluation.

---

## Datasets

1. Datasets must be in **extended XYZ (.xyz)** format.
2. The dataset used in this study is accessible via the link in the Data Availability Statement
3. Update dataset paths in your YAML configuration files accordingly.

---

## Training

Once Allegro is installed, train your model using: 

`nequip-train filename.yaml`

### YAML Configuration (filename.yaml) 

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
- edge_eng_mlp_latent_dimensions
- env_embed_multiplicity
- l_max
- latent_mlp_latent_dimensions
- num_layers
- two_body_latent_mlp_latent_dimensions

---

## Evaluation

To test your trained model on your test set, run:

`nequip-evaluate --train-dir ./training_results_directory --dataset-config check_models.yaml --batch-size 10 --output name_tested.xyz --metrics-config metric_config.yaml`

### YAML Configuration (check_models.yaml) 

Set:

`dataset_file_name` → path to your test dataset

---

## Citation

If you use Allegro or this workflow in your research, please cite:

**Albert Musaelian, Simon Batzner, Anders Johansson, Lixin Sun, Cameron J. Owen, Mordechai Kornbluth, and Boris Kozinsky.** *"Learning local equivariant representations for large-scale atomistic dynamics." Nature Communications 14, no. 1 (2023): 579*
