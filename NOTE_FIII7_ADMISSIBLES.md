# IWS — Note F-III.7 : L'axiomatique des histoires admissibles et la double filtration

**Objet.** Première pièce du chemin critique validé (𝔅-axiomatique → réduction → frontière d'appropriation). Cette note fixe l'alphabet des épisodes, le statut des délais, le monoïde des histoires et sa convention de composition, les axiomes des classes admissibles et leurs graduations, la **double filtration** (budget d'histoires × résolution d'issue), la compatibilité exacte avec Nerode (avec le rectificatif de vocabulaire qu'elle impose à F-III.2), et la proposition d'ossature — la monotonie bidimensionnelle de l'observabilité. Elle apporte enfin l'instance numérique qui manquait à tout le dispositif : **l'axe ρ en acte** — un raffinement de lecture se substitue à un enrichissement d'action (ℓ passe de 2 à 1 sur la paire E1, à budget constant). Reproductibilité : `fiii7_admissibles.py`, `output_theory/fiii7_report.json` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹). La spécification suivie ici est celle de la relecture du plan (remarques « chemin critique ») ; les choix qui y étaient tranchés sont enregistrés comme décisions.

---

## 1. Alphabet des épisodes

L'espace des générateurs actifs est ℰ = 𝒰 × 𝒢 × 𝒯 × 𝔓, un épisode s'écrivant E = (u, g, T, 𝒫) : direction u dans un ensemble déclaré 𝒰 de directions admissibles ; gain g et durée T dans des intervalles déclarés bornés ; protocole 𝒫 dans une famille déclarée 𝔓. **Axiome A-H1 : les conditions de regraine appartiennent au protocole 𝒫, non à l'état du système.** Sans cet axiome, une même histoire changerait de sens selon l'initialisation de la sonde ; avec lui, l'histoire est un mot bien défini et l'état ne transporte que ce que le modèle lui donne.

## 2. Les délais comme générateurs (Décision D-06)

**D-06.** Les délais D_δ (δ ≥ 0) sont des **générateurs à part entière** de l'alphabet, non des attributs des épisodes. Motif : un délai n'est pas une absence d'action — il détermine quelles horloges restent actives à l'épisode suivant (c'est toute la substance de P-III.6 et du chapitre 11). L'alphabet complet est ℰ ∪ 𝒟.

## 3. Le monoïde et la convention de composition (Décision D-07)

𝔐 = ⟨ℰ ∪ 𝒟⟩ avec la concaténation et l'histoire vide ε. **D-07 (convention verrouillée) : Φ_{ℋ₁·ℋ₂} = Φ_{ℋ₂} ∘ Φ_{ℋ₁}** — l'écriture des histoires se lit chronologiquement de gauche à droite, la composition fonctionnelle s'inverse. Toute notation antérieure ou future s'interprète par cette convention, sans exception.

## 4. Exécutions et lectures : la résolution d'issue

Une histoire appliquée à X produit une **exécution** Exec_ℋ(X) (la trajectoire hybride complète, événements inclus), dont l'état final n'est qu'une projection. Une **résolution** ρ est la donnée d'un espace d'observation 𝒪_ρ et d'une lecture ω_ρ : Exec → 𝒪_ρ — définie sur l'exécution, non sur le seul état final, car des résolutions naturelles (classe de calendrier, nombre de Kairos, trajectoire échantillonnée) lisent le chemin. Exemples déclarés, du plus grossier au plus fin : bassin binaire ; identité de l'attracteur ; (bassin, nombre de Kairos chargés) ; signature vectorielle ; trajectoire échantillonnée. La réponse devient ℛ_X^{𝔅,ρ}(ℋ) = ω_ρ(Exec_ℋ(X)), et l'équivalence X ∼_{𝔅,ρ} Y ⟺ ℛ_X^{𝔅,ρ} = ℛ_Y^{𝔅,ρ}.

**Axiomes de cohérence de l'observation.** O1 (déterminisme) : l'issue à la résolution choisie est une fonction de (X, ℋ). O2 (invariance après relaxation) : pour les lectures d'état final de type bassin, la lecture est invariante par prolongation de la relaxation ; pour les lectures d'exécution, le segment lu est déclaré. O3 (compatibilité des résolutions) : si ρ₂ raffine ρ₁, il existe une projection π : 𝒪_{ρ₂} → 𝒪_{ρ₁} avec ω_{ρ₁} = π ∘ ω_{ρ₂}. O4 (compatibilité des budgets) : 𝔅₁ ⊆ 𝔅₂ induit la restriction des réponses.

## 5. Classes admissibles et graduations

Une classe d'observation 𝔅 ⊆ 𝔐 satisfait : **A-B1** ε ∈ 𝔅 ; **A-B2** tous les paramètres utilisés sont déclarés et mesurables ; **A-B3** la fermeture sous préfixes est imposée *lorsque l'analyse de Nerode l'exige* (cf. §7 et QO-71) ; **A-B4** chaque histoire de 𝔅 produit une exécution hybride bien définie ; **A-B5** la complexité est définie sur 𝔅. **Mise en garde structurelle : une classe à budget borné n'est généralement pas un sous-monoïde.** Le monoïde global est 𝔐 ; les budgets sont des sous-ensembles filtrants 𝔅₁ ⊆ 𝔅₂ ⊆ ⋯ ⊆ 𝔐.

Graduations déclarées : |ℋ|_ep (nombre d'épisodes), |ℋ|_dur (durée active), |ℋ|_dose (Σ g_k T_k), et la **complexité vectorielle** c⃗(ℋ) = (n_ep, T_actif, T_total, Q). Les budgets se définissent par ensembles inférieurs 𝔅_b⃗ = {ℋ : c⃗(ℋ) ⪯ b⃗}, ce qui évite d'imposer prématurément un coût scalaire ; une fonction scalaire c : 𝔐 → ℝ₊ n'intervient qu'ensuite, pour construire ℓ_c.

**Proposition III-8 (c-indépendance du quotient).** X ∼_{𝔅,ρ} Y dépend de 𝔅 et ρ, jamais de c ; ℓ_{c,𝔅,ρ}(X, Y) dépend des trois. *Preuve.* L'équivalence est l'égalité des réponses sur 𝔅 tout entier — c n'y figure pas ; ℓ est un infimum pondéré par c. ∎ La séparation dit *si* deux systèmes diffèrent ; la complexité dit *à quelle profondeur* — comparer les ultramétriques de différentes c (lacune du chapitre 6) est donc une question de géométrie, jamais de quotient.

## 6. La proposition d'ossature

**Proposition III-7 (monotonie bidimensionnelle de l'observabilité).** Si 𝔅₁ ⊆ 𝔅₂ et si ρ₂ raffine ρ₁, alors ∼_{𝔅₂,ρ₂} ⊆ ∼_{𝔅₁,ρ₁} : toute augmentation du budget d'histoires **ou** de la résolution des issues ne peut que scinder des classes, jamais les fusionner. *Preuve.* Égalité des réponses sur 𝔅₂ à résolution ρ₂ ⟹ égalité sur 𝔅₁ ⊆ 𝔅₂ ⟹ égalité des projections π ∘ ω_{ρ₂} = ω_{ρ₁} (O3). ∎

**Corollaire.** (𝔅, ρ) ↦ 𝔛/∼_{𝔅,ρ} est un **système inverse** sur le poset produit des budgets et des résolutions, avec les applications naturelles 𝔛/∼_{𝔅₂,ρ₂} → 𝔛/∼_{𝔅₁,ρ₁}. La « limite projective » est réservée à la formulation formelle ; en français : *un état limite est l'ensemble cohérent de toutes ses classes observées, à chaque niveau de budget et de résolution.* D-05 se reformule dans ce cadre : l'objet officiel du Tome III est ce système inverse — la double filtration en est le diagramme ordonné, pas une métaphore.

Formulation canonique enregistrée : **« ce que l'on peut faire vivre × ce que l'on choisit d'observer »** — et l'individualité observée dépend des deux.

*Note de numérotation : la relecture proposait « Proposition III-6 » ; l'indice est occupé par le principe P-III.6 (F-III.6). Numérotation adoptée ici : III-7 (monotonie), III-8 (c-indépendance) — arbitrage inverse possible sur demande.*

## 7. Compatibilité avec Nerode — et le rectificatif de vocabulaire

**Lemme III-7.1 (transport par quotient à gauche).** ℛ_{Φ_{ℋ₀}(X)}^{ρ}(ℋ) = ℛ_X^{ρ}(ℋ₀·ℋ) ; donc X ∼_{𝔅,ρ} Y ⟹ Φ_{ℋ₀}(X) ∼_{ℋ₀⁻¹𝔅, ρ} Φ_{ℋ₀}(Y), où ℋ₀⁻¹𝔅 = {ℋ : ℋ₀·ℋ ∈ 𝔅}. *L'équivalence complète* ∼_{𝔐,ρ} est une congruence à droite (ℋ₀⁻¹𝔐 = 𝔐) ; une équivalence restreinte ∼_{𝔅,ρ} **ne l'est pas nécessairement** quand 𝔅 n'est pas stable par préfixation — E1 en est précisément le témoin (F-III.2 §1, relu : ℋ₀⁻¹𝔅₁ ⊉ 𝔅₁).

**Rectificatif de vocabulaire à F-III.2.** Ce que F-III.2 appelait « quotient de Nerode » à budget fini se nomme désormais : **quotient de Nerode** = classe complète (𝔐, ρ) ; **quotient d'observation** = budget fini (𝔅, ρ) — une *approximation observationnelle* du premier ; **système projectif des quotients d'observation** = l'objet effectif du Tome III. Les énoncés de F-III.2 sont inchangés ; leur nommage est corrigé.

## 8. L'axe ρ en acte (U1–U2) : les deux axes sont substituables

Instance : la paire E1 (s = 0.006 vs 0.008), budget 𝔅₁ (sondes simples, ±u₁ × T₂ = 40…140), résolutions ρ_bin (bassin) et ρ_cal = (bassin, nombre de Kairos chargés de la phase active). Cartes ρ_bin : identiques (fait connu, ℓ_{𝔅,ρ_bin} = 2). Cartes ρ_cal : **séparées au niveau 1**, deux témoins — (+u₁, T₂ = 130) : A50 contre A51 ; (+u₁, T₂ = 140) : A57 contre A58 — un Kairos de plus pour le contenu le plus riche, à issue binaire égale. Donc **ℓ_{𝔅,ρ_cal} = 1**.

Mis en regard de F-III.3-Y4 (enrichir les sondes T ≤ 130 → T ≤ 140 fait chuter ℓ de 2 à 1 à résolution fixée), le tableau est complet : **les deux axes de la double filtration se substituent l'un à l'autre** — on peut voir plus en agissant plus, ou en lisant mieux. Corollaire structurel : Θ, les cellules et les classes sont désormais indexés Θ_{𝔅,ρ} — chaque résolution engendre son propre ensemble de commutation, et les Θ des notes antérieures sont les Θ_{·,ρ_bin}.

## 9. Registres

**Décisions** : D-06 (délais générateurs séparés) ; D-07 (convention de composition verrouillée) ; vocabulaire officiel Nerode/observation/système projectif (§7).
**Axiomes** : A-H1 (regraine ∈ protocole) ; A-B1–A-B5 (classes admissibles) ; O1–O4 (cohérence de l'observation).
**Propositions** : III-7 (monotonie bidimensionnelle, preuve §6) ; III-8 (c-indépendance du quotient, preuve §5) ; Lemme III-7.1 (transport par quotient à gauche).
**Faits** : séparation de la paire E1 au niveau 1 sous ρ_cal (témoins T₂ = 130, 140 ; comptes 50/51 et 57/58) ; ℓ_{𝔅,ρ_cal} = 1 contre ℓ_{𝔅,ρ_bin} = 2 ; substituabilité démontrée des deux axes.
**Rectificatif** : vocabulaire de F-III.2 (§7).
**Questions ouvertes** : **QO-71** caractériser exactement quand l'analyse exige la stabilité par préfixation (quels théorèmes du tome utilisent le transport III-7.1, et sur quels ℋ₀⁻¹𝔅) ; **QO-72** axiomatique fine des résolutions (lectures d'exécution vs lectures d'état ; mesurabilité de ω_ρ ; le Θ_{𝔅,ρ} des issues non binaires — les points de commutation d'une lecture à valeurs finies) ; **QO-73** audit de ré-indexation (tâche éditoriale : réécrire les énoncés de F-III.2 à F-III.6 avec l'indexation (𝔅, ρ) systématique — mécanique mais nécessaire au resserrement).

## 10. Où cela mène

La garde anti-essentialiste a maintenant son infrastructure : tout objet du Tome III porte ses deux indices, et ce qui dépend du modèle, de l'observateur, du budget et de la résolution est séparé par construction. Suite du chemin critique, conformément à l'ordre validé : **F-III.8 — le théorème de réduction au contenu survivant** : dans le régime d'extinction de (p, χ, θ), il existe ω_{𝒫,ρ}(s) telle que ℛ_X^{𝔅,ρ}(𝒫) = ω_{𝒫,ρ}(s_regraine) ; l'équation b + δ = s\* n'en est que le corollaire à commutation unique, et les îles comme l'anti-monotonie deviennent des composantes de ∂{s : ω(s) = appropriation}. La définition d'horloge active (désormais propre : z_i active pour (𝔅, ρ) ssi une ablation change ℛ^{𝔅,ρ}) sera intégrée en tête de F-III.9, comme convenu.

---

*Reproductibilité : `python fiii7_admissibles.py` (U0 validation, U1 cartes aux deux résolutions, U2 conséquence sur ℓ) ; consolidé : `output_theory/fiii7_report.json`.*

---

## 11. Amendement F-III.7.1 (post-relecture)

Les formulations suivantes **supersèdent** le corps de la note.

**R1 — « Lemme de transport par préfixe ».** Le Lemme III-7.1 est renommé ainsi, avec ℋ₀⁻¹𝔅 = {ℋ : ℋ₀·ℋ ∈ 𝔅} en tête d'énoncé ; « quotient à gauche » disparaît (risque de collision avec la terminologie des congruences latérales des monoïdes).

**R2 — Stabilité par continuation commune.** L'énoncé premier est désormais : *l'équivalence complète est stable par continuation commune* — la terminologie algébrique (« congruence à droite », relative à la convention D-07) n'apparaît qu'entre parenthèses, après coup.

**R3 — c-indépendance, version exacte (Prop. III-8 reformulée).** *À classe admissible 𝔅 fixée*, le quotient est indépendant de la mesure de complexité utilisée pour ordonner les histoires de 𝔅. Deux comparaisons distinctes : (i) même 𝔅, autre c → même quotient, autre géométrie ; (ii) budget *défini par* c (𝔅ᶜ_R = {c(ℋ) ≤ R}) → changer c change aussi la classe observée, donc potentiellement le quotient. La réserve rend le résultat exact.

**R4 — Substituabilité affaiblie en résultat local.** §8 : « les deux axes sont substituables » devient **« substituabilité locale démontrée sur la paire E1 »** (compensation observationnelle : une séparation peut, *ici*, être obtenue soit par enrichissement des actions, soit par raffinement de la lecture). Aucune équivalence générale ∀Δ𝔅 ∃Δρ n'est démontrée ni revendiquée.

**R5 — Les deux axes sont des posets, pas des chaînes.** Les budgets par ensembles inférieurs 𝔅_b⃗ sont partiellement ordonnés (davantage d'épisodes mais moins de dose : incomparables) ; les résolutions aussi (« ρ₂ raffine ρ₁ » est *défini* par l'existence de la factorisation π, les autres couples restant incomparables — nombre de Kairos, dose reçue, attracteur final, temps du premier événement sont typiquement incomparables deux à deux). Le système inverse vit sur le **poset produit multidimensionnel** ; toute suite 𝔅₁ ⊆ 𝔅₂ ⊆ ⋯ n'est qu'un *chemin choisi* dans ce poset — ne pas réifier un budget unique.

**R6 — « Profil observationnel cohérent ».** La glose de la limite projective devient : *un profil observationnel complet est une famille cohérente de classes à tous les niveaux de budget et de résolution.* « État limite » disparaît (risque de confusion entre état physique, classe comportementale et élément de la limite).

**R7 — Stratification de A-B3 : QO-71 close.** Trois niveaux remplacent la clause d'usage : (i) **classe admissible minimale** — ε ∈ 𝔅, paramètres déclarés, exécutions bien définies, lectures déterministes ; (ii) **classe préfixe-fermée** — ℋ₁·ℋ₂ ∈ 𝔅 ⟹ ℋ₁ ∈ 𝔅 (naturelle pour les budgets cumulatifs inférieurs) ; (iii) **classe stable par continuation** — requise pour la stabilité de l'équivalence sans changement de budget. Chaque théorème du tome annonce désormais le niveau dont il a besoin ; le résidu (annoter les théorèmes existants) rejoint l'audit QO-73.

**R8 — Lectures terminales et lectures de chemin.** Distinction nommée et officielle : une **lecture terminale** est invariante par prolongation de la relaxation (O2) ; une **lecture de chemin** dépend du segment observé et de son origine temporelle, qui font partie de la déclaration de ρ. Les deux familles n'ont pas les mêmes propriétés et ne doivent jamais être confondues.

**R9 — Convention éditoriale d'indexation.** Le couple (𝔅, ρ) est déclaré une fois par chapitre ou par expérience ; les indices sont ensuite omis tant qu'aucune ambiguïté n'est possible, et réapparaissent obligatoirement dans les énoncés comparatifs.

**Formulation canonique enregistrée** : **« distinguabilité = puissance d'intervention + puissance de lecture. »**
