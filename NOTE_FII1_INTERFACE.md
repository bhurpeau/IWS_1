# IWS — Note F-II.1 : La plus petite interface qui transforme une influence en histoire

**Objet.** Exécution de la feuille de route R0/R1/R2 avec la discipline convenue : un mécanisme à la fois, chaque mécanisme évalué par son déplacement des trois objets de référence **(g_c, g_H, T*(g))**. En tête : les quatre corrections de F-II.0.1, adoptées et — pour la première — complétées. Reproductibilité : `fii1_interface.py`, `fii1_addendum.py`, `output_theory/fii1_report.json`.

---

## 0. Corrections de F-II.0.1 (adoptées, et complétées)

**(a) Coefficient a₃ — correction exacte, et son achèvement.** Le terme oublié ½m″(τ_ign)(√2α/β)² = 5.512 domine complètement ζ/3 = 0.267 : **a₃ = 5.779**. Mais l'expansion cohérente de la branche à l'ordre (g−g_c)² exige aussi les termes croisés b₁δx = m″(2αw/β²)δx et b₂δ² = m″(w²/β²)δ² — et là, quasi-annulation remarquable : a₃c₁² + b₁c₁ + b₂ = 27.40 − 52.31 + 26.14 = 1.25, d'où

**x_res = −2.1774(g−g_c) + 0.3216(g−g_c)² + …**

vérifié : −0.0709 vs exact −0.0710 (2g_c), −0.1411 vs −0.1421 (3g_c). *C'est la quasi-annulation des trois termes d'ordre 2 qui explique la quasi-linéarité de la branche sur toute son étendue* — la loi linéaire n'était pas approchée par chance, elle est protégée par une compensation structurelle (dont l'origine générale — coïncidence des paramètres ou identité de la classe — est QO-31).

**(b) « Rupture », pas « mort ».** Adopté ; vérifié : à g = 0.145 > g_H, la racine résistante persiste (x = −0.2453) avec max Re = +0.0036 — la configuration existe encore, elle n'est plus tenable.

