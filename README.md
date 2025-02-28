
# Netflix Movie Duration Analysis

## Overview
This project explores trends in Netflix movie durations from 2011 to 2020. The analysis investigates whether movie lengths have been declining over time and examines the impact of genres like Children, Documentaries, and Stand-Up on average durations.

## Steps

1. **Loading Data into a Dictionary**  
   - Created a dictionary `movie_dict` with `years` and `durations` lists.  
   ```python
   movie_dict = {"years": [2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020],
                 "durations": [103, 101, 99, 100, 100, 95, 95, 96, 93, 90]}
   ```

2. **Creating a DataFrame**  
   - Converted the dictionary into a pandas DataFrame.  
   ```python
   durations_df = pd.DataFrame(movie_dict)
   ```

3. **Visual Inspection**  
   - Plotted a line graph to visualize the trend in movie durations over time.  
   ```python
   plt.plot(durations_df['years'], durations_df['durations'])
   plt.title("Netflix Movie Durations 2011-2020")
   plt.show()
   ```

4. **Loading Full Dataset**  
   - Loaded the full Netflix dataset from a CSV file.  
   ```python
   netflix_df = pd.read_csv("datasets/netflix_data.csv")
   ```

5. **Filtering for Movies**  
   - Subsetted the DataFrame to include only movies and selected relevant columns.  
   ```python
   netflix_movies_col_subset = netflix_df[netflix_df['type'] == "Movie"][["title", "country", "genre", "release_year", "duration"]]
   ```

6. **Creating a Scatter Plot**  
   - Visualized movie durations by release year using a scatter plot.  
   ```python
   plt.scatter(netflix_movies_col_subset['release_year'], netflix_movies_col_subset['duration'])
   plt.title("Movie Duration by Year of Release")
   plt.show()
   ```

7. **Analyzing Short Movies**  
   - Filtered for movies with durations under 60 minutes and examined their genres.  
   ```python
   short_movies = netflix_movies_col_subset[netflix_movies_col_subset["duration"] < 60]
   ```

8. **Marking Non-Feature Films**  
   - Assigned colors to movies based on genre (Children: red, Documentaries: blue, Stand-Up: green, Others: black).  
   ```python
   colors = []
   for lab, row in netflix_movies_col_subset.iterrows():
       if row['genre'] == "Children":
           colors.append("red")
       elif row['genre'] == "Documentaries":
           colors.append("blue")
       elif row['genre'] == "Stand-Up":
           colors.append("green")
       else:
           colors.append("black")
   ```

9. **Plotting with Color**  
   - Created a scatter plot with colored genres to visualize trends.  
   ```python
   plt.scatter(netflix_movies_col_subset['release_year'], netflix_movies_col_subset['duration'], c=colors)
   plt.title("Movie Duration by Year of Release (Colored by Genre)")
   plt.show()
   ```

10. **Conclusion**  
    - Non-typical genres (Children, Documentaries, Stand-Up) are clustered at shorter durations, but further analysis is needed to confirm trends.  
    ```python
    are_movies_getting_shorter = "no"
    ```
