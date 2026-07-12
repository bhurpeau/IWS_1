# IWS — Note F-II.0 : IWS ouvert. Axiomes de l'interface et première théorie de la dyade

**Objet.** Fondation du Tome II. Le noyau (Tome I : T-1, T-2, T-3) décrit comment un IWS *existe* ; ce chantier décrit comment il *vit* — en interaction. Conformément à l'orientation : d'abord des propriétés (axiomes d'interface), puis la plus petite dyade qui les satisfait, puis ses premiers théorèmes. Résultat central : **les couplages conformes aux axiomes agissent directement sur les invariants du Tome I** — le Tome II ne part pas de zéro, il hérite de toute la machinerie Ψ. Reproductibilité : `dyad_open.py`, `output_theory/dyad_report.json`.

**Charte du programme** (principe organisateur, adopté) : *un IWS n'est jamais défini par ce qu'il contient, mais par la manière dont il préserve sa cohérence tout en intégrant des interactions.* Tome I : comment une cohérence historique autonome apparaît (fait). Tome II : comment deux cohérences interagissent (ouvert ici). Tome III : comment apparaissent les trajectoires individuelles (inexistant).

---

## 1. Axiomes de l'interface

Chaque axiome est donné avec son engagement formel minimal — pas encore ses équations générales.

- **A-I1 (projection).** Un IWS ne perçoit jamais directement un autre système : tout couplage se factorise par une projection de l'*état* seul. B n'a jamais accès à τ_A, à M(τ_A), ni au graphe de A. **Conséquence structurelle : la mémoire est privée ; elle n'est transmissible que par ses effets sur les états.**
- **A-I2 (co-modification).** L'interface porte un état propre (perméabilité, trace d'exposition) modifié par ce qui la traverse. — C'est le module « peau » de [LD] ch. 3 ; le gel de la réduction [LD] → Core est **partiellement levé pour ce module**, différé à F-II.1.
- **A-I3 (intégration conditionnelle).** Une interaction n'est intégrée que si elle devient compatible avec la cohérence interne ; sinon elle est oubliée. Mécanisme candidat adopté pour F-II.1 : **les Kairos comme opérateurs d'intégration** — l'écriture externe dans τ n'est validée qu'aux événements (l'appropriation devient discrète : quantum d'intégration). Lien direct avec la trace sélective de [LD] différée par D-02.
- **A-I4 (conditionnement dyadique).** L'interaction n'entre *jamais* comme force sur H : elle s'écrit dans τ. C'est l'axiome A0 hissé au niveau de la relation, et l'extension du Principe spectral : **l'autre n'agit sur moi que par mon spectre.** Chaîne : extérieur → mémoire → géométrie → régimes → Kairos.

## 2. La dyade minimale

F-II.0 n'active que A-I1 et A-I4 (g constant, pas de gate — la version la plus dépouillée). Niveau Δ, d = 2, un nœud par système :

- ḣ_X = v_X ; v̇_X = −Γ(τ_X)v_X − M(τ_X)h_X + ζσ(h_X)
- **τ̇_B = ασ(h_B) + g·σ(h_A) − βτ_B** (et symétriquement pour A si g_AB > 0)

L'unique canal d'influence est l'écriture saturée de la projection de l'état de l'autre dans sa propre trace.

## 3. Résultats

### II-1 — Le monde ne pousse pas `[PROP]`
h_B = 0 est invariant sous toute influence conforme (A-I4 + A0 : M(τ)·0 = 0 et σ(0) = 0 quelle que soit τ_B). Mesuré : g = 0.4 (fort), ‖τ_B‖ monte à 4.62 ≫ τ_ign, ‖h_B‖ reste 0 exactement — **paysage chargé, état inerte**. L'extérieur ne peut que re-pondérer ce qui est tenable.

### II-2 — Déstabilisation mnésique `[PROP]`
Le repos de B devient linéairement instable ssi m(‖τ_B‖) < ζ, c'est-à-dire ‖τ_B‖ > **τ_ign = m⁻¹(ζ) = 0.3780** (paramètres [P1]). L'allumage par la mémoire seule est possible — non par poussée, mais par déstabilisation du repos.

### II-3 — Les trois réponses à l'influence : inertie, résistance, appropriation `[NUM]`
Sous contact permanent avec un A actif, il n'y a pas deux régimes mais **trois** :

| Régime | Condition | Comportement |
|---|---|---|
| **Inertie** | g < g_c = βτ_ign/‖σ(h_A)‖ = 0.0327 | charge sous le seuil ; rien |
| **Résistance** | g_c < g < g_ign ≈ 1.70·g_c = 0.0556 | B développe un petit état **antiparallèle** au drive (h_B = (−0.0071, −0.0071) à 1.1g_c) dont l'écriture négative épingle sa propre trace **exactement à la marge : m(‖τ_B‖) = 0.79999 = ζ** |
| **Appropriation** | g > g_ign | allumage vers le puits, approfondi par l'écriture externe (3.267 > 3.2468) |

La résistance est la découverte de cette note : **marginalité auto-organisée**. Mécanisme : la branche antiparallèle est une rétroaction *négative* par la trace (h_B < 0 réduit ‖τ_B‖, qui remonte m, qui rappelle h_B — stable), tandis que la branche parallèle est une rétroaction positive (fuite vers le puits). B neutralise l'influence par une contre-production interne calibrée au seuil près — la « résistance de l'intérieur » de [LD] reçoit un mécanisme, et une signature quantitative (le pinning m = ζ à 10⁻⁵ près).

