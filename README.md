# Netflix Movie Duration Analysis

This project aims to explore the trend of movie durations over time on Netflix, specifically addressing the hypothesis that movies are getting shorter. By leveraging the Netflix dataset provided (`netflix_data.csv`), we perform an exploratory data analysis (EDA) to examine the duration of movies across different years and genres.

## Dataset

The analysis uses the `netflix_data.csv` dataset, which includes information about movies and TV shows available on Netflix. The dataset contains the following columns:

| Column       | Description                              |
|--------------|------------------------------------------|
| `show_id`    | The ID of the show                       |
| `type`       | Type of show (Movie or TV Show)          |
| `title`      | Title of the show                        |
| `director`   | Director of the show                     |
| `cast`       | Cast of the show                         |
| `country`    | Country of origin                        |
| `date_added` | Date added to Netflix                    |
| `release_year`| Year of Netflix release                 |
| `duration`   | Duration of the show in minutes          |
| `description`| Description of the show                  |
| `genre`      | Show genre                               |

## Analysis Steps

### 1. Data Loading
The script starts by loading the `netflix_data.csv` file into a Pandas DataFrame for processing:
\`\`\`python
netflix_df = pd.read_csv("netflix_data.csv")
\`\`\`

### 2. Data Filtering
We filter the dataset to exclude TV shows and focus solely on movies:
\`\`\`python
netflix_subset = netflix_df[netflix_df["type"] != "TV Show"]
\`\`\`

### 3. Subsetting Relevant Columns
A subset of the data is created to include only the columns relevant to our analysis:
\`\`\`python
netflix_movies = netflix_subset[["title", "country", "genre", "release_year", "duration"]]
\`\`\`

### 4. Analyzing Short Movies
We filter the dataset to identify movies that are shorter than 60 minutes:
\`\`\`python
short_movies = netflix_movies[netflix_movies["duration"] < 60]
\`\`\`

### 5. Assigning Colors Based on Genre
Colors are assigned to different genres to visualize the data more effectively:
\`\`\`python
colors = []
for index, row in netflix_movies.iterrows():
    if row["genre"] == "Children":
        colors.append("Blue")
    elif row["genre"] == "Documentaries":
        colors.append("Black")
    elif row["genre"] == "Stand-Up":
        colors.append("Yellow")
    else:
        colors.append("Green")
\`\`\`

### 6. Scatter Plot of Movie Duration by Year
A scatter plot is generated to visualize the trend of movie duration over the years:
\`\`\`python
fig = plt.figure(figsize=(12, 8))
plt.scatter(netflix_movies["release_year"], netflix_movies["duration"], c=colors, alpha=0.8)
plt.xlabel('Release year')
plt.ylabel("Duration (min)")
plt.title("Movie Duration by Year of Release")
plt.show()
\`\`\`

### 7. Conclusion
Based on the visual analysis, we conclude whether movies are indeed getting shorter. The variable `answer` is used to store this conclusion:
\`\`\`python
answer = "no"
\`\`\`

## Requirements

To run the script, you'll need the following Python packages:

- `pandas`
- `matplotlib`

You can install these packages using pip:
\`\`\`bash
pip install pandas matplotlib
\`\`\`

## How to Run

1. Ensure you have the dataset `netflix_data.csv` in the same directory as the script.
2. Run the script using a Python interpreter:
   \`\`\`bash
   python netflix_duration_analysis.py
   \`\`\`
3. The scatter plot will be displayed, showing the trend of movie durations over the years.

## Conclusion

After analyzing the data, we determined that there is no strong evidence to support the claim that movies on Netflix are getting shorter. Further analysis might be required with a larger dataset or by exploring different aspects of the data.



