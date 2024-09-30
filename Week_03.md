## Guidance
Answer the following questions considering the learning outcomes for
- [Week 03](https://learn.foundersandcoders.com/course/syllabus/developer/week03-project03-server/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
importing SpotifyWeb API
```ts
import SpotifyWebApi from "spotify-web-api-node";
import * as dotenv from "dotenv";
import { spotifyResponse, track } from "../../types/spotifyResponse.js";
import { spotifyQuery, spotifyFeatures } from "../../types/spotifyQuery.js";

dotenv.config();

async function getAccessToken() {
  const data = await spotifyApi.clientCredentialsGrant(); // Getting an access token using client credentials
  spotifyApi.setAccessToken(data.body["access_token"]); // Setting the access token for future API requests
}
```
Logging the Genre:

The first thing I added was logging the genre being searched, just to make sure everything is working and that the correct genre is being passed.
Connected the Spotify API:

I made it so the function actually queries Spotify’s API to find tracks for the given genre (like genre:jazz). I used async/await to make sure the search happens properly in the background without blocking anything else.
Extracted Track Info:

When the search results come back, I check if any tracks are found. If there are tracks, I loop through them and grab important info like the song name, artist, album, release date, and duration.
I put this info into a playlist array and log it, so I can see the tracks coming through. I even log each track individually, so I know what’s being returned.
Added TypeScript:

I added TypeScript interfaces to make sure everything’s typed correctly—no more guessing what’s coming back from the API. This makes the code more organized and easier to maintain because I know exactly what types of data I’m working with, like track names, album names, and so on.
Handled Errors:

I wrapped the whole thing in a try-catch block so that if something goes wrong (like the API call fails), I can easily log the error and know what went wrong.
```ts
 const searchResults = await sdk.search(`genre:${genre}`, ["track"]);
    // Check if any tracks are found
    if (searchResults.tracks && searchResults.tracks.items.length > 0) {
      searchResults.tracks.items.forEach((track, index) => {
        const song: track = {
          title: track.name,
          artist: track.artists[0].name,
          album: track.album.name,
          releaseDate: new Date(track.album.release_date),
          duration: track.duration_ms,
        };
        
        playlist.push(song);
        console.log(track);
        console.log(`${index + 1}. ${track.name} by ${track.artists[0].name}`);
      });
      console.log(Object.keys(searchResults.tracks.items[0].album));
      console.log(playlist);
    } else {
      console.log(`No tracks found for the genre: ${genre}`);

```

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like 
I wasn't able to complete the main MVP; I only managed to get the API to log the specified genre. A teammate of mine took the time to review the code and make changes that I initially found difficult to come up with. He built on what I had previously written and was able to add extra queries, ensuring that OpenAI and the endpoints worked smoothly.

I still need to sit down and try to understand what's going on with the code, especially when it comes to aspects like valence, energy, and danceability.
 ```ts
   const audioFeatures = await getAudioFeaturesInBatches(
        trackIds,
        spotifyApi,
      );

      // Sorting tracks based on how closely they match the desired audio features
      const sortedTracks = audioFeatures
        ?.filter((feature) => feature) // Filtering out any undefined features
        .map((feature) => {
          if (!feature) return null;

          // Calculating differences between each track's features and the target features
          return {
            feature,
            differences: {
              valence: calculateFeatureDifference(
                feature.valence,
                spotifyFeatures.valence,
              ),
              energy: calculateFeatureDifference(
                feature.energy,
                spotifyFeatures.energy,
              ),
              danceability: calculateFeatureDifference(
                feature.danceability,
                spotifyFeatures.danceability,
              ),
              tempo: calculateFeatureDifference(
                feature.tempo,
                spotifyFeatures.tempo,
              ),
              acousticness: calculateFeatureDifference(
                feature.acousticness,
                spotifyFeatures.acousticness,
              ),
            },
          };
        })
        .filter(
          (
            item,
          ): item is {
            feature: SpotifyApi.AudioFeaturesObject;
            differences: spotifyFeatures;
          } => item !== null,
        )
        .sort((a, b) => {
          // Prioritizing valence and energy equally, then danceability, tempo, and acousticness
          const valenceEnergyDifference =
            a.differences.valence +
            a.differences.energy -
            (b.differences.valence + b.differences.energy);
          if (valenceEnergyDifference !== 0) return valenceEnergyDifference;
          return (
            a.differences.danceability - b.differences.danceability ||
            a.differences.tempo - b.differences.tempo ||
            a.differences.acousticness - b.differences.acousticness
          );
        });

      // Removing duplicate artists to ensure diversity in the playlist
      const uniqueArtistTracks = sortedTracks.filter((item, index, self) => {
        const track = allTracks.find((t) => t.id === item.feature.id);
        if (!track) return false;
        const artistName = track.artists[0].name;
        // Keeping only the first occurrence of each artist
        return (
          index ===
          self.findIndex((t) => {
            const otherTrack = allTracks.find((t2) => t2.id === t.feature.id);
            return otherTrack?.artists[0].name === artistName;
          })
        );
      });
```

## Feedback (For CF's)
> [**Course Facilitator name**]

Alexander

> [*What went well*]

You really digged into the Spotify API, that is a great example there. I also like that looks like you understand a bit better async code.

> [*Even better if*]

You mention that you want to revisit "aspects like valence, energy, and danceability" those are some spotify specific parameters, so may not worth to spend much there. I would advice to solidify the basics instead.
Also try to keep your code snippets shorter
