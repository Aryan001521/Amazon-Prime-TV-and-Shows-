# 🎬 Movie Recommendation System — EDA

> Exploratory Data Analysis on Netflix Titles Dataset

---

## 📁 Project Structure

```
├── titles.csv                        # Movie/Show metadata dataset
├── credits.csv                       # Cast & crew dataset
├── final_cleaned_merged_data.csv     # Cleaned & merged dataset (generated)
├── EDA_Movie_Recommendation.ipynb    # Main EDA notebook
├── missing_values.png                # Chart: Missing values heatmap
├── chart1_imdb_distribution.png      # Chart 1: IMDb Score Distribution
├── chart2_year_distribution.png      # Chart 2: Release Year Distribution
├── chart3_runtime_distribution.png   # Chart 3: Runtime Distribution
├── chart4_top_genres.png             # Chart 4: Top 10 Genres
├── chart5_popularity_boxplot.png     # Chart 5: TMDB Popularity Boxplot
├── chart6_imdb_vs_popularity.png     # Chart 6: IMDb vs Popularity Scatter
├── chart7_imdb_vs_runtime.png        # Chart 7: IMDb vs Runtime Scatter
├── chart8_genre_imdb.png             # Chart 8: Genre-wise Avg IMDb Score
├── chart9_decade_count.png           # Chart 9: Movies by Decade
├── chart10_decade_imdb.png           # Chart 10: Avg IMDb by Decade
├── chart11_top10_popular.png         # Chart 11: Top 10 Popular Movies
├── chart12_top10_rated.png           # Chart 12: Top 10 Rated Movies
├── chart13_top_actors.png            # Chart 13: Top 10 Active Actors
├── chart14_correlation_heatmap.png   # Chart 14: Correlation Heatmap
├── chart15_pairplot.png              # Chart 15: Pair Plot
├── chart16_type_distribution.png     # Chart 16: Movie vs Show Pie
├── chart17_type_imdb.png             # Chart 17: Avg IMDb Movie vs Show
├── chart18_top_countries.png         # Chart 18: Top Production Countries
├── chart19_imdb_vs_tmdb.png          # Chart 19: IMDb vs TMDB Score
├── chart20_genre_decade_heatmap.png  # Chart 20: Genre by Decade Heatmap
└── README.md
```

---

## 📊 Dataset

| File | Rows | Columns | Description |
|------|------|---------|-------------|
| `titles.csv` | 9,871 | 15 | Movie/Show metadata |
| `credits.csv` | 1,24,235 | 5 | Cast & crew info |
| `merged` | 1,25,186 | 19 | After LEFT JOIN on id |
| `movies (EDA)` | 8,511 | 19 | Unique movies only |

### titles.csv Columns
| Column | Type | Description |
|--------|------|-------------|
| id | Object | Unique title ID |
| title | Object | Movie/Show name |
| type | Object | MOVIE or SHOW |
| description | Object | Plot summary |
| release_year | Integer | Year of release |
| age_certification | Object | PG, R, TV-MA etc. |
| runtime | Integer | Duration in minutes |
| genres | Object | List of genres |
| production_countries | Object | Countries of production |
| seasons | Float | Number of seasons (SHOWs only) |
| imdb_id | Object | IMDb title ID |
| imdb_score | Float | IMDb rating (0–10) |
| imdb_votes | Float | Total IMDb votes |
| tmdb_popularity | Float | TMDB popularity score |
| tmdb_score | Float | TMDB rating (0–10) |

### credits.csv Columns
| Column | Type | Description |
|--------|------|-------------|
| person_id | Integer | Unique person ID |
| id | Object | Title ID (links to titles.csv) |
| name | Object | Actor or Director name |
| character | Object | Character played |
| role | Object | ACTOR or DIRECTOR |

---

## ⚙️ Installation

```bash
pip install pandas numpy matplotlib seaborn
```

---

## 🚀 How to Run

1. Clone the repo
```bash
git clone https://github.com/yourusername/movie-recommendation-system.git
cd movie-recommendation-system
```

2. Add `titles.csv` and `credits.csv` in the same folder

3. Open notebook in Jupyter or Google Colab
```bash
jupyter notebook EDA_Movie_Recommendation.ipynb
```

4. Run all cells from top to bottom

---

## 🧹 Data Cleaning Steps

