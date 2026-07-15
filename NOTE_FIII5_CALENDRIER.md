# IWS — Note F-III.5 : Le calendrier comme résumé — et l'équation de seuil

**Objet.** Tester la conjecture de la relecture de F-III.4 (« le calendrier est un résumé suffisant pour la naissance des seuils ») et, par la même occasion, C-III.4/QO-63. Résultat en trois temps : (1) **le zigzag de F-III.4 était un artefact d'échantillonnage** — la grille fine révèle cinq cellules propres indexées par le compte de calendrier n = 4…8, portant chacune une branche lisse de b ; (2) **C-III.4 est confirmée sur l'exemple** — les frontières de morceaux et de cellules coïncident exactement ; (3) et le résultat qui dépasse la question posée : **l'équation de seuil** b + δ = s\* = 0.01627, vérifiée à étendue nulle (< 10⁻⁵) sur dix-sept points de toutes les cellules — le résumé suffisant de la naissance des seuils n'est pas le calendrier, c'est **un scalaire, le contenu écrit δ**, et le calendrier est suffisant *parce qu'il détermine δ*. Reproductibilité : `fiii5_calendrier.py`, `output_theory/fiii5_report.json`, figure `output_theory/fiii5_calendrier.png` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

**Protocole déclaré.** Sonde fixe T₂ = 80 ; famille : une amorce T_am ∈ [13, 24] pas 0.25, oubli 150. Le calendrier pertinent d'un seuil est celui du préfixe **pris au seuil** (rejoué à s = b) : n (Kairos chargés, ‖χ‖ > 0.01), dates, charge totale Q, ‖θ‖ à la regraine. Cellule : n constant, dates sans saut > 3 u. Morceau : |Δb| < 1.5·10⁻³ entre points adjacents. δ = ‖s‖ après préfixe − b, mesuré à s = b.

---

## 1. La grille fine (W1) : le zigzag n'existait pas

À ΔT_am = 0.25, la fenêtre se décompose en **cinq cellules propres, n = 4, 5, 6, 7, 8**, le compte s'incrémentant d'exactement un par cellule quand T_am croît : [13.00, 13.50] (n=4), [14.75, 16.25] (n=5), [16.50, 19.00] (n=6), [19.25, 21.00] (n=7), [22.00, 23.00] (n=8) — séparées soit par des sauts internes, soit par des **trous** où b sort de la plage (points morts : b > plage ; saturations : b < plage — les branches continuent hors fenêtre de contenus, elles ne disparaissent pas). Chaque branche a le même profil : petite bosse d'entrée, puis descente quasi linéaire de pente ≈ −0.0047/u, identique d'une cellule à l'autre. Le « zigzag » de F-III.4-Z2b était l'aliasing d'une grille ΔT_am = 1 sur ces branches entrelacées ; les « quasi-plateaux 19/21/23 » étaient les extrémités droites des cellules n = 6, 7, 8, qui atteignent par coïncidence la même valeur b ≈ 0.0025. **Rectificatif à F-III.4 §3** : le vocabulaire « zigzag, quasi-plateaux revisités » est retiré ; la structure vraie est « branches par cellules, échantillonnées grossièrement ».

## 2. C-III.4 confirmée sur l'exemple (W2) : QO-63 est close

Frontières de morceaux de b : **{16.375, 19.125}**. Frontières de cellules de calendrier : **{16.375, 19.125}**. Coïncidence exacte dans les deux sens, sur toutes les frontières testables (les autres transitions de n sont cachées dans les trous, où le test est trivialement inaccessible). Dans les termes de la littérature DIB (F-III.4.1-R1) : les branches de b sont continuées à signature fixée et sautent aux changements de signature. **C-III.4 passe du statut de conjecture à celui de fait établi sur l'exemple** — sa version générale (toute famille continue de protocoles) reste conjecture, désormais bien étayée.

## 3. Le test de suffisance tel que posé (W3, W4) : vide par structure — honnêteté

Le test par récurrence (« deux cellules disjointes de même n portent-elles le même b ? ») est **inapplicable dans cette famille** : n est strictement croissant en T_am, aucune signature n'est jamais revisitée — zéro paire concordante, zéro discordante. Les préfixes composites de la sonde croisée (W4) sont tous morts dans la plage (deux amorces courtes écrivent moins qu'une longue — cohérent avec la non-monotonie de la facilitation, F-III.3). Tel que posé, le test ne pouvait donc ni confirmer ni réfuter. Ce constat d'impuissance est ce qui a forcé à chercher *ce que le calendrier détermine* — et a mené au résultat central.

## 4. L'équation de seuil (W5) — le résultat central

Indice déclencheur : **‖θ‖ = 0 à la regraine, partout**. Après l'oubli de 150 u, la trace (τ_θ ≈ 8 u), la charge χ (τ_χ = 5 u) et la pression sont mortes ; **seul s survit** (τ_s = 200 u). Le préfixe n'agit donc que par ce qu'il a écrit dans s. Mesure : sur dix-sept points couvrant les cinq cellules,

