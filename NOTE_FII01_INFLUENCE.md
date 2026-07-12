# IWS — Note F-II.0.1 : Théorie analytique de l'influence unidirectionnelle

**Objet.** Élever la branche résistante du statut de fait numérique à celui de théorème, et traiter les six cibles fixées : existence locale, développement asymptotique, stabilité, nature de g_ign, loi d'appropriation, définition rigoureuse. Trois amendements de F-II.0 sont adoptés en tête. Reproductibilité : `fii01_resistance.py`, figure `output_theory/fii01.png`, données `output_theory/fii01_report.json`.

**Cadre.** Réduction scalaire exacte le long de la diagonale (par composante) de B forcé par A fixé à son puits : ẋ = v ; v̇ = −Γ(√2|θ|)v − m(√2|θ|)x + ζ tanh x ; θ̇ = α tanh x + g·w − βθ, avec w = tanh(x_A) = 0.98006.

---

## 0. Amendements adoptés (F-II.0 → F-II.0.1)

- **A1 (marginalité asymptotique).** L'énoncé « pinning m = ζ » est corrigé : à l'équilibre non nul, m = ζ·σ(x)/x < ζ strictement, avec le développement **m = ζ − (ζ/3)x² + o(x²)** pour σ = tanh (C = ζ/3 = 0.2667 ; pour σ générale impaire, C = −ζσ‴(0)/6). Vérification : à 1.5g_c, prédit 0.79966, mesuré 0.79966.
- **A2 (mémoire : trichotomie).** « Privée » signifie : **privée par support** (A-I1 : τ_A jamais transmise), **partiellement observable par ses effets** (h_A porte les effets de τ_A ; une observation longue permet d'inférer par exemple ‖τ_A‖ via les taux de relaxation — QO-27), **commune par convergence de contenu** seulement (alliance), jamais par partage du support.
- **A3 (sous-espaces des réductions).** Les réductions α_eff = α ± g valent exactement sous : systèmes identiques, couplages symétriques, sous-espace aligné/antipodal invariant. Toute asymétrie (g_AB ≠ g_BA, paramètres distincts) sort de la translation unique — c'est là que commence la spécialisation (Tome II, suite).
- **Formulation canonique de A-I4** (adoptée) : *l'extérieur ouvre le chemin de traverse ; il ne le parcourt pas à la place du système.* Ouvrir une possibilité ≠ produire un mouvement (II-1 ∧ II-2).

## 1. Théorème R-B (branche résistante) `[PROP-num]`

**(i) Naissance : bifurcation transcritique en g_c.** x = 0 est équilibre pour tout g (II-1) ; sa raideur est m(√2gw/β) − ζ, qui s'annule en **g_c = βτ_ign/(√2w) = 0.03273**. Le développement local du résidu F_g(x) = m(√2θ*(x))x − ζ tanh x donne

F_g(x) = x·[a₁(g − g_c) + a₂x + a₃x² + …],  a₁ = √2m′(τ_ign)w/β < 0, a₂ = √2m′(τ_ign)α/β < 0, a₃ = ζ/3,

structure transcritique générique (a₂ ≠ 0). Lecture géométrique : **la branche qui traverse l'origine en g_c est la selle d'allumage autonome** (x_u = +0.0717 en g = 0) : la charge externe abaisse le seuil d'allumage jusqu'à l'annuler en g_c, puis le seuil ressort de l'autre côté, *stabilisé* — le seuil de la porte devient butoir.

**(ii) Développement asymptotique.**

**x_res(g) = −(w/α)(g − g_c) + O((g−g_c)²).**

Le coefficient −w/α est la **compensation exacte** : B produit précisément la contre-écriture α·x_res qui annule l'excès de charge (g−g_c)w et maintient sa trace au voisinage de la charge critique. Vérification contre F-II.0 : prédit −0.00713 et −0.03563 ; mesuré −0.0071 et −0.0356.

**(iii) Stabilité.** Sur la branche, b := ∂v̇/∂θ = −√2m′x < 0 (x < 0, m′ < 0) : a₀ = (2ζβ/3)x² + √2|m′|α|x| > 0 (critère de branche satisfait, dominé par le terme linéaire), et la condition croisée de Routh–Hurwitz devient a₂a₁ − a₀ = Γ²β + Γβ² + Γ(m−c) − √2|m′|α|x| — **le signe automatique de R-3 est perdu** (b < 0 sort de la structure du théorème de rigidité). Estimation : violation pour |x| > 0.155.

**(iv) Mort : bifurcation de Hopf en g_H.** Continuation complète (jacobien 3D, 281 valeurs de g) : la branche résistante est stable sur **g ∈ (g_c, g_H = 0.1285)** et y meurt par traversée de l'axe d'une paire complexe (Re = −0.0025 à g = 0.120 ; 0.0000 à 0.1285 ; +0.0009 à 0.132), ω_H ≈ 0.334 (période ≈ 18.8), avec |x_res(g_H)| = 0.209 — cohérent avec l'estimation (iii). **Première bifurcation de Hopf du programme IWS** : impossible dans la classe autonome (R-3), rendue possible par le forçage qui inverse le signe du couplage trace→état sur la branche antiparallèle. Au-delà de g_H (RK4, sans artefact d'Euler) : l'oscillation croît sans saturation robuste jusqu'à **l'éjection dans le puits approprié** (à g = 0.140 : oscillation → x_final = +2.321). *La résistance ne disparaît pas : elle se rompt par oscillation, et la rupture débouche sur l'appropriation — poussée trop fort, la résistance bascule dans ce qu'elle refusait.* (Sous/supercriticité fine : QO-28 ; toute orbite périodique stable éventuelle est confinée à g − g_H ≲ 0.003.)

