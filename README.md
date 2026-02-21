Détection d’obstacles et estimation de distance par fusion YOLO/LiDAR
📌 Problématique

La caméra détecte efficacement les objets mais ne fournit pas directement leur distance.
Le LiDAR mesure précisément la distance mais ne permet pas l’identification des objets.

Comment fusionner ces deux capteurs pour obtenir une perception complète et fiable des obstacles ?

🧠 Approche choisie : Fusion tardive (Late Fusion)

La fusion tardive consiste à :

Détecter les objets en 2D avec YOLO

Projeter les points LiDAR dans l’image

Associer les points LiDAR aux bounding boxes

Estimer la distance des objets détectés

Cette approche est :

 Simple à implémenter

 Rapide

 Adaptée aux systèmes robotiques temps réel

 Dépendante de la calibration

📚 État de l’art
 Fusion précoce (Early Fusion)

Fusion des données brutes caméra + LiDAR avant détection
Méthodes :

PointFusion

Frustum PointNet

VoteFusion

Haute précision
Complexité élevée

 Fusion intermédiaire (Mid Fusion)

Fusion des représentations intermédiaires (features 2D + 3D)

Méthodes :

F-PointNet

MV3D

AVOD

 Bon compromis
 Architecture complexe

 Fusion tardive (Late Fusion) — Approche retenue

Détection 2D → Projection LiDAR → Estimation distance

Approche utilisée notamment dans des systèmes industriels comme
Tesla Autopilot

 Outils utilisés

 YOLOv8 — Détection d’objets 2D

 KITTI — Dataset caméra + LiDAR calibré

 OpenCV — Traitement d’images

 Point Cloud Library — Traitement nuage de points

 NumPy / Python — Calcul et pipeline

 Matrices de calibration — Projection 3D → 2D

 Pipeline de fusion

Détection des objets via YOLOv8

Chargement du nuage de points LiDAR

Projection des points 3D dans le plan image

Association points–bounding box

Calcul distance moyenne / médiane

Affichage distance sur l’image

📊 Résultats

 Détection robuste des véhicules et piétons

 Estimation précise à courte et moyenne distance

 Légère perte de précision pour objets lointains

 Pipeline compatible temps réel

La fusion tardive offre un bon compromis entre :

Précision

Simplicité

Coût computationnel


Notebook available here:
https://colab.research.google.com/drive/1HR--8BAA1EWBcEWZgdmZd2KW-OpoT64c?usp=sharing


![Results](assets/result.png)


