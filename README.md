# Netflix–IMDb Catalog Wrangling

A reproducible data-wrangling project that connects Netflix catalog metadata with IMDb audience ratings, resolves quality and tidiness issues, and produces a tidy movie–genre analysis table.

This project was completed for the **Advanced Data Wrangling** course in the Data Analyst Nanodegree and polished for portfolio use.

## Project Highlights

- Gathered two related datasets with two methods: a manual Netflix CSV download and programmatic IMDb archive downloads.
- Preserved raw acquisitions separately from the cleaned data store.
- Assessed and corrected two data-quality issues and two tidiness issues.
- Reconciled ambiguous IMDb title/year candidates with a documented highest-vote rule.
- Split multi-value genre fields into one movie–genre membership per row.
- Validated a many-to-one title/year merge to prevent unexpected row multiplication.
- Retained 6,097 matched Netflix titles in a 13,933-row tidy dataset.

## Key Findings

- Classic Movies and Documentaries had the highest median IMDb ratings among genres with at least 40 matched, sufficiently rated titles.
- Older release cohorts generally had higher median ratings than the newest cohorts in the matched catalog.
- That time pattern likely reflects catalog selection and survivorship, not a decline in movie quality.

## Data Sources

- [Netflix Movies and TV Shows on Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows): manually downloaded catalog snapshot.
- [IMDb non-commercial datasets](https://developer.imdb.com/non-commercial-datasets/): programmatically gathered title basics and title ratings archives.

The repository includes a filtered raw IMDb acquisition extract rather than the full multi-gigabyte title catalog. The extract preserves every title/year candidate needed for the Netflix join before cleaning.

## Run Locally

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyter lab
```

Open `Data_Wrangling_Project_Starter.ipynb` and choose **Restart Kernel and Run All Cells**. The submitted raw files are included, so normal execution does not require network access.

## Repository Structure

```text
.
├── data
│   ├── raw
│   │   ├── netflix_titles.csv
│   │   └── imdb_titles_ratings_raw.csv
│   └── clean
│       └── netflix_imdb_clean.csv
├── Data_Wrangling_Project_Starter.ipynb
├── Data_Wrangling_Project_Starter.html
├── requirements.txt
└── README.md
```

## Limitations

Exact normalized title/year matching favors precision over recall and can miss valid matches when source titles or years differ. IMDb ratings reflect self-selected users, and the Netflix CSV is a historical catalog snapshot rather than the current service.
