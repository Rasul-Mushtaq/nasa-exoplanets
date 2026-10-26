# What the Telescopes Cannot See

Selection bias in the NASA exoplanet catalog.

Every planet in the catalog was found by a specific method, and every method has blind spots. The transit method only works when a planet's orbit lines up with our line of sight. The radial velocity method favors heavy planets orbiting close to bright, quiet stars. In this notebook I measured how much those biases shape the catalog, corrected for one of them, and looked at which small planets in the habitable zone we have actually found so far.

## What's in here

- `exoplanets.ipynb` - the analysis. It pulls the confirmed-planet table (`pscomppars`) from the NASA Exoplanet Archive, breaks discoveries down by method, quantifies the detection biases, applies a correction, and trains a quick model to flag the small habitable-zone planets in the data.
- `exoplanets_raw.csv` - a local copy of the raw catalog (6451 planets, 14 columns). The notebook downloads it automatically, but falls back to this file if the archive is unreachable.

## How to run it

You'll need Python with the usual scientific stack:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

Then open the notebook:

```bash
jupyter notebook exoplanets.ipynb
```

Cell 1 downloads the data from the NASA Exoplanet Archive TAP API and saves a local copy as `exoplanets_raw.csv`. If the request fails, the notebook reads the local CSV instead, so you can run it offline once the file is there.

## Data

NASA Exoplanet Archive, table `pscomppars` - one row per confirmed planet. Columns include planet name, host star, discovery method, discovery year, orbital period, semi-major axis, radius, mass, equilibrium temperature, and stellar properties.

## Limitations

This is exploratory. The bias correction is a rough first pass, and the model is just a sanity check on which small habitable-zone planets appear in the catalog, not a prediction of what's actually out there.
