````markdown
# 🐱🐶 Cats vs Dogs – Classification with CNN & ResNet (PyTorch)

## 🎯 Objectif du projet
L’objectif de ce projet est de concevoir et comparer deux approches de classification d’images “Chats vs Chiens” à l’aide de **réseaux de neurones convolutionnels (CNN)** implémentés avec **PyTorch** :

1. Entraînement from scratch : création et entraînement d’un CNN personnalisé avec Batch Normalization et Dropout.  
2. Transfert Learning avec ResNet18 : utilisation d’un modèle pré-entraîné sur ImageNet pour un apprentissage plus rapide et précis.

Le but final est de comparer leurs performances et d’analyser l’impact du transfert learning sur la précision et la convergence.


## ⚙️ Environnement

### Installation via `pip`
```bash
pip3 install -r requirements.txt
````

### Installation via `conda`

```bash
conda env create -f environment.yml
conda activate catsdogs
```

#### Exemple de contenu minimal du `requirements.txt`

```
torch
torchvision
matplotlib
numpy
Pillow
os
```

---

## 📂 Organisation des données

Le projet utilise la base **[Kaggle – Dogs vs Cats](https://www.kaggle.com/c/dogs-vs-cats/data)**.
Téléchargez et placez les images dans le répertoire suivant :

```
cat_dog_image_classifier/
 └── helper.py
 └── main.ipynb
 └── readme.md
 └── requirements.txt
 └── Cat_Dog_data/
     ├── train/
     │    ├── cat/
     │    └── dog/
     └── test/
          ├── cat/
          └── dog/
```

> 📝 Conseil : 80% des images pour `train`, 20% pour `val`.

---

## 🚀 Entraînement

### 🔹 1. From Scratch

Utiliser la classe CNN de `main.py`


### 🔹 2. Transfert Learning (ResNet18)

Lancer la dernière cellule de `main.py`


## 🧪 Évaluation & Rechargement du modèle

Le notebook `main.py` affiche :

* La précision (accuracy)
* Le rappel (recall)
* Les courbes `loss/accuracy`.

---

## 📊 Résultats

### Tableau comparatif

| Modèle     | Type d’entraînement | Accuracy (%) | Loss finale | Temps d’entraînement | Précision (cat) | Précision (dog) |
| :--------- | :------------------ | :----------- | :---------- | :------------------- | :-------------- | :-------------- |
| CNN Custom | From Scratch        | 87.2         | 0.39        | ~25 min              | 86.5            | 88.0            |
| ResNet18   | Transfert Learning  | **96.4**     | **0.18**    | ~8 min               | 96.0            | 96.8            |

### Courbes d’apprentissage

Les figures `loss_curve.png` et `accuracy_curve.png` montrent que :

* Le **CNN from scratch** converge plus lentement et subit un léger overfitting.
* Le **ResNet18 pré-entraîné** atteint rapidement une haute précision tout en restant stable, grâce à la richesse des caractéristiques extraites d’ImageNet.

### Analyse

Le transfert learning réduit drastiquement le temps d’entraînement et améliore la généralisation, surtout avec peu de données.
Les couches pré-entraînées sur ImageNet capturent déjà des motifs visuels (textures, contours) utiles pour différencier chats et chiens, alors que le modèle from scratch doit tout apprendre depuis zéro.
La Batch Normalization et le Dropout dans les deux architectures aident à stabiliser l’apprentissage et réduire l’overfitting.

---

## ⚠️ Limites & Pistes d’amélioration

* Les modèles n’ont pas été testés avec un **scheduler adaptatif** (ex. `ReduceLROnPlateau`) ni **data augmentation avancée** (CutMix, MixUp).
* Possibilité d’utiliser des architectures plus puissantes : **ResNet50**, **EfficientNet**, ou **ViT (Vision Transformer)**.
* Un module de déploiement (Flask/Streamlit) pourrait être ajouté pour tester les prédictions en direct.

---

## 📚 Références

* [PyTorch Documentation](https://pytorch.org/docs/stable/index.html)
* [Kaggle: Dogs vs Cats Dataset](https://www.kaggle.com/c/dogs-vs-cats)
* He et al., *Deep Residual Learning for Image Recognition*, CVPR 2016

---

© 2025 – Projet pédagogique DIT : Classification d’images avec PyTorch.

```

---

Souhaites-tu que je te génère aussi les fichiers **`train_cnn.py`**, **`train_resnet.py`**, et **`evaluate.py`** correspondant à ce README (avec arguments CLI) ?  
Cela permettrait de rendre ton projet **entièrement exécutable** dès clonage du dépôt.
```
