# Understanding and Improving the Exemplar-based Generation for Open-domain Conversation

Code for the paper: "Understanding and Improving the Exemplar-based Generation for Open-domain Conversation", annonymous AAAI 2022 submission.
Our implementation is based on [ParlAI](https://github.com/facebookresearch/ParlAI), so before you start we recommend you to read the README of ParlAI and prepare for the experimental setting.
You can see our implementations in `parlai/agents/transformer/corge.py` and `parlai/agents/transformer/exemplar_based_generator.py`.

## Preliminaries

You should prepare the pre-trained generator and retriever model to train your exemplar-based generator.
For the generator, we use [zoo:blender/blender_90M/model](https://parl.ai/projects/recipes/) from ParlAI, however it is okay to use the model which is pre-trained on the Pushshift.
For the retriever, we fine-tuned the [zoo:pretrained_transformers/bi_model_huge_reddit/model](https://parl.ai/projects/polyencoder/) from ParlAI using BST+ dataset.
We assume your generator and retriever is stored in `GENERATOR_MODEL_PATH` and `RETRIEVER_MODEL_PATH`, respectively.

## Training Exemplar-based Generator

```bash
export RETRIEVER_MODEL_PATH=[];
export GENERATOR_MODEL_PATH=[];
export FIXED_CANDIDATE_PATH=[];

./scripts/train_model.sh exp 5 32 7e-6;
```

## Evaluating Exemplar-based Generator

```bash
# You don't need to load retriever and generator after you trained your exemplar-based generator.
export FIXED_CANDIDATE_PATH=[];

./scripts/eval_model.sh [MODEL_PATH];
```

We also provided the automatic evaulation scripts in [jupyter notebook](https://github.com/aaai22-corge/aaai22-corge/blob/master/scripts/automatic_evaluations.ipynb).

## Get Inference Results from the Exemplar-based Generator

```bash
# You don't need to load retriever and generator after you trained your exemplar-based generator.
export FIXED_CANDIDATE_PATH=[];

./scripts/inference_model.sh [MODEL_PATH];
```
