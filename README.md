# Project Name
Effective Meeting Summaries with LLMs (CS224v)

## Description
This project is a code repository for preprocessing data, making structured data, and generating meeting summaries. Right now, we have been asked to not provide the datasets for privacy reasons. If you want to know more please contact us or our mentor Dr. Alissa Cooperman for the datasets.

## Installation
1. Install the needed dependencies for the notebook.
2. Likely will need pandas and numpy
3. Easiest option is to pull all the files into Google Colab since many cells have been set up to read from a Google Drive.

## Basic explanation
1. You need to setup the notebook by doing the Google drive mounts and relevant installations. Also make sure to add open ai org and api keys where marked.
2. Get the datasets, both the gold labeled and the raw meeting transcripts.
3. Preprocess the data by running the breakdown finder.
4. To run summarizations, go to one of the model sections (Naive 1, Naive 1+, Naive 2, Complex 1, Complex 2) and run all the cells for a section. It will send the output to a google doc
5. Note that Complex 1 is in a different notebook called Complex1 CS224v project.ipynb. But the section for Complex 1 is exactly the same.


## Usage
1. Open the CS224v project.ipynb
2. Run all cells that pip install. For example: !pip install --upgrade openai
3. If you want to preprocess the data, look at the "Find breakdowns in structured data" section and "Complex 2" section
4. If you want to run evals for the breakdown finder, it should be under the "Evaluate breakdown finder" section
4. Complex 2 has some function at the beginning to process a raw transcript, make a transcript out of the labeled data.
5. Follow the format of existing cells. For example, in the Naive 1 section, you can make a summary with Naive 1 by getting the raw transcript, then calling naive1_summarize
6. Generated summaries are saved to your Google Drive as a docx. Adjust the file path accordingly.
7. As another example, if you want to just run the Complex 2 summaries, just go to the Complex 2 section and run all the cells. It will again output to your specified file path as a doc. However, you need to have first generated the labeled data with breakdowns for a specific meeting.
8. You can generate all the breakdown tags and the context windows by going to the Find breakdowns in structured data section. Just run all those cells.
9. If you need to follow a less confusing example, please check out the CS224V Project Demo.ipynb and the demo video. Again, the demo notebook still needs to you preprocess the transcripts ahead of time using the steps above.
10. If you want to run the automated evaluations, go to the Complex 1 CS224v project.ipynb. Start from A/B evaluation using LLMs section. Change the file names appropriately, like the input should be the gold summary and the generated summary from a model. Run all those cells.
11. For those evaluations, there is one section called "original for comparing every summary to gold", which will compare summaries to the gold summary. There is also a section called "A/B testing for complex 1 and complex 2" which will compare complex 1 and complex 2 summaries. This is important because the inputs are different and have different prompts.
12. If you want to see our second attempt at automating the MtD Coding process by using binary classification to find rows that are directive + product, run the CS224V_Direct_Product.ipynb in its entirety.


## Outputs 
If you run the notebooks correctly you should get the following files:
- preprocessed_{meeting date}.csv which should have columns for turn, start time, speaker, utterance, speech act, deepand, rrs, pop, ffb, conversation, combined_utterance, breakdown_context, context_speakers, breakdown
- breakdown_convos_{meeting date}.txt which should be a paragraph of breakdown conversations with the speaker prepended to each conversation
- convos_code_{meeting date}.txt which should be the labeled transcript but prepended with the speaker and the tags as (speech act, deepand, pop, breakdown?)
- {model name}_{meeting date}_meeting_summary.docx which should be the outputted meeting summary from running a model on a transcript (either the raw transript for naive models or convos coded for complex models)

## Authors
Justin Lim and Winston Shum

