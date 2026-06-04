# freq
# Freq 🎵

An emotion-aware music recommendation system that generates personalized playlists by combining Spotify listening history with real-time mood detection.

## Overview

Traditional recommendation engines rely solely on listening history. **Freq** goes further by layering emotional intelligence on top — classifying the user's current mood from free-text input and using it to influence what gets recommended, and why.

## How It Works

1. **Spotify Integration** — Users authenticate via OAuth 2.0. Freq pulls top tracks, artists, and genre preferences to build a listening profile.
2. **Mood Detection** — The user inputs how they're feeling in plain text. A RoBERTa model fine-tuned on the GoEmotions dataset classifies this into one of six emotions: `Happy` `Sad` `Stressed` `Motivated` `Relaxed` `Anxious`.
3. **Hybrid Recommendation Engine** — Three signals are combined:
   - *Content-Based Filtering* — matches songs via Spotify audio features (valence, energy, tempo, danceability) aligned to the detected mood.
   - *Collaborative Filtering* — surfaces tracks enjoyed by users with similar listening patterns.
   - *Mood Weighting Layer* — dynamically adjusts signal weights based on emotion intensity.

   Final score: `score = α × content + β × collaborative + γ × mood`

4. **Explainable Output** — Every recommendation includes a plain-language reason (e.g. *"matches your relaxed mood · fits your acoustic indie preference · popular among similar listeners"*).

## Tech Stack

| Layer | Tools |
|---|---|
| Frontend | Next.js, Tailwind CSS |
| Backend | FastAPI, Python |
| ML | PyTorch, HuggingFace Transformers, Scikit-learn |
| Database | PostgreSQL |
| APIs | Spotify Web API |
| Deployment | Vercel, Render |

## Evaluation Metrics

Precision@K · Recall@K · F1 Score · Playlist Completion Rate · Song Skip Rate · User Satisfaction Rating

## Privacy

Spotify data is accessed only with explicit user consent. Emotion input is processed in-session and never stored. Users can revoke access at any time.

## Status

🚧 Under development as a pre final-year AI/ML research project — focused on emotion-aware recommendations and explainable AI.
