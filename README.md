# 🪙 Egyptian Coin Counter & Detector

Object detection project that identifies Egyptian coins (1 EGP and 0.5 EGP) in an image using **YOLOv8**, then automatically calculates the total monetary value detected.

The trained model is served through a **Streamlit** app where users upload a photo of coins (or use their mobile camera) and get back an annotated image, a coin breakdown, and the total value in EGP.

## Dataset
The dataset was **manually collected and labeled** (Egyptian 1 EGP and 0.5 EGP coins), hosted and versioned on [Roboflow](https://roboflow.com). It is not included in this repo — running the notebook will pull it automatically via the Roboflow API (see Setup below).

## Tech Stack
- YOLOv8 (Ultralytics)
- Roboflow (dataset hosting/versioning)
- Streamlit (web app)
- ONNX (model export for inference)
- Google Colab + Google Drive (training & checkpoint storage)
- ngrok (public tunnel for the Streamlit app)

## How it Works
1. Downloads the labeled dataset from Roboflow
2. Trains YOLOv8n on the coin dataset (two experiments: 50 vs. 100 epochs)
3. Exports the best-performing model to ONNX
4. Runs a Streamlit app that detects coins in an uploaded/captured image and sums their value

## Setup
This notebook needs two API keys, loaded securely via **Colab Secrets** 

| Secret name | Where to get it |
|---|---|
| `ROBOFLOW_API_KEY` | [Roboflow account settings](https://app.roboflow.com) |
| `NGROK_TOKEN` | [ngrok dashboard](https://dashboard.ngrok.com) |

Add each as a secret with notebook access enabled before running.
