# IWS — Note F-III.2 : Le quotient de Nerode d'un IWS. Congruence, ultramétrique de séparabilité, résumés suffisants

**Objet.** Donner à la relation X₁ ∼ X₂ ⟺ ℛ_{X₁} = ℛ_{X₂} son statut algébrique (congruence sur le monoïde des histoires), munir le quotient de sa géométrie naturelle (une **ultramétrique** de séparabilité — théorème, pas choix de modélisation), rendre décidable ligne à ligne le tableau des résumés suffisants, et trancher le statut de la loi d'action 𝒢 (décision D-04). Reproductibilité : `fiii2_quotient.py`, `output_theory/fiii2_report.json` ; intégrateur scalaire validé à l'identique contre la référence F-III.0 (P4 : ‖x_PC‖ = 3.246573235196, écart 0).

**Portée déclarée.** Tous les énoncés numériques sont relatifs à une classe d'histoires déclarée 𝔅 (grilles listées en §3) et à la résolution d'issue « bassin binaire » (‖x‖ > 1 après relaxation 300). Les propositions III-2 et III-3 sont, elles, exactes et indépendantes des grilles.

---

## 1. Le monoïde des histoires et la congruence (Proposition III-2)

Soit ℳ le monoïde des histoires (F-III.0 : concaténation, histoire vide pour neutre), avec la propriété de composition **(H-compo)** Φ_{ℋ₀·ℋ} = Φ_ℋ ∘ Φ_{ℋ₀}. La carte de réponses est ℛ_X : ℳ → issues, ℛ_X(ℋ) = issue(Φ_ℋ(X)), et ∼ est son noyau : X ∼ Y ⟺ ℛ_X = ℛ_Y.

**Proposition III-2 (congruence).** ∼ est invariante à droite : X ∼ Y ⟹ Φ_{ℋ₀}(X) ∼ Φ_{ℋ₀}(Y) pour toute ℋ₀ ∈ ℳ. Le monoïde agit donc sur le quotient 𝔛/∼ par [X]·ℋ := [Φ_ℋ(X)], et cette action est bien définie.

*Preuve.* Pour toute ℋ : issue(Φ_ℋ(Φ_{ℋ₀}(X))) = issue(Φ_{ℋ₀·ℋ}(X)) = ℛ_X(ℋ₀·ℋ) = ℛ_Y(ℋ₀·ℋ) = issue(Φ_ℋ(Φ_{ℋ₀}(Y))) par (H-compo) et X ∼ Y. ∎

C'est l'équivalence de **Nerode** transposée aux systèmes hybrides à mémoire : deux états sont équivalents si aucun futur ne les distingue ; les issues jouent le rôle des acceptations, les histoires celui des mots. **E1 reçoit ici sa forme algébrique** : l'équivalence ∼_gen définie par la seule restriction de ℛ aux générateurs (épisodes simples) n'est **pas** invariante à droite — la paire (s₁, s₂) = (0.006, 0.008) est ∼_gen-équivalente sur 𝔅₁ mais séparée après le préfixe ℋ₀ = (amorce 20u, oubli 150). Donc ∼_gen ⊋ ∼ strictement, et seule l'équivalence définie sur le monoïde entier porte une structure de quotient. Statut : instance démontrée dans la classe déclarée ; l'énoncé général « ℛ sur les générateurs ne détermine pas ℛ sur le monoïde engendré », pour les systèmes dynamiques observables, reste au registre des conjectures.

