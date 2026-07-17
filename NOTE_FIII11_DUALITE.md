# IWS — Note F-III.11 : Le test frontal de la dualité — et sa requalification

**Objet.** Exécution de QO-81 : tenter de casser C-III.10 (dualité protocole/état) par ses deux flancs, conformément au programme et à l'anticipation enregistrés (F-III.10.1-R10). Verdict : **la dichotomie est morte, mais pas du côté attendu.** Le candidat désigné de réfutation côté état — l'axe p aux grandes valeurs — échoue complètement (0 K sur 11 transitions, calendrier rigide jusqu'à p = 1.3 ≥ Θ_K) ; c'est le côté *protocole* qui cède : **trois transitions sur trois le long de la durée T₂ sont des plis C**, à exécution identique jusqu'à la coupure. C-III.10 est requalifiée en **C-III.10′** : la vraie ligne de partage n'est pas protocole/état — c'est *recomposition combinatoire de l'exécution* contre *déformation continue de l'état de coupure* — assortie d'une carte de propensions mesurées. Deux faits neufs en passant : des **micro-bandes d'appropriation le long de p** et un **plafond en pression** (retour au repos au-delà de p ≈ 1.25). Déclaration (𝔅, ρ) : sondes de cette note, bassin binaire ; état lent aligné ; critère K identique à F-III.4/F-III.10. Reproductibilité : `fiii11_dualite.py`, `output_theory/fiii11_report.json` ; intégrateur validé contre F-III.0 (écart < 10⁻⁹).

---

## 1. L'attaque côté état (Y1) : le candidat désigné échoue — et révèle des micro-bandes

Axe p ∈ [0, 1.3], trois colonnes s ∈ {0.0150, 0.0155, 0.0160}, sonde 80. Le compte de calendrier est **rigoureusement constant (n = 30) sur toute la plage**, y compris au-delà du seuil d'événement Θ_K = 1.25 : le premier Kairos *chargé* ne peut ni apparaître ni disparaître par p, car la charge χ met ~0.4 u à franchir le seuil de charge — la pression initiale déclenche au plus des événements *vides*, invisibles à la signature. Le candidat de réfutation était donc structurellement voué à l'échec, et c'est instructif : **la pression ne recompose pas l'exécution, elle la déphase** (dérives de dates ≤ 0.48 u). Les **11 transitions d'issue sont toutes C**.

Faits neufs : à s = 0.0150, la colonne montre `..............A.A.AAAAAAAA.` — des **micro-bandes** d'appropriation le long de p (fibres multicomposantes, toutes C) ; et aux trois s, un **retour au repos au-delà de p ≈ 1.25** : trop de pression initiale nuit — le troisième « plafond » du programme après ceux de θ et du contenu (QO-83).

## 2. L'attaque côté protocole (Y2) : la durée plie

Axe T₂ ∈ [78, 92] au pas 0.25, trois s ∈ {0.0157, 0.0159, 0.0161}. Les trois bascules d'issue tombent **strictement à l'intérieur d'une marche de n** (30 → 30, 31 → 31), dates communes identiques : **3/3 C sur un axe de protocole.** Le mécanisme est limpide et c'est le cœur de la note : à l'intérieur d'une marche, l'exécution de la sonde est *identique* jusqu'à la coupure du drive — allonger T₂ de 0.25 u ne change rien au calendrier, cela déplace continûment l'**état au moment de la coupure**, dont dépend la capture post-drive. **La durée-dans-une-marche est un paramètre d'état déguisé.** La prédiction de la relecture (« une variation de durée peut déplacer continûment une frontière sans changer le calendrier ») est vérifiée au premier essai.

## 3. La requalification (Y3) : C-III.10′ et la carte des propensions

| axe | nature | transitions K |
|---|---|---|
| T_am (composition du préfixe) — F-III.5 | protocole | 2/2 (100 %) |
| (θ, s) — F-III.10 | état | 14/54 (26 %) |
| p — Y1 | état | **0/11** |
| T₂ (durée dans une marche) — Y2 | protocole | **0/3** |

**C-III.10 est retirée** — cassée côté protocole, et son candidat de réfutation côté état invalidé. **C-III.10′ (requalification).** La ligne de partage n'est pas protocole/état : *une transition est K quand la direction parcourue **recompose la succession des événements** ; elle est C quand la direction **déforme continûment l'exécution** (état initial, phase, ou état de coupure) sans la recomposer.* Le contenu non tautologique est la **carte des propensions** : la composition du protocole recompose presque toujours (100 % observé) ; l'état recompose rarement (26 %, jamais via p) ; la durée à l'intérieur d'une marche jamais. La formulation canonique de F-III.10 §4 est retirée et remplacée : **« ce qui recompose l'exécution recoud la frontière ; ce qui la déforme la plie. »** — et « protocole/état » redevient ce qu'il était : une heuristique de propension, utile et désormais chiffrée.

## 4. Registres

**Faits** : calendrier rigide en p (n = 30 sur [0, 1.3], dérives ≤ 0.48 u ; mécanisme : la pression ne peut déclencher que des Kairos vides avant la charge de χ) ; 11/11 transitions C sur l'axe p ; micro-bandes d'appropriation le long de p ; **plafond en pression** (repos au-delà de p ≈ 1.25) ; 3/3 transitions C sur l'axe T₂, à l'intérieur des marches de n, dates communes identiques ; mécanisme de la durée = paramètre continu de l'état de coupure.
**Rectificatif** : **C-III.10 retirée**, remplacée par C-III.10′ (recomposition vs déformation, avec carte de propensions) ; formulation canonique de F-III.10 §4 remplacée.
**Clôture** : **QO-81 close** — la conjecture a été testée par ses deux flancs et requalifiée, exactement selon le programme.
**Questions ouvertes** : **QO-82** classification a priori des directions — prédire la propension K d'une direction sans scanner (critère candidat : la direction modifie-t-elle la succession des événements au premier ordre, ou seulement leurs dates et l'état de coupure ?) ; **QO-83** les plafonds et micro-bandes de l'axe p — mécanisme, et parenté avec la ligne morte et le plafond en θ (une même famille de plis « l'excès nuit » sur trois axes distincts : contenu, trace, pression — y a-t-il une explication unifiée par la position relative à la séparatrice ?) — à joindre à QO-80.

## 5. Où cela mène

Le chapitre 12 a maintenant sa conclusion stabilisée et testée : *une surface pliée à l'intérieur de cellules hybrides, ponctuellement recousue lorsque l'exécution se recompose* — avec la carte chiffrée de qui recompose et qui déforme. Trois notes consécutives ont porté sur la mécanique des seuils ; elle est mûre. Je recommande maintenant la **Partie V : F-III.12 = QO-56, la plasticité de 𝒢** — en attente depuis F-III.2 (D-04), et dont le protocole est écrit d'avance par F-III.9/F-III.10 : égaliser le paysage et l'état lent, comparer les frontières d'appropriation Σ_𝒫, attribuer tout déplacement résiduel à 𝒢 — en gardant la mise en garde du plan (un 𝒢 plastique est observationnellement équivalent à une variable lente cachée : la frontière espèce/individu pourrait être indécidable depuis ℛ seule, et ce serait alors *le* théorème du chapitre 13). QO-80/QO-77 (la dérivation analytique des plis) restent en réserve théorique.

---

*Reproductibilité : `python fiii11_dualite.py` (Y0 validation, Y1 axe p, Y2 axe T₂, Y3 propensions) ; consolidé : `output_theory/fiii11_report.json`.*
