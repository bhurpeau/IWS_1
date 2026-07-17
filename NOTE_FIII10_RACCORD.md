# IWS — Note F-III.10 : Le raccord des nappes — et la dualité protocole/état

**Objet.** Exécution du programme F-III.9.1-R8 (calendrier par calendrier) sur la région de réorganisation θ ∈ [0.05, 0.15] du plan (θ, s), à p = χ = 0, sonde fil-rouge 80. Résultat principal, et c'est un **rectificatif au programme du chapitre 12** : la stratification par calendriers, démontrée à 100 % dans l'axe *protocole* (F-III.5 : chaque frontière de morceau de b(T_am) était un changement de calendrier), est **réfutée comme description exhaustive dans l'axe *état*** — ici, 74 % des transitions d'issue sont de type C strict (compte constant *et* dates dérivant de moins de 0.15 u), y compris toute la géométrie riche : la bande bornée, son plafond s_c⁺, et une **ligne entièrement morte à θ = 0.105**. Les nappes de Σ_𝒫 naissent de deux mécanismes distincts qui coexistent dans le même volume : des **raccords K** aux bords de cellules (26 %, dont la frontière élevée du témoin) et des **plis C** internes aux cellules. Déclaration (𝔅, ρ) : sondes de cette note, bassin binaire ; signature = calendrier chargé de la sonde (compte + dates, critère de saut 5 u identique à F-III.4). Reproductibilité : `fiii10_raccord.py`, `output_theory/fiii10_report.json`, figure `output_theory/fiii10_raccord.png` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

---

## 1. La carte (X1) : le calendrier est plat là où la géométrie est riche

Sur la grille 21 × 21, le compte n de Kairos chargés de la sonde est **quasi uniforme (n = 30) sur toute la moitié gauche** de la carte — précisément là où l'issue dessine sa structure la plus riche : la montée régulière de la frontière basse (θ ≤ 0.095), la **bande bornée** à θ = 0.100 (appropriation sur [~0.009, ~0.0187] seulement), la **ligne morte** à θ = 0.105 (fibre entièrement au repos, sur toute la plage de s), le retour partiel à θ = 0.110. Les cellules de calendrier ne commencent à se succéder rapidement (n : 29 → 37) que sur le flanc droit (θ ≥ 0.105, s croissant), où l'issue est déjà presque uniformément appropriée.

## 2. La classification (X2) : 26 % K, 74 % C stricts

Sur les 54 transitions d'issue de la grille, avec le critère de F-III.4 (K si le compte change *ou* si une date saute de plus de 5 u) : **14 K (26 %), toutes par compte ; 40 C stricts (74 %)**. Le raffinement de la signature aux dates ne requalifie *aucune* transition C : les dates dérivent de façon parfaitement continue (0.15 u au franchissement du plafond s_c⁺). La géométrie de Σ_𝒫 dans les directions d'état n'est donc pas, majoritairement, une géométrie de raccords combinatoires : c'est une géométrie de **plis de la fonctionnelle continue à calendrier fixé**.

## 3. Les terminaisons (X3) : les deux mécanismes, côte à côte

