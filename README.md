# Knowledge Tracing Benchmark

This repository provides a unified framework to train, evaluate, and compare various Knowledge Tracing (KT) models on multiple datasets. It supports:

- Training a **single model** on all datasets
- Training **all models multiple times** (`n_runs`) to ensure robustness and account for randomness in deep learning

---

## Project Structure

- `dataloader.py`: Handles loading and preprocessing of KT datasets
- `evaluation.py`: Contains training, testing, and custom loss functions
- `n_runs.py`: Trains all models for multiple runs and aggregates results
- `run.py` (optional): Used to train a single model once
---

## Train a Single Model (Example: LSTM)

To train one model on all datasets:

```bash
python run.py --lstm --hidden=128 --epochs=10
```
## Train All Models with Multiple Runs
```bash
python n_runs.py --hidden=128 --epochs=10
```
Iterates through all model types (defined in model_types)
Runs each model n_runs times (default: 5)

## Why Use Multiple Runs?
Training deep learning models is stochastic: performance varies depending on random initialization, batch order, dropout, etc.

Running each model multiple times helps to:

  Reduce variance
  
  Report mean performance and standard deviation
  
  Make comparisons between models more reliable

## Datasets

Only two datasets are included in this repository.
All other datasets must be downloaded separately from their official sources.

After downloading, datasets should be placed in the `dataset/` directory, with one subfolder per dataset (e.g., `dataset/assist2009/`, `dataset/statics/`, etc.).
Each folder must contain the required CSV files (`builder_train.csv`, `builder_test.csv`) following the specified format.

Once this structure is respected, all scripts (`run.py`, `n_runs.py`) will run automatically without additional configuration.

## Dataset Format
Each .csv file should follow a three-line structure for each sequence:
```bash
<sequence_length>
<question_id_1>,<question_id_2>,...
<correctness_1>,<correctness_2>,...
```
---
## Citation

If you use KTBench in your research, please cite our paper:

```bibtex
@conference{csedu26,
  author={Anass {El Ayady} and Maxime Devanne and Germain Forestier and Nour {El Mawas}},
  title={KTBench: A Unified Evaluation Framework for Deep Knowledge Tracing},
  booktitle={Proceedings of the 18th International Conference on Computer Supported Education - Volume 1: CSEDU},
  year={2026},
  pages={106-117},
  publisher={SciTePress},
  organization={INSTICC},
  doi={10.5220/0014823100004021},
  isbn={978-989-758-833-4},
  issn={2184-5026}
}
```

---
## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgement

This work was supported by the COPCOT project (ANR-22-CE38-0003), funded by the French National Research Agency (ANR).

