---
title: "Exploratory Data Analysis of Most Streamed Spotify songs"
excerpt: "Data Analysis of the most streamed Spotify songs up to 2024."
collection: portfolio
---
![Illustration of combining vision and language modalities](/images/spotify_logo.png){:.align-right width="200px"}
Spotify is a popular music streaming service that offers a vast library of songs, podcasts, and other audio content. Launched in 2008, Spotify allows users to listen to millions of tracks from various artists across the globe. Users can create and share playlists, discover new music through personalized recommendations, and access curated playlists for different moods and genres. Spotify offers both free and premium subscription options, with the latter providing benefits such as ad-free listening, offline downloads, and higher sound quality. It is accessible on multiple devices, including smartphones, tablets, and computers, making it a versatile platform for music and audio entertainment.

In this project I have performed a complete Data Exploration of the most streamed Spotify songs up to 2024.  The dataset used in this project was retrieved on [Kaggle](https://www.kaggle.com/datasets/pragyantiwari/spotify-refined-explicity-classified-1). It contains 4600 different tracks and a total of 30 columns that provide with important information per each track, e.g. the release date, the artist, the track score, number of streams etc. After cleaning the dataset from duplicated values and useless (for the scope of my project) columns and fill the left NaN values with the median, I was left with 4598 tracks and 22 columns.

Firstly, I investigated how the number of released songs varied with the year till 2023.
<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_spotify/num_tracks_year.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 1: Number of released tracks as a function of the year till 2023.</em></p>
</div>
Figure 1 shows an exponential growth of the number of songs released from 2015. Moreover, while during 2015-2020 nearly 50 songs per year were released, in the last three years 2021-2023, the release rate nearly reaches 400 songs per year.  

Then, I checked if there was a preferred month when artist decide to release their new albums.
<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_spotify/months.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 2: Number of released tracks per months till 2023.</em></p>
</div>
Figure 2 shows the number of tracks per months till 2023. We did not take into account 2024 since the year is not finished yet, it would have yielded unbalanced results. Figure 2 evidences that January is the preferred release month by the artist with 431 songs (9.3% from total), followed by October with 384 songs (8.3% from total). On contrary April is the least preferred with 257 tracks (5.5% from total) alongside with February with 267 tracks (5.8%). 
Any possible reasons?

Succesively, I examined which are the most streamed songs and artists on the three major platforms (Spotify, YouTube and TikTok) and reported in Figure 3 and 4 respectively.

<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_spotify/most_streamed_tracks" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 3: Most streamed tracks on Spotify (upper panel), YouTube (middle panel) and TikTok (bottom panel).</em></p>
</div>

<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_spotify/most_streamed_artists" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 3: Most streamed artist on Spotify , YouTube  and TikTok .</em></p>
</div>


![Image](/images/portfolio_spotify/df_corr.png){:.align-center width="400px"}

![Image](/images/portfolio_spotify/exp_friends_year.png){:.align-center width="400px"}
