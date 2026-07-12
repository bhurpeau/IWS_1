# IWS — Note F-II.1.1 : Théorie du cycle événementiel de l'interface

**Objet.** Comprendre R2 avant d'ajouter quoi que ce soit, selon le programme fixé : (1) construire l'application de retour entre Kairos ; (2) séparer les seuils hybrides ; (3) expliquer les fenêtres de sommation par la phase de réception ; puis seulement (4) tester QO-34 avec une unique variable lente. Les quatre précisions préalables sont adoptées en tête. Reproductibilité : `fii11_cycle.py`, `output_theory/fii11_report.json`, vérifications complémentaires dans l'historique du dépôt.

---

## 0. Précisions adoptées

1. **Renommage.** La valeur 0.1632 n'est pas un g_c : c'est **g_app^{R2}(x₀ ; 𝒫)** — seuil d'appropriation pour une graine, un protocole, une cadence endogène et une interface donnés. g_c reste réservé au seuil transcritique R0/R1. Le véritable analogue local est g_F ci-dessous (stabilité hybride du repos), désormais calculé.
2. **A-I3 à moitié réalisé.** R2 implémente « l'écriture n'entre qu'aux événements », pas « elle n'est intégrée que si compatible » : le saut τ⁺ = τ⁻ + κ_Q χ⁻ valide sans critère. *Validation événementielle, pas encore conditionnelle* ; le tri est fait en aval, dynamiquement, par la résistance. Distinction actée pour la suite.
3. **« Bassins finement structurés, non ordonnés par l'amplitude de la graine »** remplace « entrelacés » — la propriété topologique reste à démontrer (QO-32 reformulée).
4. **Support persistant généralisé.** La conclusion de F-II.1 vaut *dans R2 minimal* ; la formulation générale est adoptée : pour qu'une exposition non appropriée laisse un après, elle doit modifier au moins une variable lente ou structurelle qui survit à la sollicitation — interface, graphe, trace lente, structure, ou monde couplé. La peau est le candidat naturel, non une nécessité logique exclusive.

## 1. L'application de retour 𝒫_g `[PROP]`

Au repos exact (x = 0, invariant par II-1), le sous-système (χ, p) est autonome et converge vers un **cycle événementiel** de période Δ(g) ; la trace reçoit alors l'échelle

τ_{n+1}⁺ = e^{−βΔ}τ_n⁺ + κ_Q χ⁻_* → **τ_∞ = κ_Q χ⁻_*/(1 − e^{−βΔ})**,

de moyenne temporelle exacte

**θ̄ = κ_Q χ⁻_*/(βΔ)** — *la charge continue équivalente est le débit de quanta divisé par l'oubli.*

Vérification (quatre valeurs de g) : prédit/mesuré 0.1293/0.1288, 0.2886/0.2885, **0.3953/0.3952**, 0.7216/0.7216. La carte complète 𝒫_g : (τ, χ, p, x, v)_n ↦ (·)_{n+1} est celle du programme ; près du repos, ses composantes (χ, p, τ) sont en forme close (exponentielles + transcendante pour Δ), et le bloc (x, v) est la monodromie linéaire sur la dent de scie τ(t) — c'est elle qui fournit g_F.

## 2. Les seuils séparés `[PROP + NUM]`

| Seuil | Valeur | Nature | Méthode |
|---|---|---|---|
| **g_K** | **0.03608** | apparition de l'activité événementielle soutenue | **formule close** : g_K = Θκ₃λ_χ/(κ_χ√2 w) |
| **g_F** | **0.0763** | perte de stabilité hybride du repos | multiplicateur de Floquet exact de la monodromie (x,v) sur le cycle |
| g_F^{qs} | 0.0760 | idem, critère moyenné θ̄ = θ_ign | quasi-statique — **quasi exact** (Δ ≈ 3–4 ≪ 1/β : le moyennage est légitime) |
| **g_app^{R2}(x₀;𝒫)** | 0.1632 | franchissement de bassin + persistance | protocolaire (graine standard) |
| **g_H^{R2}** | **> 0.30** | rupture de la résistance pulsée | rampe lente depuis l'attracteur pulsé : *aucune rupture jusqu'au plafond de rampe* |