| Step | Action | Result |
|------|--------|--------|
| 1 | Remove Duplicates | titles: 9871→9868, credits: 124235→124179 |
| 2 | Standardize Column Names | Lowercase + strip spaces |
| 3 | Clean ID Column | Strip whitespace — critical for merge |
| 4 | Drop Missing ID rows | Remove unusable rows |
| 5 | Merge Datasets (LEFT JOIN) | 9868 + 124179 → 125186 rows, 19 cols |
| 6 | Fill Numeric Missing → Median | imdb_score, tmdb_popularity etc. |
| 7 | Fill Text Missing → Not Applicable | age_certification, seasons etc. |
| 8 | Strip Whitespace from Text | Clean all text columns |
| 9 | Save Cleaned Data | final_cleaned_merged_data.csv |
| 10 | Filter Movies Only | 8,511 unique movies for EDA |

---

## 📈 20 Charts — EDA Summary

### 🔵 Univariate Analysis (Charts 1–5)

| Chart | Type | Insight |
|-------|------|---------|
| Chart 1 | Histogram | Most movies score 5–7 on IMDb — near normal distribution |
| Chart 2 | Histogram | Massive content growth after 2000 |
| Chart 3 | Histogram | Most movies are 80–120 minutes long |
| Chart 4 | Bar Chart | Drama is #1 genre (3,500+ movies) |
| Chart 5 | Boxplot | TMDB popularity heavily right-skewed — max 1,437 |

### 🟢 Bivariate Analysis (Charts 6–10)

| Chart | Type | Insight |
|-------|------|---------|
| Chart 6 | Scatter | IMDb vs Popularity — weak correlation (0.08). Popular ≠ Quality |
| Chart 7 | Scatter | IMDb vs Runtime — no strong relation |
| Chart 8 | Bar Chart | Documentation highest avg IMDb. Horror lowest |
| Chart 9 | Bar Chart | 2010s has most movies. Pre-1970 very rare |
| Chart 10 | Line Chart | Older movies have higher avg IMDb scores |

### 🟠 Multivariate Analysis (Charts 11–20)

| Chart | Type | Insight |
|-------|------|---------|
| Chart 11 | Horizontal Bar | Popular movies ≠ high quality movies |
| Chart 12 | Horizontal Bar | Top rated movies are niche/regional hidden gems |
| Chart 13 | Bar Chart | Some actors appear in 50+ movies — fan following data |
| Chart 14 | Heatmap | imdb_score & tmdb_score: strong +0.72 correlation |
| Chart 15 | Pair Plot | Clear linear relation between IMDb and TMDB scores |
| Chart 16 | Pie Chart | 86% MOVIES, 14% SHOWS — platform is movie-heavy |
| Chart 17 | Bar Chart | Shows have slightly higher avg IMDb than Movies |
| Chart 18 | Bar Chart | USA dominates content production |
| Chart 19 | Scatter | IMDb vs TMDB — strong positive trend (+0.72) |
| Chart 20 | Heatmap | Drama & Comedy grew fastest in 2010s and 2020s |

---

## 🔑 Key EDA Findings

- Most movies score **5–7 on IMDb** — near-normal distribution
- **Drama** is the most common and consistently above-average genre
- **TMDB popularity** has weak correlation (+0.08) with IMDb — popular ≠ quality
- **Older movies (pre-1970)** have higher average ratings — classics are undervalued
- Content production grew **exponentially after 2000**
- **IMDb and TMDB scores** are strongly correlated (+0.72)
- **USA dominates** content production — international diversity needed
- **Shows** have slightly higher avg ratings than movies
- Merged dataset **actor data** enables actor-based analysis (Chart 13)

---

## 💡 Business Recommendations

1. **Quality Filter** — Only surface movies with IMDb ≥ 6.0
2. **Genre Sections** — Dedicated Drama and Comedy homepage sections
3. **Classics Section** — Old movies have higher avg ratings — feature them
4. **Critics Choice** — High IMDb but low popularity = hidden gems
5. **International Content** — Expand beyond US — India, Korea, Europe
6. **Balanced Scoring** — Combine normalized IMDb + TMDB popularity
7. **Actor-Based Suggestions** — Use merged actor data for fan recommendations
8. **Invest in Shows** — Shows have higher avg IMDb — drives binge-watching

---

## 🛠️ Tech Stack

- Python 3
- Pandas
- NumPy
- Matplotlib
- Seaborn

---

## 👤 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
