# Patch iws-core-0.1.1-patch1

Regle : ne jamais modifier le comportement historique par defaut.
`IWSConfig.legacy_p1()` reproduit model.py bit-a-bit (verifie par run_checks.py, C1) ;
chaque decision du Core (D-02, D-03, D-04, D-07, D-08) s'active independamment.

Fichiers :
- iws_core/config.py      configuration par mecanisme + audit A1-A7 code/article
- iws_core/engine.py      moteur parametrable (invariants, journaux, symetrie)
- iws_core/inputs.py      port d'entree u (zero / fixe / bruit pre-genere apparie)
- iws_core/validation.py  comparaison dt vs dt/2 (observables + temps d'evenements)
- run_checks.py           criteres de reussite du patch (7 verifications)
- run_x0.py               campagne X0 (recalibration, 3 bras, provenance complete)
- run_x4b.py              campagne X4b (brisure de symetrie, bras 1a/1b/2/3/4/5)

Usage :
    python run_checks.py     # doit afficher 7/7
    python run_x0.py         # sorties dans output_x0/
    python run_x4b.py        # sorties dans output_x4b/

Resultats et analyse : RAPPORT_X0_X4b.md
