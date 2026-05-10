# 🎙️ Call Transcriber

A Streamlit app that transcribes insurance call recordings and generates structured summaries using Google Gemini.

## What It Does

Upload an audio file of an insurance call and the app will:
1. **Transcribe** the full conversation with timestamps and speaker labels (`Caller` / `Insurance Agent`)
2. **Summarize** it into a structured 10-field report covering patient, medication, insurance details, and call outcome

## Demo

| Transcript | Summary |
|---|---|
| `[00:12] Caller: Hi, I'm calling to verify...` | `Patient_Name: John Doe` |
| `[00:18] Insurance Agent: Sure, what's the member ID?` | `Status: Approved` |

## Setup

### 1. Clone the repo
```bash
git clone https://github.com/Hamza-farid/call-transcriber.git
cd call-transcriber
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Add your API key

Create a `.streamlit/secrets.toml` file:
```toml
GOOGLE_API_KEY = "your-gemini-api-key-here"
```

Get a free API key at [aistudio.google.com](https://aistudio.google.com).

### 4. Run the app
```bash
streamlit run main.py
```

## Supported Audio Formats

`mp3` · `wav` · `m4a` · `ogg` · `flac` · `webm` · `mp4`

## Summary Fields

Each call produces exactly these 10 fields:

| Field | Description |
|---|---|
| `Date_&_Time` | Extracted from filename — format `MM-DD-YYYY HH-MM` |
| `Caller_Name` | Name of the agent who made the call |
| `Duration` | Last timestamp in the transcript |
| `Patient_Name` | Patient on the insurance record |
| `Medication` | Drug being verified/authorized |
| `Pharmacy` | Pharmacy on file |
| `Insurance` | Insurance/PBM name |
| `Member_ID` | Member ID number |
| `Prescriber` | Prescribing physician |
| `Response` | Outcome —>  Approved / Denied / Other with details |

## Project Structure

```
├── main.py           # Streamlit UI
├── transcribe.py     # Gemini audio transcription
├── summarize.py      # Gemini summarization
└── requirements.txt  # Dependencies
```

## Requirements

- Python 3.8+
- A Google Gemini API key (uses `gemini-2.5-flash`)
