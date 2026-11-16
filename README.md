# Factory de mots de passe

Projet de génération de mots de passe par apprentissage automatique (AMS – Sujet 2).
Il entraîne et compare plusieurs modèles de langage au niveau caractère (n-gram, RNN, LSTM, GRU, TCN, Transformer, Seq2Seq débruiteur) sur un corpus de mots de passe, puis génère de nouveaux mots de passe avec chacun d'eux.

> Avertissement : projet à but pédagogique. Ne l'utilisez que sur des données dont vous avez le droit de vous servir.

## Table des matières

- [Fonctionnalités](#fonctionnalités)
- [Structure du projet](#structure-du-projet)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Modèles](#modèles)
- [Évaluation](#évaluation)
- [Résultats](#résultats)
- [Auteur](#auteur)

## Fonctionnalités

- Analyse du corpus d'entraînement (distribution des longueurs, statistiques)
- Entraînement de plusieurs architectures :
  - Modèle **n-gram**
  - **RNN**, **LSTM** et **GRU** au niveau caractère
  - **TCN** (Temporal Convolutional Network)
  - **Transformer**
  - **DAE Seq2Seq** (Denoising Auto-Encoder)
- Génération de mots de passe avec chaque modèle
- Évaluation et comparaison des modèles

## Structure du projet

```
amssujet2/
├── analyse_corpus.py          # Analyse statistique du corpus
├── train_ngram.py             # Entraînement du modèle n-gram
├── train_char_rnn.py          # Entraînement RNN / LSTM / GRU
├── prof_style_rnn.py          # Variante RNN (style de référence)
├── train_tcn.py               # Entraînement du TCN
├── train_transformer.py       # Entraînement du Transformer
├── train_dae_seq2seq.py       # Entraînement du DAE Seq2Seq
├── generate_all_models.py     # Génération avec tous les modèles
├── generate_dae_passwords.py  # Génération avec le DAE Seq2Seq
├── train.txt                  # Corpus d'entraînement
├── eval.txt                   # Jeu d'évaluation
├── length_distribution.csv    # Distribution des longueurs
├── generated_passwords.txt    # Mots de passe générés
├── lstm_pw.txt                # Mots de passe générés par le LSTM
├── model_rnn.pt  model_lstm.pt  model_gru.pt  model_tcn.pt
├── best_transformer.pt        # Meilleur Transformer
├── best_dae_seq2seq.pt        # Meilleur DAE Seq2Seq
└── results/                   # Résultats des expériences
```

## Installation

**Prérequis** : Python 3.9+ et PyTorch (À COMPLÉTER : version exacte).

```bash
git clone https://github.com/chaiebyassine/amssujet2.git
cd amssujet2

python -m venv venv
source venv/bin/activate        # Windows : venv\Scripts\activate

pip install torch numpy pandas   # À COMPLÉTER : ajouter les autres dépendances
```

## Utilisation

### 1. Analyser le corpus
```bash
python analyse_corpus.py
```

### 2. Entraîner les modèles
```bash
python train_ngram.py
python train_char_rnn.py
python train_tcn.py
python train_transformer.py
python train_dae_seq2seq.py
```

### 3. Générer des mots de passe
```bash
python generate_all_models.py       # tous les modèles
python generate_dae_passwords.py    # DAE Seq2Seq uniquement
```

Les modèles pré-entraînés (`.pt`) sont déjà fournis : vous pouvez passer directement à l'étape 3.

## Modèles

| Modèle | Fichier d'entraînement | Poids sauvegardés |
|---|---|---|
| N-gram | `train_ngram.py` | — |
| RNN | `train_char_rnn.py` | `model_rnn.pt` |
| LSTM | `train_char_rnn.py` | `model_lstm.pt` |
| GRU | `train_char_rnn.py` | `model_gru.pt` |
| TCN | `train_tcn.py` | `model_tcn.pt` |
| Transformer | `train_transformer.py` | `best_transformer.pt` |
| DAE Seq2Seq | `train_dae_seq2seq.py` | `best_dae_seq2seq.pt` |

## Évaluation

Les modèles sont évalués sur `eval.txt` (À COMPLÉTER : métriques utilisées, par ex. perplexité, taux de couverture/hits, unicité, distribution des longueurs).

## Résultats

À COMPLÉTER : tableau comparatif des modèles, par exemple :

| Modèle | Métrique 1 | Métrique 2 |
|---|---|---|
| LSTM | … | … |
| Transformer | … | … |

Les résultats détaillés se trouvent dans le dossier `results/`.

## Auteur

**Yassine Chaieb** – [@chaiebyassine](https://github.com/chaiebyassine)