- **Le plafond s_c⁺ (θ = 0.10) est un pli C** : n = 30 des deux côtés, saut de date 0.15 u. Le « trop de contenu fait échouer » n'est pas une bifurcation de protocole — c'est la fonctionnelle qui redescend.
- **La bande se ferme par un pli** : présente à θ = 0.100, absente à θ = 0.105 — les branches s_c⁻ et s_c⁺ se rejoignent et la composante meurt quelque part dans ]0.100, 0.105[, à calendrier constant : une naissance/mort de composante de type fronce, entièrement C (localisation fine : QO-80).
- **La bascule tout-approprié à bas contenu est C** : à s = 0.002, l'issue bascule entre θ = 0.120 et 0.122 *à n = 29 constant*.
- **La colonne du témoin est K** : à (p = 0.053, χ = 0.0064, θ = 0.1044), la frontière élevée (0.015 → 0.016) coïncide exactement avec n : 30 → 29 — le mécanisme de l'anti-facilitation du témoin est bien un raccord de cellules, à quelques 10⁻² des plis C ci-dessus. Les deux mécanismes coexistent dans le même voisinage de l'état lent.

## 4. Le rectificatif, et la dualité

**Rectificatif à C-III.4 / programme du chapitre 12.** La conjecture de stratification est **démontrée dans l'axe protocole** (F-III.5 : coïncidence exacte morceaux ↔ cellules le long de T_am) et **réfutée comme description exhaustive dans l'axe état** (cette note : 74 % de plis C le long de θ et s). L'énoncé du chapitre 12 — « les changements de calendrier raccordent plusieurs morceaux de surface » — se corrige : *certains* raccords sont des changements de calendrier ; d'autres nappes, dont les plus spectaculaires (plafond, fronce, ligne morte), sont des plis internes. Σ_𝒫 = ⋃_C Σ_{𝒫,C} reste vrai comme partition, mais les frontières des nappes ne sont pas majoritairement aux bords des cellules.

**Conjecture C-III.10 (dualité protocole/état).** Dans la classe déclarée : les discontinuités de la géométrie de seuils le long des directions de **protocole** (durées, doses, composition des histoires) sont de type K — le calendrier s'y réorganise par crans ; le long des directions d'**état lent**, à protocole fixé, la frontière évolue par **plis C** de la fonctionnelle continue, les changements de calendrier y étant rares et non nécessaires aux nappes. C'est le prolongement naturel de la formulation de F-III.4 — *continue dans le contenu, combinatoire dans le protocole* — étendue de l'axe s à tout l'état lent, et désormais étayée des deux côtés (F-III.5 pour le protocole, F-III.10 pour l'état). Formulation canonique candidate : **« le calendrier découpe la frontière là où le protocole varie ; là où l'état varie, la frontière se plie toute seule. »**

## 5. Registres

**Faits** : compte n quasi uniforme (30) sur la moitié riche de la carte ; ligne morte θ = 0.105 (fibre au repos sur toute la plage, calendrier constant) ; bande bornée fermée par une fronce dans ]0.100, 0.105[ ; classification 14 K / 40 C stricts (aucune requalification par les dates, dérive ≤ 0.15 u aux plis) ; bascule tout-A à n constant ; frontière du témoin = raccord K exact (n : 30 → 29) ; montée rapide des cellules (29 → 37) sur le flanc droit.
**Rectificatif** : portée de C-III.4 et de l'énoncé du chapitre 12 (§4) — stratification vraie dans l'axe protocole, non exhaustive dans l'axe état.
**Conjecture** : C-III.10 (dualité protocole/état).
**Clôture partielle** : **QO-79** — la région de réorganisation est cartographiée et son organisation comprise (dualité K/C, les quatre terminaisons classées) ; reste ouverte la géométrie fine des plis.
**Questions ouvertes** : **QO-80** mécanisme dynamique des plis C — la ligne morte θ = 0.105 en premier (anti-résonance de l'efficacité des boosts en θ ? dérivation depuis M(θ), joint à QO-77) et localisation de la fronce ; **QO-81** test frontal de C-III.10 — un contre-exemple serait une discontinuité K le long d'une direction d'état pur à protocole fixé (chercher aux grandes valeurs de p, où le premier événement de la sonde peut apparaître/disparaître : candidat naturel de réfutation), ou un pli C le long d'une direction de protocole pur.

## 6. Où cela mène

Le chapitre 12 a maintenant sa forme vraie : la surface de commutation n'est pas un patchwork de morceaux raccordés par la seule combinatoire — c'est une **surface pliée, ponctuée de raccords**, et la part de chaque mécanisme dépend de la direction dans laquelle on la traverse. Suites naturelles, par ordre de valeur : **QO-81** (tester la dualité — une note courte, à fort pouvoir de réfutation, qui déciderait si C-III.10 entre au chapitre 12 comme théorème de structure ou comme heuristique) ; QO-80/QO-77 (la première dérivation analytique du tome, depuis le paysage M(θ) du Tome I) ; puis la Partie V (QO-56), inchangée dans la file.

---

*Reproductibilité : `python fiii10_raccord.py` (X0 validation, X1 carte, X2 classification K/C à signature complète, X3 terminaisons) ; consolidé : `output_theory/fiii10_report.json` ; figure : `output_theory/fiii10_raccord.png`.*
