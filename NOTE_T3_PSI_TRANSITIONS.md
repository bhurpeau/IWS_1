# IWS — Note T-3 : Ψ comme objet central et théorie des transitions

**Objet.** Suite aux orientations post-T-2 : (0) amendement de portée (T-2.1) ; (A) promotion de Ψ au rang d'objet central — relation d'équivalence, coordonnée canonique, **résolution du problème inverse** (théorèmes de réalisation), invariants vs jauge, démonstration de synthèse « à la carte » ; (B) théorie des transitions — le Kairos réhabilité comme **opérateur de transport entre paysages dynamiques**, avec une surface de transition qui se révèle être elle-même un invariant de Ψ. Reproductibilité : `theory_psi.py`, `theory_transitions.py`, `output_theory/transitions_report.json`.

**Convention.** `[PROP]` démontré · `[PROP-num]` démontré modulo vérifications numériques d'inégalités · `[NUM]` fait expérimental (simulateur) · `[CONJ]` conjecture.

---

## 0. Amendement T-2.1 — portée des énoncés

1. Toute occurrence de « le seul canal possible » (et formulations voisines de R-2) est amendée en : **« dans cette classe axiomatique, l'histoire ne peut créer un état actif qu'en abaissant le rappel effectif sous le couplage. »** D'autres classes de systèmes produisent de l'activité auto-entretenue ; la nécessité démontrée est interne à 𝒦 × 𝒮.
2. R-2 est requalifiée : ce n'est pas un résultat de robustesse mais une **caractérisation par signatures pathologiques** — chaque axiome porte le régime qui apparaît quand on le retire (A2 → extinction ; saturation de σ → fuite ; A3 → surcharge ; A0 → dérive du repos). C'est le résultat principal de T-2 ; R-4 (robustesse) en est le complément.
3. Le principe est promu, avec sa portée : **Principe spectral (portée : classe 𝒦 × 𝒮).** *L'histoire n'agit que sur le spectre de la linéarisation : elle ne pousse pas, elle ne crée pas de dynamique — elle re-pondère la stabilité, et par là ce qui est tenable.* Chaîne : mémoire → spectre → stabilité → dynamique.

---

## Partie A — Ψ comme objet central

### A.1 Équivalence et coordonnée canonique `[PROP]`

Définition : (m, σ) ~ (m′, σ′) ssi ils induisent la même Ψ(u) = σ⁻¹(u)·m((α/β)u)/u sur leurs domaines appariés. Par R-0/R-1/R-3, **le portrait qualitatif sur Δ est une fonction de la classe [Ψ]** : nombre et positions (en u) des équilibres, motif de stabilité, ζ_min, diagramme de bifurcation en (ζ, u). La coordonnée naturelle de la théorie n'est pas x mais **u = σ(x)** — la coordonnée saturée, seule à être invariante de représentation. Les opérateurs deviennent secondaires : la théorie porte sur la géométrie de Ψ.

### A.2 Théorème de réalisation I (jauge σ fixée) `[PROP]`

*Soit σ ∈ 𝒮 et s(u) = σ⁻¹(u)/u (croissante de 1 à ∞ par convexité de σ⁻¹). Une fonction Ψ continue sur (0, u_max) avec Ψ(0⁺) = 1 est σ-réalisable dans 𝒦 ssi h := Ψ/s est non croissante et inf h > 0. Le m réalisant, m(θ) = h((β/α)θ), est alors unique sur l'ensemble atteignable.*

Conséquence : **la fibre au-dessus de [Ψ] est exactement paramétrée par le choix de la saturation σ** — c'est la jauge de la théorie.

### A.3 Théorème de réalisation II (problème inverse libre) `[PROP-num]`

*Soit Ψ ∈ C¹ avec Ψ(0⁺) = 1 et Ψ(u) → ∞ en u_max. Décomposons (log Ψ)′ en parties positive et négative et posons*

s*(u) = exp ∫₀ᵘ [(log Ψ)′]₊ ,  h*(u) = exp(−∫₀ᵘ [(log Ψ)′]₋).

*Alors s*·h* = Ψ, h* est non croissante avec h*(0) = 1, et Ψ est réalisable dès que la variation décroissante totale de log Ψ est finie (elle vaut −log m_∞) — modulo la condition de régularité u·s*(u) convexe, qui peut placer le représentant sur le bord de la classe (σ localement affine) sans altérer le motif de stabilité (vérifié).*

