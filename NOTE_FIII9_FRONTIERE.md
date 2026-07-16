# IWS — Note F-III.9 : La frontière d'appropriation dans l'état lent

**Objet.** Troisième pièce du chemin critique — le sommet annoncé du Tome III. Pour la sonde fil-rouge 𝒫 (u₁, G2, T₂ = 80, regraine canonique, relaxation 300) et ρ = bassin binaire, on définit sur l'état lent aligné z = (p, χ, θ, s) l'**ensemble d'appropriation** A_𝒫 = {z : ℛ_z(𝒫) = A} et sa frontière Σ_𝒫 = ∂A_𝒫, on démontre que z est un paramétrage **exact** de la réponse (Proposition III-10, par invariance du sous-espace aligné — la fermeture numérique fait 12/12 avec résidus hors-axe *nuls*), on cartographie trois sections de Σ_𝒫, on montre que les histoires réelles de F-III.6 vivent *sur* cette frontière (facilitation à 3·10⁻⁴ près, résidus ordonnés par χ), on classe l'activité des horloges aux trois niveaux, et l'on résout QO-69 : **l'anti-facilitation du témoin est une élévation locale de la frontière, prédite à −0.00076 contre −0.0006 mesuré.** Le théorème III-9 devient ce qu'il devait être : la section {p = χ = θ = 0} de Σ_𝒫. Déclaration (𝔅, ρ) : sondes de cette note, bassin binaire ; famille alignée. Reproductibilité : `fiii9_frontiere.py`, `output_theory/fiii9_report.json`, figure `output_theory/fiii9_frontiere.png` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

---

## 1. Définitions

**État lent aligné.** z = (p, χ, θ, s) ∈ ℝ₊ × ℝ³, injecté sur la graine canonique : (x, v) = regraine, θ⃗ = θ·u₁, χ⃗ = χ·u₁, s⃗ = s·u₁, ssc = 0.

**Ensemble d'appropriation et frontière.** A_𝒫^{𝔅,ρ} = {z : ℛ_z^{𝔅,ρ}(𝒫) = A} ; Σ_𝒫 = ∂A_𝒫. Aucune hypothèse de graphe : Σ_𝒫 peut avoir plusieurs nappes et A_𝒫 des composantes bornées — c'est un fait mesuré (§3).

**Activité d'une horloge (F-III.8.1-R8).** z_i est active **ponctuellement** en z si son ablation (z_i := 0) change l'issue en z ; **localement** si elle change la carte sur un voisinage déclaré ; **globalement sur 𝔅** si elle change au moins une réponse de la classe. Une cellule fragile n'est pas une variable structurante.

## 2. Proposition III-10 : l'état lent aligné est un paramétrage exact

**Proposition III-10.** Sur la famille alignée, ℛ_z^{ρ}(𝒫) = Ω̂_{𝒫,ρ}(p, χ, θ, s) exactement.

*Preuve.* (i) *Invariance du sous-espace aligné* : les équations du modèle sont symétriques sous l'échange des composantes, et toutes les entrées (graine, drive u₁, contenus) sont alignées ; le sous-espace {x₁ = x₂, v₁ = v₂, θ₁ = θ₂, χ₁ = χ₂, s₁ = s₂} est donc invariant par le flot et par les événements — les résidus hors-axe sont *identiquement nuls* (mesure W3 : 0.00e+00, sur douze états réels produits par histoires). (ii) *Inertie de ssc* : sous la loi 𝒢_lin, ssc n'apparaît dans aucune équation active — elle est comportementalement inerte. (iii) *Déterminisme* (O1). ∎ — Portée : famille alignée et loi 𝒢_lin déclarées ; hors alignement, Σ vit dans l'état vectoriel complet (QO-76) ; sous 𝒢 lisant ssc, (ii) tombe et ssc rejoint z.

**Vérification de fermeture (W3).** Douze états de regraine *réels* — histoires (T_am, D) couvrant tous les étages, D = 12 inclus — classés par l'état synthétique aligné : **12/12**. Les quatre coordonnées lentes suffisent à classer ce que les histoires produisent ; III-9 est bien la section {p = χ = θ = 0} de cet objet, et non un principe à part.

## 3. Trois sections de Σ_𝒫 (W1–W2)

**Section (θ, s), p = χ = 0.** La frontière plonge — facilitation forte : s_c passe de 0.01627 (θ = 0) à 0.00930 (θ = 0.10) ; à θ ≥ 0.125, la plage entière [2·10⁻⁴, 0.020] est appropriée. Et à θ = 0.100, la fibre est **multicomposante : une bande d'appropriation bornée [0.00930, 0.01873]** — au-dessus du bord supérieur, le repos revient. L'appropriation a, en ce point, un *plafond* : Σ_𝒫 possède une nappe supérieure. La zone θ ∈ [0.075, 0.125] est une **région de réorganisation** (vraisemblablement un changement de calendrier de la sonde en θ — QO-79) : la structure de fibre y est très sensible, cf. §5.

