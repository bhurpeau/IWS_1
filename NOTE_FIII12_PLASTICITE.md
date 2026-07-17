# IWS — Note F-III.12 : La plasticité de la loi d'action — détectable comme horloge, indécidable comme ontologie

**Objet.** QO-56, en attente depuis F-III.2/D-04 : une histoire peut-elle modifier la loi d'action 𝒢, et peut-on le savoir ? La note construit une **extension plastique minimale conforme** (le gain de la loi devient une variable γ à fatigue événementielle et récupération très lente, τ = 2000 — une *cinquième horloge*, la plus lente du système ; la classe canonique est le cas r_γ = ε_γ = 0, validé **bit à bit**), exécute le protocole en cinq étapes de la relecture de F-III.11, et livre les deux moitiés du résultat, chacune tranchée : **la plasticité est détectable** — deux histoires d'usage inégal, à paysage identique et état lent égalisé à 10⁻⁶, produisent des cartes de sondes différentes, et le résumé à quatre horloges cesse de fermer — **et la plasticité est indécidable comme ontologie** : Théorème III-11, toute loi plastique de la classe est ℛ-équivalente, pour toute (𝔅, ρ), à une loi figée lisant une variable d'état supplémentaire (preuve par rebaptême ; vérification : exécutions identiques au bit près). La frontière espèce/individu relative à 𝒢 devient déclarative (Décision D-08, amendant D-04) — c'est le théorème du chapitre 13, tel que le plan l'avait anticipé. Déclaration (𝔅, ρ) : sondes (u₁, G2, T₂ = 40…140, regraine canonique, relaxation 300), bassin binaire, famille alignée. Reproductibilité : `fiii12_plasticite.py`, `output_theory/fiii12_report.json` ; validation Z0 exacte contre F-III.0.

---

## 1. L'extension plastique minimale (déclarée)

boost = 1 + γ·CS·pr, avec **fatigue** γ ← γ(1 − r_γ) à chaque Kairos chargé (r_γ = 0.005) et **récupération** dγ/dt = ε_γ(1 − γ), ε_γ = 5·10⁻⁴ (τ_γ = 2000 u : sous l'horloge s d'un facteur dix). La hiérarchie des horloges devient p (2) < χ (5) < θ (8.3) < s (200) < γ (2000). Conformité : à r_γ = ε_γ = 0, l'arithmétique est identique au modèle canonique (1.0·x = x en IEEE) — Z0 le vérifie au bit près sur la référence P4.

## 2. Le protocole en cinq étapes (Z1–Z2) : la détection

Deux histoires d'usage inégal — **H1 lourde** (trois amorces 41.9, oublis 150 : **45 Kairos chargés**) et **H2 légère** (une amorce : **15 Kairos chargés**) — égalisées par bisection de leurs oublis finaux sur la **cible commune** ‖s‖ = 0.030 (écarts ≤ 1.3·10⁻⁶ ; θ et p morts à ≤ 3·10⁻⁷). Même paysage, même état lent à 10⁻⁶ — et γ₁ = 0.8342 contre γ₂ = 0.9323.

**Détection.** Les cartes de sondes diffèrent : H1 `....AAAAAAA`, H2 `...AAAAAAAA` — à T₂ = 70, le système peu usé s'approprie, le système usé non. *Deux histoires laissant le même état lent ne sont pas ℛ-équivalentes dans l'espèce plastique* : le résumé (p, χ, θ, s) est incomplet, exactement comme le protocole devait le révéler. Et les frontières se séparent quantitativement : à γ figé pendant la sonde, s\*(0.8342) ≈ 0.0300+ contre s\*(0.9323) ≈ 0.0226 — Σ^{(1)} ≠ Σ^{(2)} à z égal, le déplacement résiduel est là.

Deux contrôles précieux : (i) **s\*_figé(γ = 1) = 0.01627** — la valeur de III-5, retrouvée depuis l'espèce plastique, à la précision de bisection ; (ii) la courbe à **sonde plastique** est systématiquement au-dessus de la courbe à γ figé (+0.0005 à +0.0013) : *la sonde use la loi qu'elle mesure* — « toute sonde est déjà une histoire » vaut désormais aussi pour 𝒢.

## 3. La fermeture étendue (Z3) : P-III.6 gagne un étage

L'injection (0, 0, 0, s, **γ₁**) reproduit la carte réelle de H1 **cellule à cellule** ; l'injection (0, 0, 0, s) avec γ omis (:= 1) échoue. Le résumé suffisant de l'espèce plastique est **(p, χ, θ, s, γ)** — l'échelle des résumés s'étend d'un étage, à τ = 2000, et le principe P-III.6 (les horloges encore battantes) absorbe la plasticité sans se modifier : *la loi qui s'use est une horloge de plus.*

## 4. Le Théorème III-11 : l'indiscernabilité de la plasticité

**Théorème III-11.** Soit 𝒢_pl une loi plastique de la classe déclarée : le gain est une fonction d'une variable interne γ dont la dynamique est autonome-événementielle et causale. Alors le système (Ψ, 𝒢_pl) est **ℛ-équivalent, pour toute classe (𝔅, ρ)**, au système (Ψ ⊕ γ, 𝒢_fig) où γ est promue coordonnée d'état et où la loi, figée, lit cette coordonnée.