Le couple (h*, s*) est le **représentant à mémoire minimale** de [Ψ] : toute la partie croissante de Ψ est portée par la saturation, la mémoire ne porte que la décroissance irréductible. Remarque : pour une Ψ unimodale, ce représentant vérifie **m_∞ = ζ_min** — le plancher de mémoire coïncide avec la frontière de bistabilité.

### A.4 Invariants et jauge `[PROP]`

| Invariants de [Ψ] | Dépendants de jauge (σ) |
|---|---|
| positions u des équilibres, leur nombre | positions x = σ⁻¹(u), traces θ* |
| motif de stabilité (signe a₀ = signe Ψ′ ; RH automatique) | valeurs propres (taux), friction Γ* |
| ζ_min, diagramme (ζ, u), nœuds-cols | bassins d'attraction |
| **seuil de transition r_c = ζ_min/ζ (partie B)** | vitesses de transport, temporalité |

La « non-universalité des bassins » de T-2 §4 reçoit ainsi son statut exact : ce n'est pas un défaut d'universalité, c'est une **dépendance de jauge**. La dynamique qualitative est une fonction de [Ψ] ; la métrique temporelle et les bassins sont la jauge.

### A.5 Synthèse « à la carte » (démonstration) `[NUM]`

Cible prescrite : Ψ(u) = e^{−au}/(1−u), a = 2.51 — donc u* = 1 − 1/a = 0.6016 et ζ_min = a·e^{1−a} = **0.5545** prescrits à l'avance. Factorisation canonique en formes closes : s* = 1 puis ((1−u*)/(1−u))e^{−a(u−u*)} ; h* = e^{−au}/(1−u) puis constante. Résultats (`theory_psi.py`) : reconstruction Ψ à **1.5·10⁻⁸** près ; ζ_min mesuré = 0.5545 ; racines prédites à ζ = 0.8 : u ∈ {0.1569, 0.8531} ; simulation du système synthétisé : extinction depuis x₀ = 0.05, **puits actif atteint à u = 0.8531 exactement** depuis x₀ = 0.5 et 3.0.

**Le problème inverse est résolu : IWS devient une théorie de synthèse.** On peut prescrire (ζ_min, u_s, m_∞) et fabriquer un opérateur qui les réalise — les invariants deviennent des paramètres de conception.

---

## Partie B — Théorie des transitions : le Kairos réhabilité

### B.1 Le bon objet : la surface d'existence des régimes `[PROP]`

Équilibre bipartitionné : blocs égaux (taille N/2), bloc 1 au puits +h*, bloc 2 en −h*, sur un graphe deux-blocs régulier (d_in, d_out). Par symétrie antipodale, chaque bloc voit le champ de voisinage r·h₁ avec

r = ρ_part = (1 + d_in − d_out)/(1 + d_in + d_out)  (valeur propre du mode de partition de Ã).

L'équation d'équilibre par bloc, en coordonnée canonique u = tanh(rx), devient **Ψ(u) = r·ζ** : *la structure bipartitionnée obéit à la même fonctionnelle universelle, avec un couplage effectif rζ*. D'où :

**La branche bipartitionnée existe ssi r > r_c := ζ_min/ζ — le seuil de transition est un invariant de Ψ.**

Valeurs ([P1], d = 2 diagonal) : ζ_min,₂ = 0.3986 ⇒ **r_c = 0.4982**. Vérifications : modèle réduit deux-blocs — fusion à r = 0.4382 et 0.4882, persistance à 0.5082 et 0.5582 (**seuil encadré à ±0.01**) ; réseau N = 20, Kairos OFF — fusion à r₀ = 0.25, persistance à r₀ = 0.75 et 0.80 (séparations 6.11 et 6.24). `[NUM]`

### B.2 Le Kairos comme opérateur de transport `[NUM]`

Bras décisif (r₀ = 0.25 < r_c) : Kairos OFF → **fusion** ; Kairos ON → les recâblages homophiles (les traces des blocs étant antipodales : similarité intra ≈ +1, inter ≈ −1, la règle retire des arêtes croisées et ajoute des arêtes internes) **transportent ρ_part à travers r_c en ~10 pas**, r atteint 0.92, et la bipartition survit (sép. 6.29).

