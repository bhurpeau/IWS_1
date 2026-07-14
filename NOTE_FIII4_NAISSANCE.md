# IWS — Note F-III.4 : La naissance d'un seuil

**Objet.** Suivant la réorientation actée après F-III.3 (comprendre le *mécanisme* qui crée un seuil plutôt que photographier Θ), cette note instrumente le calendrier Kairos, classifie la naissance des dix seuils de Θ_{𝔅₃}, cartographie une famille génératrice, et en tire trois choses : un mécanisme dominant (**la naissance est continue dans le contenu, combinatoire dans le protocole**), deux **rectificatifs à F-III.3** (la monotonicité en s est fausse en général ; Θ₃ était une borne inférieure), et une conjecture de structure pour Θ_∞ (C-III.4, stratification par les calendriers). Reproductibilité : `fiii4_naissance.py`, `output_theory/fiii4_report.json`, figure `output_theory/fiii4_naissance.png` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

**Protocole déclaré.** Calendrier d'une histoire = suite des Kairos **chargés** (‖χ‖ > 0.01 à l'événement) survenant pendant les phases actives et les oublis, hors relaxation finale (les Kairos vides du bassin approprié, χ ≈ 0, ne portent aucune information). Classification au seuil b : scan s ∈ [b − 2·10⁻⁴, b + 2·10⁻⁴], 9 points ; **type K** si le nombre d'événements change ou si une date saute de plus de 5 u entre points adjacents ; **type C** sinon. Tout est relatif aux familles déclarées (garde F-III.3.1-A3).

---

## 1. Typologie et bilan (Z1) : la naissance est génériquement continue dans le contenu

Sur les dix seuils de Θ_{𝔅₃} : **9 de type C, 1 de type K.** Pour les neuf C, le calendrier est rigoureusement identique de part et d'autre (mêmes comptes, dérive des dates ≤ 0.43 u) : à calendrier fixé, la fonctionnelle continue des charges croise le niveau d'appropriation — le seuil est un **zéro régulier**, pas une bifurcation. L'unique K est b = 0.00504 (amorce 20, sonde 110) : un Kairos chargé disparaît en traversant le seuil (49 → 48, saut de date 0.93 u) — la bifurcation de protocole existe, mais elle est minoritaire à ces budgets.

## 2. Deux faits imprévus — rectificatifs à F-III.3

**(R-a) La monotonicité des issues en s est fausse en général : QO-60 est close par la négative.** Témoin : l'histoire (amorce 10, sonde 110) a des issues *décroissantes* en s — motif `[AAAA.....]` autour de b = 0.01183 : **davantage de contenu, moins d'appropriation.** Type C pourtant (calendrier constant) : c'est la fonctionnelle de charge elle-même qui est localement décroissante en s. Les six témoins de F-III.3-Y1 restent monotones ; l'hypothèse générale, elle, tombe.

**(R-b) Micro-structure : une histoire peut définir plusieurs points de commutation.** Près de b = 0.00463, le scan fin révèle `[.A..AAAAA]` — une micro-île d'appropriation à ~1.5·10⁻⁴ sous le seuil. À échelle fine, « le » seuil d'une histoire est un *ensemble* de points de commutation.

**Conséquence formelle — III-4(c′), version affaiblie et correcte de III-4(c).** Chaque histoire définit un ensemble fini de points de commutation ; Θ_𝔅 est l'union de ces ensembles ; les **cellules** (intervalles entre points consécutifs de Θ_𝔅) portent des réponses constantes ; les **classes** sont des unions de cellules — plus nécessairement connexes. Le principe de réduction aux seuils (F-III.3.1-A1) survit intégralement, mais il compte des cellules, pas des classes.

**Rectificatif explicite à F-III.3 §3** : (i) les « n_classes » du tableau sont des comptages de **cellules** (bornes supérieures du nombre de classes) ; (ii) **Θ₃ y est une borne inférieure** — la bisection suppose un croisement unique par histoire et manque les îles et les histoires à nombre pair de croisements ; (iii) la non-stationnarité observée, elle, est inchangée (une borne inférieure qui croît suffit).

## 3. La carte génératrice (Z2, Z2b, Z2c) : continue en s, combinatoire en T_am

Famille à un paramètre : une amorce de durée T_am, oubli 150, sonde fixe. Faits :

