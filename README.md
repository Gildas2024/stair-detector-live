# 🪜 Stair Detection & Step Counting (Computer Vision)

Ce projet vise à **détecter automatiquement un escalier** dans une image/vidéo et à **estimer le nombre de marches visibles**.  
Deux stratégies de vision par ordinateur sont comparées :

1. **Annotation globale de l’escalier** (un seul objet) + **estimation du nombre de marches** par post-traitement.
2. **Annotation par marche** (chaque marche annotée par une bounding box) + **comptage direct**.

📌 Le projet a été conçu et testé en conditions réelles (Île-de-France), où certains motifs architecturaux peuvent être confondus avec des escaliers (risque élevé de faux positifs).

---

## 🎯 Objectifs

- Détecter la présence d’un escalier dans une scène (image/vidéo)
- Estimer le **nombre de marches** visibles
- Comparer deux méthodes d’annotation/détection
- Réduire les **faux positifs** observés en environnement urbain

---

## 🧠 Méthodes comparées

### ✅ Méthode 1 — Annotation globale de l’escalier
- Classe : `staircase`
- Modèle : Détection / segmentation de la zone escalier
- Comptage : post-traitement (analyse structurelle dans la zone détectée)

📌 Avantages : annotation rapide, bonne détection globale  
⚠️ Limites : comptage plus complexe (perspective, ombres, occlusions)

---

### ✅ Méthode 2 — Annotation de chaque marche
- Classe : `step`
- Modèle : Object detection (bounding boxes)
- Comptage : nombre de boxes détectées (filtrage par confiance + suppression de doublons)

📌 Avantages : comptage direct, validation facile  
⚠️ Limites : annotation longue, sensibilité aux petites marches / flou / occlusions

---

## 📷 Protocole de prise de vue (réduction des faux positifs)

Afin d’améliorer la robustesse du système, les conditions d’acquisition sont standardisées :

- 📌 Hauteur caméra : **1,4 m à 1,6 m**
- 📌 Caméra inclinée **vers le bas** avec un angle contrôlé
- 📌 Éviter la caméra orientée vers le haut (forte hausse des faux positifs)

🔍 Exemple de cas réel : lors d’un test à **Place de la République**, une orientation vers le haut a généré beaucoup de faux positifs (façades, motifs urbains détectés comme marches).

---

## 🗂️ Structure du dépôt