## 2. Nature de g_ign : réponse à la question 4 `[NUM]`

**C'est l'option 2 — un phénomène de bassin, pas une bifurcation.** Hiérarchie complète des seuils :

| Seuil | Valeur | Nature |
|---|---|---|
| g_c | 0.0327 | transcritique : le repos cède, la résistance naît |
| **g_ign** | **0.0556 = 1.70g_c** | **bassin/transitoire** : depuis la CI standard (graine +10⁻³, θ₀ = 0), le transitoire (contraction précoce, oscillation, charge) cesse d'être capturé par la branche — laquelle reste stable bien au-delà |
| g_H | 0.1285 | structurel : mort de la résistance par Hopf → éjection vers l'appropriation |

Preuve du caractère de bassin : à g = g_ign + ε, une CI posée *sur* la branche y reste ; la CI standard s'échappe. La branche existe et est stable sur tout (g_c, g_H).

## 3. Loi d'appropriation `[PROP-num]`

**Prédicteur sans paramètre ajusté** : linéarisation non autonome le long de la charge — (x, v) linéaire à raideur ζ − m(√2θ(t)) et friction Γ(θ(t)), θ(t) intégrant charge (t < T) puis décroissance libre (t > T) ; **appropriation ssi l'amplification linéaire de la graine franchit la selle autonome (x = 0.0717) avant expiration de la charge.**

| g | T* prédit | T* mesuré (dyade complète) |
|---|---|---|
| 0.05 | jamais | jamais |
| 0.08 | 31.6 | 31.7 |
| 0.10 | 24.8 | 24.8 |
| 0.15 | 17.8 | 17.9 |
| 0.20 | 14.9 | 15.0 |
| 0.30 | 12.2 | 12.3 |

Accord < 0.5 % partout, zone de résistance correctement classée « jamais ». La frontière empirique (g, T) de F-II.0 est désormais une **loi** : trois ingrédients seulement (charge exponentielle de τ, instabilité spectrale du repos, selle autonome), zéro calibration.

## 4. Définition formelle de l'appropriation (cible 6, adoptée)

Soit Φ_g^T le flot couplé de durée T et Φ₀^∞ le flot autonome. L'interaction (g, T) est **appropriée** par B depuis x₀ si

ω-lim Φ₀^∞(Φ_g^T(x₀)) = 𝒜 avec 𝒜 ≠ ω-lim Φ₀^∞(x₀) et 𝒜 attracteur autonome de B.

Indépendante du vocabulaire, testable, et satisfaite par les résultats : après découplage, B siège dans *son* puits (‖h_B‖ = 3.2468), auquel sa condition initiale n'accédait pas. Elle exclut proprement : la copie (𝒜 est autonome), la transmission de mémoire (A-I1), la persistance artificielle de l'entrée (Φ₀ après T).

## 5. Registres

**Propositions** : R-B(i)–(iii) `[PROP-num]` (développements vérifiés à 3–5 décimales) ; loi d'appropriation `[PROP-num]` (< 0.5 %) ; définition §4 `[DEF]`.
**Faits** : Hopf en g_H = 0.1285, ω ≈ 0.334 ; hiérarchie g_c < g_ign(bassin) < g_H ; éjection post-Hopf vers l'appropriation.
**Remarque théorique** : le système forcé **sort de la classe de rigidité de T-2** (b change de signe sur les branches antiparallèles) — le Tome II possède des comportements (oscillations relationnelles) structurellement interdits au Tome I. C'est la première propriété du Tome II qui n'est pas une réutilisation de Ψ.
**Questions ouvertes** : QO-27 inférence de ‖τ_A‖ depuis h_A (observabilité de la mémoire par ses effets) ; QO-28 premier coefficient de Lyapunov en g_H (sous/supercritique) ; QO-29 la triade {transcritique, bassin, Hopf} et la loi d'appropriation valent-elles dans toute la classe 𝒦×𝒮 (les développements n'utilisent que m′ < 0 et σ‴(0) < 0 — conjecture : oui, avec coefficients (−w/α, ζ-dépendants) universels) ; QO-30 oscillations relationnelles au-delà de g_H dans la dyade bidirectionnelle (g_AB, g_BA > 0) : battements, verrouillage ?

## 6. Prochaine étape

F-II.1 peut maintenant s'ouvrir sur des fondations analytiques : perméabilité dynamique (A-I2), écriture validée aux Kairos (A-I3), avec le contraste central *écriture continue vs écriture événementiellement validée* — et des questions précises : les Kairos déplacent-ils T*(g) (loi §3 recalculée), protègent-ils la résistance (g_H déplacé ?), créent-ils des quanta d'intégration ou une hystérésis relationnelle ? La loi d'appropriation fournit la référence exacte contre laquelle chaque mécanisme d'interface sera mesuré.

> L'extérieur ouvre un chemin ; l'intérieur peut l'ignorer, lui résister, ou se l'approprier — et lorsqu'il résiste trop près de sa limite, c'est la résistance elle-même qui, en oscillant, le fait basculer. Ce qu'il devient, dans tous les cas, reste son propre régime.

---

*Reproductibilité : `python fii01_resistance.py` ; vérifications Hopf/RK4 dans l'historique du dépôt.*