- **Sonde T₂ = 60 : stérile** — aucun seuil dans la plage, pour aucun T_am ∈ [5, 60]. La sonde génératrice doit être assez longue pour être critique (QO-64).
- **Sonde T₂ = 80 : une fenêtre génératrice étroite T_am ∈ [13, 23]**, hors de laquelle rien (T_am ≤ 12 : tout-repos) ou tout (T_am ≥ 24 : **saturation**, extrémités A|A — le seuil est passé *sous* la plage, il n'a pas disparu).
- **Dans la fenêtre, b(T_am) zigzague** : 13→0.0122, 14→**point mort** (tout-repos en pleine fenêtre), 15→0.0121, 16→0.0074, 17→0.0116, 18→0.0097, 19→0.0026, 20→0.0073, 21→0.0025, 22→0.0044, 23→0.0024 — avec des quasi-plateaux revisités (19/21/23 ≈ 0.0025 ; 16 ≈ 20 ≈ 0.0073) entrelacés par des sauts d'un ordre de grandeur entre T_am adjacents.
- **Z2c écarte l'artefact** : aux T_am du zigzag (17, 19), le croisement en s est simple à la résolution du scan — le zigzag est réel dans le paramètre de famille.

D'où la synthèse-mécanisme de la note, qui répond point par point à la question « pourquoi un nouveau seuil apparaît-il ? » : **la naissance d'un seuil est de type C dans le contenu et de type K dans le protocole.** À protocole fixé, le seuil naît comme zéro régulier d'une fonctionnelle de charge ; mais en déplaçant le protocole (T_am), le calendrier du préfixe se réorganise par crans, et le zéro *saute*. Parmi les cinq hypothèses de la relecture (Kairos supplémentaire, mémoire plus longue, changement de bassin, interaction de préfixes, bifurcation de protocole), la dominante est la dernière — mais elle vit dans l'axe des familles, pas dans l'axe des contenus. Un seuil ne naît pas dans le système : il naît dans le couple, exactement comme l'exigeait la garde anti-essentialiste.

## 4. La paire serrée (Z3) : une collision accidentelle, pas une accumulation

Les deux seuils voisins {0.00463, 0.00504} relèvent de **mécanismes différents** (C de niveau 1 contre K de niveau 2) : leur proximité est une coïncidence de deux généalogies indépendantes, pas le début d'une condensation. Et la famille dense de 90 histoires (préfixes {10, 15, 25, 30, 35} simples et doubles, sondes {70, 80, 90}) bissectée dans l'intervalle étroit **n'insère aucun seuil dans ]0.0046, 0.0051[**. Aucune accumulation locale par les familles discrètes testées.

## 5. Conjecture C-III.4 — stratification de Θ_∞ par les calendriers

Les faits assemblés (type C en s, type K en T_am, quasi-plateaux, saturation aux bords, zéro insertion dans le trou) motivent :

**C-III.4 (conjecture).** Pour une famille continue de protocoles, Θ_∞ se **stratifie par les cellules de calendrier** : sur chaque cellule (calendrier du préfixe constant), b(·) varie continûment et balaie un sous-intervalle de contenus ; les cellules sont séparées par des sauts K. La géométrie de Θ_∞ serait alors **mixte** : des bandes balayées (où Θ_∞ contient des intervalles — et où, par conséquent, le quotient limite *sépare les points* : individuation ponctuelle), entrelacées de zones à seuils isolés — ni fini, ni Cantor, dans la classification de QO-59′.

Statut : conjecture appuyée par douze points d'une seule famille ; les « morceaux » ne sont pas résolus à la résolution Δ T_am = 1 u (le zigzag 16–20 peut cacher des morceaux entrelacés fins). Le test décisif est QO-63.

## 6. Registres

**Proposition** : III-4(c′) (réduction aux seuils, version cellules : points de commutation, cellules à réponse constante, classes = unions de cellules).
**Faits** : 9 C / 1 K sur Θ_{𝔅₃} ; contre-exemple à la monotonicité (amorce 10, sonde 110, motif `AAAA.....`) ; micro-île sous b = 0.00463 ; fenêtre génératrice [13, 23] à sonde 80, stérilité de la sonde 60, point mort T_am = 14, saturation T_am ≥ 24 ; zigzag de b(T_am) à croisements simples en s ; quasi-plateaux revisités ; zéro insertion dans ]0.0046, 0.0051[ (90 histoires) ; paire serrée = collision de mécanismes indépendants.
**Rectificatifs à F-III.3** : comptages = cellules (bornes supérieures des classes) ; Θ₃ = borne inférieure ; non-stationnarité inchangée. **QO-60 close par la négative.**
**Conjecture** : C-III.4 (stratification de Θ_∞ par les calendriers ; bandes balayées ⟹ individuation ponctuelle locale).
**Questions ouvertes** : **QO-62** caractériser les histoires anti-monotones et borner le nombre de points de commutation par histoire (de quoi dépend la parité du motif ?) ; **QO-63** résoudre les morceaux de b(T_am) (grille ≤ 0.25 u sur [13, 23], appariée aux calendriers de préfixe : chaque morceau correspond-il à une cellule de calendrier, comme le veut C-III.4 ?) ; **QO-64** la longueur critique de sonde génératrice (pourquoi 60 est stérile et 80 féconde — lien avec « toute sonde est déjà une histoire » : la sonde doit durer assez pour écrire).

## 7. Où cela mène

La stratégie « comprendre la naissance plutôt qu'explorer » a payé en une note : un mécanisme dominant, deux rectificatifs de fond, et une conjecture de structure testable. **F-III.5 = test frontal de C-III.4 via QO-63** : résolution fine de la fenêtre génératrice avec appariement seuil ↔ calendrier de préfixe — si les morceaux de b(T_am) coïncident avec les cellules de calendrier, la stratification est établie sur l'exemple et la géométrie de Θ_∞ cesse d'être une inconnue pour devenir une comptabilité de calendriers. QO-56 (plasticité de 𝒢) reste en file, après.

---

*Reproductibilité : `python fiii4_naissance.py` (Z0 validation, Z1 classification, Z2/Z2b/Z2c carte génératrice, Z3 paire serrée) ; consolidé : `output_theory/fiii4_report.json` ; figure : `output_theory/fiii4_naissance.png`.*
