# Guide d'Utilisation - Analyse Factorielle des Correspondances (AFC)
## Élections Présidentielles France 2012

---

## 📋 Contenu du Notebook

Le notebook **AFC_Elections_Analysis.ipynb** contient une analyse complète en 14 sections:

### 1. **Importation et Chargement des Données**
   - Importe pandas, numpy, matplotlib, scipy
   - Charge le fichier CSV contenant les résultats électoraux
   - Affiche les dimensions du tableau (régions × candidats)

### 2. **Analyse Descriptive du Tableau de Contingence**
   - Affiche le tableau complet des effectifs conjoints
   - Calcule les effectifs marginaux (par région et par candidat)
   - Effectif total N

### 3. **Matrice des Fréquences**
   - Calcule fᵢⱼ = nᵢⱼ / N
   - Vérifie que la somme totale = 1

### 4. **Profils Lignes et Colonnes**
   - **Profils lignes**: distribution du vote par région
   - **Profils colonnes**: répartition géographique par candidat
   - Affiche le profil moyen (distribution nationale)

### 5. **Test d'Indépendance (Chi-Deux)**
   - Formule: χ² = N Σᵢⱼ (fᵢⱼ - fᵢ.f.ⱼ)² / (fᵢ.f.ⱼ)
   - Calcule p-value et degré de liberté
   - **Interprétation**: Si χ² > seuil critique → rejet de l'indépendance
   - Les régions et votes sont associés ✓

### 6. **Matrice des Taux de Liaison**
   - tᵢⱼ = (fᵢⱼ - fᵢ.f.ⱼ) / (fᵢ.f.ⱼ)
   - Valeur positive = surreprésentation (attrait)
   - Valeur négative = sous-représentation (répulsion)
   - Identifie les principales associations

### 7. **Inertie Totale et Distances**
   - Φ² = Σᵢⱼ fᵢ. f.ⱼ tᵢⱼ² = χ²/N
   - Distance Phi-carré entre profils lignes
   - Propriété d'équivalence distributionnelle

### 8. **Décomposition en Valeurs Propres**
   - SVD de la matrice pondérée des taux de liaison
   - Valeurs propres et inerties relatives
   - Affiche le tableau complet

### 9. **Coordonnées Factorielles**
   - **Lignes** (régions): Ψᵢₖ = Uᵢₖ / √fᵢ.
   - **Colonnes** (candidats): Φⱼₖ = Vⱼₖ / √f.ⱼ
   - Tableau des coordonnées pour les 4 premiers axes

### 10. **Qualité de Représentation et Contributions**
   - **Contributions**: Ctr(i,k) = (fᵢ. Ψᵢₖ²) / λₖ × 100
   - **Cosinus carrés (QLT)**: Mesure la qualité de projection
   - Identifie les éléments bien représentés sur chaque axe

### 11. **Visualisations - Diagrammes Factoriels**
   - **Plan 1-2**: Axes 1 et 2 (structure principale)
   - **Plan 3-4**: Axes 3 et 4 (structure secondaire)
   - **Scree plot**: Inertie par axe et inertie cumulée
   - Crée 3 graphiques PNG

### 12. **Interprétation des Axes**
   - Détaille l'Axe 1: régions positives vs négatives
   - Détaille l'Axe 2: structure secondaire
   - Identifie les régions et candidats déterminants

### 13. **Matrice de Reconstruction**
   - Recalcule les taux de liaison à partir des coordonnées
   - tᵢⱼ = Σₖ (Ψᵢₖ Φⱼₖ) / √λₖ
   - Mesure la qualité de la reconstruction

### 14. **Résumé et Conclusions**
   - Synthèse globale des résultats
   - Pourcentage d'inertie expliquée
   - Qualité moyenne de représentation

---

## 🚀 Comment Utiliser