### II-4 — Théorème d'appropriation (contact transitoire) `[NUM]`
Frontière dans (g, T), graine d'état 10⁻³, relaxation libre de 300 unités après découplage :
- g = 0.05 (zone de résistance) : **aucune durée n'approprie** — même T = 160 relapse après découplage : *exposition sans appropriation* ;
- g = 0.10 : T* ≈ 40 ; g ≥ 0.20 : T* ≈ 20 (plancher = temps de charge + croissance).

**Permanence** : après découplage long, ‖h_B‖ = **3.2468** — le puits *autonome* de B, pas une copie de l'état de A. L'appropriation en trois temps : **charge** (τ_B monte), **bascule** (m < ζ, le repos cède), **autonomisation** (B écrit désormais sa propre trace ; la charge externe peut disparaître). *Le paysage extérieur est devenu intérieur, matériellement : τ_B est désormais la production de B.* C'est la réponse — partielle mais précise — à la question directrice.

### II-5 — Compétition : translation exacte de α `[PROP + NUM]`
Paire antipodale (A en +puits, B en −puits) à couplage mutuel g : sur le sous-espace antipodal, σ(h_B) = −σ(h_A) donne la réduction **exacte** τ̇ = (α − g)σ(h) − βτ : la compétition est une translation α → α − g. D'où le seuil g_comp résolvant ζ_min((α−g)/β) = ζ : **g_comp = 0.3757**.
- Sous le seuil : coexistence, puits rétrécis prédits exactement (3.0904 prédit, 3.090 mesuré) ;
- Au-dessus : la branche antipodale disparaît. Issues : **extinction mutuelle** (symétrie exacte, vérifiée : les deux → 0) ou, génériquement, **conversion** — capture dans le même puits (vérifié : h_A = h_B = (2.342, 2.342)). *Au-delà du seuil, la compétition se résout par conversion, pas par destruction.*

### II-6 — Alliance : α + g `[PROP + NUM]`
Même direction : réduction exacte α_eff = α + g. **Stabilisation mutuelle = abaissement partagé de la frontière d'existence** : ζ_min passe de 0.3986 à 0.3772 (g = 0.2), et le puits s'approfondit — prédit 3.3116, mesuré 3.312 (le puits de conversion de II-5 est exactement le puits d'alliance).

## 4. Les cinq questions de la dyade — état des réponses

| Question | Réponse F-II.0 |
|---|---|
| Se synchroniser ? | Oui — conversion (II-5) et alliance (II-6), avec puits communs prédits exactement |
| Se stabiliser mutuellement ? | Oui, quantifié : abaissement partagé de ζ_min (II-6) |
| Entrer en compétition ? | Oui, avec seuil g_comp et trois issues : coexistence rétrécie / extinction symétrique / conversion générique (II-5) |
| Partager une mémoire ? | **Au sens strict, non — A-I1 rend la mémoire privée.** Mais l'alliance produit une mémoire commune *par contenu* (co-écriture convergente des traces), jamais *par accès*. Distinction structurelle du cadre. |
| Se spécialiser ? | Régime de coexistence sous g_comp ; les asymétries (g_AB ≠ g_BA, paramètres différents) sont le chantier suivant (QO-25) |

## 5. Registres

**Propositions** : II-1, II-2, réductions α_eff de II-5/II-6 `[PROP]` ; seuils g_c, g_comp `[PROP]` (formules) avec validations exactes.
**Faits** : triade inertie/résistance/appropriation, pinning m = ζ, g_ign ≈ 1.70g_c, frontière (g,T), permanence au puits autonome, conversion, puits prédits à 3–4 décimales.
**Questions ouvertes** : QO-21 théorie analytique de la branche de résistance (équilibre joint {m = ζ + O(h²), βτ = ασ(h) + gσ(h_A)} : existence, stabilité, disparition en g_ign — probablement accessible) ; QO-22 g_ign analytique (col entre branche de résistance et fuite) ; QO-23 dyade hors Δ (réseaux couplés ; A-I3 : intégration aux Kairos — F-II.1, avec dégel du module peau de [LD]) ; QO-24 mesure de la mémoire commune par contenu (convergence des traces sous alliance) ; QO-25 spécialisation par asymétrie ; QO-26 la résistance existe-t-elle dans toute la classe 𝒦×𝒮 (le pinning m = ζ n'utilise que A2 — conjecture : oui).

## 6. Où en est le programme

Le Tome II s'ouvre avec cinq seuils calculés (τ_ign, g_c, g_ign, g_comp, ζ_min(α_eff)), trois réductions exactes vers les invariants du Tome I, un phénomène propre (la résistance à marginalité auto-organisée), et une réponse opérationnelle à la question directrice : *un paysage extérieur devient intérieur par charge, bascule, autonomisation — sauf quand l'intérieur produit exactement de quoi rester au bord.* La suite naturelle : F-II.1 (interface vivante : A-I2 + A-I3, Kairos-intégration, dyade en réseau) — c'est là que la peau de [LD] rentre au bercail.

---

*Reproductibilité : `python dyad_open.py` ; diagnostics de la résistance et de la conversion dans l'historique du dépôt.*
