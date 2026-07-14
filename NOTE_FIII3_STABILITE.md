# IWS — Note F-III.3 : Stabilité de la structure d'observabilité sous accroissement du budget

**Objet.** F-III.2.1 a conditionné l'adoption du quotient comme espace du Tome III à une question : *la structure est-elle stable lorsqu'on enrichit la classe des histoires ?* Cette note pose le cadre exact (Prop. III-4), le réduit — sous une monotonicité vérifiée — à la stationnarité d'un ensemble de seuils sur la droite des contenus, mesure ce raffinement sur trois budgets emboîtés, et enregistre un fait qui tranche par l'exemple : **ℓ n'est pas un invariant absolu ; il dépend de la classe déclarée** (la paire inter-espèces passe de ℓ = 2 à ℓ = 1 quand on allonge les sondes de 130 à 140). Verdict aux budgets explorés : **pas de stationnarité** — le quotient reste un candidat, et l'objet robuste est la filtration elle-même (D-05). Reproductibilité : `fiii3_stabilite.py`, `output_theory/fiii3_report.json`, figure `output_theory/fiii3_stabilite.png` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

**Portée déclarée.** Budgets 𝔅₁ ⊂ 𝔅₂ ⊂ 𝔅₃ : sondes simples (u₁, G2, T₂), T₂ = 40…140 pas 10 (contrôle −u₁ inclus) ; puis une amorce (T_am ∈ {10, 20, 30, 40}, oubli 150) avant sonde ; puis deux amorces ({20, 40}², oubli 150 chacune). Population : la droite des contenus S(s), s ∈ [0.002, 0.0135]. Bisection à 1.1·10⁻⁵ ; dédoublonnage des seuils à 10⁻⁴.

---

## 1. Le cadre de la filtration (Proposition III-4)

Soit (𝔅_k) une filtration croissante d'histoires, ∼_k le noyau de ℛ restreinte à 𝔅_k, et ℓ_k la séparabilité au budget k.

**Proposition III-4.**
**(a) Monotonie et limite.** ∼₁ ⊇ ∼₂ ⊇ …, ℓ_k décroissante en k pour chaque paire, ∼ = ⋂_k ∼_k et ℓ = inf_k ℓ_k = lim ℓ_k. *(Immédiat : l'inf est pris sur un ensemble croissant.)*
**(b) Borne de raffinement — et sa limite épistémique.** Pour toute population finie P de systèmes, la suite des partitions P/∼_k est un raffinement monotone : elle compte au plus |P| − 1 scissions strictes. Mais **leurs positions dans la filtration ne sont pas bornées** : une partition constante sur les budgets k ∈ [k₀, K] peut se scinder en K + 1. Une stationnarité observée n'est donc jamais une preuve de stabilité — seule une borne structurelle (finitude d'index, cf. QO-59) peut clore la question. *(Preuve de la borne : chaque scission stricte diminue d'au moins 1 le nombre de systèmes par classe agrégée ; le reste est un contre-exemple générique.)*
**(c) Réduction aux seuils.** Si, sur une famille à un paramètre S(s), l'issue de chaque histoire ℋ est **monotone en s**, alors ℋ définit au plus un seuil b_ℋ, chaque classe de ∼_k est un **intervalle**, la partition au budget k est découpée par Θ_k = {b_ℋ : ℋ ∈ 𝔅_k}, et le quotient limite est la droite des contenus quotientée par l'adhérence de Θ_∞. **La stabilité de la structure équivaut alors à la stationnarité de Θ_k.** *(Immédiat une fois la monotonicité acquise — qui, elle, est un fait à établir, pas une évidence.)*

C'est le cadre de Nerode revisité : pour un automate fini, le raffinement de partition converge en un nombre d'étapes borné par l'index (Myhill–Nerode). Ici l'espace d'état est continu : **rien ne garantit un index fini**, et c'est toute la question.

## 2. La monotonicité (fait Y1) et sa portée

Six histoires-témoins (deux par niveau), huit points chacune : les motifs d'issue sont tous de la forme `…AAA` — **monotones en s, 6/6**. Contrôle : les sondes −u₁ ne présentent aucun seuil dans la plage (l'individuation par contenus alignés est unilatérale à ce budget). Statut : fait sur les témoins + hypothèse de travail pour la réduction (c) ; la monotonicité générale dans la classe d'axiomes est **QO-60** — un contre-exemple (contenus non alignés, lois non linéaires) casserait la structure d'intervalles, pas les propositions III-2/3/4.

Deux témoins méritent mention : (40, ; T₂ = 60) et (20, 20 ; T₂ = 60) sont *tout-repos* sur la plage — **davantage d'amorçage n'est pas davantage de facilitation** (les Kairos intermédiaires consomment la charge). Le raffinement n'est pas une simple translation de seuils vers le bas.

## 3. Le raffinement observé (Y2–Y3) : pas de stationnarité

| budget | histoires | seuils nouveaux | Θ cumulés → classes | écart min |
|---|---|---|---|---|
| 𝔅₁ | 11 (+11 contrôle −u₁) | 3 : {0.00372, 0.00463, 0.01315} | 3 → **4 classes** | 9.1·10⁻⁴ |
| 𝔅₂ | +44 | +6 : {0.00504, 0.00557, 0.00731, 0.00905, 0.00995, 0.01183} | 9 → **10 classes** | 4.0·10⁻⁴ |
| 𝔅₃ | +44 | +1 : {0.00657} | 10 → **11 classes** | 4.0·10⁻⁴ |