C'est la formalisation exacte de l'intuition directrice : *les Kairos ne créent pas la différence ; ils déplacent le graphe à travers la surface d'existence du régime différencié.* La dynamique continue construit et stabilise les régimes (T-1) ; la classe fixe lesquels sont possibles (T-2) ; **les Kairos transportent le système entre les paysages où ces régimes existent** — et la frontière de ce transport, r_c, est elle-même invariante de représentation (A.4).

### B.3 La boucle d'ancrage/érosion et la bistabilité de régime `[NUM]`

Le suivi conjoint (r, cosinus croisé des traces, séparation) sur 3 graines × 2 graphes révèle la dynamique de second niveau :

- **Boucle de rétroaction** : capture d'un nœud par le bloc opposé → sa trace bascule → le cosinus croisé remonte de −1 par **pas quantifiés de 2/N_bloc = 0.2** (chaque pas = un nœud capturé) → l'homophilie perd son pouvoir discriminant → les recâblages réinjectent des arêtes croisées → r ↓ → la branche s'affaiblit → nouvelles captures. Sens inverse tout aussi auto-renforçant.
- **Plafond de saturation homophile** : la règle conservative m/m a une capacité finie (d_in ≤ N_bloc − 1) ; blocs saturés, les ajouts sont *forcés* vers l'autre bloc — c'est l'amorce structurelle de la boucle d'érosion. (Le graphe de départ d_in = 6 laisse 3 créneaux internes par nœud : il s'érode dans 2–3 graines sur 3 ; d_in = 4 en laisse 5 : il s'ancre dans 2 sur 3.)
- **Contingence** : à graphe et paramètres fixés, l'issue dépend de la graine (graine 5 : ancrage r ≈ 0.86–0.91 ; graine 13 : érosion r → 0.49) — l'historicité structurelle HS (P-7) se manifeste ici **au niveau des régimes** : la dynamique couplée (graphe, états) possède deux attracteurs de régime, {bipartition ancrée} et {homogénéisation}, départagés par l'ordre des événements.

### B.4 Relecture et conséquences

Le Kairos retrouve sa centralité, au bon endroit : non comme créateur d'événements spectaculaires, mais comme **le seul canal par lequel le système déplace sa propre surface d'existence des régimes** (dans le noyau, seul J modifie A, donc r). Les expériences gelées se relisent immédiatement dans ce cadre : X2 (homophile vs aléatoire) = transport dirigé vs marche non biaisée de r ; X3 (conservatif vs densifiant) = position du plafond de saturation ; X1 (endogène vs exogène) = couplage ou non du transport à la tension. Leur exécution devient une mesure de (Δr par événement, taux de capture) — les deux coordonnées de la boucle B.3.

### Registres

**Propositions** : A.1, A.2, A.4, B.1 `[PROP]` ; A.3 `[PROP-num]` (régularité de bord vérifiée, non démontrée en général).
**Faits** : A.5 (synthèse exacte), B.1 (encadrement ±0.01), B.2 (sauvetage par transport), B.3 (boucle, quantification 2/N_bloc, contingence).
**Questions ouvertes** : QO-16 stabilité transverse de la branche bipartitionnée hors du sous-espace antipodal (les vérifications sont dynamiques) ; QO-17 théorie quantitative de la boucle — critère d'ancrage vs érosion en fonction de (Δr/événement, taux de capture, marge r − r_c) ; QO-18 variantes de règle de recâblage repoussant le plafond homophile (et leur coût : densification, cf. D-03) ; QO-19 partitions non antipodales et asymétriques : Ψ(u) = rζ se généralise-t-elle en un système de contraintes Ψ(u_k) = (Σ r_{kl}·)ζ par cluster ? ; QO-20 caractérisation complète de la condition de régularité de A.3 (u·s* convexe).

### Où en est la théorie

Trois notes, trois objets emboîtés : **T-1** — ce que fait le noyau (bistabilité historique sur Δ) ; **T-2** — pourquoi cette forme (caractérisation de la classe par signatures pathologiques) ; **T-3** — de quoi la théorie parle vraiment : **les classes d'équivalence de Ψ, leurs invariants, et le transport événementiel entre les paysages qu'elles définissent.** Le programme de caractérisation demandé est en place : universel = [Ψ] ; spécifique = jauge ; transitions = déplacements de r à travers des surfaces qui sont elles-mêmes des invariants.

---

*Reproductibilité : `python theory_psi.py` (synthèse inverse), `python theory_transitions.py` (r_c, transport, boucle) ; diagnostics de B.3 dans le corps du script.*