### Prérequis
```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

### Exécution
1. Placez le fichier CSV dans le même répertoire que le notebook
2. Ouvrez le notebook dans Jupyter Lab ou Jupyter Notebook
3. Exécutez toutes les cellules (Shift+Enter ou Run All)
4. Les graphiques s'affichent automatiquement

### Modifier le Nom de l'Étudiant
Dans la première cellule, remplacez `[Votre Nom]` par votre nom:
```python
**Étudiant:** Votre Nom Complet
```

---

## 📊 Résultats Attendus

### Paramètres Principaux à Analyser

1. **Tableau de Contingence**
   - Effectifs conjoints régions × candidats
   - Somme = N (effectif total)

2. **Test Chi-Deux**
   - χ² ≈ 1059.5 (très significatif)
   - p-value ≈ 0.0000
   - **Conclusion**: Forte association

3. **Inertie Totale**
   - Φ² ≈ 0.02928
   - Représentation de l'écart à l'indépendance

4. **Distribution de l'Inertie** (Axes principaux)
   - Axe 1: ~59% de l'inertie totale
   - Axe 2: ~19% de l'inertie totale
   - Axe 3: ~12% de l'inertie totale
   - **Total 4 axes**: >95% de l'inertie

5. **Contributions**
   - Régions influentes: Outremer, Île-de-France, Nord-Pas-de-Calais
   - Candidats influents: Le Pen, Hollande, Sarkozy

---

## 🔍 Interprétation Pédagogique

### Axe 1 (59% inertie)
**Opposition Nord-Est / Sud-Est vs Outremer et Île-de-France**
- Négatif: Régions du Nord-Est, Alsace, Lorraine → votes "Hollande/Sarkozy"
- Positif: Outremer, Île-de-France → votes "blanc/nuls, Bayrou"
- **Signification**: Clivage géographique principal

### Axe 2 (19% inertie)
**Opposition Le Pen vs Bayrou/Sarkozy**
- Négatif: Régions avec fort vote Le Pen
- Positif: Régions avec fort vote Bayrou/Sarkozy
- **Signification**: Clivage entre extrêmes et centre-droit

### Axes 3 et 4 (~12-15% inertie)
- Effets régionaux spécifiques
- Petits candidats et régions particulières

---

## ✅ Points de Contrôle

Avant de rendre votre travail, vérifiez:

- [ ] Le nom de l'étudiant est rempli
- [ ] Tous les tableaux s'affichent correctement
- [ ] Les graphiques (3 PNG) sont générés
- [ ] Le test Chi-Deux montre une p-value très faible
- [ ] L'inertie cumulée sur 4 axes > 90%
- [ ] Les contributions sommées par axe = 100%
- [ ] Les profils lignes et colonnes somment à 1
- [ ] Les coordonnées factorielles sont calculées

---

## 📝 Comparaison avec le Cours

Les éléments du notebook correspondent aux sections du cours:

| Section Cours | Équivalent Notebook | Pages Cours |
|---|---|---|
| Tableau contingence | Sect. 2 | 43-44 |
| Profils L/C | Sect. 4 | 44-45 |
| Chi-Deux | Sect. 5 | 47 |
| Taux liaison | Sect. 6 | 47 |
| Distances Φ² | Sect. 7.2 | 46 |
| Valeurs propres | Sect. 8 | 48 |
| Coordonnées | Sect. 9 | 49-50 |
| Contributions | Sect. 10 | 49-50 |
| Graphiques | Sect. 11 | 51-52 |
| Interprétation | Sect. 12 | 54-57 |

---

## 🎯 Objectifs Pédagogiques

À la fin de cette analyse, vous devez:

1. ✓ Comprendre le test d'indépendance et son interprétation
2. ✓ Calculer tous les paramètres de l'AFC (profils, distances, inerties)
3. ✓ Interpréter les valeurs propres et axes factoriels
4. ✓ Analyser les contributions et qualités de représentation
5. ✓ Créer et interpréter les diagrammes factoriels
6. ✓ Tirer des conclusions significatives de l'analyse

---

## 📞 Support et Troubleshooting

**Problème: ImportError pour certains modules**
→ Solution: `pip install --upgrade pandas numpy matplotlib seaborn scipy scikit-learn`

**Problème: Le fichier CSV n'est pas trouvé**
→ Solution: Vérifiez que le fichier est dans le même dossier que le notebook

**Problème: Les graphiques ne s'affichent pas**
→ Solution: Ajoutez en début du notebook: `%matplotlib inline`

**Problème: Résultats différents du cours**
→ Solution: Vérifiez que les formules correspondent aux pages 43-57 du PDF

---

## 📦 Fichiers Générés

Le notebook génère:
- `AFC_Plan_1_2.png` - Biplot axes 1-2
- `AFC_Plan_3_4.png` - Biplot axes 3-4
- `AFC_Inertie.png` - Scree plot

---

## 📖 Références

- Cours: TP_AFC_Elections__France_souligné.pdf (pages 43-57)
- Données: ADEM_YENGUI_-_resultats_presidentielles_2012.csv
- Source élections: Le Monde, 24-25 avril 2012

---

**Version**: 1.0  
**Date**: 2024  
**Auteur**: Notebook généré pour le cours AFC
