# paper_itaconic_acid_2018

Archive of the analysis code and data behind a 2018 itaconic acid (IA) paper: regression of titers on
expression levels, contour plots of the fitted models, an Echo picklist builder, flow cytometry histograms,
and flux data. Not under development; scripts are kept as published.

## For whom
- Regression, contour and histogram outputs (xlsx, pdf): Eric, run by hand from each script's own folder, to reproduce the paper's figures.
- Echo picklists (`picklist_*.csv`): the Echo liquid handler, for assembling designs in the lab.
- Feeds / reads no other repo.

## Where
- Runs on: any machine with the old Python (3.5 / 2.7 per the script headers); local only. How to run each script is in README.md.
- Data: in the repo, one folder per analysis (`ia_*`). Real flow files other than `white-cells.fcs` and the paper PDF are not in the repo. Ground truth: the files themselves.

riker: light
