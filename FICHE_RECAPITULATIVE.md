# Fiche Récapitulative AFC - Élections 2012

## 📋 FORMULES PRINCIPALES

### 1. Matrice des Fréquences
```
f_ij = n_ij / N
```
où N = effectif total = Σᵢⱼ nᵢⱼ

### 2. Profils Lignes (Distribution par région)
```
f_i|j = f_ij / f_i. = n_ij / n_i.
```
Somme pour chaque région = 1

### 3. Profils Colonnes (Distribution par candidat)
```
f_j|i = f_ij / f_.j = n_ij / n_.j
```
Somme pour chaque candidat = 1

### 4. Profils Moyens
```
Profil moyen lignes: f_i. = Σⱼ f_ij
Profil moyen colonnes: f_.j = Σᵢ f_ij
```

### 5. Test d'Indépendance (Chi-Deux)
```
χ² = N × Σᵢⱼ (f_ij - f_i. × f_.j)² / (f_i. × f_.j)

Hypothèse H₀: Indépendance des variables
Rejet si χ² > χ²_critique ou p-value < 0.05
```

### 6. Taux de Liaison
```
t_ij = (f_ij - f_i. × f_.j) / (f_i. × f_.j)

Positif (+) = Surreprésentation (attrait)
Négatif (-) = Sous-représentation (répulsion)
```

### 7. Inertie Totale
```
Φ² = Σᵢⱼ f_i. × f_.j × t_ij² = χ² / N
```

### 8. Distance Phi-Carré entre Régions
```
d²_Φ(i, i') = Σⱼ (f_i|j - f_i'|j)² / f_.j
```
Propriété: Équivalence distributionnelle

### 9. Valeurs Propres et Inerties
```
λ₁ ≥ λ₂ ≥ ... ≥ λₚ (valeurs propres)
Inertie relative: λₖ / Σλ × 100%
Inertie cumulée: Σₖ₌₁ᵐ λₖ / Σλ × 100%
```

### 10. Coordonnées Factorielles
Régions: Ψ_ik = U_ik / √f_i.
Candidats: Φ_jk = V_jk / √f_.j

### 11. Contributions à l'Inertie
```
Régions: Ctr(i,k) = (f_i. × Ψ_ik²) / λ_k × 100%
Candidats: Ctr(j,k) = (f_.j × Φ_jk²) / λ_k × 100%
```
(Somme par axe = 100%)

### 12. Qualité de Représentation (Cosinus Carrés)
```
QLT(i,k) = Ψ_ik² / d²(i, O) × 100%
QLT(j,k) = Φ_jk² / d²(j, O) × 100%
```
(O = origine des axes)

### 13. Reconstruction
```
t_ij = Σₖ (Ψ_ik × Φ_jk) / √λ_k
```

---

## 📊 DONNÉES DU PROBLÈME

### Variables
- **Lignes (régions)**: 23 régions françaises
- **Colonnes (candidats)**: 11 candidats
- **Effectif total**: ~37 millions de votes

### Candidats
1. Hollande (PS)
2. Sarkozy (UMP)
3. Le Pen (FN)
4. Bayrou (MoDem)
5. Mélenchon (Gauche)
6. Joly (EELV)
7. Dupond-Aignan (Debout)
8. Poutou (NPA)
9. Arthaud (LO)
10. Cheminade (Sci-Fi)
11. Blancs/Nuls

---

## 🎯 RÉSULTATS CLÉS

### Test d'Indépendance
- χ² ≈ 1059.5
- p-value ≈ 0.0000
- **Conclusion**: FORTE ASSOCIATION (rejet H₀)

### Inertie
- Φ² ≈ 0.02928
- Axe 1: ~59% (Principal)
- Axe 2: ~19% (Secondaire)
- Axe 3: ~12%
- Axes 1-4: >95% cumulé

### Régions Influentes
- Axe 1+: Outremer, Île-de-France
- Axe 1-: Nord-Est, Alsace, Lorraine
- Axe 2+: Alsace, Pays de Loire
- Axe 2-: Outremer, Île-de-France

### Candidats Influents
- Axe 1: Le Pen (-), Hollande (+)
- Axe 2: Bayrou (+), Le Pen (-)
- Axes 3-4: Petits candidats, blanc/nuls

---

## ✅ INTERPRÉTATION

### Axe 1 - Opposition Principale
```
NÉGATIF (-) ← Axe 1 → POSITIF (+)
Le Pen          |         Hollande
↓               |         ↓
Nord-Est        |      Île-de-France
Alsace          |      Outremer
Lorraine        |      Bretagne
```

