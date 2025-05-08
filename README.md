# Kidney-stone-detection
Nous allons en fait creer un modele capable de detecter les calculs renaux
Structure recommandé du repository :

```
kidney-stone-detection/
├── data/...                      # Dossier pour stocker les images (localement ou lien vers drive)
├── notebooks/...                 # Notebooks Jupyter d'exploration ou de test
├── scripts/                   # Scripts Python (prétraitement, utils…)
│   └── preprocess_dicom.py
│   └── preprocess_dataset.py ...
├── results/...                   # Cartes de chaleur, visualisations, logs…
├── README.md                  # Présentation du projet
├── requirements.txt           # Dépendances Python
└── .gitignore                 # Fichiers à ignorer (DICOM, outputs lourds…)


# Documentation de la partie Prétraitement
Le prétraitement est fait en deux étapes:
- il y'a d'abord une phase d'exploration des images; c'est-à-dire:
1)Vérifier que les images sont correctement chargées
2)Identifier des variations de dimensions
3)Documenter le dataset avant un prétraitement plus poussé

- puis ensuite vient le prétraitement proprement dit des images, structuré comme suit dans preprocess_dataset.py:

RAW_DIRS: Dossiers sources contenant les images ("normal" et "stone")

OUTPUT_ROOT: Dossier de destination pour les images traitées

TARGET_SIZE: Taille de redimensionnement (224x224 pixels)

COLOR_MODE: Conversion en RGB (couleur) ou L (niveaux de gris)

RATIOS: Répartition train/val/test (70%/15%/15%)

EXTENSIONS: Formats d'image acceptés (JPG, PNG, etc.)

AUGMENTATIONS: Techniques d'augmentation pour l'entraînement (retournement, rotation, luminosité).
Cette phase a pour fonctionnalités principales: la validation des images avec une gestion des erreurs, la conversion de l'espace colorimétrique, le redimensionnement et application d'augmentation pour le jeu d'entrainement seulement.
Les points forts de cette étape sont sa robustesse(gestion des erreurs et validation d'images), sa flexibilité et la visualisation(vérification visuelle des résultats avec des échantillons).

cette étape est importante pour s'assurer que les données sont propres et bien structurées et optimisées pour l'apprentissage.
