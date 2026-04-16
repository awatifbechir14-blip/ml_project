#  Pipeline de Traduction Automatique et Évaluation BLEU

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Black](https://img.shields.io/badge/code%20style-black-000000.svg)
![Pytest](https://img.shields.io/badge/tested%20with-pytest-green)

Projet réalisé dans le cadre du **Master 1 BIDABI** — Université Sorbonne Paris Nord  
**Auteur** : Awatif Bechir 

---

##  Description

Ce projet implémente un pipeline modulaire de traduction automatique français → anglais,  
en utilisant le modèle **HelsinkiNLP/opus-mt-fr-en** (HuggingFace).  
La qualité des traductions est évaluée automatiquement via la métrique **BLEU**.

---

##  Structure du projet

- **src/**
  - **loaders/** — Chargement des données (CSV, JSON)
    - `base_loader.py`
    - `csv_loader.py`
    - `json_loader.py`
    - `loader_factory.py`
  - **translators/** — Interface avec les modèles HuggingFace
    - `base_translator.py`
    - `translator.py`
  - **processors/** — Nettoyage et transformation des données
    - `base_processor.py`
    - `data_processor.py`
  - **evaluators/** — Calcul des métriques (BLEU)
    - `base_evaluator.py`
    - `evaluator.py`
  - **orchestrator/** — Coordination du pipeline
    - `pipeline.py`
    - `orchestrator.py`
  - `config.py` — Configuration générale
  - `main.py` — Point d'entrée principal
  - `main01.py`
  - `main02.py`
- **data/** — Fichiers d'entrée (sample.json, sample02.json)
- **output/** — Résultats du pipeline
- **tests/** — Tests unitaires
- `.github/workflows/` — Pipeline CI/CD GitHub Actions

---

##  Installation

```bash
# Créer et activer l'environnement virtuel
python -m venv .venv
.venv\Scripts\activate        # Windows
source .venv/bin/activate     # Linux / macOS

# Installer les dépendances
pip install -r requirements.txt
```

---

##  Lancer le pipeline

```bash
python src/main.py
```

---

##  Tests et qualité du code

```bash
# Lancer les tests unitaires
pytest

# Vérifier le formatage
black --check .

# Appliquer le formatage automatiquement
black .
```

---

##  Fonctionnement du pipeline

1. **Chargement** — Les données sont lues depuis `data/` (CSV ou JSON)
2. **Traduction** — Le modèle HelsinkiNLP traduit les textes français en anglais
3. **Post-traitement** — Nettoyage et normalisation des textes traduits
4. **Évaluation** — Calcul du score BLEU pour mesurer la qualité
5. **Sortie** — Les résultats sont enregistrés dans `output/`

---

##  Technologies utilisées

- Python 3.10
- HuggingFace Transformers
- BLEU (sacrebleu)
- pytest
- black
- Cookiecutter (template)
- GitHub Actions (CI/CD)
