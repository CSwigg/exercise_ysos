**Notebook Creator:** Cameren Swiggum  
**Class:** Star Formation: From Molecular Clouds to Protostars (W2024)

---

##### Submit your solutions by uploading either the completed notebook with your solutions clearly visible or a PDF version of the notebook with all solutions displayed.

##### If you have issues, you can post them on the github repository's issues section (https://github.com/CSwigg/exercise_ysos/issues), or you can contact me at cameren.swiggum@univie.ac.at

---

# Introduction: Exploring YSOs in Orion A

In this exercise, you will analyze a catalog of stars located in the Orion A molecular cloud, observed at infrared wavelengths. This dataset provides key measurements such as fluxes, magnitudes, and extinction values, allowing us to explore the properties and evolutionary stages of young stellar objects (YSOs).

Your tasks include:
- Investigating the spectral energy distributions (SEDs) of selected stars.
- Classifying stars based on their spectral indices and evolutionary stages.
- Visualizing spatial distributions and extinction properties.
- Fitting models to the data to estimate physical parameters like temperature, radius, and disk properties.


---

### SED Fitting with SEDFitter

The equations above directly relate to fitting the spectral energy distributions (SEDs) of young stellar objects (YSOs):

1. **Observed Data ($y_{\text{obs},i}$)**:
   - Represents the photometric fluxes of YSOs measured in various filters (e.g., Gaia, 2MASS, WISE).
   - These fluxes are the input data for the fitting process.

2. **Model Predictions ($y_{\text{model},i}$)**:
   - Represent the theoretical fluxes predicted by the SED models for specific physical parameters, such as stellar temperature, disk mass, and extinction.
   - The models are pre-computed and convolved with the same filter response functions as the observations.

3. **Uncertainties ($\sigma_i$)**:
   - Correspond to the photometric errors associated with the observed fluxes.
   - These uncertainties weigh the residuals in both $\chi^2$ and likelihood calculations, emphasizing data points with smaller errors.

In this notebook, we will use **SEDFitter** to implement this framework. By minimizing the $\chi^2$ statistic or maximizing the likelihood function, we aim to identify the best-fitting models for the observed SEDs of YSOs. This allows us to infer their physical properties, such as the size and temperature of their central stars, the structure and mass of their circumstellar disks, and the level of extinction in their surrounding environment.

</div>

<div style="color: #FF4500;">

## Installing SEDFitter
Instructions to download SEDFitter are available here: [SEDFitter Installation](https://sedfitter.readthedocs.io/en/stable/installation.html)

## Downloading the SED Models
SEDFitter only includes the code to perform the model fitting, not the models themselves. We will be using the SED models from this paper: [SED Models Paper](https://arxiv.org/abs/1703.05765)

- Navigate to the following data repository: [Zenodo Repository](https://zenodo.org/records/166732)
- Scroll and click on the file 'sp--s-i.tar.gz' (this will download to your computer).
- Go to the location on your computer where the file downloaded.
- Double click on the file so that it unzips/untars.
- You should now have a folder titled 'sp--s-i' that contains `models.conf`, `parameters.fits`, `stellar.fits`, `flux.fits`, and a sub-directory titled 'convolved'.

</div>