Hiérarchie : **g_K < g_F < g_app^{R2} < g_H^{R2}** — cinq phénomènes, cinq objets, plus aucun « seuil d'appropriation » fourre-tout. Deux faits notables : (i) le critère moyenné capture g_F à 0.4 % près — le cycle est rapide devant la trace, la théorie continue reste le bon squelette ; (ii) **la quantification protège aussi la résistance** : la résistance pulsée survit au moins jusqu'à g = 0.30, contre g_H = 0.1285 en continu (facteur ≥ 2.3) — et son pinning persiste : à g = 0.12, m(√2θ̄) = 0.7976 ≈ ζ (marginalité auto-organisée, version pulsée, écart −0.0024 porté par l'amplitude x̄ = −0.064 conformément à la correction « asymptotique »).

## 3. Réceptivité temporelle : la théorie des fenêtres `[NUM]`

Scan fin (g = 0.18, T_sub = 41.9, D = 2 à 60 pas 2) :

```
D :  2 ......................................60
     [S.....SSSS....SSS....SSS......]
```

Bandes sommantes de période **≈ 14, à comparer à la période de la spirale du repos 2π/ω = 14.63** (ω² = (1−ζ) − γ₀²/4). Trois régimes de délai, avec leurs discriminants mesurés à l'arrivée de la seconde exposition :

1. **Mémoire de charge (D ≲ 10)** : p, χ, θ résiduels décident (à D = 2 : θ = 0.72 encore massif — sommation malgré une phase défavorable) ;
2. **Mémoire de phase (10 ≲ D ≲ 48)** : la charge est oubliée (θ < 0.12) ; sur toutes les cellules diagnostiquées, **sommation ssi la vitesse résiduelle v est positive** (dirigée vers la séparatrice) : D = 14, 20, 32, 44 (v > 0 : S) contre D = 8, 26, 38 (v < 0 : échec) ;
3. **Oubli (D ≳ 50)** : l'amplitude résiduelle passe sous le budget ln(1/x₀) de la loi d'appropriation — plus aucune bande.

La quantité pertinente est donc bien **T₂*(g, D, φ_D)** et non T₂*(g, D). La formulation demandée est acquise avec sa signature quantitative : *deux histoires ayant reçu la même dose totale produisent des devenirs différents parce que les expositions n'ont pas rencontré le système à la même phase de sa dynamique interne* — et cette phase a une période mesurable, celle de la spirale du repos. (Théorie analytique des bandes par perturbation de la carte : QO-37.)

## 4. QO-34 — L'amorçage d'interface, établi `[NUM]`

**Modèle** (le tien, à l'identique) : ṡ = ε_s(χ − s), ε_s = 0.005 ≪ λ_χ ; couplage κ_Q(s) = κ_Q(1 + c_s s), c_s = 8.

**Vérification d'oubli.** Après une amorce sous-critique (41.9 u) et un oubli de 300 u : |x| ~ 10⁻¹⁸, θ ~ 10⁻¹⁵, χ ~ 10⁻²⁸, p ~ 10⁻¹⁷ — **tout est revenu à la base, sauf s = 0.0095** (boost initial des quanta : +7.6 % seulement).

**Expérience décisive** (mêmes dynamiques des deux côtés, seule différence : s₀ = résidu ou 0 ; observable robuste à la phase : bandes d'appropriation en T₂ à g = 0.18) :

| | cellules appropriées (T₂ = 40…155) | première durée appropriante |
|---|---|---|
| s₀ = 0 | 17 / 24 | T₂ ≈ 75 |
| s₀ = 0.0095 | **24 / 24** | **T₂ ≤ 40** |

**T₂* < T₁*** : la première exposition n'a changé aucun bassin autonome, mais elle a durablement abaissé le coût d'une appropriation ultérieure — la définition expérimentale de l'amorçage d'interface est satisfaite. Le levier est frappant : un résidu de 0.0095 (7.6 % de boost initial) divise T₂* par ≈ 2, par recomposition — la tête d'avance porte sur la variable lente qui est le goulot, et chaque quantum agrandi accélère l'échelle qui agrandit les quanta.

**Dissociation structurante.** Le seuil *soutenu* est, lui, insensible au résidu (Δg_app = −0.0014) : en temps infini, s se recharge de toute façon.

> **La mémoire d'interface ne change pas ce qui est possible en temps infini ; elle change ce qui est accessible dans le temps d'une rencontre.**

C'est le premier effet, mesuré, d'une interaction qui demeure sans avoir été appropriée par l'intérieur — la « peau qui se souvient » a maintenant sa variable, son expérience et sa loi de levier.

## 5. Registres

**Propositions** : formule close de g_K ; loi d'échelle θ̄ = κ_Qχ⁻/(βΔ) (vérifiée à 10⁻⁴) ; quasi-exactitude du critère moyenné pour g_F `[PROP-num]`.
**Faits** : hiérarchie g_K < g_F < g_app^{R2} < g_H^{R2} ; pinning pulsé ; bandes de réceptivité de période 2π/ω ; discriminant sign(v) en régime de phase ; amorçage d'interface (T₂* < T₁*) avec dissociation fini/infini.
**Questions ouvertes** : QO-37 théorie analytique des bandes (perturbation de 𝒫_g à la phase φ — la règle sign(v) demande sa preuve) ; QO-38 g_H^{R2} exact au-delà de 0.30 (existe-t-il une rupture pulsée ?) ; QO-39 articulation s ↔ q (R1) : deux implémentations d'un même rôle, ou deux mémoires d'interface distinctes (amplitude vs gain de validation) ? ; QO-40 **habituation** : c_s < 0 donnerait une désensibilisation durable (T₂* > T₁*) — l'interface pourrait apprendre à ne plus intégrer ; prédiction riche et immédiatement testable ; QO-41 la validation *conditionnelle* de A-I3 (critère de compatibilité au saut) — maintenant que le cycle est compris, c'est la prochaine brique légitime.

## 6. La réconciliation des Tomes (formulation adoptée)

- Le **Tome I** décrit les paysages autonomes et leurs bassins ;
- le **Tome II** décrit comment l'interface transforme l'**amplitude** (R1 : g ↦ g_eff), la **temporalité** (R2 : continu ↦ quanta) et la **phase** (§3 : bandes de réceptivité) des influences qui donnent accès à ces bassins ;
- l'**appropriation** est un changement durable de bassin autonome ;
- l'**amorçage** est une modification durable de l'*accessibilité* des bassins sans changement immédiat de bassin — désormais établi (§4) ;
- l'**individuation** pourra être comprise comme la trajectoire composée de ces appropriations et amorçages successifs.

Et le chemin de traverse a ses trois conditions, chacune désormais mesurée :

> **un paysage qui l'autorise** (Ψ, r_c) **+ une fenêtre où il est accessible** (bandes de réceptivité, période 2π/ω) **+ une interface qui peut se souvenir de l'avoir entrevu** (s ; T₂* < T₁*).

---

*Reproductibilité : `python fii11_cycle.py` ; expérience d'amorçage isolée (mêmes dynamiques, seul s₀ diffère) consignée dans l'historique.*
