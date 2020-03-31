## Updating molecular subtyping output with pathology feedback

**Author of code and documentation:** [@jaclyn-taroni](https://github.com/jaclyn-taroni)

As part of this project, we have undertaken several analyses that use molecular data to subtype biospecimens. 
In some cases, our analyses have resulted in an update of the `integrated_diagnosis` field included in the clinical file (`pbta-histologies.tsv` [[doc](https://github.com/AlexsLemonade/OpenPBTA-analysis/blob/master/doc/data-formats.md#data-caveats)]).

The objective of this module is two-fold:

1. Aggregate the molecular subtyping calls from the following modules that produced results:
   * [`molecular-subtyping-EPN`](https://github.com/jaclyn-taroni/OpenPBTA-analysis/tree/645-pathology-feedback/analyses/molecular-subtyping-EPN) (in progress, see [#555](https://github.com/AlexsLemonade/OpenPBTA-analysis/pull/555))
   * [`molecular-subtyping-EWS`](https://github.com/jaclyn-taroni/OpenPBTA-analysis/tree/645-pathology-feedback/analyses/molecular-subtyping-EWS)
   * [`molecular-subtyping-HGG`](https://github.com/jaclyn-taroni/OpenPBTA-analysis/tree/645-pathology-feedback/analyses/molecular-subtyping-HGG)
   * [`molecular-subtyping-LGAT`](https://github.com/jaclyn-taroni/OpenPBTA-analysis/tree/645-pathology-feedback/analyses/molecular-subtyping-LGAT)
   * [`molecular-subtyping-embryonal`](https://github.com/jaclyn-taroni/OpenPBTA-analysis/tree/645-pathology-feedback/analyses/molecular-subtyping-embryonal)
2. Incorporate feedback from CHOP pathologists Maria Rita Santi and Angela Viaene. 
Specifically, there are instances where the final `integrated_diagnosis` calls from pathology will deviate from the logic included in molecular subtyping modules based on additional information outside the scope of the repository (e.g., pathology reports, slides, etc.). 
The goal is to make sure that the _final calls_ are recorded in an aggregated table (see point 1 above) and documented in this repository.

For more background, see [#609](https://github.com/AlexsLemonade/OpenPBTA-analysis/issues/609).

### Usage

To run all steps in this module, run the following command:

```sh
bash run-subtyping-aggregation.sh
```

### Module contents

`01-compile-subtyping-results.Rmd` aggregates results from the modules listed above into a single table (`results/compiled_molecular_subtypes.tsv`).