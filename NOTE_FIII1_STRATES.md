# IWS — Note F-III.1 : Ruptures de compressibilité et les trois strates de l'individu

**Objet.** Suite directe de ta relecture de F-III.0 : adoption des reformulations (nom du théorème, programme, définition de l'individu), puis deux théorèmes-expériences qui réalisent tes points 4 et 6 — et montrent qu'ils sont le même point à deux strates. Reproductibilité : `fiii1_strates.py` + corrections consignées, `output_theory/fiii1_report.json`.

---

## 0. Adoptions

- III-1 est renommé : **Théorème de compression des histoires sous-critiques** (alias : *principe de suffisance mnésique*). Sa lecture positive est actée : il définit une classe entière d'histoires compressibles dans un état suffisant — et par là, il localise où la nouveauté ne peut pas naître.
- Le programme est reformulé : **le Tome III n'est pas une théorie générale de l'histoire ; c'est une théorie des ruptures de compressibilité.**
- La phrase du Tome III est adoptée : *une histoire ne transforme pas seulement l'état ; elle transforme l'espace des futurs possibles.*
- L'individu est redéfini : **ℛ_X : ℋ_futures → issues** — un opérateur sur les histoires, non une carte de stimuli. Et cette montée d'un cran n'est pas cosmétique : c'est un théorème (E1).
- La question du Tome III est adoptée : **« Quand deux intérieurs cessent-ils d'être interchangeables ? »**

## 1. E1 — L'individu répond à des histoires, pas à des stimuli `[NUM]`

**Construction.** Les seuils d'appropriation en s forment un ensemble discret {b_T} ; deux contenus dans un même intervalle sont invisibles à toute sonde simple. Paire retenue : s₁ = 0.006, s₂ = 0.008 — **cartes d'épisodes rigoureusement identiques** sur les 11 cellules T = 40…140 (motif commun [.....A.AAAA], y compris la cellule anomale à T = 90 héritée de la structure fine non monotone des bassins).

**Séparation.** L'histoire composée (amorce 20 u + oubli 150 + épisode 80 u) translate la paire sur un seuil :

| | individu s₁ = 0.006 | individu s₂ = 0.008 |
|---|---|---|
| tout épisode-test T = 40…140 | même issue, cellule à cellule | même issue |
| **histoire composée** | **repos** | **approprié** |

**Conséquence.** L'égalité des réponses à *tous* les épisodes-tests n'implique pas l'interchangeabilité : la carte de stimuli ne détermine pas l'opérateur. La définition ℛ_X : ℋ → issues est **strictement plus fine** que ℛ_X(u, g, T) — ton point 4, démontré. (Précision honnête : dans le modèle déterministe, états étendus égaux ⟹ opérateurs égaux ; E1 établit que des observations *complètes en épisodes* restent insuffisantes — l'individualité est un invariant d'opérateur, pas de carte.)

## 2. E2 — La troisième strate : la géométrie des transitions, formalisée `[NUM]`

Ton point 6 reçoit sa formalisation : l'individu a **trois strates** —

**X_individu = ( paysage [Ψ] , contenu mnésique s⃗ , loi d'action 𝒢 )**,

où 𝒢 : (s, χ) ↦ modulation des quanta est la règle A-I3 généralisée — *la manière dont la mémoire agit sur les transformations*. Expérience : deux lois de même pente à l'origine, 𝒢_lin(p) = c·p et 𝒢_sat(p) = c·s₀ tanh(p/s₀) :

- **cartes d'épisodes vierges identiques** sur la classe de sondes bornée déclarée (T = 40…130 : deux motifs vides) ;
- histoire cumulative (trois amorces) : **contenus mnésiques identiques à 10⁻⁴ (s = 0.0478 des deux côtés — la dynamique de s est la même)** ;
- et pourtant **Φ_ℋ diffère** : l'épisode final approprie sous 𝒢_lin (T_C = 70–90) et échoue sous 𝒢_sat.

**Même paysage, même mémoire — et deux devenirs.** L'individuation peut vivre dans la loi d'action, pas seulement dans le contenu ; et cette strate n'est observable que par des histoires cumulatives excédant le budget des sondes. D'où l'unification : tes points 4 et 6 sont le même théorème à deux strates — *l'opérateur voit ce que les cartes ne voient pas ; la strate 3 est ce que même les contenus ne portent pas.*

## 3. Taxonomie des histoires — premières définitions formelles

Équivalence de base : X₁ ~ X₂ ssi ℛ_{X₁} = ℛ_{X₂} sur toutes les histoires futures. Alors :

| Catégorie | Définition opérationnelle | Instance établie |
|---|---|---|
| **compressible** | Φ_ℋ(X₀) ~ (repos, s⃗) avec s⃗ donné par superposition | classe de III-1 (sous-critique, séparée, mémoire linéaire) |
| **conditionnelle** | contient un épisode dont l'issue de bassin dépend de l'état hérité | C = (u₁, 0.18, 100), F-III.0 §4 |
| **appropriante** | change le bassin autonome atteint | II-4 |
| **réversible** (dans une classe) | ∃ℋ′ : Φ_{ℋ′}Φ_ℋ(X) ~ X | l'annulation u puis −u ajustée ~ vierge (F-III.0 §5) |
| **génératrice d'individuation** | sépare deux états auparavant ~-équivalents | **l'histoire séparatrice d'E1** |
| **irréductible** | hors de toute classe compressible donnée (viole le test d'injection) | à construire (QO) |

Le véritable objet mathématique du Tome III est acté : **l'histoire elle-même**, munie de cette taxonomie — s⃗ n'est que le résumé des histoires compressibles.

## 4. Réponse opérationnelle à la question du Tome III

*Quand deux intérieurs cessent-ils d'être interchangeables ?* — **Quand une histoire les sépare au sens de ℛ.** Et nous savons désormais : construire des paires inséparables par épisodes (intervalles entre seuils), construire leurs histoires séparatrices (translation δ(ℋ) des contenus sur un seuil : condition ∃T, b_T ∈ (s₁, s₂) + δ(ℋ)), et exhiber une strate d'individualité que même l'égalité des contenus ne clôt pas (𝒢). Trois niveaux d'interchangeabilité, trois niveaux de rupture.

## 5. Registres

**Faits** : E1 (paire à cartes identiques séparée par une histoire) ; E2 (même paysage + même contenu + lois d'action distinctes ⟹ Φ_ℋ distincts, sous classe de sondes bornée déclarée) ; définitions taxonomiques instanciées.
**Questions ouvertes** : QO-52 géométrie des histoires séparatrices (l'ensemble {ℋ : δ(ℋ) sépare (s₁,s₂)} — sa structure, sa mesure) ; QO-53 hiérarchie d'observabilité (formaliser « invisible aux sondes de budget B » — les strates comme filtration) ; QO-54 critères effectifs de réversibilité et d'irréductibilité ; QO-55 axiomatique des lois d'action 𝒢 admissibles (le pendant Tome-III de la classe 𝒦×𝒮 — lien avec la loi canonique QO-47).

## 6. Où cela mène

Le Tome III a maintenant sa colonne vertébrale et ses trois résultats fondateurs : la **compression** (où la nouveauté ne peut pas naître), la **conditionnalité** (où l'ordre fabrique de l'irréversible), la **séparation** (quand deux intérieurs cessent d'être interchangeables — par contenu, ou plus profondément par loi d'action). La suite naturelle : QO-52/53 — caractériser les histoires génératrices d'individuation et la filtration des sondes, c'est-à-dire répondre non plus à « qu'est-ce qu'un individu ? » mais à **« combien d'histoire faut-il pour le voir ? »**

---

*Reproductibilité : `python fiii1_strates.py` (E1/E2 initiaux) ; corrections E1′/E2′ (paire à cartes exactement égales, classe de sondes bornée) consignées dans l'historique et `output_theory/fiii1_report.json`.*
