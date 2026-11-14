# paper_itaconic_acid_2018

Analysis code and data behind a 2018 itaconic acid (IA) paper (`2018_ia_paper.pdf` is git-ignored).
This is an archive. Scripts have no argument parsing; each is run by executing the file from inside its own folder
(inputs and outputs use relative paths). All facts below come from the files.

## ia_regression
- **Computes:** ordinary least squares regressions (statsmodels `ols`) for each library dataset (`libA_avg`, `libAR_avg`, `libAF_avg`, `libB_avg`, `libC_avg`, `all_avg`, `highcad_avg`), each regression order (`1`, `2`, `in`) and each response (`ia`, `mmia`, `tia`, `sa`, `ma`, `ia2mmia`); fit statistics, equation, ANOVA, dbetas, variable and diagnostic plots.
- **Input:** `ia_regression_data.xlsx` (one sheet per library); `ia_regression_history.xlsx` (sheet `reg_history`) is opened for appending but is not in the repo.
- **Output:** `<lib>_<order>_<response>_regression.xlsx`, `..._regression.pdf`, `..._<var>_diag.pdf`, and rows appended to `ia_regression_history.xlsx`.
- **Language / libraries:** Python 3.5.2 (per header); pandas, numpy, statsmodels, matplotlib, openpyxl.
- **Run:** `python ia_regression.py` (calls `main()` at import).

## ia_contourplot
- **Computes:** contour plots of the fitted regression equations (from `ia_regression` output) over pairs of log-expression variables (CAD, ITE, PYC, ACDH, CSC, ACO) at Low/Med/High levels of a fixed variable. `models.py` holds the equation forms (`second_order_model`, `second_order_nosquare_model`, `linear_model`).
- **Input:** `<lib>_avg_<n>_<response>_regression.xlsx` (sheet `equation`) and `fixed_values.xlsx` (sheets `range`, `z_range`, `Low`/`Med`/`High`).
- **Output:** `<name>_<effect>.pdf` figures.
- **Language / libraries:** Python 3.5.2 (per header); pandas, numpy, matplotlib (incl. `pylab`).
- **Run:** `python contour_plot.py` (calls `main()` at import; imports `models.py` from the same folder).

## ia_echo
- **Computes:** builds an Echo liquid-handler picklist (500 transfer volume) for assembling designs from a source plate map to a destination plate layout.
- **Input:** `source_<A|B>_L1.xlsx`, `dest_EY_<A|B>_P<n>.xlsx` (sheet named after the file). Plate/picklist ids are hard-coded in `main()` (currently `source_B_L1`, `dest_EY_B_P1`, `B1`).
- **Output:** `picklist_<id>.csv` (also printed to stdout); committed: `picklist_A1/A2/B1.csv`.
- **Language / libraries:** Python (version not stated); openpyxl.
- **Run:** `python echo_assembly.py` after editing the ids in `main()`.

## ia_flux
- Data only, no script: `ItaFlux.csv`, `iMM904_GM.mat`, `ita_design_flux.mat`. What they feed is unclear from the code (names suggest the iMM904 yeast model and flux results).

## ia_histograms_flowcal
- **Computes:** 1D flow cytometry histograms (channel `B1-A`, Venus expression, log scale 0 to 1e6) for a hard-coded list of promoter-terminator combinations plus `white-cells`.
- **Input:** `<combo>.fcs` files; only `white-cells.fcs` is in the repo.
- **Output:** `<combo>_log.pdf`.
- **Language / libraries:** Python 2.7 (header says it must run there); FlowCal, matplotlib.
- **Run:** `python combo_histogram_ia.py` (top-level script, no `main`).