**Sections (χ, s) et (p, s).** Facilitation douce et monotone à cette résolution : s_c descend de 0.01627 à 0.01520 le long de χ ∈ [0, 0.03], et à ≈ 0.01460 le long de p ∈ [0, 1.2] — chaque horloge vivante abaisse l'exigence, aucune fibre multicomposante détectée sur ces axes.

## 4. Les histoires réelles vivent sur la frontière (W4)

Les dix-neuf points de la strate D ≥ 15 de F-III.6 (facilitation mesurée par familles de préfixes) sont posés sur la section (θ, s) : résidu médian **2.8·10⁻⁴**, maximum 9.3·10⁻⁴ — et les résidus sont *tous positifs et ordonnés par χ* (le pire : χ = 0.0149), exactement ce que la section (χ, s) prédit : la dispersion « inexpliquée » de F-III.6-V3 était la coordonnée χ de la surface. La facilitation n'est plus une courbe empirique : c'est la trace de Σ_𝒫, et ses résidus sont la profondeur de la nappe suivante.

## 5. QO-69 résolue : l'anti-facilitation est une élévation locale de la frontière (W6)

Le témoin anti-facilitant de F-III.6 (T_am = 5.5, D = 12) a pour coordonnées exactes z = (0.053, 0.0064, 0.1044, ·). La fibre de Σ_𝒫 en (p, χ, θ) du témoin est **simple mais élevée** : frontière à 0.01703 > s\* = 0.01627 — facilitation prédite **−0.00076**, mesurée en F-III.6 : **−0.0006**. Le mécanisme est identifié et quantitatif : dans la région de réorganisation, la frontière s_c(p, χ, θ) est non monotone en θ et peut monter au-dessus de s\* ; « anti-facilitation » = passage local de la frontière au-dessus de sa valeur d'extinction. Fait complémentaire et distinct : à p = χ = 0 exactement, la même région porte la bande bornée du §3 — de petites valeurs de p, χ suffisent à retourner la structure de fibre. Les deux faits ensemble délimitent QO-79.

## 6. L'échelle des horloges, relue comme géométrie (W5)

| point | z | issue | p | χ | θ |
|---|---|---|---|---|---|
| tardif | (0, 0, 0, 0.0160) | . | –– | –– | –– |
| θ-vivant | (0, 0, 0.12, 0.0110) | A | –– | –– | **P L** |
| χ-vivant | (0, 0.015, 0.05, 0.0125) | . | –– | –L | –L |
| profond | (0.6, 0.015, 0.10, 0.0100) | A | **P L** | **P L** | **P L** |

