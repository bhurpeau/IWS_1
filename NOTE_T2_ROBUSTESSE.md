# IWS — Note T-2 : Pourquoi M(τ) ? Théorème de robustesse et nécessité structurelle

**Objet.** Réponse à la question posée après T-1 : « M(τ) est-il un choix parmi mille, ou pratiquement le seul opérateur raisonnable possédant extinction, activité, bistabilité, mémoire ? » La réponse tient en une phrase, démontrée en cinq volets : **la formule est un choix parmi une infinité ; la classe est une nécessité à quatre axiomes ; et dans la classe, le portrait qualitatif est rigide.** Vérifications : `theory_robustness.py` (16 opérateurs, lemmes de destruction, injection réseau), figure `output_theory/robustness.png`.

**Convention.** `[PROP]` démontré · `[PROP-num]` démontré modulo inégalités vérifiées numériquement · `[CONJ]` conjecture. Cadre : système réduit sur Δ, d = 1 (T-1 §1), trace saturée, paramètres (α, β, γ₀, γ₁) fixés, ζ < 1 sauf mention.

---

## 1. La classe axiomatisée

**Couplage 𝒮.** σ : ℝ₊ → ℝ₊ avec σ(0) = 0, σ′(0) = 1 (normalisation), σ strictement concave croissante, bornée (σ_∞ = u_max < ∞). La même σ écrit la trace (θ̇ = ασ(x) − βθ), donc l'ensemble atteignable de la trace est [0, (α/β)σ_∞].

**Opérateur 𝒦.** L'histoire agit par un préconditionneur : la force de rappel est −m(θ)x, avec :
- **(A0) conditionnement** : la force historique s'annule au repos — F(0, θ) = 0 pour tout θ ;
- **(A1) normalisation** : m(0) = 1 (sans histoire, rappel unitaire) ;
- **(A2) affaiblissement** : m non croissante (l'histoire relâche la contrainte, ne la resserre pas) ;
- **(A3) saturation de l'affaiblissement** : m_∞ = inf m > 0 (le rappel ne s'annule jamais), jointe à la bornitude de la trace atteignable (D-02).

La forme rationnelle de la spécification, m(θ) = (1+θ²)/(1+(1+λ)θ²), est un membre parmi d'autres. Autres membres testés : exponentiel, algébrique, logistique ; couplages testés : tanh, x/(1+x), erf, 2tanh(x/2).

## 2. R-0 — Réduction universelle `[PROP]`

Posons u = σ(x) ∈ (0, u_max) et **Ψ(u) := σ⁻¹(u)·m((α/β)u)/u**. Alors le résidu d'équilibre G(x) = m(θ(x))x − ζσ(x) s'écrit **G = u·(Ψ(u) − ζ)** : *tous* les équilibres non nuls sont les intersections de Ψ avec le niveau ζ, et sign G′(x) = sign Ψ′(u) aux racines. De plus Ψ(0⁺) = m(0)/σ′(0) = 1 et Ψ(u_max⁻) = +∞ (σ⁻¹ diverge).

**Conséquence structurelle : l'opérateur n'entre dans la structure d'équilibre que par le profil composé μ(u) = m((α/β)u).** Deux opérateurs de même profil composé sont indiscernables sur Δ. La forme fonctionnelle exacte est donc sans importance — première moitié de la réponse.

## 3. Théorème R — Universalité, nécessité, rigidité

### R-1 — Trichotomie universelle `[PROP]`

Pour tout (m, σ) ∈ 𝒦 × 𝒮, avec ζ_min[m, σ] := min_{(0,u_max)} Ψ :

1. **Extinction** : si ζ ≤ ζ_min et ζ < 1, l'origine est le seul équilibre (Ψ ≥ ζ_min ≥ ζ, croisement impossible sauf tangence).
2. **Bistabilité** : si ζ_min < ζ < 1, il existe un nombre pair ≥ 2 de racines (Ψ part de 1 > ζ et finit à +∞ > ζ) ; la plus petite a Ψ′ < 0 donc G′ < 0 donc a₀ = βG′ < 0 : **instable** ; la plus grande a Ψ′ > 0 : **stable** (par R-3). Sous unimodalité de Ψ, la paire est unique. En ζ = ζ_min : nœud-col générique.
3. **Activité forcée** : si ζ > 1, l'origine est instable (raideur 1 − ζσ′(0) = 1 − ζ < 0) et le nombre de racines est impair ≥ 1 (Ψ part sous le niveau).

L'origine est stable ssi ζ < 1, **pour tout membre de la classe** (la linéarisation en 0 ne voit que les normalisations A1 et σ′(0) = 1).

*Vérification :* 16/16 paires conformes ; motif de racines toujours [instable, stable] quand ζ_min < 0.8, zéro racine sinon ; la courbe ζ_min(λ) de T-1 est retrouvée par min Ψ à 10⁻⁴ près (écart max 0.0000).

### R-2 — Nécessité de chaque axiome (lemmes de destruction) `[PROP-num]`

