# Automated Presentation Coach

This repository contains a Python script that acts as an AI-powered presentation coach. It analyzes a JSON file containing detailed data from a presentation—including slide content, speech transcription, and delivery metrics (like gaze and emotion)—and generates a comprehensive feedback report.

The script uses a local LLM (Large Language Model) via Ollama to provide qualitative, human-like coaching advice, identifying both high-level patterns and specific per-slide issues.

## Features

* **Overall Performance Analysis:** Generates a high-level summary of the entire presentation, including pacing, use of filler words, and overall delivery tone.
* **Key Issue Detection:** Automatically identifies and summarizes the most critical, recurring problems in the presentation, such as text-heavy slides, inconsistent eye contact, or distracting body language.
* **Narrative Coaching with Mistral:** Leverages the Mistral LLM to provide actionable, coach-like advice on the most important areas for improvement.
* **Per-Slide Breakdown:** Offers a detailed analysis for each slide, including a specific "Coaching Tip" from the LLM to address the most significant issue on that slide.
* **Data-Driven Insights:** Combines quantitative data (word counts, timings) with qualitative analysis to give a holistic view of the speaker's performance.

## Prerequisites

Before running the script, you need to have the following installed and configured:

1.  **Python 3:** Make sure you have a working Python 3 environment.
2.  **Ollama:** The script relies on the Ollama command-line tool to interact with the local LLM. You can download it from <https://ollama.com/>.
3.  **Mistral Model:** You need to have the Mistral model pulled and available in Ollama. You can get it by running:
    ```bash
    ollama pull mistral
    ```

## How to Use

1.  **Place Your JSON File:** Put the JSON analysis file (the one you want to analyze) in the same directory as the Python script. The script is designed to automatically find the first `.json` file in the directory.
2.  **Run the Script:** Open your terminal or command prompt, navigate to the directory containing the script and your JSON file, and run the following command:
    ```bash
    python your_script_name.py
    ```
    *(Replace `your_script_name.py` with the actual name of the script file, e.g., `presentation_analysis.py`)*
3.  **Review the Report:** The script will process the data and query the local Mistral model. This may take a few moments. Once complete, it will generate a text file named `presentation_analysis_report_v2.txt` in the same directory. This file contains the full analysis and coaching feedback.

## Input JSON Format

The script expects a JSON file with a specific structure, containing a `video_info` object and a list of `segments` (slides). Each segment should include details like `slide_id`, `duration`, `video_word_count`, `audio_word_count`, `dominant_emotion`, and `gaze_recommendation`.

## Output

The output is a single `.txt` file that includes:

* A summary of the most critical issues.
* A narrative coaching summary from the LLM.
* A detailed data breakdown of the presentation.
* A slide-by-slide analysis with specific coaching tips for each.
