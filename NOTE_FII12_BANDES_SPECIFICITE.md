# IWS — Note F-II.1.2 : Bandes de phase et spécificité de la mémoire d'interface

**Objet.** Les deux objectifs fixés : (1) théorie des bandes de sommation comme perturbation de l'application de retour ; (2) spécificité de l'amorçage (global, directionnel, dépendant du partenaire ?) — plus les trois contrôles demandés. Les corrections éditoriales sont adoptées en tête. Reproductibilité : `fii12_bands_specificity.py` (+ vérifications finales dans l'historique), `output_theory/fii12_report.json`.

---

## 0. Corrections adoptées

1. **Quatre seuils, pas cinq** : g_F^{qs} est une approximation de g_F, non un cinquième phénomène. La hiérarchie est g_K < g_F < g_app^{R2} < g_H^{R2}.
2. **« Application de retour explicite »** remplace « exacte » : la carte (χ, p, τ) est en forme fermée *une fois Δ connu*, Δ reste transcendant, le multiplicateur de Floquet est numérique.
3. La règle « sommation ssi v > 0 » reste `[NUM]`, limitée aux cellules diagnostiquées — elle est d'ailleurs remplacée ci-dessous par un prédicteur plus fort.
4. g_H^{R2} : la table dit désormais **« aucune perte de stabilité observée jusqu'à g = 0.30 »** — borne, pas seuil identifié (Hopf pulsé lointain, stabilité pour tout g, autre bifurcation, ou changement d'attracteur suivi par la rampe : indécidé).

## 1. Théorie des bandes de phase `[NUM, mécanisme identifié]`

**Le mécanisme tient en trois ingrédients :**

1. **Spirale libre.** Pendant le délai D, l'état résiduel suit la dynamique libre linéarisée avec θ(t) = θ_d e^{−βt} (instable tant que θ > θ_ign, soit t ≲ 8.3, puis spirale amortie de pulsation ω, période 2π/ω = 14.63).
2. **Temps de charge.** La seconde exposition ne déstabilise le repos qu'après la montée de l'échelle : t_c = 4.74 (mesuré une fois sur la carte). La phase pertinente est donc celle de l'état à l'instant D + t_c.
3. **Asymétrie de capture.** Une fois l'instabilité ouverte, la croissance est massive (taux ≈ 0.2, facteur ~e⁸ sur T₂) : **l'amplitude du résidu ne décide plus, seul son signe compte** — parce que la résistance pulsée, stable à g = 0.18 (borne g_H^{R2}), capture le côté négatif. Vérifié : *tous* les atterrissages sommés sont à +2.30 (le puits +), tous les échecs de phase relaxent à ~0 via la résistance.

**Prédicteur de signe, zéro constante calibrée** : sommation ssi x_lib(D + t_c) > 0, où x_lib est l'extrapolation libre depuis l'état de découplage mesuré (x_d = −0.0061, v_d = −0.0011, θ_d = 0.7255). Sur le régime de phase (10 ≤ D ≤ 48) :

```
mesuré : [S.....SSSS....SSS....SSS......]
prédit : [????...SSS....SSSS...SSS??????]     score 18/20
```

Les deux erreurs sont des cellules de **bord de bande** (décalage ≈ 2 en D — QO-42). Période et positions des bandes : prédites ; extinction (D ≳ 50) : entrée du résidu dans la zone des bassins finement structurés (QO-32), où le déterminisme fin de la capture prend le relais du signe. La forme proposée A(D)cos(ωD+φ₀) > A_crit est ainsi précisée : dans le régime de phase, A_crit ≈ 0 (critère de signe pur) ; elle redevient la bonne description près de l'extinction, où l'amplitude cesse de dominer la structure fine.

Le contraste des trois régimes est confirmé et affiné : **mémoire de charge** (D ≲ 10 : θ résiduel massif décide, la phase est secondaire) ; **mémoire de phase** (10–48 : signe de x_lib(D + t_c)) ; **structure fine** (D ≳ 50).

## 2. Les trois contrôles de l'amorçage `[NUM]`

**(a) Gain constant vs boucle.** Cellules d'appropriation (T₂ = 40…155) : non-amorcé 17 (première durée 75) ; amorcé, gain constant figé à +7.6 % : 23 (45) ; amorcé, boucle dynamique complète : 24 (40). Verdict honnête : **l'essentiel de l'effet est la tête d'avance ; la boucle de recomposition est un raffinement** (+1 cellule, −5 sur la première durée) — la formulation « levier par recomposition » de F-II.1.1 est rétrogradée en contribution secondaire au c_s testé.

**(b) Charge livrée égale.** Q_net = Σκ_Q(s_n)χ_n⁻ : D = 14 → Q_net = 8.255, **appropriée** ; D = 26 → Q_net = 8.322, **oubliée**. Dose quasi identique, issues opposées : *la charge livrée n'est pas la variable explicative ; la phase de réception l'est* — le contrôle demandé tranche.

