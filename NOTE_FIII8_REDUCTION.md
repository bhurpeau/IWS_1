# IWS — Note F-III.8 : Le théorème de réduction au contenu survivant

**Objet.** Deuxième pièce du chemin critique. Le résultat central de la mécanique des seuils cesse d'être l'équation b + δ = s\* et devient ce qu'il devait être : **la réduction de la réponse au contenu survivant** — Théorème III-9, avec sa preuve, dont III-5 n'est qu'un corollaire à commutation unique. Les vérifications rapportent quatre faits : la mesure *directe* de ω retombe sur s\* = 0.01627 sans passer par aucun préfixe ; la carte entière d'un système préfixé se *prédit* depuis ω et δ, cellule à cellule ; la courbe d'exigence s\*(T₂) est non monotone et **la sonde nue possède ses propres îles** ; et le mécanisme du témoin anti-monotone de F-III.4 est résolu — écriture croissante traversant une île de repos interne de ω (accord pointwise 10/10 là où le prédicat naïf faisait 5/10). Déclaration (𝔅, ρ) : histoires de cette note, bassin binaire. Reproductibilité : `fiii8_reduction.py`, `output_theory/fiii8_report.json`, figure `output_theory/fiii8_reduction.png` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

---

## 1. Le théorème et sa preuve