Lecture : (i) **le raffinement continue au niveau 3** — stationnarité observée : non ; le quotient aux budgets explorés n'est pas stable ; (ii) le seuil 0.00731 du niveau 2 est celui qui scinde la paire E1 (0.006 | 0.008) — cohérence exacte avec F-III.2 ; (iii) l'écart minimal entre seuils est divisé par deux au niveau 2 (0.00463 | 0.00504) — **compatible avec une accumulation, nullement conclusif** (Prop. III-4b interdit précisément de conclure) ; (iv) la décélération (3, +6, +1) est réelle mais peut refléter la géométrie particulière des préfixes choisis autant qu'une convergence. La figure `fiii3_stabilite.png` montre la partition en couches.

## 4. Le fait Y4 : ℓ est relatif à la classe déclarée — démonstration en acte

Dans la classe de sondes T₂ ≤ 140, la paire inter-espèces (𝒢_lin, 𝒢_sat) à (Ψ, s = 0) est séparée **au niveau 1** : témoin (T₂ = 140), lin → approprié, sat → repos. Or F-III.2 (X4) avait mesuré ℓ = 2 — dans la classe *déclarée alors*, T₂ ≤ 130. Les deux valeurs sont correctes, chacune dans sa classe : **ℓ(𝒢_lin, 𝒢_sat) = 2 pour 𝔅(T ≤ 130), = 1 pour 𝔅(T ≤ 140)** — la monotonie de la Prop. III-4a en acte, et la vindication empirique de R4 : *aucune valeur de ℓ n'est un invariant du couple de systèmes seul ; c'est un invariant du couple (systèmes, classe d'observation).* Mécanisme : à s = 0 le contenu ne dort pas — la sonde elle-même écrit dans s pendant qu'elle dure, et à T₂ = 140 la projection atteint la zone où lin et sat diffèrent au troisième ordre ; la sonde longue est déjà une petite histoire. Annotation rétroactive de F-III.2 §3 : la phrase « la strate 𝒢 est visible dès le niveau 2 » devient « dès le niveau 1, pour des sondes assez longues ».

## 5. Décision D-05 — l'objet officiel est la filtration

Puisque (i) le quotient à budget fixé n'est pas stationnaire aux budgets explorés, (ii) ℓ est démontré relatif à la classe, et (iii) la limite ∼ = ⋂ ∼_k existe toujours mais son index n'est pas contrôlé :

**D-05.** L'espace de travail officiel du Tome III est le **système projectif des quotients** (𝔛/∼_{𝔅_k})_k muni de ses cartes de raffinement — la filtration elle-même, dont tout quotient à budget fixé n'est qu'une coupe et dont la limite projective est l'objet idéal. Toute valeur de ℓ, toute classe, tout résumé s'énonce désormais **avec son budget en indice**. L'orientation « classes comme types » (F-III.2.1 R4) est adoptée *au niveau de la filtration* : un type est une classe stable sur un segment déclaré de budgets, et son adoption définitive reste conditionnée à QO-59.

Réversibilité : si QO-59 établit un index fini (Θ_∞ fini sur tout compact de contenus), le système projectif se stabilise, la limite devient effective, et D-05 dégénère en « l'espace du Tome III est le quotient limite » — la décision est construite pour être absorbée par sa propre résolution.

## 6. Registres

**Proposition** : III-4 (a monotonie/limite ; b borne de raffinement et limite épistémique ; c réduction aux seuils sous monotonicité).
**Faits** : monotonicité des issues en s sur 6/6 témoins ; aucun seuil sur −u₁ (niveau 1) ; Θ par niveau (3, +6, +1 ; 11 classes ; écart min 4·10⁻⁴) ; **non-stationnarité au budget 𝔅₃** ; non-monotonie de la facilitation en nombre d'amorces ; **relativité de ℓ à la classe** : ℓ(𝒢_lin, 𝒢_sat) = 2 (T ≤ 130) vs 1 (T ≤ 140), témoin T₂ = 140.
**Décision** : D-05 (l'objet officiel = la filtration des quotients ; budgets en indice partout).
**Questions ouvertes** : **QO-59** index du quotient limite — Θ_∞ est-il fini sur un compact de contenus, ou s'accumule-t-il (candidat : près des frontières de bassin) ? attaque proposée : zoom de bisection multi-échelle autour de la paire serrée {0.00463, 0.00504} avec des familles de préfixes denses ; **QO-60** monotonicité des issues en s dans la classe d'axiomes (preuve, ou contre-exemple hors alignement) ; **QO-61** caractériser les paires dont ℓ chute sous enrichissement (pourquoi la sonde longue suffit-elle ? lien avec l'écriture de la sonde dans s — « toute sonde est déjà une histoire »).

## 7. Où cela mène

La dernière pièce conceptuelle demandée est en place, sous sa forme honnête : le Tome III ne repose pas sur *un* espace mais sur une **filtration d'espaces**, dont la stabilité est désormais une question précise (QO-59) et non un implicite. Deux suites naturelles, par ordre de priorité proposée : **F-III.4 = attaque frontale de QO-59** (zoom multi-échelle sur Θ : soit une borne de finitude locale émerge, soit l'accumulation est mesurée — dans les deux cas le statut de la limite est fixé) ; puis QO-56 (plasticité de 𝒢), qui rouvrira la frontière espèce/individu avec, cette fois, l'espace qu'il faut pour l'énoncer.

---

*Reproductibilité : `python fiii3_stabilite.py` (Y0 validation, Y1–Y5) ; consolidé : `output_theory/fiii3_report.json` ; figure : `output_theory/fiii3_stabilite.png`.*
