# IWS — Note T-1 : Théorie sur la variété homogène Δ (Étapes A et B)

**Objet.** Analyse du système réduit sur Δ (Étape A) et amorce de l'analyse transverse (Étape B), conformément à la feuille de route révisée : « écrire et analyser le système réduit sur Δ », avec pour cible la bistabilité extinction / activité collective. Tous les résultats numériques sont reproductibles par `theory_delta.py` et `part5_transient.py` (sorties dans `output_theory/`).

**Paramètres de référence** (Core 0.1.1 / [P1]) : ζ = 0.8, λ = 2, α = 0.45, β = 0.12, γ₀ = 0.25, γ₁ = 1.25, d = 2 ; κ = (0.6, 0.4, 0.5), Θ = 1.25, r_P = 0.35, r_V = 0.5.

**Convention de statut.** `[PROP]` démontré · `[PROP-num]` démontré modulo vérification numérique d'inégalités explicites · `[CONJ]` conjecture · `[ERRATUM]` correction d'un résultat antérieur · `[INTERP]` interprétation.

---

## 1. Système réduit sur Δ

P-8 (rapport X0/X4b) établit l'invariance de Δ = {Hᵢ ≡ h, Vᵢ ≡ v, τᵢ ≡ θ, Pᵢ ≡ p} par le flot et par les cascades de sauts, pour tout graphe et toute entrée uniforme, parce que Ã est stochastique en lignes : (ÃH)ᵢ = h sur Δ. Le système réduit (Core : trace saturée, u = 0) est :

- ḣ = v
- v̇ = −Γ(θ)v − M(θ)h + ζ tanh(h)
- θ̇ = α tanh(h) − βθ
- ṗ = κ₁‖h‖ + κ₂‖v‖ − κ₃p

avec Γ(θ) = γ₀ + γ₁‖θ‖ et M(θ) = I − [λ/(1+(1+λ)‖θ‖²)] θθᵀ. La pression est **esclave** : elle ne rétroagit sur (h, v, θ) que par les événements, lesquels ne modifient pas les états sur Δ (P-8) hormis la relaxation uniforme v ← r_V v, p ← r_P p. Le sous-système (h, v, θ) ∈ ℝ^{3d} est autonome entre cascades.

## 2. Classification complète des équilibres sur Δ