**(c) Signe.** c_s = −8 sans garde : régime d'anti-écriture (quanta négatifs effaçant τ) — artefact, pas habituation. c_s = −2 (levier apparié −1.9 %) : effet indétectable. **La voie scalaire de l'habituation reste ouverte** (QO-43 : il faut un couplage donnant un levier négatif comparable au positif) — mais voir §3 : l'habituation émerge d'elle-même du modèle directionnel.

## 3. Spécificité : de la sensibilisation générale à la mémoire individualisée `[NUM]`

Modèle vectoriel d = 2 (M(τ) complet, drive directionnel), deux mémoires comparées : **s scalaire** (‖χ‖, celle de F-II.1.1) et **s vectoriel** avec règle de compatibilité au saut — la première implémentation non plaquée d'A-I3 :

τ⁺ = τ⁻ + max(1 + c_s·⟨s⃗, χ̂⟩, 0)·κ_Q χ⁻.

Protocole : amorce le long de u₁, oubli 300, exposition 2 le long de u₂ ∈ {u₁, u⊥, −u₁}, **graine appariée au début de l'exposition 2** (nécessité méthodologique consignée : sans elle, l'érosion de graine domine tout et masque la spécificité). Cellules d'appropriation (T₂ = 40…150) :

| première exposition | même direction | orthogonale | opposée | (base sans amorce) |
|---|---|---|---|---|
| **s scalaire** | 5/12 (1ʳᵉ : 110) | 5/12 (110) | 5/12 (110) | 2/12 (140) |
| **s vectoriel** | 5/12 (110) | **2/12 (140)** | **1/12 (140)** | 2/12 (140) |

Trois lectures :

1. **s scalaire : amorçage global, confirmé.** Même facilitation dans les trois directions — « il mémorise qu'il s'est passé quelque chose, pas ce qui s'est passé ». La limite identifiée est démontrée, pas seulement pressentie.
2. **s vectoriel : mémoire directionnelle.** Facilitation pour la même direction ; **neutralité exacte pour l'orthogonale** (2/12 = base : le produit scalaire nul rend l'amorce invisible — la sélectivité est celle de la géométrie, pas d'un réglage) ;
3. **et habituation émergente pour l'opposée** (1/12 < base) : ⟨s⃗, −χ̂⟩ < 0 réduit les quanta — *la suppression directionnelle sort du même mécanisme que la facilitation*, là où la version scalaire (contrôle c) n'y parvenait pas. Deux phénomènes, un produit scalaire.

C'est la première **mémoire d'interface individualisée** : elle ne code plus seulement une intensité d'exposition mais une *relation* — et elle répond à la formulation exigée pour A-I3 : le critère de compatibilité ne décide pas seulement « écrire ou non », il détermine **quel type d'expérience modifie quel canal futur**. La question « dépendant du partenaire ? transférable ? » reste ouverte (QO-44 : plusieurs partenaires de directions voisines, oubli directionnel, saturation de s⃗).

## 4. Registres

**Faits** : mécanisme des bandes (3 ingrédients, atterrissages +2.30 / relaxations 0) ; prédicteur de signe 18/20 à zéro constante ; Q_net non explicatif ; tête d'avance > boucle ; table de spécificité (globalité scalaire, sélectivité + habituation vectorielles).
**Questions ouvertes** : QO-42 théorie des bords de bande (les 2 cellules d'écart, ≈ décalage de phase de 2 en D — probablement la non-linéarité de la capture) ; QO-43 habituation scalaire à levier apparié ; QO-44 mémoire directionnelle : partenaires multiples, transférabilité, oubli de s⃗ ; QO-45 formalisation complète d'A-I3 sur la base du critère produit scalaire (validation conditionnelle au saut, avec ses conséquences sur g_F et la loi d'appropriation — chaque seuil de §F-II.1.1 à recalculer sous compatibilité).

## 5. Où en est le chemin de traverse

L'encadré de F-II.1.1 tenait en trois conditions ; chacune a maintenant sa théorie et la troisième vient de gagner un contenu :

> un paysage qui l'autorise (Ψ, r_c) **+** une fenêtre où il est accessible (bandes : signe de x_lib(D + t_c), période 2π/ω) **+** une interface qui peut se souvenir de l'avoir entrevu — *et désormais, se souvenir **de quoi** elle a été touchée* (s⃗, table de spécificité).

Une interaction peut ne rien changer immédiatement à l'intérieur, tout en changeant durablement — et *sélectivement* — la manière dont une interaction future sera reçue. Le Tome III a maintenant ses deux briques élémentaires : l'appropriation qui compose les bassins, l'amorçage directionnel qui compose les accessibilités.

---

*Reproductibilité : `python fii12_bands_specificity.py` ; prédicteur de signe, habituation douce et table finale (graine appariée) consignés dans l'historique du dépôt.*
