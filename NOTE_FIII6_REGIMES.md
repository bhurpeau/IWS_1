# IWS — Note F-III.6 : Les régimes de résumé — prédiction inter-axes et échelle des horloges

**Objet.** Traiter QO-66 (sortir du régime de séparation de III-5). La prédiction de F-III.5 §4 — « à oubli court, l'équation à un scalaire doit tomber » — est corrigée par l'expérience en trois temps : (1) pour les préfixes **féconds**, le régime θ-vivant est *inaccessible* — et la « chute » attendue est en réalité une **prédiction inter-axes exacte** de III-5 (la bascule sur l'axe D se produit à ‖s‖ = s\* à 10⁻⁵ près, θ mort) ; (2) le régime θ-vivant existe pour les préfixes **faibles**, où la facilitation par θ atteint un tiers de s\*, avec une loi à une variable qui n'est qu'une approximation de strate ; (3) les ablations révèlent **l'échelle des résumés** : {s} → {θ, s} → {p, χ, θ, s}, chaque horloge réintégrant le résumé quand l'oubli descend sous quelques constantes de temps (principe P-III.6). QO-66 est close. Reproductibilité : `fiii6_regimes.py`, `output_theory/fiii6_report.json`, figure `output_theory/fiii6_regimes.png` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

**Protocole déclaré.** Sonde fixe T₂ = 80, relaxation 300 ; plage de contenus [0.0002, 0.0135] ; regraine canonique ; δ = ‖s‖_regraine − s₀ ; θ, χ, p mesurés à la regraine ; bisections en s (11 itérations) et en D (10 itérations) ; ablations par extinction de variables à la regraine (déclarées variante par variante).

---

## 1. La prédiction inter-axes (V1–V2) : III-5 renforcée, et un rectificatif

Diagnostic (V1, T_am = 17.5, s₀ ≈ 0) : le long de l'axe D, les horloges s'éteignent dans l'ordre de leurs τ (p : 2 u ; χ : 5 u ; θ : 8.3 u ; s : 200 u), et la bascule d'issue se produit entre D = 90 (‖s‖ = 0.01639 → approprié) et D = 100 (‖s‖ = 0.01559 → repos) — **avec θ = 2·10⁻⁵, mort**. La saturation à D court n'est pas un régime nouveau : c'est III-5 qui la prédit (moins d'oubli ⟹ moins de décroissance du contenu ⟹ δ seul excède s\* ⟹ le seuil sort de la plage par le bas).

Test frontal (V2) : bisection de la bascule D\* sur trois préfixes féconds —

| T_am | D\* mesuré | ‖s‖(D\*) | écart à s\* = 0.01627 | θ(D\*) |
|---|---|---|---|---|
| 15.5 | 90.28 | 0.01628 | +1·10⁻⁵ | 1.4·10⁻⁵ |
| 17.5 | 91.36 | 0.01628 | +1·10⁻⁵ | 1.4·10⁻⁵ |
| 20.0 | 108.64 | 0.01627 | −0 | 2·10⁻⁶ |

**L'invariant mesuré sur l'axe des contenus prédit la bascule sur l'axe des oublis à 10⁻⁵ près.** Proposition III-5, portée renforcée : l'équation de seuil vaut sur toute la variété (s₀, T_am, D) du régime de séparation, et la frontière du domaine sur l'axe D est prédite par l'équation elle-même.

**Rectificatif à F-III.5 §4.** La prédiction « hors du régime, l'équation à un scalaire doit tomber » était fausse telle qu'énoncée : pour les préfixes féconds, **le régime θ-vivant est inaccessible** — la séparation des échelles (τ_θ = 8.3 contre τ_s = 200) fait que lorsque le contenu total est redescendu dans la plage des seuils, θ est mort depuis longtemps ; les deux fenêtres ne se recouvrent jamais. L'équation ne peut tomber que là où le régime θ-vivant est atteignable : chez les préfixes faibles.

## 2. Le régime θ-vivant (V3) : facilitation, strate, et son témoin de rupture

Fenêtre atteignable : T_am ∈ [5, 7] (écriture insuffisante pour saturer), D ∈ [12, 25]. Faits :

- **La facilitation est réelle** : s\* − (b + δ) atteint +0.0056 (un tiers de s\*) — θ vivant abaisse le contenu requis.
- **Dans la strate D ≥ 15** (χ ≤ 0.008), la facilitation suit une fonction croissante commune de ‖θ‖ (pente ≈ 0.07) sur les cinq familles T_am : dispersion transverse à θ apparié 9.3·10⁻⁴ sur 25 paires — un effondrement *approché* (résidus ~10–20 % du signal, ordonnés par χ). La « courbe s\*(θ) » est donc une **approximation de strate**, pas une loi.
- **À D = 12, la loi à une variable casse**, et le témoin est net : (T_am = 5.5, D = 12) et (T_am = 6.0, D = 12) ont θ ≈ 0.105 *égaux* et des facilitations *opposées* — **−0.0006 (anti-facilitante) contre +0.0056**. Même θ, même contenu comparable, devenirs contraires : à cette profondeur, aucune fonction de (θ, contenu) ne décrit le seuil.

## 3. L'échelle des résumés (V4) : les ablations, cellule à cellule

Au voisinage du seuil (sept contenus encadrant b, T_am = 6), extinction de variables à la regraine :

| D | complet | (χ, θ, s) | (θ, s) | s seul | verdict |
|---|---|---|---|---|---|
| 21 | `...AAAA` | `...AAAA` | `...AAAA` | `.......` | **{θ, s} suffit exactement** ; s seul échoue totalement |
| 12 | `...AAAA` | `......A` | `.......` | `.......` | **même {χ, θ, s} échoue : p est requise** — χ récupère une cellule, p les trois autres |

**Principe P-III.6 (principe d'échelle des résumés).** Au voisinage d'un seuil, le résumé suffisant d'un préfixe est **l'état de ses horloges non éteintes**, ordonnées par leurs constantes de temps ; chaque horloge réintègre le résumé lorsque l'oubli descend sous quelques τ. Instances démontrées : étage {s} avec loi exacte (III-5) ; étage {θ, s} exact (V4, D = 21) ; nécessité conjointe de {p, χ} à l'étage profond (V4, D = 12). Statut : principe à instances, pas théorème — la version formelle est QO-70. Formulation canonique candidate : *« le résumé d'une histoire est l'ensemble de ses horloges encore battantes. »*

Connexion à F-III.0 : le cahier des charges dual (s_sc, s⃗) est l'axiomatisation de l'étage stationnaire de cette échelle ; V4 en exhibe la version dynamique complète — la profondeur mnésique d'un système n'est pas un choix de modélisation, c'est une lecture de ses τ.

## 4. Registres

**Proposition** : III-5 renforcée (validité sur la variété (s₀, T_am, D) ; prédiction inter-axes vérifiée à ≤ 10⁻⁵ sur trois préfixes).
**Principe** : P-III.6 (échelle des résumés ; instances démontrées aux trois étages).
**Faits** : ordre d'extinction des horloges le long de D ; bascule à ‖s‖ = s\* avec θ mort ; **inaccessibilité du régime θ-vivant aux préfixes féconds** (fenêtres disjointes par séparation des échelles) ; fenêtre atteignable (T_am ∈ [5, 7], D ∈ [12, 25]) ; facilitation jusqu'à +0.0056 ; effondrement approché de strate (dispersion 9.3·10⁻⁴, D ≥ 15) ; témoin de rupture à θ égal et facilitations opposées (D = 12), dont une **anti-facilitation** ; ablations du tableau ci-dessus.
**Rectificatif à F-III.5 §4** : la prédiction QO-66 telle qu'énoncée ; l'équation ne « tombe » pas où prévu — elle tombe par étages, là où les horloges battent.
**Clôture** : **QO-66 close.**
**Questions ouvertes** : **QO-68** mécanisme et forme de la facilitation f(θ) dans la strate (pré-inclinaison du paysage M(θ) : dérivation attendue depuis Tome I) ; **QO-69** l'anti-facilitation de l'étage profond (parenté avec l'anti-monotonie QO-62 : même famille de renversements ?) ; **QO-70** la loi de l'étage profond — existe-t-il une **surface de commutation de codimension 1 dans l'état lent complet** (p, χ, θ, contenu), dont III-5 serait la trace à l'étage {s} et P-III.6 l'énoncé de stratification ? (prédiction : oui — ce serait le théorème unificateur de la mécanique des seuils). QO-67 reste ouverte (récurrence des signatures dans la famille (T_am, D) ; la grille V3 en fournit la matière première).

## 5. Où cela mène

La mécanique des seuils est désormais comprise sur trois niveaux emboîtés : *où* ils naissent (cellules de calendrier, F-III.5), *de quoi* ils dépendent (l'équation de niveau et son échelle de résumés, III-5/P-III.6), *quand* chaque description vaut (les strates d'horloges, cette note). Deux suites possibles : **QO-70** (le théorème unificateur — la surface de commutation dans l'état lent complet) ou **le retour à QO-56** (plasticité de 𝒢), en attente depuis F-III.2 et pour laquelle nous avons maintenant tout l'outillage : si une histoire peut modifier 𝒢, ses effets se liront précisément comme des déplacements de la surface de commutation à état lent fixé — c'est-à-dire que l'outillage de cette note est *exactement* le détecteur qu'il fallait pour la frontière espèce/individu. Ma recommandation : **F-III.7 = QO-56**, avec QO-70 en réserve théorique.

---

*Reproductibilité : `python fiii6_regimes.py` (V0 validation, V1 diagnostic, V2 prédiction inter-axes, V3 régime θ-vivant, V4 ablations) ; consolidé : `output_theory/fiii6_report.json` ; figure : `output_theory/fiii6_regimes.png`.*