Relativisation : pour une classe déclarée 𝔅 ⊂ ℳ, on note ∼_𝔅 le noyau de ℛ restreinte à 𝔅 ; la filtration 𝔅₁ ⊂ 𝔅₂ ⊂ … donne ∼_{𝔅₁} ⊇ ∼_{𝔅₂} ⊇ … et ∼ = ⋂_𝔅 ∼_𝔅 (c'est le cadre formel de QO-53).

## 2. Séparabilité : le théorème ultramétrique (Proposition III-3)

Soit c : ℳ → ℝ₊ une mesure de complexité **quelconque** (nombre d'épisodes, durée active, dose…). La **séparabilité** est

ℓ_c(X, Y) = inf { c(ℋ) : ℋ ∈ 𝔅, ℛ_X(ℋ) ≠ ℛ_Y(ℋ) }   (inf ∅ = +∞),

et on pose d_c = e^{−ℓ_c}.

**Proposition III-3 (inégalité ultramétrique).** Pour tous X, Y, Z : ℓ_c(X, Z) ≥ min(ℓ_c(X, Y), ℓ_c(Y, Z)), donc **d_c(X, Z) ≤ max(d_c(X, Y), d_c(Y, Z))**. d_c est une pseudo-ultramétrique sur les systèmes, et une ultramétrique sur le quotient 𝔛/∼_𝔅 lorsque c est minorée sur 𝔅 (cas c = nombre d'épisodes : c ≥ 1).

*Preuve.* Si ℓ_c(X, Z) = ∞ il n'y a rien à montrer. Sinon, soit ℋ séparant X et Z avec c(ℋ) arbitrairement proche de ℓ_c(X, Z). Les trois issues ℛ_X(ℋ), ℛ_Y(ℋ), ℛ_Z(ℋ) ne peuvent être toutes égales ; ℛ_Y(ℋ) diffère donc d'au moins l'une des deux autres, et ℋ sépare (X, Y) ou (Y, Z) : min(ℓ_c(X,Y), ℓ_c(Y,Z)) ≤ c(ℋ). Passage à l'inf. Symétrie et d(X,X) = 0 sont immédiates ; sur le quotient, d = 0 ⟺ aucune histoire de 𝔅 ne sépare ⟺ même classe. ∎

La preuve n'utilise que le fait que ℛ_X est une **fonction** sur les histoires — trois lignes, mais la conséquence est structurelle : **le quotient d'un IWS n'est pas un espace métrique quelconque, c'est un espace ultramétrique.** Tout triangle y est isocèle à base courte ; deux boules sont emboîtées ou disjointes ; la géométrie du quotient est celle d'un **arbre** (dendrogramme), comme les espaces p-adiques ou les arbres phylogénétiques. L'intuition « géométrie complètement nouvelle » du quotient est donc identifiée et nommée : elle est **hiérarchique** — et c'est précisément ce qui rend cohérente la lecture de la taxonomie comme *hiérarchie des résumés suffisants* : la boule fermée de rayon e^{−k} autour de [X] est l'ensemble des classes indiscernables de X par toute histoire de complexité < k (correspondance boules ↔ résumés : conjecture précise en QO-58). Enfin, la filtration est monotone : 𝔅 ⊂ 𝔅′ ⟹ d_𝔅 ≤ d_{𝔅′} — grossir le budget d'observation ne peut que séparer davantage.

## 3. Numérique : le triplet fondateur et les deux paires de F-III.1

Grilles déclarées : sondes 𝔅₁ = {±u₁} × {T₂ = 40…140, pas 10} ; 𝔅₂ = 𝔅₁ ∪ {(amorce u₁, T_am ∈ {10,20,30,40}) · (oubli 150) · sonde de 𝔅₁}. Systèmes S(s) = repos + contenu s·u₁.

| | carte 𝔅₁ (+u₁ ; −u₁ tout « . ») | ℓ (épisodes) |
|---|---|---|
| a = S(0.006) | `.....A.AAAA` | ℓ(a,b) = **2** |
| b = S(0.008) | `.....A.AAAA` | ℓ(a,c) = **1** |
| c = S(0.012) | `.......AAAA` (+ A à T=140 sur −u₁) | ℓ(b,c) = **1** |

- **ℓ(a,b) = 2, avec témoin unique.** Sur toute 𝔅₂, une seule histoire sépare la paire E1 : (amorce 20u) · (oubli 150) · (épisode +u₁, 80u) — a → repos, b → approprié. C'est exactement l'histoire séparatrice de F-III.1, qui se révèle **minimale et unique dans la classe déclarée** (progrès direct sur QO-52 : l'ensemble séparateur de niveau 2 est un singleton).
- **Ultramétrique vérifiée, configuration isocèle** : d(a,b) = e⁻² < d(a,c) = d(b,c) = e⁻¹ — les trois inégalités fortes tiennent, deux avec égalité, la signature même de l'ultramétricité. Lecture en arbre : a et b cohabitent dans la boule de rayon e⁻¹ dont c est exclu.
- **La paire 𝒢 (E2) : ℓ(𝒢_lin, 𝒢_sat) = 2 — raffinement de F-III.1.** Cartes vierges identiques sur la classe bornée T ≤ 130 ; **une seule amorce** (41.9u, oubli 150) suffit ensuite : à l'épisode T₂ = 70, lin → approprié, sat → repos, avec des contenus mnésiques égaux à la précision de mesure (‖s‖ = 0.0252 des deux côtés). L'histoire cumulative longue de F-III.1 n'était pas nécessaire : la strate 𝒢 est visible dès le niveau 2. Deux « espèces » (cf. D-04) de mêmes paysage et contenu sont donc à distance e⁻² — la même distance que deux individus de contenus distincts (a, b) : la profondeur de la strate ne se lit pas dans d, elle se lit dans *ce qu'il faut égaliser* pour que la séparation subsiste.

## 4. Résumés suffisants : la ligne conditionnelle est testée

Méthodologie actée : la **suffisance** d'un résumé se démontre par injection (protocole III-1(b) : injecter le résumé dans un système vierge, comparer les signatures cellule à cellule), l'**insuffisance** par exhibition (protocole E1). Chaque ligne du tableau est donc décidable. Protocole déclaré pour ce test : avant toute sonde, χ := 0 et p := 0 (variables rapides et pression au repos — l'hypothèse même de III-1).

État de référence : l'état vrai post-histoire conditionnelle PC (F-III.0 P4, T_C = 100), dans le bassin approprié, s⃗_ref = (0.0295, 0.0295). Résumé candidat : (𝒜, s⃗) — l'attracteur autonome atteint (x*, θ* canoniques du puits, obtenus par relaxation autonome d'une graine forte) plus le contenu mnésique.

| état sondé | signature (+u₁ ; −u₁), T₂ = 40…140 pas 20 |
|---|---|
| référence PC | `AAAAAA` ; `......` |
| injection (𝒜, s⃗) | `AAAAAA` ; `......` — **identiques cellule à cellule** |
| s⃗ seul (bassin omis) | `..AAAA` ; `......` |
| 𝒜 seul (contenu omis) | `AAAAAA` ; `...AAA` |

**Résultat.** (𝒜, s⃗) est un résumé suffisant de l'histoire conditionnelle (instance), et le résumé est *minimal en ses deux composantes*, chacune portant une moitié identifiée de la signature : sans le bassin, la facilitation du puits manque (les sondes courtes +u₁ échouent) ; sans le contenu, **l'inhibition directionnelle manque** (les sondes −u₁ longues approprient alors qu'elles ne le devraient pas). Le tableau devient :

| classe | résumé suffisant | statut |
|---|---|---|
| compressible | s⃗ | théorème dans sa classe (III-1) |
| conditionnelle | (𝒜, s⃗) | **instance démontrée (X5), minimalité des deux composantes démontrée** |
| irréductible | l'histoire elle-même | définition |

Honnêteté de portée : la ligne conditionnelle est une instance (une histoire, une grille de sondes), pas encore un théorème de classe — la généralisation est le pendant « résumés » de QO-46.

## 5. Décision D-04 — statut de la loi d'action 𝒢

**Critère adopté : 𝒢 appartient à l'individu si et seulement s'il existe une histoire admissible qui le modifie.** Dans la classe d'axiomes actuelle, 𝒢 est figé par construction ; en conséquence :

- **𝒢 est un paramètre d'espèce** ; (Ψ, s⃗) définit un individu dans l'espèce ;
- E2/X4 se relit comme une comparaison **inter-espèces au même point** (Ψ, s⃗) — le fait mesuré est inchangé, sa légende est fixée ;
- la frontière espèce/individu est exactement la question de la **plasticité de 𝒢** (une histoire peut-elle modifier la loi d'action elle-même, et non plus seulement le contenu ?) — ouverte sous QO-56, et adossée à l'axiomatique QO-55 des lois admissibles.

Cette décision est réversible par le critère lui-même : si QO-56 exhibe une plasticité de 𝒢 dans une extension conforme, 𝒢 réintègre l'individu et E2 redevient une comparaison intra-espèce — sans rien changer aux faits.

## 6. Registres

**Propositions** : III-2 (congruence de Nerode, preuve §1) ; III-3 (inégalité ultramétrique pour toute mesure de complexité, preuve §2).
**Faits** : cartes et ℓ du triplet (ℓ(a,b) = 2 à témoin unique = l'histoire séparatrice de F-III.1 ; ℓ(a,c) = ℓ(b,c) = 1) ; ultramétrique vérifiée, triangle isocèle à base courte ; ℓ(𝒢_lin, 𝒢_sat) = 2 à contenus égaux (0.0252) ; suffisance exacte de (𝒜, s⃗) pour l'instance conditionnelle, avec nécessité démontrée de chaque composante.
**Décision** : D-04 (statut de 𝒢 : espèce, par critère de plasticité).
**Questions ouvertes** : QO-56 plasticité de 𝒢 (frontière espèce/individu ; lien QO-47/QO-55) ; QO-57 mesures de complexité continues (durée, dose) : l'infimum est-il atteint, d_durée sépare-t-elle encore le quotient, les distances induites sont-elles équivalentes ? ; QO-58 correspondance boules ↔ résumés (conjecture : toute boule fermée de rayon e^{−k} de (𝔛/∼_𝔅, d) est exactement une classe d'équivalence de résumé de complexité k — la taxonomie *est* la structure des boules) ; QO-52 mis à jour : l'ensemble séparateur minimal de la paire E1 est un singleton dans 𝔅₂ — sa géométrie hors classe déclarée reste ouverte.

## 7. Où cela mène

Le Tome III possède désormais son espace : **le quotient de Nerode muni de son ultramétrique de séparabilité** — un arbre, dont les attracteurs du Tome I habitent les classes, dont les histoires compressibles sont les flèches triviales, et dont les histoires séparatrices font changer de branche. Les trois questions des trois tomes se referment en une seule phrase : un intérieur existe (I), s'ouvre (II), et se distingue — à une profondeur d'arbre mesurable en quantité d'histoire (III). Suite naturelle : F-III.3 — le **dendrogramme effectif** d'une petite population de systèmes (calcul de d sur toutes les paires, reconstruction de l'arbre, lecture des boules comme résumés — première attaque de QO-58), ou l'ouverture de QO-56 si la priorité est la frontière espèce/individu.

---

*Reproductibilité : `python fiii2_quotient.py` (X0 validation exacte contre F-III.0, X1–X5) ; résultats consolidés : `output_theory/fiii2_report.json`.*
