# Rapport de campagne — Patch 0.1.1, X0 / X4 / X4b

**Périmètre.** Patch `iws-core-0.1.1-patch1` sur IWS_1 (commit 2bab269), campagnes X0 (recalibration), X4 (endogénéité, dynamique historique) et X4b (origine de la brisure de symétrie). Protocole : 5000 pas, dt = 0.05, 10 graines (X0) ou 5 graines (bras aléatoires), sorties avec configuration complète, graine, version, temps de Kairos, violations.

---

## 1. Critères de réussite du patch : 7/7

| Critère | Résultat |
|---|---|
| C1 reproduction bit-à-bit du legacy | PASS (3 graines, 800 pas, 6 observables + états finaux, égalité exacte) |
| C2 borne de trace saturée ‖τ‖ ≤ α√d/β | PASS (max 5.2137 < 5.3033, zéro violation) |
| C3 invariant \|E\| en mode conservatif | PASS (\|E\| strictement constant sur ~7800 Kairos) |
| C4 u = 0 exactement nul | PASS |
| C5 symétrie du flot (X4b-1a) | PASS (écart inter-nœuds ≤ 1.3·10⁻¹⁵) |
| C6 brisure conventionnelle journalisée (X4b-1b) | PASS (1er Kairos simultané à 20 nœuds, pas 255) |
| C7 flux RNG séparés, bras appariables | PASS |

Un correctif a été nécessaire pour C1 : l'ordre de sommation de dP différait d'un ulp (le terme κ_rel était ajouté après −κ₃P). L'ordre exact du code historique est répliqué en mode `legacy`.

## 2. Audit code ↔ article (constat de reproductibilité)

Le code publié diffère du texte de [P1] sur des points non anecdotiques, tous paramétrés dans le patch :

- **(A1)** la pression contient un terme κ_rel·‖H_i − (ÃH)_i‖ (surprise relationnelle, κ_rel = 0.7) absent de l'article ;
- **(A2)** le recâblage codé = retirer 2 / **ajouter 2** avec **plafond de densité 0.35** — l'article dit retirer 2 / ajouter 3, sans plafond ;
- **(A3)** chaque Kairos ajoute un coup de bruit H_i += N(0, 0.1) absent de l'article ;
- **(A4)** l'intégrateur est un Euler **semi-implicite de fait** (aliasing : H avance avec la nouvelle vitesse) ;
- **(A5)** gain de couplage 0.8 et ε = 0.15 codés en dur ;
- **(A6)** un seul générateur partagé ;
- **(A7)** le terme κ₁‖∇Φ‖ de la pression est évalué sur le H **déjà mis à jour** (aliasing de référence).