*Preuve.* Les deux présentations définissent le même système dynamique hybride — mêmes équations, mêmes événements, donc mêmes exécutions pour toute histoire ; et ℛ^{𝔅,ρ} ne dépend que des exécutions (O1). Le rebaptême de γ (« paramètre de loi devenu variable d'état ») ne change aucun objet dont ℛ dépende. ∎ — Vérification Z4 : les deux présentations, implémentées séparément, produisent des exécutions **identiques au bit près**.

**Corollaires.** (C1) La question « est-ce 𝒢 qui a changé, ou une variable lente cachée alimentant un 𝒢 figé ? » **n'est pas décidable depuis ℛ** — quelle que soit la puissance d'intervention et de lecture. Ce que ℛ décide : l'insuffisance d'un résumé déclaré, l'existence d'une horloge active supplémentaire, sa constante de temps, sa loi d'usage — jamais sa localisation ontologique. (C2) Dans la trichotomie de la privauté mnésique du Tome II : la plasticité est privée *par support*, publique *par effets* — et seuls les effets sont l'observable. (C3) La mise en garde du plan (« ne pas confondre modification de paramètre et nouvel état caché ») n'était pas une précaution : c'était un théorème.

## 5. Décision D-08 — la frontière espèce/individu est déclarative

**D-08 (amende D-04).** Le critère de D-04 (« 𝒢 appartient à l'individu ssi une histoire peut le modifier ») se lit désormais **dans la présentation déclarée** : il tranche relativement à un espace d'état déclaré, jamais absolument. L'invariant observationnel de la frontière espèce/individu est le **spectre des horloges actives** — leur nombre, leurs τ, leurs lois d'usage — relatif à (𝔅, ρ) (QO-85). Un même comportement admet une présentation « espèce plastique » et une présentation « espèce figée à état plus riche » : le choix entre elles est une convention de modélisation, à déclarer comme telle. E2/X4 (F-III.2) et D-04 restent valides dans leur présentation ; leur portée est maintenant exacte.

## 6. Registres

**Théorème** : III-11 (indiscernabilité de la plasticité ; preuve §4 ; vérification bit à bit).
**Décision** : D-08 (frontière espèce/individu déclarative ; D-04 amendée ; invariant observationnel = spectre des horloges actives).
**Faits** : validation Z0 bit à bit (extension conforme) ; usages 45/15 Kairos, γ 0.8342/0.9323, égalisation à 10⁻⁶, horloges mortes ; **détection** (cartes différentes à z égal, témoin T₂ = 70) ; s\*(γ) décroissante, Σ^{(1)} ≠ Σ^{(2)} ; s\*_figé(1) = 0.01627 (III-5 retrouvée) ; la sonde use la loi qu'elle mesure (+0.0005 à +0.0013) ; fermeture cellule à cellule du résumé à cinq horloges, échec du résumé à quatre.
**Clôture** : **QO-56 close, dans les deux sens** — la plasticité est détectable (comme horloge supplémentaire) et indécidable (comme ontologie).
**Questions ouvertes** : **QO-84** la vraie frontière de III-11 est la *réalisabilité markovienne* — existe-t-il des plasticités non réalisables par variable d'état (lois à mémoire non markovienne de dimension infinie, ou non causales) ? c'est la limite exacte du théorème ; **QO-85** l'invariant observationnel — le spectre des horloges actives (dimension minimale du résumé, τ, lois d'usage) comme signature d'espèce relative à (𝔅, ρ) : le définir, prouver son invariance par rebaptême, et en faire le contenu positif du chapitre 13.

## 7. Où cela mène — le plan est structurellement couvert

Avec cette note, chaque chapitre du plan du Tome III possède son matériau : Parties I–II (F-III.0–F-III.2, III-1/2/3), Partie III (F-III.3/F-III.7, III-4/7/8, D-05), Partie IV (F-III.4–F-III.11, III-5/9/10, P-III.6, la conclusion stabilisée du chapitre 12), **Partie V (cette note, III-11, D-08)** — et la conclusion du tome a sa réponse : deux intérieurs cessent d'être interchangeables lorsqu'une histoire admissible les sépare, à un budget et une résolution donnés, et ce que l'observation peut en dire s'arrête exactement au spectre de leurs horloges. Je propose comme prochaine étape **F-III.13 — la note de synthèse** : cartographie notes ↔ chapitres, registre consolidé (théorèmes, propositions, principes, décisions D-01…D-08, formulations canoniques, rectificatifs, QO ouvertes/closes), et la liste de rédaction résiduelle (audit QO-73, dérivations analytiques QO-74/77/80/82/83, QO-84/85) — l'outil de travail pour passer des notes au manuscrit du tome.

---

*Reproductibilité : `python fiii12_plasticite.py` (Z0 validation bit à bit, Z1 histoires égalisées, Z2 détection et s\*(γ), Z3 fermeture étendue, Z4 indiscernabilité) ; consolidé : `output_theory/fiii12_report.json`.*