### Axe 2 - Opposition Secondaire
```
NÉGATIF (-) ← Axe 2 → POSITIF (+)
Hollande        |       Bayrou
Mélenchon       |       Sarkozy
↓               |       ↓
Outremer        |       Alsace
Île-de-France   |       Pays-Loire
```

---

## 🔄 CHECKLIST ANALYSE

### Avant l'analyse
- [ ] Données chargées (23 régions × 11 candidats)
- [ ] Tableau de contingence complet
- [ ] N = effectif total calculé

### Chi-Deux
- [ ] Fréquences théoriques calculées
- [ ] χ² = N × Σ(f_obs - f_theo)²/f_theo
- [ ] p-value < 0.05 → rejet indépendance ✓
- [ ] Degrés de liberté: 22 × 10 = 220

### Profils et Distances
- [ ] Profils lignes: somme par région = 1
- [ ] Profils colonnes: somme par candidat = 1
- [ ] Distance Φ²: symétrique et positive
- [ ] Propriété équivalence distributionnelle

### Valeurs Propres
- [ ] SVD ou ACP sur matrice pondérée
- [ ] Inertie totale Φ² = somme λ
- [ ] Inertie cumulée axes 1-4: >90%
- [ ] Scree plot montre décroissance

### Coordonnées et Contributions
- [ ] Ψ et Φ calculés pour n_axes
- [ ] Contributions somment à 100% par axe
- [ ] QLT = cosinus² entre 0-100%
- [ ] Elements bien représentés identifiés

### Interprétation
- [ ] Axes 1-2 analysés complètement
- [ ] Régions structurantes identifiées
- [ ] Candidats influents repérés
- [ ] Associations principales décrites

### Visualisation
- [ ] Plan 1-2 généré et interprété
- [ ] Plan 3-4 généré et interprété
- [ ] Scree plot montrant inertie
- [ ] Tous graphiques nommés correctement

---

## 🎓 COMPÉTENCES ÉVALUÉES

| Compétence | Notebook | Pages Cours |
|---|---|---|
| Tableau contingence | Sect. 2-3 | 43-44 |
| Profils L/C | Sect. 4 | 44-45 |
| Test Chi-Deux | Sect. 5 | 47 |
| Taux liaison | Sect. 6 | 47 |
| Distances | Sect. 7 | 46 |
| Valeurs propres | Sect. 8 | 48 |
| Coordonnées | Sect. 9 | 49-50 |
| Contributions | Sect. 10 | 49-50 |
| Graphiques | Sect. 11 | 51-52 |
| Interprétation | Sect. 12-14 | 54-57 |

---

## 💾 STRUCTURE FICHIERS

```
📦 Livraison
├── AFC_Elections_Analysis.ipynb      ← MAIN FILE (À exécuter)
├── GUIDE_UTILISATION_AFC.md          ← Explications détaillées
├── FICHE_RECAPITULATIVE.md           ← Ce fichier
├── ADEM_YENGUI_nom_prenom.pdf        ← Export PDF du notebook
└── [graphiques générés]
    ├── AFC_Plan_1_2.png
    ├── AFC_Plan_3_4.png
    └── AFC_Inertie.png
```

---

## 🔗 RESSOURCES

- **Cours complet**: TP_AFC_Elections__France_souligné.pdf
- **Données**: ADEM_YENGUI_-_resultats_presidentielles_2012.csv
- **Formules**: Pages 43-57
- **Exemples**: Pages 43-57 (élections France)

---

## ⚠️ ERREURS COURANTES À ÉVITER

1. ❌ Oublier le nom de l'étudiant
   ✓ Ajouter en début: **Étudiant: Votre Nom**

2. ❌ Mauvaise formule chi-deux
   ✓ χ² = N × Σᵢⱼ (fᵢⱼ - fᵢ.f.ⱼ)²/(fᵢ.f.ⱼ)

3. ❌ Sommes pas à 1 (profils/fréquences)
   ✓ Vérifier: sum(f_ij) = 1, sum(profils) = 1

4. ❌ Contributions pas à 100%
   ✓ Summing(Ctr(i,k)) par colonne doit = 100%

5. ❌ Confusion Ψ et Φ
   ✓ Ψ pour lignes (régions), Φ pour colonnes (candidats)

6. ❌ Mauvaise interprétation du signe
   ✓ Positif = surreprés., Négatif = sous-représ.

---

**Dernière mise à jour**: 2024
**Durée analyse**: 45-60 minutes
**Niveau**: L2 Statistiques