Retirer un axiome ne dégrade pas la bistabilité : il la **remplace par un régime pathologique identifié**, à chaque fois différent.

- **(A2) retiré — l'histoire renforce ou n'agit pas.** Si m ≥ 1 sur l'ensemble atteignable (trace passive m ≡ 1, ou renforcement m croissante), alors Ψ(u) = (σ⁻¹(u)/u)·m > 1 > ζ pour u > 0 : extinction seule. Version pointue : *un état actif exige inf m < ζ sur l'atteignable* — **l'histoire doit pouvoir abaisser le rappel effectif sous le couplage ; c'est le seul canal d'apparition de l'activité dans cette classe.** [Vérifié : x₀ = 3 → 0 dans les deux cas.]
- **(𝒮) retiré — couplage non saturant (σ = identité).** Les équilibres non nuls exigent m(θ(x)) = ζ : au plus un point x_c, qui est un **répulseur** (en dessous m > ζ contracte, au-dessus m < ζ expulse) ; au-delà, fuite monotone — le confinement est perdu, aucun attracteur actif. **L'attracteur actif existe parce que le couplage sature tandis que le rappel affaibli ne s'annule pas.** [Vérifié : x_c = 0.1007 ; 0.9x_c → 0 ; 1.1x_c → fuite monotone, x(600) ≈ 60.]
- **(A3) retiré — rappel évanescent + trace non bornée.** Si m(θ) = o(1/θ) et la trace est linéaire (θ ~ (α/β)x), alors m(θ(x))x → 0 < ζσ(x) pour x grand : plus de racine supérieure. Argument de vitesse terminale : v ≈ δ/Γ(x) ∝ 1/x ⇒ **dérive x ~ √t sans équilibre** — c'est précisément le régime de *surcharge* (E2). [Vérifié : exposant log-log mesuré 0.497.] Corollaire : la définition positive uniforme du préconditionneur **et** la saturation de trace (décision D-02) sont les deux verrous structurels contre la surcharge — D-02 reçoit ici sa justification théorique définitive.
- **(A0) retiré** : voir R-5.

### R-3 — Rigidité : pas de Hopf sur Δ, dans toute la classe `[PROP]`

À tout équilibre non nul de tout membre : (i) m* − c = ζ(σ(x*)/x* − σ′(x*)) > 0 par stricte concavité de σ (la moyenne de σ′ sur [0, x*] excède sa valeur au bord) ; (ii) b = −m′(θ*)x* ≥ 0 par A2 ; donc

a₂a₁ − a₀ = Γ*²β + Γ*β² + Γ*(m* − c) + αbσ′(x*) > 0 automatiquement.

La condition croisée de Routh–Hurwitz **ne peut jamais être violée** : la stabilité de chaque branche est entièrement décidée par le signe de a₀ = β·G′(x*), c'est-à-dire par la géométrie de Ψ. Le portrait de phase sur Δ (d = 1) est rigide dans toute la classe : {origine, selle, nœud actif}, sans route oscillatoire. (La « fraction RH violée = 0.000 » de la carte T-1 cesse d'être une observation : c'est un théorème.)

### R-4 — Ouverture : la bistabilité est structurellement stable `[PROP]`

|Ψ₁(u) − Ψ₂(u)| = (σ⁻¹(u)/u)|m₁ − m₂|((α/β)u) : ζ_min est lipschitzien en m (uniformément sur tout compact évitant u_max) et continu en σ ; donc {(m, σ, ζ) : ζ_min < ζ < 1} est **ouvert**. Toute perturbation suffisamment petite de l'opérateur — ou du couplage — préserve la bistabilité, la paire nœud-col, et les stabilités (a₀ ≠ 0 persiste). *Réponse à la première branche de l'alternative : non, « toute perturbation raisonnable » ne détruit pas la bistabilité — elle est robuste, et c'est une force, pas une faiblesse, car la robustesse est confinée à une classe dont chaque axiome est nécessaire (R-2).*

### R-5 — Conditionnement vs forçage : la formalisation du « ciment » `[PROP]`

**Proposition.** F(0, θ) = 0 pour tout θ ⟺ l'état d'extinction existe pour *toute* histoire. Dans la classe conditionnante (A0), l'histoire n'agit que sur le spectre de la linéarisation — donc sur la **stabilité et l'accessibilité** des états — jamais sur l'**existence** du repos. Dans une classe forçante (F(0, θ) = f(θ) ≠ 0), le repos lui-même dérive avec l'histoire.