**b + δ(T_am, b) = s\* = 0.01627, à étendue 0.00000 (< 10⁻⁵), pendant que b varie de 0.01089.**

**Proposition III-5 (équation de seuil ; portée déclarée).** Dans le régime de séparation (oubli assez long pour tuer θ, χ, p ; assez court pour préserver s ; famille alignée sur u₁), le seuil de la famille est la ligne de niveau du contenu total au moment de la sonde : b = s\*(sonde) − δ(préfixe), où s\*(sonde) est un invariant de la sonde seule et δ le contenu écrit par le préfixe. *Statut : fait établi sur 17 points / 5 cellules ; l'énoncé général dans le régime déclaré est une proposition dont la preuve formelle (via III-1) est attendue courte — hors du régime (oubli court, θ survivant), l'équation à un scalaire doit tomber, et c'est une prédiction testable.*

**Conséquences.**
- **La réponse à la question posée, en plus fort.** Le résumé suffisant de la naissance des seuils n'est pas le calendrier : c'est **le scalaire δ**. Le calendrier est suffisant *en tant que déterminant de δ* : dans une cellule, δ croît continûment avec T_am (χ s'intègre dans s) et b descend en ligne de niveau ; à chaque Kairos supplémentaire, χ est consommé (χ → 0.2 χ), l'écriture ultérieure chute d'un cran, et b saute vers le haut. La chaîne de compression est complète : **histoire → calendrier → δ** — chaque flèche perd exactement ce qui ne compte pas.
- **C-III.4 n'est plus seulement confirmée : elle est expliquée.** Les cellules de calendrier sont les morceaux de continuité de δ ; les branches de b sont les lignes de niveau {δ = s\* − b}. La stratification de Θ par les signatures, dans ce régime, *est* la stratification de l'écriture mnésique.
- **La boucle avec III-1 se referme.** C'est le Théorème de compression au niveau des seuils : le préfixe sous-critique bien séparé est ℛ-équivalent à son écriture dans s — la naissance des seuils, dans ce régime, est entièrement mnésique.
- **QO-64 se réduit** à une propriété de s\* : la sonde 60 est stérile si s\*(60) excède ce que contenu + écriture peuvent atteindre dans la plage (test en une bisection, différé).

## 5. Registres

**Proposition** : III-5 (équation de seuil b + δ = s\*, portée déclarée ; preuve formelle attendue via III-1).
**Faits** : cinq cellules n = 4…8, incrément de un par cellule ; branches lisses de pente commune ≈ −0.0047/u avec bosse d'entrée ; trous = sorties de plage (points morts en haut, saturations en bas) ; coïncidence exacte morceaux ↔ cellules {16.375, 19.125} ; test de récurrence vide par structure ; composites morts dans la plage ; ‖θ‖ = 0 à la regraine partout ; **b + δ = 0.01627 à étendue < 10⁻⁵ sur 17 points**.
**Rectificatif à F-III.4** : « zigzag » et « quasi-plateaux revisités » retirés (artefact d'échantillonnage) ; la carte génératrice vraie est « branches par cellules de signature ».
**Clôtures** : **QO-63 close** (coïncidence exacte, C-III.4 établie sur l'exemple et expliquée par III-5).
**Questions ouvertes** : **QO-65** preuve formelle de III-5 dans le régime déclaré (dérivation depuis III-1 + séparation des échelles) et détermination de s\*(T₂) — qui absorbe QO-64 ; **QO-66** hors régime : oubli court (θ survivant à la regraine) — le résumé suffisant redevient-il vectoriel (θ, s), et l'équation de seuil devient-elle une surface de niveau dans le plan (θ, s) ? (prédiction : oui) ; **QO-67** le test de suffisance du calendrier dans une famille où les signatures peuvent se répéter (famille (T_am, D) à deux paramètres : même n sur des composantes disjointes ⟹ même δ ?).

## 6. Où cela mène

La question « le calendrier est-il un résumé suffisant ? » a reçu une réponse plus profonde qu'espéré : dans le régime de séparation, **tout ce qui naît d'un préfixe passe par un seul nombre**, et la combinatoire des calendriers est la comptabilité de ce nombre. Le graphe des calendriers (F-III.4.1-R3) se précise : ses sommets portent chacun une valeur d'écriture, ses arêtes K un décrément d'écriture — c'est un graphe *valué* par δ. Suites naturelles : **F-III.6 = QO-66** (sortir du régime de séparation : oubli court, résumé vectoriel — c'est aussi le chemin qui reconnecte au cahier des charges dual (s_sc, s⃗) de F-III.0) ou **QO-65** (la preuve formelle, qui consoliderait III-5 en théorème de régime). QO-56 (plasticité de 𝒢) toujours en file.

---

*Reproductibilité : `python fiii5_calendrier.py` (W0 validation, W1 grille fine, W2 morceaux/cellules, W3 récurrence, W4 composites, W5 équation de seuil) ; consolidé : `output_theory/fiii5_report.json` ; figure : `output_theory/fiii5_calendrier.png`.*