**P-9 (structure des équilibres)** `[PROP]` *Tout équilibre du système réduit vérifie v = 0, θ* = (α/β) tanh(h*), et h* est parallèle à tanh(h*) (tanh composante par composante). En conséquence, les composantes de h* appartiennent à {0, ±x_q}, où x_q > 0 (s'il existe) résout l'équation scalaire*

x = ζ Λ_q(x) tanh(x),  Λ_q(x) = 1 + λ q(α/β)² tanh²x / (1 + q(α/β)² tanh²x),

*q ∈ {1, …, d} étant le nombre de composantes non nulles.*

*Preuve.* v̇ = 0 et θ̇ = 0 donnent θ* = (α/β)s avec s = tanh(h*), puis M(θ*)h* = ζs ⇒ h* = ζQ(θ*)s = ζ[1 + λ‖θ*‖²/(1+‖θ*‖²)]s (car θ* ∥ s), donc h* = c·tanh(h*) composante par composante pour un c commun : chaque composante résout la même équation scalaire, de solutions {0, ±x} ; en réinjectant ‖s‖² = q tanh²x on obtient l'équation en Λ_q. ∎

**Valeurs numériques (paramètres [P1])** : q = 1 : x ∈ {0.1021, 2.2376} ; q = 2 : x ∈ {0.0717, 2.2959}, soit ‖h*‖ = **3.2468** — exactement la valeur observée dans les simulations (rapport §5.3). Un balayage de Newton (400 départs aléatoires sur le champ réduit 6D) ne trouve **aucune autre famille** : composantes ∈ {0, ±0.0717, ±0.1021, ±2.2376, ±2.2959} uniquement, conformément à P-9.

**Seuil d'allumage** `[PROP]` Développement petite amplitude : la racine instable vérifie x_u ≈ √[(1/ζ − 1)/(λq(α/β)² − 1/3)] (0.095 vs 0.1021 exact pour q = 1 ; 0.067 vs 0.0717 pour q = 2). Aux paramètres [P1], le seuil d'allumage est **minuscule** (≈ 0.07–0.10) : presque toute condition initiale allume l'activité.

## 3. L'état actif est un effet pur de la trace

**P-10 (extinction structurelle)** `[PROP]` *Si ζ(1+λ) ≤ 1, l'origine est le seul équilibre sur Δ.* — Preuve : Λ_q < 1+λ et tanh x < x pour x > 0, donc ζΛ_q tanh x < x. ∎

**P-11 (extinction globale à λ = 0)** `[PROP]` *Pour λ = 0 et ζ < 1, toutes les trajectoires du système réduit convergent vers l'origine.* — Preuve : 𝒱(h, v) = ½‖v‖² + ½‖h‖² − ζΣₖ log cosh(hₖ) est radialement non bornée (car ζ < 1) de minimum unique en 0, et 𝒱̇ = −Γ(θ)‖v‖² ≤ −γ₀‖v‖² ; LaSalle : l'ensemble invariant dans {v = 0} impose M(θ)h = ζtanh h, soit h = ζ tanh h (M = I), soit h = 0 ; puis θ → 0. Vérifié numériquement (‖h(∞)‖ = 5.5·10⁻³⁵). ∎

**Corollaire** `[INTERP]` À λ = 0, le noyau meurt ; à λ > 0 suffisant, un état actif auto-entretenu apparaît. **L'activité collective est intégralement portée par la trace** : l'histoire (θ* ≠ 0) affaiblit le rappel (m(θ*) ≈ 0.349 au lieu de 1) et rend viable un régime qui n'existe pas dans la dynamique sans mémoire. C'est exactement la propriété pressentie : la trace ne crée pas la différence entre nœuds, elle crée une activité collective historiquement soutenue.

## 4. Stabilité locale et sélection diagonale

**P-12 (d = 1, Routh–Hurwitz explicite)** `[PROP-num]` Le polynôme caractéristique en (x*, 0, θ*) est s³ + a₂s² + a₁s + a₀ avec a₂ = Γ* + β, a₁ = Γ*β + (m* − c), a₀ = β(m* − c) − αb·sech²x*, où m* = m(θ*), c = ζ sech²x*, b = 2λθ*x*/(1+(1+λ)θ*²)². De plus **a₀ = β·G′(x*)** où G(x) = m(θ_eq(x))x − ζtanh x : le signe de a₀ est le critère de branche (la racine basse a a₀ < 0, automatiquement instable ; la haute a a₀ > 0). Aux paramètres [P1] : branche basse x = 0.1021 instable (a₀ = −0.033) ; branche haute x = 2.2376 stable (a₀ = +0.037, a₂a₁ − a₀ = +4.39 ≫ 0).

**Stabilité de l'origine** `[PROP]` Linéarisation à 0 : (s+β)ᵈ·(s² + γ₀s + 1 − ζ)ᵈ ⇒ stable ssi ζ < 1 (valeur propre lente = −β = −0.12). Confirme la conjecture de la revue : ζ = 0.8 ⇒ origine localement stable, effondrements observés cohérents.

**Sélection diagonale (résultat inattendu, d = 2)** `[PROP-num]` Le jacobien 6×6 sur Δ donne : point d'axe (2.2376, 0) **instable** (max Re = +0.114) ; points diagonaux (±2.2959, ±2.2959) **stables** (max Re = −0.0459). Mécanisme : au point d'axe, la composante éteinte h₂ = 0 est allumée par le couplage croisé trace→préconditionneur : ∂v̇₂/∂θ₂ = +cθ₁x > 0 crée la boucle positive δh₂ → δθ₂ → δv̇₂, et le coefficient a₀ transversal β(1−ζ) − α·cθ₁x = 0.024 − 0.179 < 0. **Les seuls attracteurs ponctuels sur Δ sont les 4 points « toutes composantes allumées »** — ce qui explique pourquoi les simulations atterrissent toujours à ‖h*‖ = 3.2468 et jamais à 2.2376.

## 5. Théorème T-A — Bistabilité historique

**T-A** `[PROP-num]` *Aux paramètres [P1] (et sur un ouvert autour), le système réduit sur Δ possède simultanément : (i) l'origine, localement exponentiellement stable ; (ii) quatre équilibres actifs diagonaux, localement exponentiellement stables ; (iii) des équilibres-selles (racines basses et points d'axe) organisant les bassins. Le bassin atteint dépend de la condition initiale — donc de l'histoire.*

