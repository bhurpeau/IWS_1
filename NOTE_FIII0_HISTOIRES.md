# IWS — Note F-III.0 : Histoires, signatures, et la naissance de l'effet d'ordre

**Objet.** Ouverture formelle du Tome III sur la base des sept chantiers fixés : définition d'une histoire, état de l'individu, composition, séparation ordre/récence, loi canonique de mémoire, portée (contenus vs partenaires), séquences. Cette note livre les définitions, deux propositions démontrées-vérifiées — dont une qui résout le point 4 plus radicalement que prévu — et le premier effet d'ordre propre. Reproductibilité : `fiii0_histoires.py` (P1–P3), `fiii0_fin.py` (P3-duale, P4), `output_theory/fiii0_report.json`.

---

## 1. Définitions (adoptées)

- **Épisode** : E = (u, g, T, 𝒫) — direction, intensité, durée, protocole (ici : contact brutal, graine appariée en début d'épisode-test).
- **Histoire** : ℋ = (E₁, D₁, E₂, D₂, …, E_n) ; **opérateur** X_fin = Φ_ℋ(X₀) ; **composition** Φ_{ℋ₂∘ℋ₁} = Φ_{ℋ₂} ∘ Φ_{ℋ₁}.
- **État étendu** : X = (H, V, τ, P, χ, s⃗) (+ q, graphe selon le modèle).
- **Individualité opérationnelle** : la **carte de réponses** ℛ_X(u, g, T) — implémentée comme *signature* : motif d'appropriation par direction de sonde (u₁, −u₁) sur une grille de durées. Deux systèmes au même repos sont distincts ssi ℛ_{X₁} ≠ ℛ_{X₂}. C'est la définition de travail du Tome III.

## 2. Impossibilité de la compensation croisée `[PROP]`

Le contrôle envisagé « égaliser la contribution de récence entre A∘B et B∘A » est **impossible pour u_A ∦ u_B** : les résidus s'écrivent σ_A w_loin u_A + σ_B w_près u_B contre σ_B w_loin u_B + σ_A w_près u_A, et l'égalité vectorielle exigerait w_loin = w_près (pas d'oubli). Le bon contrôle n'est pas la compensation mais la **suffisance d'état** :

## 3. Proposition III-1 — Suffisance de s⃗ et réductibilité à la récence `[PROP + NUM]`

Pour des épisodes **sous-critiques** séparés par des délais où les variables rapides (x, v, τ, χ, p) reviennent à leur base :

**(a) Superposition.** ṡ = ε_s(χ − s) est linéaire et χ ne dépend que de l'épisode courant : s⃗(test) est la superposition des résidus solo à poids de récence exacts. *Vérifié : s⃗(AB) lu (0.01793, −0.00966) = prédit (0.01793, −0.00966) ; idem BA à 10⁻⁴.*

**(b) Suffisance.** L'état étendu au temps de test est (repos, s⃗) : **injecter s⃗ dans un système vierge reproduit la signature de l'histoire complète**, cellule à cellule, pour les deux ordres. *Vérifié : ℛ(hist AB) ≡ ℛ(inject s⃗_AB) et ℛ(hist BA) ≡ ℛ(inject s⃗_BA).*

**(c) Corollaire (résolution du point 4).** L'effet d'ordre existe (ℛ_AB = {+u₁: ....AA} ≠ ℛ_BA = {+u₁: ..AAAA}) mais il est **entièrement l'arithmétique de récence sur s⃗** : dans cette classe d'histoires, la décomposition demandée — effet d'ordre = récence prévisible + composition proprement dite — se résout par **composition ≡ 0**. La séparation n'est donc pas seulement un problème méthodologique : c'est un théorème de structure du modèle minimal, qui dit *où la composition ne peut pas être* et donc où la chercher :

> (i) épisodes **appropriants** (changement de bassin) ; (ii) **délais courts** (mémoire de charge et de phase, F-II.1.1/1.2) ; (iii) lois de mémoire **non linéaires**.

## 4. Le théorème de l'épisode conditionnel — premier effet d'ordre propre `[NUM]`

Soit P l'amorce (u₁, 0.18, 41.9) et C l'épisode **conditionnel** (u₁, 0.18, 100) — choisi dans la fenêtre où il *réussit si amorcé, échoue nu* (vérifié : amorce→A, nu→.). Alors, à épisodes identiques, dose identique, durée totale identique :

| Ordre | Issue |
|---|---|
| **P puis C** | **approprié** — ‖x_fin‖ = 3.247 (le puits) |
| **C puis P** | **repos amorcé** — ‖x_fin‖ = 0.000 |

**Bassins finaux différents** : irréductible à la récence par construction (III-1 ne s'applique plus dès qu'un épisode change de bassin dans un ordre et pas dans l'autre). C'est la case **PA ≠ AP** du tableau des compositions, remplie — et la leçon est nette :

> **L'ordre compte quand une expérience est reçue par un système que l'expérience précédente a rendu capable — ou incapable — de la traverser.** La composition propre ne vit pas dans l'arithmétique de la mémoire ; elle vit dans les épisodes conditionnels qui franchissent des bassins.

Deux histoires peuvent différer de trois façons désormais distinguées : par récence (III-1, calculable), par phase (F-II.1.2, prédictible au signe près), par conditionnalité (ici, catégorique).

## 5. L'annulation et la question de la loi canonique `[NUM]`

**Limitation démontrée.** L'histoire (u₁ puis −u₁, durée ajustée : ‖s⃗(test)‖ = 10⁻⁴) a une signature **identique au système vierge** : la mémoire vectorielle unique perd les histoires contradictoires — u + (−u) = 0 n'est plus une inquiétude, c'est un fait mesuré.

**Mémoire duale : le support subsiste, l'effet reste à calibrer.** En ajoutant le canal scalaire (boost ×(1 + c₀s_sc), c₀ = 4), l'histoire annulée conserve s_sc = 0.0136 ≠ 0 — *le support de « il s'est passé quelque chose » survit à l'annulation directionnelle* — mais à ce levier, les signatures annulée/vierge restent indiscernables à la résolution de sonde. La solution existe en principe ; sa calibration comportementale est ouverte (QO-48). Décision de loi canonique reportée avec le cahier des charges acté : un vecteur unique est insuffisant pour les histoires longues ; candidats : couple (s_sc, s⃗), ou banc de traces directionnelles à seuil de fusion (QO-47).

## 6. Portée et programme

La portée actuelle est celle annoncée : **individuation par les contenus et leur ordre** — pas encore par partenaires singuliers (deux partenaires de même projection restent indiscernables, QO-51). Le tableau des compositions :

| | puis appropriation | puis amorçage |
|---|---|---|
| **appropriation** | AA : QO-49 | AP : **repos amorcé** si le second est conditionnel-nu... — voir PA/AP ci-dessus |
| **amorçage** | **PA : approprié** (théorème §4) | PP : réductible à la récence si sous-critiques séparés (III-1) ; sinon phase (F-II.1.2) |

Les cases restantes (AA, séquences ≥ 3, répétition/saturation) sont le programme immédiat, désormais outillé : ℛ comme observable, III-1 comme étalon du « rien de plus que la récence », l'épisode conditionnel comme générateur d'ordre.

**Registres.** Propositions : §2, III-1(a,b,c). Faits : effet d'ordre de récence (AB≠BA porté par s⃗) ; épisode conditionnel PA≠AP (bassins) ; annulation ≡ vierge ; survie du support scalaire. Questions ouvertes : QO-46 condition nécessaire et suffisante d'effet d'ordre propre (conjecture : ∃ épisode dont l'issue de bassin dépend de l'état étendu hérité) ; QO-47 loi canonique de mémoire ; QO-48 mémoire duale à levier calibré ; QO-49 séquences longues, AA, saturation ; QO-50 composition aux délais courts (phase) ; QO-51 mémoire relationnelle (partenaires).

## 7. Ce que le Tome III peut désormais dire

Un individu, dans ce cadre, n'est pas un état : c'est une **carte de réponses**. Deux systèmes au repos dans le même bassin peuvent différer — et nous savons maintenant *en quoi* : par ce que leur interface retient (s⃗, récence calculable), par la phase où on les rencontre (prédictible), et par ce que leurs expériences passées ont rendu traversable (conditionnalité, catégorique). L'histoire n'est pas une somme de doses — c'est démontré deux fois (Q_net, III-1) — et l'ordre n'est pas un mystère : il a trois canaux identifiés, dont un seul, le conditionnel, fabrique de l'irréversible.

---

*Reproductibilité : `python fiii0_histoires.py` (P1–P3 ; long), `python fiii0_fin.py` (P3-duale, P4 ; avec cache d'état). Résultats consolidés : `output_theory/fiii0_report.json`.*
