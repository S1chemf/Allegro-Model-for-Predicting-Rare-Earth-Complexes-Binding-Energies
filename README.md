# Building an Allegro model to predict binding energies of rare-earth metal complexes 

## Allegro training

1. Install Allegro using the instructions found here: https://github.com/mir-group/allegro
2. A sample .yaml file (filename.yaml) is provided. Once Allegro is installed, use your dataset in the yaml file to train the model with the following training command: `nequip-train filename.yaml` 

## Allegro evaluation

1. Test the trained model on your test set by running the `nequip-evaluate command`. A sample .yaml file is provided for this step (check_models.yaml).
2. Plot the parity plots comparing binding energies predicted by the Allegro model against ground truth values for the test set.
