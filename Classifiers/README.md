This repository implements Bayesian-optimized deep learning classifiers evaluated using 5-fold stratified cross-validation to ensure robust and reliable performance estimation. Experiments are conducted across four training configurations:

🔹 Traditional augmentation

🔹 StyleGAN3-R augmented dataset

🔹 Vanilla LDM augmented dataset

🔹 Proposed PL-LDGAN augmented dataset

For fair evaluation, the test set is kept completely original and unseen during training and validation, and is used strictly for final performance assessment. Classification metrics are recorded separately for each augmentation strategy to enable a clear and unbiased comparison of their impact on model generalization.