**(c) g_ign(x₀, θ₀, v₀ ; protocole).** Notation adoptée, et rendue vivante : à cible identique g = 0.10, l'exposition brutale ou en rampe courte (T = 20) **s'approprie** ; la rampe lente (T = 400) laisse B **résistant** — le transitoire adiabatique suit la branche résistante (stable jusqu'à g_H). *La montée progressive protège ; la soudaineté approprie.* La dépendance à l'histoire n'est pas une faiblesse de la notion : elle en est le contenu.

**(d) Définition par bassins.** Adoptée telle quelle : interaction appropriée ssi x₀ et y_T = Φ_g^T(x₀) appartiennent aux bassins de deux attracteurs autonomes distincts — généralisation immédiate aux attracteurs non ponctuels. La conclusion de F-II.0.1 est remplacée par ta formulation (fin de note).

## 1. R0 — Référence (rappel)

g_c = 0.0327 ; g_H = 0.1285 ; T*(g) : {0.08 : 31.7 ; 0.10 : 24.8 ; 0.15 : 17.9 ; 0.20 : 15.0 ; 0.30 : 12.3} ; zone résistante : jamais.

## 2. R1 — Perméabilité dynamique `[PROP + NUM]`

Modèle : q̇_B = ρ(1−q_B) − η q_B g w (ouverture au repos, usure par le trafic), l'écriture devenant q_B·g·σ(h_A). Un seul objet ajouté, deux paramètres.

**Structure analytique.** À l'équilibre q_∞ = ρ/(ρ+ηgw) : le couplage effectif **g_eff(g) = ρg/(ρ+ηgw) sature à ρ/(ηw)**. Tous les seuils quasi-statiques se transportent par g_eff :
- **g_c^{R1} = ρg_c⁰/(ρ − ηw g_c⁰)** si ρ > ηw g_c⁰, sinon *jamais* — condition de **protection absolue** : si ρ/(ηw) < g_c⁰, aucun contact soutenu, si intense soit-il, ne peut allumer B ;
- **g_H^{R1}** de même — et pour (ρ, η) = (0.05, 1) : g_eff sature à 0.0510 < g_H⁰ ⇒ **g_H^{R1} = jamais : la peau protège structurellement la résistance** — la rupture par Hopf devient inaccessible en amplitude. La question « la peau protège-t-elle la branche résistante ? » reçoit un oui *structurel*.

**Mesures** ((ρ, η) = (0.05, 1)) : g_c^{R1} formule 0.0913, dynamique 0.0863 (le transitoire à q(0) = 1 profite de la fenêtre initiale d'ouverture — bonus de 6 %, la peau ferme *après*) ; **T*(g)** : 24.8 → 88.9 (g = 0.10), 15.0 → 32.1 (0.20), 12.3 → 26.2 (0.30) — l'étranglement progressif de la charge allonge fortement la fenêtre critique.

**Réponses aux quatre questions R1** : déplace g_c ✓ (formule exacte) ; protège la résistance ✓ (structurellement) ; hystérésis d'ouverture/fermeture : **non pour cette loi d'usure** (q_∞ univoque en g) — une hystérésis exigerait une loi à seuil ou une usure cumulative (χ-dépendante), QO-33 ; transforme T*(g) ✓ (tableau).

## 3. R2 — Validation événementielle `[NUM]`

Modèle : l'influence n'écrit plus τ ; elle s'accumule à l'interface, χ̇ = gσ(h_A) − λ_χχ ; l'exposition pressurise (ṗ += κ_χ‖χ‖) ; au Kairos : τ⁺ = τ⁻ + κ_Q χ⁻, χ⁺ = (1−r_χ)χ⁻, p⁺ = r_P p⁻. (λ_χ = 0.2, κ_Q = 0.6, r_χ = 0.8, κ_χ = 2.5.)

**(a) La validation protège — massivement.** Seuil d'appropriation au contact permanent : **g ≈ 0.1632, trois fois le seuil R0 (0.0556)**. La trace monte en escalier (quanta κ_Q·χ contre décroissance β entre événements). Fait saillant à g = 0.10 : **271 Kairos, τ_max = 0.66 > τ_ign — et pas d'appropriation** (x_final = −0.034, capture par une configuration résistante sous charge pulsée). D'où la distinction que ta cinquième question visait : **validation ≠ appropriation.** L'interface peut valider des centaines de quanta sans que rien ne devienne bascule ; la résistance empêche non pas la validation, mais sa conversion en changement de bassin.

**(b) Sommation d'expositions sous-critiques : oui, mais non monotone.** À g = 0.18 (T* = 76.2), deux expositions de 41.9 (chacune sous-critique) : D = 30 → **sommées, appropriation** ; D = 5, 80, 200 → oubliées. *Le timing compte plus que la dose* : la sommation dépend de la phase du transitoire d'état relativement à la cadence des quanta — la frontière en T d'une exposition unique reste, elle, monotone (grille vérifiée). Caractérisation des fenêtres sommantes : QO-31.

**(c) Amorçage : aucun, et c'est instructif.** Après une exposition sous-critique puis un délai D, T* de la seconde *augmente* avec D (76.2 → 117.4 → 295.9 pour D = 0, 100, 400). Résolution : une fois τ, χ, p oubliés (échelles 8.3, 5, 2), rien ne subsiste — et le délai **érode la graine d'état**, or la loi d'appropriation dépend de ln(1/x₀). Conséquence conceptuelle nette, qui répond à « une exposition oubliée laisse-t-elle une interface modifiée ? » : **dans R2 minimal, non — l'amorçage exige un support persistant.** Prédiction testable pour la suite : c'est l'interface elle-même (q de R1 à récupération lente, ou χ à λ_χ petit) qui peut porter l'amorçage, jamais la dynamique nue. La « peau qui se souvient » de [LD] cesse d'être une image : c'est une *nécessité fonctionnelle* pour qu'exister ait un après.

**(d) Zone d'issues entrelacées.** Entre g ≈ 0.10 et 0.163, l'issue au contact permanent dépend finement de la graine (une graine érodée à ~10⁻⁸ s'approprie là où 10⁻³ est capturée par la résistance) : bassins entrelacés dans l'espace (graine, phase) — QO-32. Le seuil 0.1632 vaut pour la graine standard.

**(e) N_K* n'est pas la bonne quantité.** 444 Kairos pendant le contact critique à g = 0.18, 271 sans appropriation à g = 0.10 : le *nombre* d'événements ne quantifie pas l'appropriation — la quantité pertinente reste le franchissement de séparatrice, les quanta n'étant que le véhicule de la charge. La conjecture N_K*(g) est à reformuler : non « nombre minimal d'événements », mais « charge nette minimale livrée par événements avant érosion » — ce qui ramène, encore, à la loi d'appropriation.

## 4. Le tableau des trois objets

| | R0 (continu) | R1 (perméabilité) | R2 (validation) |
|---|---|---|---|
| g_c | 0.0327 | 0.0913 (formule ; jamais si ρ/ηw < g_c⁰) | ≈ 0.16 pour l'appropriation effective (graine standard) |
| g_H | 0.1285 | **jamais** (ρ/ηw < g_H⁰) : résistance structurellement protégée | résistance sous charge pulsée observée ; continuation à faire (QO) |
| T*(0.10 / 0.20 / 0.30) | 24.8 / 15.0 / 12.3 | 88.9 / 32.1 / 26.2 | jamais (0.10) / — / frontière monotone, sommation non monotone |

Lecture d'ensemble : **chaque couche d'interface déplace les trois objets dans le sens de la protection, mais par des mécanismes différents** — R1 étrangle l'amplitude (transport de g_eff), R2 discrétise la charge et découple validation et appropriation. La hiérarchie inerte → résistant → approprié survit aux deux couches ; ce qui change, c'est le prix du passage.

## 5. Registres

**Propositions** : transport des seuils par g_eff, condition de protection absolue `[PROP]` ; expansion d'ordre 2 complète de la branche `[PROP-num]`.
**Faits** : rampe protectrice ; g_c^{R1} dynamique < formule (fenêtre d'ouverture initiale) ; protection ×3 par validation ; validation ≠ appropriation (271 événements stériles) ; sommation non monotone (fenêtre à D = 30) ; absence d'amorçage nu et érosion en ln(1/x₀) ; bassins entrelacés.
**Questions ouvertes** : QO-31 origine de la quasi-annulation d'ordre 2 (classe ou coïncidence) et cartographie des fenêtres de sommation ; QO-32 structure des bassins entrelacés de R2 ; QO-33 lois de perméabilité à hystérésis (seuil, usure cumulative) ; QO-34 **l'amorçage porté par l'interface** (prédiction : q lent ou χ lent restaure T*₂ < T*₁ — test décisif de A-I2) ; QO-35 continuation de la branche résistante sous R2 (existe-t-elle comme objet moyenné ?) ; QO-36 rampe + interface : la protection adiabatique se compose-t-elle avec la protection de peau ?

## 6. Conclusion (formulation adoptée)

> L'extérieur ouvre un chemin ; l'intérieur peut rester inerte, produire une résistance ou franchir ce chemin. Lorsqu'il le franchit, l'extérieur n'est plus nécessaire au maintien du nouvel état : ce qui a été rendu possible par la relation est désormais soutenu par la cohérence propre du système.

Et F-II.1 y ajoute sa ligne : *entre l'extérieur et le chemin, l'interface décide du prix — elle peut l'étrangler, le quantifier, ou le fermer à jamais ; mais pour que l'exposition laisse un après, il faut que quelque chose, à l'interface même, se souvienne.*

---

*Reproductibilité : `python fii1_interface.py` ; vérifications complémentaires consignées dans `fii1_addendum.py`.*
