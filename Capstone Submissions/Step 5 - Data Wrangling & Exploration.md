# Capstone Step 5: Data Wrangling & Exploration

In this project phase, I focused on cleaning, wrangling, and exploring the raw data collected to develop a real-time audio transcription system for live baseball games. The dataset comprises a significant volume of YouTube metadata enriched with detailed information from the ESPN API. The goal was to prepare a clean, consistent, and comprehensive dataset suitable for experimenting with the performance of ASR models under varying conditions.

## Data Collection and Organization

### YouTube Metadata Retrieval

Initially, I utilized the YouTube Data API to collect metadata for approximately 350,000 baseball-related videos. I applied several filtering criteria to refine this extensive dataset to relevant content. I selected videos that matched the typical length of full baseball games to ensure they contained complete game commentaries. Videos containing terms like “highlights,” “recap,” or “condensed” were filtered out to exclude non-full-game content. Additionally, I ensured that the videos were in English to match the target transcription language. As a result of these filtering steps, I narrowed down the dataset to 32,000 full-length game commentaries suitable for analysis.

Enrichment with ESPN API Data  
To enhance the dataset with more detailed information, I integrated data from the ESPN API. I extracted the game date, home team, and away team from the YouTube metadata and matched this information with ESPN’s database to find the corresponding event IDs. I pulled detailed game data using these event IDs, including team rosters and player statistics. I merged the ESPN data with the YouTube metadata to enrich each video entry with comprehensive game information that I used to create more personalized initial prompts.

Data Cleaning Steps

Standardizing Team Names  
One of the issues encountered was consistency in team names due to variations in abbreviations, nicknames, and misspellings across different data sources. To address this, I developed a metadata class to standardize team names. This class used a mapping dictionary to convert all variations to a standard format—for example, “NY Yankees” and “New York Yankees” were both converted to “nya.” I applied the normalization class during data ingestion to ensure consistency throughout the dataset.

Handling Missing Values  
Some YouTube videos lacked information about the home team or away team. To handle this, I implemented a backfilling strategy. When the game date and one team’s name were known, I queried the ESPN API for games on that date involving the known team and retrieved the missing team’s name. This method was only effective when the game date was available and accurate; in cases where the date was missing or multiple games occurred on the same day, the missing data remained unfilled. Nonetheless, this approach successfully backfilled missing team data for a significant portion of the entries, reducing the number of incomplete records.

Addressing Outliers  
I identified games involving opponents outside MLB, such as college, international, and all-star teams. To maintain the focus on MLB games, I excluded these games from the primary dataset, marking them as outliers for potential future analysis. This approach ensured that the dataset remained relevant to the project’s scope, improving the model’s generalization ability across MLB games.

Data Quality Assurance  
To ensure the dataset’s quality, I removed duplicate video entries by identifying and removing them based on unique video IDs. I also conducted consistency checks to verify that all date formats were standardized (e.g., YYYY-MM-DD) and ensured that numerical fields like durations and view counts were correctly typed. I filled in placeholders or median values for non-critical missing fields, whereas records with critical missing data were excluded to maintain dataset integrity.

Exploratory Data Analysis (EDA)

Data Distribution Insights  
I performed a temporal analysis by charting the number of games per season to identify gaps or spikes. This analysis revealed expected decreases during strike years or seasons impacted by external events. Additionally, I analyzed the frequency of games per team and observed that some teams had disproportionately more games, indicating potential bias in the dataset. These insights allowed me to focus my research on games during the 2014 \- 2017 seasons.

Correlation Studies  
I explored correlations between view counts and game features such as rivalry games, playoff appearances, or star player participation. This analysis found higher engagement in games with significant events or popular teams, providing insights into audience interests. This was not a practical data point in the experiments that I ran, but it helped my understanding of the data and reinforced the robustness of the data set.

Audio Quality Considerations  
To assess potential challenges for the ASR model, I sampled audio snippets to evaluate variations in commentary styles, accents, and audio quality. This examination identified background crowd noise and overlapping commentators, which could affect transcription accuracy. In the experiment, I used audio processing to remove the background noise and VAD to segment the audio to mitigate its impact.

Dataset Size Management  
After data enrichment, the total dataset size is approximately 500 GB. The original, unprocessed audio files take up an additional 3.9 TB. Recognizing that processing the entire dataset might be impractical for initial experimentation, I devised a strategy for prototype experimentation. I created a sample representing all teams and a variety of game situations from the 2014 through 2017 seasons. This reduced the working dataset to a manageable size while retaining diversity. This approach allowed for efficient experimentation and iteration during experimentation and enabled using available computational resources without significantly degrading performance.

## Conclusion

The data wrangling and exploration phase was crucial in preparing a high-quality dataset for the project. I ensured dataset robustness and suitability for running experiments on the ASR model by systematically cleaning the data, addressing missing values, and handling outliers. The exploratory analysis provided valuable insights into the data’s characteristics, guiding subsequent modeling decisions. The refined dataset will be a solid foundation for developing an effective real-time transcription system for live baseball games.  