**Théorème III-9 (réduction au contenu survivant).** Soit 𝒫 une sonde admissible et ρ une résolution satisfaisant O1. Si, à la regraine, p = χ = θ = 0 (*régime d'extinction exacte*), alors il existe une fonction ω_{𝒫,ρ} telle que, pour tout système X de la famille,
ℛ_X^{ρ}(𝒫) = ω_{𝒫,ρ}(s⃗_regraine).
Pour une famille alignée (s⃗ = s·u₁), ω est une fonction d'une variable réelle. *Niveau de classe requis (F-III.7.1-R7) : classe admissible minimale — aucune stabilité par continuation n'est utilisée.*

*Preuve.* (i) Par A-H1, la regraine appartient au protocole : elle fixe (x, v) à la graine canonique indépendamment de l'état antérieur. (ii) Par hypothèse d'extinction, (p, χ, θ) = 0. L'état hybride complet au départ de la sonde est donc (x₀, 0, 0, 0, 0, s⃗) — fonction de s⃗ seul. (iii) Par O1, l'exécution Exec_𝒫 est une fonction déterministe de l'état initial ; donc Exec, et toute lecture ω_ρ(Exec), est une fonction de s⃗. ∎

La preuve tient en trois lignes *parce que* F-III.7 a payé le prix en amont : sans A-H1, l'étape (i) serait fausse ; sans O1 et le statut des lectures, l'étape (iii) serait informelle.

**Proposition III-9b (extinction approchée — énoncé, preuve différée).** Si les résidus vérifient ‖(p, χ, θ)‖ ≤ ε à la regraine, alors l'issue coïncide avec ω(s⃗) hors d'un voisinage η(ε) de ∂A_ω, sous transversalité du croisement (points de type C) ; **aucune borne uniforme n'est revendiquée au voisinage des changements de calendrier de la sonde (type K)**. Preuve et quantification : QO-74. (F-III.6-V2 en donne déjà une instance forte : à résidus ~10⁻⁵, la bascule est prédite à 10⁻⁵ près.)

## 2. Les corollaires

**C1 (l'équation de seuil, III-5 retrouvée).** Si un préfixe éteint écrit δ, alors s_regraine = s₀ + δ et issue = ω(s₀ + δ). Si ω n'a qu'une commutation s\* sur la plage parcourue, le seuil de la famille vérifie b + δ = s\*. **QO-65 est close** : la preuve formelle de III-5 est acquise, comme corollaire.

**C2 (structure générale des motifs).** Sans hypothèse de commutation unique, issue(s₀) = ω(s₀ + δ(s₀)) : tout motif non monotone provient soit (a) des **composantes multiples** de ∂A_ω, soit (b) d'une **écriture δ(s₀) non monotone** — et de rien d'autre. Les îles et l'anti-monotonie cessent d'être des anomalies : ce sont les deux termes d'une composition.

## 3. Les vérifications

**T1 — ω mesurée directement.** Sonde nue T₂ = 80, scan fin sur [2·10⁻⁴, 0.025] : **une seule commutation**, et s\*₈₀ = **0.01627** — la valeur que III-5 avait inférée à travers cinq cellules de calendrier et dix-sept préfixes retombe sur la sonde nue, sans aucun préfixe. Contrôle indépendant réussi.

**T3 — la prédiction par translation.** Pour deux préfixes éteints (T_am = 17.5 et 20.0), la carte entière du système préfixé est prédite par [s₀ + δ(s₀) ≥ s\*₈₀] — δ mesuré une fois par point, aucune sonde sur le système préfixé — et coïncide **cellule à cellule** avec la carte mesurée. Le théorème n'est pas une redescription : c'est une machine à prédire.

**T2 — la courbe d'exigence, et les îles de la sonde nue.** s\*(T₂) sur plage étendue [2·10⁻⁴, 0.06] : 60 → *aucune commutation* (stérile jusqu'à 0.06 : **QO-64 close quantitativement** — l'exigence de la sonde 60 excède tout contenu atteignable) ; 70 → 0.0251 ; 80 → 0.0163 ; 90 → 0.0155 ; 100 → 0.0131 ; 110 → 0.0153 ; 120–130 → 0.0037 ; 140 → *tout-approprié* (exigence sous la plage). La courbe est **non monotone**, et deux sondes présentent des **îles propres** : ω₉₀ une île d'appropriation isolée (~0.008), ω₁₁₀ une île de repos interne, cartographiée à **[0.01399, 0.01534]**. Les îles ne sont donc pas un artefact de composition avec un préfixe : *la sonde nue en a*. Lecture : la non-monotonie de s\*(T₂) et les îles sont la trace, dans le plan (s, T₂), de la stratification par calendriers **de la sonde elle-même** — le pendant sonde de C-III.4, et une conséquence directe de « toute sonde est déjà une histoire ». Honnêteté de tableau : les valeurs s\*(T₂) bisectées désignent *une* commutation, pas nécessairement la seule — la colonne de scan fait foi.

**T5 — le mécanisme de l'anti-monotonie, résolu.** Témoin de F-III.4 (amorce 10, oubli 150, sonde 110), fenêtre s₀ ∈ [0.0100, 0.0136] : l'écriture est **croissante** (s_total de 0.01317 à 0.01479), le prédicat naïf à commutation unique échoue (5/10), et l'évaluation pointwise ω₁₁₀(s_total) est exacte **10/10** : la fenêtre anti-monotone est exactement la traversée de l'île de repos [0.01399, 0.01534] par une écriture normale. Le témoin relève de l'option (a) de C2. **Le mécanisme de QO-62 est résolu sur le témoin**, et la question se reformule : QO-62′ — borner les composantes de ∂A_ω par sonde, et caractériser les profils d'écriture δ(s₀) ; toute anti-monotonie est un produit de ces deux inventaires.

## 4. Registres

**Théorème** : III-9 (réduction au contenu survivant, preuve §1, niveau de classe : minimale).
**Proposition** : III-9b (extinction approchée ; énoncé avec portée déclarée, preuve = QO-74).
**Corollaires** : C1 (III-5 démontrée — QO-65 close) ; C2 (dichotomie exhaustive des motifs non monotones).
**Faits** : s\*₈₀ = 0.01627 mesuré directement, commutation unique sur la plage ; prédiction par translation exacte cellule à cellule (deux préfixes) ; courbe d'exigence non monotone ; stérilité quantifiée de la sonde 60 et saturation de la sonde 140 ; îles propres de ω₉₀ et ω₁₁₀ (repos interne [0.01399, 0.01534]) ; anti-monotonie du témoin = écriture croissante × île interne (10/10 pointwise, naïf 5/10).
**Clôtures** : **QO-64** (quantitative), **QO-65** (III-5 démontrée par C1), mécanisme de **QO-62** sur le témoin (reformulée en QO-62′).
**Questions ouvertes** : **QO-74** version quantitative de III-9b (η(ε), transversalité aux C, absence de borne aux K) ; **QO-75** théorie de s\*(T₂, u, g, 𝒫) et des îles de ω — la stratification par calendriers de sonde (structure de ∂A_ω dans le plan (s, T₂) : branches, îles, et leur comptabilité par signatures) ; **QO-62′** (ci-dessus).

## 5. Où cela mène

Le centre du dispositif est maintenant démontré, pas seulement mesuré : *toute la naissance des seuils du régime de séparation passe par une fonction d'une variable, et cette fonction se mesure sur la sonde nue.* Troisième pièce du chemin critique : **F-III.9 — la frontière d'appropriation ∂A_𝒫 dans l'état lent complet** (p, χ, θ, s), ouverte comme convenu par la définition propre des horloges actives (z_i active pour (𝔅, ρ) ssi son ablation change ℛ^{𝔅,ρ}). Le théorème III-9 en décrit la section {p = χ = θ = 0} ; T2/T5 viennent d'en livrer la géométrie sur l'axe s (multi-composantes, îles) ; F-III.6-V4 en a déjà sondé les sections θ et p. Il reste à assembler l'objet — et c'est le sommet théorique annoncé du Tome III.

---

*Reproductibilité : `python fiii8_reduction.py` (T0 validation, T1 ω directe, T2 courbe d'exigence, T3 prédiction par translation, T5 mécanisme de l'anti-monotonie) ; consolidé : `output_theory/fiii8_report.json` ; figure : `output_theory/fiii8_reduction.png`.*