**Honnêteté requise :** un forçage additif sigmoïde peut aussi produire une bistabilité — la bistabilité *seule* ne discrimine pas le multiplicatif. Ce qui le discrimine est la **conjonction** : *repos indépendant de l'histoire* (A0) *+ activité rendue possible par l'histoire* (A2, seule voie d'apparition par R-2). Cette conjonction est la signature propre d'IWS.

C'est exactement le contenu mathématique de la phrase-ciment : *« une histoire n'est pas une force qui agit sur le système ; c'est une déformation durable de l'espace des états accessibles »*. Traduction : l'histoire entre par M(θ), qui fixe 0 (elle ne pousse pas) et re-pondère le spectre (elle rend tenable ce qui ne l'était pas — m(θ) < ζ ouvre le puits actif). La phrase n'est plus une interprétation plaquée : R-2(A2) affirme que dans cette classe **c'est le seul mécanisme possible d'apparition de l'activité**, et R-5 que c'est le seul qui laisse l'extinction invariante par l'histoire.

## 4. Ce qui n'est PAS universel

La séparation exacte entre structure (universelle) et quantités (spécifiques) :

1. **La position de la frontière.** ζ_min varie de 0.38 à 0.98 sur les 16 paires ; trois paires (σ à saturation lente × affaiblissement lent) sont en extinction à ζ = 0.8 — même trichotomie, frontière déplacée.
2. **Les bassins.** P(actif | h₀ ~ 𝒩(0, 0.6), d = 1) = 0.505 (rationnel) contre 0.215 (exponentiel) : l'allumage est une **course transitoire** entre la contraction rapide (taux ~ (1−ζ)) et la montée de la trace (ασ(x) vs pente de m près de 0) — le profil de m près de l'origine, invisible dans ζ_min, gouverne le bassin dynamique. Confirmé en réseau : avec l'opérateur exponentiel, les tirages standards s'effondrent majoritairement, **mais le puits prédit existe et est stable** : réseau initialisé au puits ‖h*‖ = 2.8334 → atteint à 4 décimales sur 3 graines (2.8331–2.8334), O6 ~ 10⁻⁸ décroissante.
3. **La multiplicité.** Sans unimodalité de Ψ (m en escalier lisse), plusieurs paires de racines sont admissibles : la classe autorise une multistabilité étagée — prédiction, pas défaut (QO-12).

D'où la conséquence pratique pour la spécification : le Core peut remplacer la forme rationnelle par tout m admissible sans toucher aux théorèmes ; les vrais paramètres d'étalonnage naturels deviennent **(ζ_min, x_s, taille de bassin)** — trois invariants au lieu d'une formule.

## 5. Réponse à la question posée

- **« Un choix parmi mille ? »** La formule rationnelle : oui — une parmi une infinité, toutes qualitativement équivalentes (R-0, R-1, R-4). Cela ne rend pas la théorie plus faible : cela la rend *indépendante d'un choix de représentation*, ce qui est le critère d'une bonne théorie.
- **« Ou le seul opérateur raisonnable ? »** La *classe*, oui, au sens fort : chacun des quatre axiomes est individuellement nécessaire — le retirer produit un régime pathologique nommable (extinction structurelle, fuite, surcharge, repos dérivant) — et à l'intérieur, le portrait est rigide (R-3 : pas même une bifurcation de Hopf n'est possible).

**M(τ) n'est ni un artifice ni un miracle : c'est le représentant générique d'une nécessité structurelle à quatre axiomes.** Le théorème de robustesse demandé existe et il est double : la bistabilité est *stable* dans la classe (R-4) et la classe est *minimale* (R-2).

## 6. Registres

**Propositions** : R-0, R-1, R-3, R-4, R-5 `[PROP]` ; R-2 `[PROP-num]` (les trois lemmes ont preuve + vérification ; l'argument de dérive √t est au niveau esquisse rigoureuse, exposant mesuré 0.497).
**Questions ouvertes** : QO-12 multistabilité étagée sous Ψ non unimodale (construction explicite + stabilité) ; QO-13 théorie des bassins — critère analytique de l'allumage dynamique (course (1−ζ) vs α·m′(0⁺), candidat à un second théorème quantitatif) ; QO-14 extension d > 1 : la sélection diagonale de T-1 n'utilise que b > 0 = A2 — **conjecture : « toutes composantes allumées » est universelle dans la classe** (indice réseau : le puits atteint par l'opérateur exponentiel est diagonal) ; QO-15 caractérisation complète de la classe forçante (au-delà de R-5).

## 7. Où cela mène

L'objet central de la théorie a changé deux fois : d'abord de l'individuation vers la cohérence (rapport X0/X4b), maintenant de l'opérateur vers la **classe**. L'Étape C (frontière de stabilité transverse) peut désormais être menée *au niveau de la classe* : le jacobien par mode J(ρ) de T-1 ne dépend de l'opérateur que par (m*, c, b, Γ*) — quatre scalaires évalués au puits. La carte des régimes cherchée sera donc, elle aussi, une carte de classe, paramétrée par les invariants (ζ_min, x_s, m*, b) plutôt que par (λ, k, …) : c'est la bonne monnaie d'échange entre la théorie et n'importe quelle instanciation future d'IWS.

---

*Reproductibilité : `python theory_robustness.py` (16 opérateurs, lemmes de destruction, injection réseau par monkeypatch de `_metric_action`) ; figure `output_theory/robustness.png` ; données `output_theory/robustness_report.json`.*