(P = ponctuelle, L = locale ; l'activité globale sur 𝔅 se lit dans les sections W1–W2.) Le principe P-III.6 reçoit sa forme géométrique : *une horloge est active là où Σ_𝒫 dépend de sa coordonnée* — l'échelle des résumés est le feuilletage de la frontière par les axes d'horloges.

## 7. Registres

**Proposition** : III-10 (paramétrage exact par l'état lent aligné ; preuve par invariance + inertie + déterminisme ; portée déclarée).
**Faits** : fermeture 12/12, résidus hors-axe identiquement nuls ; sections (θ, s), (χ, s), (p, s) cartographiées ; fibre multicomposante à θ = 0.10 (bande [0.00930, 0.01873] — nappe supérieure de Σ_𝒫) ; plage tout-appropriée à θ ≥ 0.125 ; facilitation douce monotone en χ et p ; les dix-neuf points réels de F-III.6 sur la section à 2.8·10⁻⁴ médian, résidus positifs ordonnés par χ ; fibre du témoin anti-facilitant simple et élevée (0.01703), facilitation prédite −0.00076 vs −0.0006 mesurée ; table d'activité des horloges aux étages successifs.
**Clôtures** : **QO-69 close** (mécanisme quantitatif de l'anti-facilitation) ; la dispersion résiduelle de F-III.6-V3 expliquée (coordonnée χ).
**Questions ouvertes** : **QO-76** hors alignement — Σ dans l'état vectoriel complet (directions de θ⃗, χ⃗, s⃗ non colinéaires ; c'est aussi la porte vers la mémoire directionnelle du Tome II) ; **QO-77** dérivation analytique de la section (θ, s) depuis le paysage M(θ) du Tome I (absorbe QO-68) ; **QO-78** les sections de Σ_𝒫 pour les sondes multicomposantes (110 : l'île de repos se déforme-t-elle continûment le long de θ ?) ; **QO-79** la région de réorganisation θ ∈ [0.075, 0.125] — cartographie 2D fine, appariement aux calendriers de la sonde, et raccord des nappes (le programme du chapitre 12 : les changements de calendrier raccordent les morceaux de surface).

## 8. Où cela mène — le chemin critique est parcouru

𝔅-axiomatique (F-III.7) → réduction démontrée (F-III.8) → **frontière dans l'état lent (F-III.9)** : les trois pièces déclarées bloquantes sont en place, et la quatrième (les horloges actives) est intégrée ici en définition et en table. Le point de convergence éditorial annoncé existe désormais comme objet : *la frontière d'appropriation, filtrée par les histoires (qui déposent z) et par les horloges (qui feuillettent Σ_𝒫), lue à la résolution choisie.* Les trois livres possibles n'en font plus qu'un. Restent, par ordre de valeur pour le tome : QO-79 (le raccord des nappes par calendriers — dernière pièce du chapitre 12), QO-74 (III-9b quantitative), puis la Partie V (QO-56, plasticité de 𝒢, dont le protocole est maintenant écrit d'avance : égaliser Ψ et z, comparer les Σ_𝒫, attribuer tout déplacement résiduel à 𝒢).

---

*Reproductibilité : `python fiii9_frontiere.py` (W0 validation, W1–W2 sections, W3 fermeture, W4 facilitation, W5 activité, W6 témoin) ; consolidé : `output_theory/fiii9_report.json` ; figure : `output_theory/fiii9_frontiere.png`.*

---

## 9. Amendement F-III.9.1 (post-relecture)

Les formulations suivantes **supersèdent** le corps de la note.

**R1 — Proposition III-10 renommée : « Suffisance de l'état lent aligné », avec son corollaire.** « Paramétrage » suggérait un système de coordonnées ; le résultat est plus fort : *sur la section de regraine alignée, l'histoire passée n'agit sur la sonde qu'à travers z*. Corollaire explicite : **z(X) = z(Y) ⟹ ℛ_X^ρ(𝒫) = ℛ_Y^ρ(𝒫)** — deux histoires produisant le même état lent sont indiscernables par la sonde déclarée. La fermeture 12/12 est la vérification expérimentale de ce quotient par z.

**R2 — Preuve et validation, registres séparés.** Démontré analytiquement : invariance du sous-espace aligné ; absence de ssc dans la loi active ; déterminisme. Vérifié numériquement : les histoires testées produisent des états alignés au niveau machine, et les douze états synthétiques reproduisent les douze issues. La nullité exacte des résidus vient de l'invariance mathématique ; la mesure confirme que l'implémentation la respecte — deux registres, jamais mélangés.

**R3 — Notation des branches.** s_c est réservée aux fibres à commutation unique. Dans les régions multicomposantes : Σ_θ = ∂A_θ, branches **s_c⁻(θ)** et **s_c⁺(θ)**. Conséquence conceptuelle actée : la facilitation n'est pas seulement l'abaissement d'un seuil inférieur — elle peut créer un **plafond d'appropriation** ; davantage de contenu n'est pas toujours préférable, même à état lent fixé. La figure est corrigée : la branche supérieure de la fibre θ = 0.10 apparaît désormais explicitement.

**R4 — Section, projection, résidu transverse (triptyque officiel).** Fixer une coordonnée donne une *section* ; oublier une coordonnée donne une *projection* ; afficher un point réel sur une section de référence donne un *résidu transverse*. W4 compare des histoires à χ ≠ 0 à la section χ = 0 : les résidus sont des résidus transverses — et une partie des anciennes « lois de strate » étaient des projections ou des comparaisons à une section, pas des frontières complètes. Formulation canonique enregistrée : **« un résidu systématique peut être la trace d'une dimension lente omise. »**

**R5 — P-III.6, version séparée.** Deux notions distinctes : la **structure géométrique** (Σ_𝒫 varie selon la coordonnée z_i — infinitésimale, ∂_{z_i}F ≠ 0 là où une représentation locale existe) et l'**activité décisionnelle** (l'ablation de z_i change l'issue ou la carte — opérationnelle). Elles coïncident près de la frontière, pas nécessairement loin d'elle (une frontière peut dépendre fortement de p sans que l'ablation de p ne change rien pour un point profond dans A_𝒫). Formulation exacte : *l'horloge structure la frontière lorsque Σ_𝒫 varie selon sa coordonnée ; elle est active en un point lorsque cette variation suffit à modifier la lecture choisie.*

**R6 — Table W5, notation lisible.** Codage officiel : **0** (inactive), **L** (locale seulement), **P+L** (ponctuelle et locale). La table du §6 se relit : tardif — p:0, χ:0, θ:0 ; θ-vivant — p:0, χ:0, θ:P+L ; χ-vivant — p:0, χ:L, θ:L ; profond — p:P+L, χ:P+L, θ:P+L.

**R7 — Portée de la clôture.** **QO-69 est close pour le témoin étudié et dans la famille alignée** ; d'autres mécanismes d'anti-facilitation ne sont pas exclus hors alignement ou sous une autre sonde. Le mécanisme de *ce* cas est identifié et quantifié.

**R8 — Programme adopté pour QO-79 (méthode calendrier par calendrier).** Pas de cartographie uniforme aveugle : (1) identifier la signature événementielle de part et d'autre ; (2) localiser la frontière de changement de calendrier ; (3) cartographier Σ_𝒫 à calendrier fixé ; (4) vérifier comment les nappes se terminent, se croisent ou se replient au raccord. Objet global visé : **Σ_𝒫 = ⋃_C Σ_{𝒫,C}**, chaque morceau associé à une cellule de calendrier — nappes supérieures et îles pouvant naître des repliements ou des raccords. C'est le programme de F-III.10.
