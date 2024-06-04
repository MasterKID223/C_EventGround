<h1 align="center">EventGround: Narrative Reasoning by Grounding to Eventuality-centric Knowledge Graphs</h1>



This repo copy of : https://github.com/HKUST-KnowComp/EventGround


## Requirements

Install the following packages:

```
dgl==0.8.1
pytorch==1.9.1
allennlp==2.9.3
transformers==4.21.0
datasets==2.0.0
sentence-transformers==2.2.2
faiss-gpu==1.7.2
wandb==0.12.14
```

## Data

Start by downloading the KG data and the related datasets.

### `./data`

This directory is for storing ASER KGs, embeddings, Faiss index, and so on.

Download aser data to `./data` from here: https://hkust-knowcomp.github.io/ASER

### `./dataset`

This directory is for storing narrative reasoning datasets.

## Preprocessing

To set up the eventuality retriever, first embed ASER nodes with `retrieval_pipeline/get_aser_event_embeds.py`. Then, train a Faiss accelerator with `retrieval_pipeline/train_faiss.py`.

With the retriever prepared, run the preprocessing scripts in the following order to obtain grounded eventuality subgraphs.

1. `preprocess_[DATASET]_events.py` for event extraction.
2. `preprocess_[DATASET]_pairs.py` to find event anchors for the extracted events.
3. `preprocess_[DATASET]_sp.py` to find shortest paths on eventuality KGs.
4. `preprocess_[DATASET]_graphs.py` to construct subgraphs.

## Training

Refer to the `run.py` scripts under dataset specific folders (`SCT`, `MCNC`).
All the training and evaluation results will be found in the wandb panel.

## Misc

If you use this research, please cite us:
```bibtex
@article{jiayang2024eventground,
  title={EventGround: Narrative Reasoning by Grounding to Eventuality-centric Knowledge Graphs},
  author={Jiayang, Cheng and Qiu, Lin and Chan, Chunkit and Liu, Xin and Song, Yangqiu and Zhang, Zheng},
  journal={arXiv preprint arXiv:2404.00209},
  year={2024}
}
```

If you have any questions, please send an email to `jchengaj@cse.ust.hk`.