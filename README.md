# Sparse Conversation Structure Modeling for Early Rumor Verification

Research code accompanying the manuscript **Sparse Conversation Structure Modeling for Early Rumor Verification**. SSEE combines RoBERTa node encoding, a two-layer GAT, Structural Evidence Mining (SEM), Adaptive Global Context Compensation (AGCC), and Adaptive Structural Enhancement (ASE).

## What is included

| Notebook | Experiment |
| --- | --- |
| `notebooks/01_drweibo_early_windows.ipynb` | Initial DRWeibo early-window runs; resume-aware version |
| `notebooks/02_drweibo_multiseed.ipynb` | DRWeibo GAT and SSEE at 10/30/60/120/240 min across five seeds |
| `notebooks/03_pheme_loeo_multiseed.ipynb` | PHEME leave-one-event-out runs for semantic-only, GAT, SSEE |
| `notebooks/04_drweibo_ablation.ipynb` | Five-seed SSEE remove-one-component ablations |
| `notebooks/05_drweibo_parameter_sensitivity.ipynb` | 10-min DRWeibo parameter sensitivity |
| `notebooks/06_drweibo_complexity.ipynb` | 10-min DRWeibo parameter, runtime, and memory analysis |
| `notebooks/07_drweibo_case_study.ipynb` | 10-min DRWeibo case study and interpretability analysis |

Notebooks retain their original code. Their saved outputs and execution counts were cleared for publication. They have **not** been rerun in this package.

## Datasets

Download the original datasets from their providers. Original social-media data is not included in this repository.

- DRWeibo: https://github.com/CcQunResearch/DRWeibo
- PHEME veracity classification (nine events): https://figshare.com/articles/dataset/PHEME_dataset_for_Rumour_Detection_and_Veracity_Classification/6392078

These notebooks expect already processed JSONL files under the `BASE_DIR` configured near the top of each notebook. In particular, DRWeibo uses `splits/DRWeibo/{train,val,test}.jsonl` and early-window data under `DRWeibo/`. PHEME expects a processed full JSONL with an event field. The exact JSONL schema and data preparation scripts **are not yet included**; downloading the original datasets alone does not make these notebooks runnable.

## Environment and execution

The imports used by this collection include PyTorch, Transformers, NumPy, pandas, scikit-learn, and tqdm; see `requirements.txt`. Dependency versions and pretrained model weights have not yet been pinned.

Before running, adjust `BASE_DIR` in each notebook (currently an AutoDL filesystem path), provide the processed dataset files and local pretrained model folders (`chinese_roberta_wwm_ext` and `roberta_base`), and verify the output directory and checkpoint settings. Run cells in order with a CUDA-capable environment. The multiseed and ablation notebooks can reuse earlier saved results/checkpoints, so check those dependencies before starting a clean run.

The experimental seeds in the multiseed notebooks are `42, 52, 62, 72, 82`. DRWeibo uses five early observation windows; PHEME uses leave-one-event-out evaluation. These notebooks have not been validated end-to-end outside the original compute environment.

## Coverage and remaining release work

The provided notebooks implement the controlled semantic-only / GAT / SSEE experiments, ablations, sensitivity, complexity and case study. **BiGCN and RAGCL implementations used for the external comparisons are not among the supplied notebooks**, so the entire paper is not yet reproducible from this repository. Add the baseline implementations, exact fixed splits or split-generation code, preprocessing scripts and schema, model-weight instructions, pinned dependency versions, and machine-readable result summaries before describing this repository as a complete reproduction package.

## Citation

Citation details will be added once the manuscript is publicly available.