Conséquence : la « ligne de base historique » est le **code**, pas le texte. Toute comparaison publiée devra déclarer ces écarts (et l'article devra être corrigé ou le code aligné).

## 3. X0 — Recalibration

**Question 1 (reproduction) : oui**, bit-à-bit (C1).

**Question 2 (la saturation seule) : la structure qualitative survit.** X0-P1 vs X0-S (un seul mécanisme changé, tout le reste identique, graines appariées) :

| Observable (final, 10 graines) | X0-P1 (linéaire) | X0-S (saturée) |
|---|---|---|
| O1 trace | 12.10 ± 0.95 | 5.14 ± 0.06 (= borne α√d/β, comme prédit) |
| O2 pression | 0.866 ± 0.051 | 0.841 ± 0.048 |
| O6 variance d'état | 2.10 ± 1.77 | 1.86 ± 1.56 |
| O4 arêtes | 67.7 ± 0.5 | 67.7 ± 0.5 |
| Kairos totaux | ~9300 | ~9300 |

Seule O1 change (saturation au niveau théorique) ; O2, O4, O6 et le taux d'événements sont statistiquement indiscernables. **D-02 est validée empiriquement : la saturation ne détruit pas le régime E3.** (Réfutation prévue par X0 : non déclenchée.)

**Bras cumulé X0-Core** (6 décisions changées à la fois — non attribuable, comme convenu) : monde très différent. Kairos par graine bimodal ({1, 407, 1624} vs ~7000–7900), O6 = 0.37 ± 0.37, O4 = \|E\| initial conservé. Voir §5 pour l'explication.

## 4. Validation d'intégrateur (dt vs dt/2)

Le critère strict Δ_k < 0.05 **échoue pour les trois bras** — mais le détail par observable est décisif :

| Bras | O1 | O2 | O5 | O6 | O7 | écart nb évén. | écart temps évén. |
|---|---|---|---|---|---|---|---|
| X0-P1 (kick=0) | 0.031 | **0.138** | 0.017 | 0.041 | 0.032 | 114/8384 | 3.35 |
| X0-S (kick=0) | 0.029 | **0.139** | 0.018 | 0.072 | 0.058 | 283/9004 | 6.70 |
| X0-Core | 0.002 | **0.120** | 0.003 | 0.005 | 0.017 | 16/6950 | 0.58 |

Le Δ est dominé partout par **O2** : le sup-en-temps est sensible au jitter des instants d'événements (un pic de pression décalé de quelques pas produit un écart ≈ profondeur de relaxation), phénomène attendu dans un système événementiel à dépendance sensible — la convergence trajectorielle n'est pas un critère atteignable ici, quel que soit dt. Pour X0-Core, toutes les autres observables sont < 0.02 et l'appariement d'événements est excellent (16/6950, 0.58 unité de temps). **Verdict :** dt = 0.05 est adéquat pour les statistiques de régime du noyau (avec la mise en garde consignée) ; recommandation : dt = 0.025 pour les campagnes Core décisives, et rapporter systématiquement les Δ par observable plutôt qu'un verdict binaire. Les moyennes finales seules ne sont jamais utilisées comme preuve de convergence, conformément au protocole.

## 5. X4 / X4b — Le résultat central de la campagne

### 5.1 Proposition P-8 (nouvelle, démontrée) : invariance de la variété homogène

Soit Δ = {x : H_i ≡ h, V_i ≡ v, τ_i ≡ θ, P_i ≡ p ∀i}. Alors, pour **tout** graphe A et toute entrée uniforme entre nœuds (dont u ≡ 0) :
(i) Δ est invariante par le flot — car Ã est stochastique en lignes, donc (ÃH)_i = h sur Δ, **indépendamment de la structure du graphe** ; tous les termes des EDO coïncident alors entre nœuds ;
(ii) Δ est invariante par la cascade de sauts — depuis Δ, toutes les pressions franchissent Θ simultanément ; la cascade relaxe chaque nœud identiquement ; le recâblage modifie le graphe (asymétriquement, via le départage D-08) mais ne touche pas les états.

**Corollaire 1.** Aucune différenciation ne peut naître d'un état exactement homogène : la question empirique est entièrement celle de la **stabilité transversale** de Δ.
**Corollaire 2 (raffine E-06′).** Le départage min(index) brise la symétrie **du graphe**, mais ne peut pas briser la symétrie **des états**. Confirmé numériquement : bras 1b, 7940 Kairos, O6 final ≈ 5·10⁻³¹ ; écart d'états ≤ précision machine avant comme après les événements.

### 5.2 Stabilité transversale mesurée : les perturbations décroissent

Balayage ε₀ ∈ {10⁻⁸, 10⁻⁶, 10⁻⁴, 10⁻²} (Core, circulant, u = 0) : taux de croissance **G ≈ −0.458** (identique à 4 décimales sur 4 ordres de grandeur de ε₀ — décroissance linéaire propre), amplification O6/ε₀² ≈ 10⁻¹³. Bruit isotrope σ = 10⁻⁶ : variance entretenue ~ 5·10⁻¹⁵ ≈ O(σ²), sans amplification. Graphe aléatoire + états identiques : homogénéité préservée (P-8, vérification). Graphe régulier + états aléatoires (hétérogénéité **macroscopique**) : O6 décroît de ~10 ordres de grandeur, G ≈ −0.45.

> **Verdict sur C-4 (reformulée) : réfutée dans ce régime de paramètres.** Le noyau n'amplifie pas des hétérogénéités arbitrairement petites ; la variété homogène est transversalement stable (aucune instabilité de type Turing ici). Critère de réfutation de X4b : déclenché.

### 5.3 Ce que le système fait réellement avec u = 0

La phénoménologie endogène, par graine (Core sur ER ; confirmé en legacy-u0) :

1. **Effondrement** vers l'origine (h_norm = 0, ~1 Kairos) — le rappel gagne ;
2. **Synchronisation hors origine** : tous les nœuds convergent vers un même point de norme ≈ 3.246, avec activité Kairos soutenue (~7000+). Explication : point fixe auto-cohérent M(τ*)h* = ζ tanh(h*) — le préconditionneur affaiblit le rappel le long de τ (facteur m₀ = 1/3 à λ = 2) et l'équation h*/3 ≈ 0.8·tanh(h*) donne ‖h*‖ ≈ 3.2, exactement la valeur observée ;
3. **Clustering** : variances finales quasi quantifiées (0, 0.250, 0.501, 1.001) = partitions en un petit nombre de groupes co-localisés.

Et sur la dynamique historique (X4 proprement dit, 5 graines) :

| Bras legacy | O6 final |
|---|---|
| εW (référence [P1]) | 2.46 ± 2.25 |
| u = 0, kick 0.1 (A3 actif) | 1.14 ± 1.78 |
| u = 0, kick 0 | 0.88 ± 1.76 (4/5 graines ≈ 0 ou synchronisées ; 1/5 à 4.39) |
| bruit blanc apparié σ = 0.045 | 1.59 ± 1.72 |

**Lecture honnête :** (i) le forçage εW gonfle substantiellement le chiffre-titre de [P1] (≈ ×3 par rapport au cas strictement endogène) ; (ii) le coup de bruit de Kairos (A3), non documenté dans l'article, contribue lui aussi à la variance ; (iii) la « différenciation soutenue » strictement endogène est **rare et bimodale** — l'issue typique est la synchronisation hors origine ou le clustering grossier.

### 5.4 Conséquences pour le programme

- **C-4 à réécrire** : non pas « amplification d'hétérogénéités arbitrairement petites », mais quelque chose comme : *sélection, quantification et stabilisation de partitions (clustering) à partir d'une hétérogénéité initiale macroscopique* — avec l'ampleur de la différenciation fortement dépendante du forçage. La question directrice devient : dans quelle région de paramètres la stabilité transversale de Δ se perd-elle (G > 0) ?
- **Cible théorique nette (remplace l'attaque frontale de C-2)** : linéarisation autour de Δ. Sur Δ, le transversal se décompose sur les modes propres de Ã ; les exposants transversaux sont calculables par mode de graphe — c'est exactement l'analyse de type Turing-sur-graphe anticipée en Q-01, désormais avec un objet précis (Δ, P-8) et une mesure empirique de référence (G ≈ −0.458 à reproduire analytiquement).
- **Le point fixe h\*** (M(τ\*)h\* = ζ tanh(h\*)) et la bistabilité effondrement/activation sont des résultats exacts accessibles (système à 3 équations scalaires sur Δ) : premier théorème de régime réaliste, bien plus abordable que C-2 en général.

## 6. Erratum E-06′ (intégré)

La formulation de E-06 (« le bras 1 doit rester exactement symétrique ») est précisée : la symétrie **des états** est préservée par le flot **et** par les événements (P-8, Corollaire 2) ; la symétrie **du graphe** est rompue conventionnellement par le départage D-08 au premier événement simultané — conséquence de la spécification, journalisée (`symmetry_log`), jamais comptée comme violation. Sous-bras X4b-1a (Kairos OFF, contrôle du flot) et X4b-1b (Kairos ON, mesure de la brisure) implémentés.

## 7. Suites

1. Théorie : (a) analyse sur Δ (bistabilité, h\*) ; (b) exposants transversaux par mode de Ã ; les deux avant X3–X1.
2. Expériences : X3 (conservatif vs densifiant) puis X2 (homophile vs aléatoire) puis X1 (endogène vs exogène), à dt = 0.025 pour les bras Core, en rapportant les Δ par observable.
3. Rédaction : l'audit A1–A7 impose un erratum au dépôt (ou à l'article) **avant** toute nouvelle publication s'appuyant sur les chiffres de [P1] ; le rôle de εW et du kick (A3) dans O6 doit être déclaré.
