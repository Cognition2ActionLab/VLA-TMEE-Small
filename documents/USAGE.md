# Usage

##  LIBERO Experiments

Following [DOWNLOAD_DATASET](documents/DOWNLOAD_DATASET.md) and [DOWNLOAD_MODEL](documents/DOWNLOAD_MODEL.md), we have prepared the required datasets and models.
Then, before training, we need to modify:

- The **directory of data**: `root_dir`
- The **path of the language embedding model**: `embedding_model_path`

These configurations can be updated in [libero_exp/configs/base/data/default.yaml](../libero_exp/configs/base/data/default.yaml).

Please refer to [scipts files](libero_exp/scripts) of LIBERO.
To start an experiment, please choose:
- `Benchmark` from `['libero_spatial', 'libero_object', 'libero_goal', 'libero_10']`
- `Policy` from `['bc_policy', 'bc_mee_policy']`
- `Backbone` from `['rnn', 'transformer', 'dp']`
- `if you want to modify the noise shapes, please read the libero_exp/data/train_dataset.py for more details.`
### Training with base

```bash
# for bc_policy
#                                       benchmark        policy      backbone     train_ratio seed
bash libero_exp/scripts/main_libero.sh 'libero_spatial' 'bc_policy' 'transformer' 1.0 0
# for bc_mee_policy
#                                     benchmark        policy      backbone     train_ratio   seed  mee_sigma   mee_weight
bash libero_exp/scripts/main_libero_mee.sh 'libero_spatial' 'bc_mee_policy' 'transformer' 1.0 0 0.5 1.0
```

### Training with few-shot

```bash
# for bc_policy
#                                                   benchmark        policy      backbone     train_ratio   seed 
bash libero_exp/scripts/train/few_shot/main_libero_few_shot.sh 'libero_spatial' 'bc_mee_policy' 'transformer' 0.2 0
# for bc_mee_policy
#                                                   benchmark        policy      backbone     train_ratio   seed  mee_sigma   mee_weight
bash libero_exp/scripts/train/few_shot/main_libero_mee_few_shot.sh 'libero_spatial' 'bc_mee_policy' 'transformer' 0.2 0 0.5 1.0
```

### Training with imbalance

```bash
# for bc_policy
#                                              benchmark        policy      backbone     imbalance_flag    ratio1    ratio2   seed
bash libero_exp/scripts/train/imabalance/main_libero_imbalance.sh 'libero_spatial' 'bc_mee_policy' 'transformer' true 0.2 0.8 0
# for bc_mee_policy
#                                              benchmark        policy      backbone     imbalance_flag    ratio1    ratio2   seed  mee_sigma   mee_weight
bash libero_exp/scripts/train/imabalance/main_libero_mee_imbalance.sh 'libero_spatial' 'bc_mee_policy' 'transformer' true 0.2 0.8 0 0.5 1.0
```

### Training with noise

```bash
# for bc_policy
#                                           benchmark        policy      backbone     train_ratio     noise_flag    seed
bash libero_exp/scripts/train/noise/main_libero_noise.sh 'libero_spatial' 'bc_mee_policy' 'transformer' 1.0 true 0
# for bc_mee_policy
#                                           benchmark        policy      backbone     train_ratio     noise_flag   seed   mee_sigma   mee_weight
bash libero_exp/scripts/train/noise/main_libero_mee_noise.sh 'libero_spatial' 'bc_mee_policy' 'transformer' 1.0 true 0 0.5 1.0
```

### Evaluation

If using [eval_libero.sh](../libero_exp/scripts/eval/eval_libero.sh), the command is as follows:
```bash
# for bc_policy
#                                        diectory of checkpoint            only evalute on final checkpoint
bash libero_exp/scripts/eval/eval_libero.sh 'outputs/libero/bc_policy/dp/libero_goal/1130_1137_seed0' False
# for bc_mee_policy
bash libero_exp/scripts/eval/eval_libero_mee.sh 'outputs/libero/bc_mee_policy/dp/libero_goal/1130_1137_seed0' False
```

If using [eval_libero_all.sh](../libero_exp/scripts/eval/eval_libero_all.sh), you need to specify the directory of the testing model in the evaluation script before running the evaluation:

```bash
#                        only evalute on final checkpoint
bash libero_exp/scripts/eval/eval_libero_all.sh' False
```

