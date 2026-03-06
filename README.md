# Rock–Paper–Scissors Image Classifier (CNN)

## Description

Ce projet implémente un **modèle de deep learning capable de reconnaître les gestes Rock, Paper et Scissors à partir d’images de mains**.  
Le modèle est basé sur un **Convolutional Neural Network (CNN)** entraîné avec **TensorFlow/Keras**.

L’objectif est de montrer de façon simple comment construire un pipeline complet de **Computer Vision** :

1. Charger un dataset d’images  
2. Préparer et transformer les données  
3. Construire un réseau de neurones convolutionnel  
4. Entraîner le modèle  
5. Évaluer sa performance  
6. Faire des prédictions sur de nouvelles images  

Ce projet constitue un **exemple pédagogique de classification d’images avec deep learning**.

---

# Fonctionnement général

Le modèle apprend à reconnaître les formes des mains en analysant les images.

Le pipeline du projet est le suivant :
dataset images -> prétraitement des données -> data augmentation -> réseau CNN -> entraînement -> validation -> sauvegarde du meilleur modèle -> prédiction sur nouvelles images


Le réseau de neurones apprend progressivement à détecter :

- des **bords**
- des **textures**
- des **formes de doigts**
- la **forme globale de la main**

afin de classifier l’image comme : rock, paper, scissors

---

# Structure du projet
```text
.
│
├── data/ # Dataset d'entraînement et de validation
│
├── models/ # Modèles sauvegardés
│ └── rps.keras # Meilleur modèle entraîné
│
├── test/ # Images utilisées pour tester le modèle
│ ├── p.jpg
│ ├── r.jpg
│ └── s.jpg
│
├── rps.ipynb # Notebook principal (entraînement + tests)
├── requirements.txt # Dépendances Python du projet
└── README.md # Documentation du projet
```

---

# Technologies utilisées

Le projet utilise les outils suivants :

| Outil | Utilisation |
|------|-------------|
| Python | Langage principal |
| TensorFlow / Keras | Construction et entraînement du modèle |
| NumPy | Manipulation des tableaux |
| Matplotlib | Visualisation des images et des performances |
| PIL (Pillow) | Chargement des images |
| Jupyter Notebook | Environnement interactif pour l'entraînement |

---

# Installation

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```
Puis ouvrir :

```bash
notebook/rps_training.ipynb
```
et exécuter les cellules dans l’ordre.

---

# Entraînement du modèle

Le modèle est un CNN composé de plusieurs couches convolutionnelles.

Architecture simplifiée :

```text
Input (150x150x3)
↓
Conv2D + ReLU
↓
MaxPooling
↓
Conv2D + ReLU
↓
MaxPooling
↓
Conv2D
↓
Flatten
↓
Dense
↓
Softmax (3 classes)
```

Le modèle est entraîné avec :

- RMSprop optimizer
- Categorical Crossentropy loss
- Accuracy metric

Pendant l'entraînement :

- les images sont augmentées artificiellement (rotation, zoom, flip)
- le meilleur modèle est sauvegardé automatiquement

---

# Résultats

Sur ce dataset, le modèle atteint généralement : ≈ 90% – 98% accuracy sur les données de validation.

--- 

# Exemple de prédiction

Une nouvelle image peut être passée au modèle :

```bash
prediction = model.predict(image)
```

Le modèle retourne une probabilité pour chaque classe :

```bash
[0.02, 0.94, 0.04]
```
La classe prédite est celle avec la probabilité la plus élevée :

```bash
paper
```