**Bassins mesurés** : 99.0 % du carré h₀ ∈ [−3,3]² (v₀ = 0, θ₀ = 0) atteint l'état actif ; sous la loi initiale de [P1] (h₀ ~ 𝒩(0, 0.6)), **P(actif) ≈ 0.85** (2000 tirages). Cela prédit la bimodalité observée en X4 : sur 5 graines, P(exactement 1 effondrement) ≈ 0.39, P(aucun) ≈ 0.44 — l'observation « 4/5 actives, 1/5 effondrée » est typique. (Réserve : le bassin sur Δ approxime le bassin du réseau complet à états hétérogènes ; l'accord est d'ordre de grandeur.)

**C'est le résultat cible de la feuille de route** : « pour certains paramètres, le système homogène possède simultanément un équilibre nul stable et un équilibre actif stable ; le bassin atteint dépend de l'histoire initiale » — établi, avec en prime la sélection diagonale et les seuils d'allumage explicites.

## 6. Carte de régimes d = 1 (Étape C amorcée)

Balayage (λ, ζ) ∈ [0,6]×[0.05,1.6] (figure b) : quatre régions — extinction seule ; **bistable** (ζ < 1, racine haute existante et RH satisfaite) ; actif seul (ζ > 1, origine instable) ; la région « RH violée » (oscillatoire/Hopf) est **vide sur toute la fenêtre balayée** (fraction 0.000). Dans cette tranche, la branche active est stable partout où elle existe : pas de route oscillatoire ici (à réévaluer dans (λ, α/β) et avec γ₁ réduit — la forte friction historique Γ* ≈ 4.8–6.7 suramortit tout). La courbe ζ_min(λ) (frontière d'existence de la bistabilité) est calculée et tracée ; [P1] est profondément dans la région bistable.

## 7. Spectre transverse et validation de G (Étape B)

**Jacobien par mode** `[PROP]` Autour d'un état homogène (h*, 0, θ*), les perturbations se décomposent sur les modes propres ρ_r de Ã (symétrique ici), chaque mode obéissant au bloc 3d×3d :

J(ρ) = [[0, I, 0], [−M* + ζρS, −Γ*I, −D_M], [αρS, 0, −βI]],  S = diag(sech²h*), D_M = ∂_θ(M(θ)h*)|θ*.

Cohérence vérifiée : J(ρ=1) redonne le spectre sur Δ (−0.0459).

**Prédiction vs mesure au point actif (circulant N = 20, mode le plus lent ρ = 0.904)** :

| Quantité | Valeur |
|---|---|
| G prédit (spectral, flot seul) | **−0.0927** |
| G mesuré (simulateur, Kairos OFF) | −0.1000 (écart 7 %, dissipation d'Euler) |
| G mesuré (Kairos ON, fenêtre tardive) | −0.080 à −0.084 (3 graines) |
| G prédit (variationnel le long du transitoire, relaxations d'événements incluses, graphe gelé) | **−0.0803** (accord < 5 %) |

**E-X4b-G** `[ERRATUM]` La valeur G ≈ −0.4577 du rapport X0/X4b **est un artefact de fenêtre d'ajustement** : `growth_rate()` ajustait, en cas de décroissance immédiate, sur les **10 premiers pas** (t ∈ [0, 0.5]) — la phase balistique de rotation de la perturbation de la position vers la vitesse. Reproduction exacte : G_x4b = −0.4618 (graine 7), −0.4390 (graine 11), rigoureusement invariant en ε₀ par linéarité (ce qui expliquait la coïncidence « à 4 décimales »). Le **verdict qualitatif est maintenu et renforcé** (Δ transversalement stable, C-4 réfutée), mais la valeur de référence devient −0.093 (flot) / −0.082 (avec événements). L'estimateur est corrigé dans `run_x4b.py` (fit sur le segment central pré-plancher). Les G positifs du bras 5 (bruit infinitésimal) relevaient du même artefact.

**Rôle causal des Kairos à ces paramètres (réponse à la question G_K)** `[INTERP]` Les relaxations d'événements **ne resynchronisent pas plus vite** : la décroissance transverse avec Kairos (−0.082) est légèrement *plus lente* que le flot pur (−0.100). Raison : au point actif le régime est suramorti (Γ* ≈ 6.75), δv est esclave — la contraction δv ← r_V δv à chaque cascade mord peu sur le mode lent (δh, δθ), tandis que les cascades font osciller la trajectoire de base. **G_K ≈ 1 : rôle topologique secondaire** ; la resynchronisation est portée par le flot, c'est-à-dire par la friction historique Γ(θ). (Réserve méthodologique : le variationnel ignore les matrices de saltation — sensibilité des instants d'événements — et gèle le graphe ; l'accord à 5 % suggère que ces effets sont ici du second ordre. QO-9.)

**Où chercher la perte de stabilité transverse** : a₀(ρ) = βm* − ρ(βc + αb·sech²x*) est *décroissante* en ρ, et ρ ≤ 1 = mode synchrone : à ces paramètres, **aucun mode transverse n'est plus instable que le mode synchrone** — la différenciation ne peut pas naître d'une instabilité de Δ ici. La frontière G_transverse = 0 doit être cherchée en paramètres (Étape C) : candidats prioritaires ζ → 1⁻ (la raideur transverse 1 − ζρ s'annule d'abord au mode ρ max < 1 : instabilité transverse *avant* l'instabilité synchrone possible si couplée au terme +b), γ₁ ↓ (désuramortissement), et α/β.

## 8. Décodage des états en clusters (C-5 précisée)

Les variances finales « quasi quantifiées » observées (rapport §5.3 : 0, 0.250, 0.501, 1.001) se décodent **exactement** comme des partitions des nœuds sur {origine} ∪ {4 puits diagonaux} (a = 2.2959, N = 20, d = 2) :

| Partition | O6 prédit | O6 observé |
|---|---|---|
| tous synchronisés | 0 | 0 |
| 1 nœud à l'origine, 19 au puits | a²·(1/N)(1−1/N)·2/d = **0.2504** | 0.250 |
| 1 nœud à coordonnée basculée (a,a)→(a,−a) | (2a)²(1/N)(1−1/N)/d = **0.5008** | 0.501 |
| 1 nœud au puits opposé (−a,−a) | **1.0015** | 1.001 |

**C-5 (reformulée)** `[CONJ]` Le réseau complet possède des équilibres mixtes (« clusters ») où chaque nœud occupe l'un des puits de P-9, stables lorsque la fraction minoritaire est faible (le champ de voisinage ÃH reste proche du puits majoritaire) ; le régime de clustering observé est la sélection historique de telles partitions. La correspondance à 3 décimales ci-dessus en est une première vérification forte.

## 9. Registres mis à jour

**Propositions** : P-9 à P-12, T-A (statuts ci-dessus) ; formule J(ρ) et validation de G.
**Erratum** : E-X4b-G (§7), estimateur corrigé dans le dépôt.
**Conjectures** : C-5 reformulée (§8) ; **C-4 close et remplacée** par la lecture bistable : le noyau à ces paramètres est un système {extinction ↔ cohérence active} historiquement départagé ; la différenciation n'est pas une instabilité de Δ ici — c'est une occupation mixte des puits, héritée de l'hétérogénéité initiale macroscopique.
**Questions ouvertes** : QO-8 caractérisation globale des bassins (au-delà du numérique) ; QO-9 Floquet hybride rigoureux (saltation + graphe évolutif) ; QO-10 cartographie de la frontière de stabilité transverse en (ζ, λ, γ₁, α/β) — l'objet exact de l'Étape C ; QO-11 existence/stabilité des équilibres mixtes de C-5 (réseau complet, perturbation du cas tous-au-puits).

## 10. Lecture d'ensemble

Le noyau IWS, sur Δ, est désormais compris : **un système bistable extinction / activité collective, dont l'état actif n'existe que par la trace, dont les attracteurs sont « toutes composantes allumées », au seuil d'allumage minuscule, transversalement stable — donc synchronisant — avec des cascades de Kairos auto-entretenues (κ₁‖h*‖/κ₃ = 3.90 > Θ) qui jouent ici un rôle topologique et non différenciateur.** La reformulation directrice de la feuille de route (« comment un IWS passe-t-il de la cohérence à la différenciation ? ») reçoit une traduction mathématique précise : trouver où, dans l'espace des paramètres, max_{ρ<1} Re λ(J(ρ)) traverse 0 — Étape C — puis relire X3/X2/X1 comme des déplacements de cette frontière.

---

*Reproductibilité : `python theory_delta.py` (parts 0–4, figure `output_theory/theory_delta.png`, rapport JSON) ; `python part5_transient.py` (résolution de l'écart G) ; erratum d'estimateur dans `run_x4b.py`.*
