WhatsApp Chat Analyzer & NLP Insights
An interactive web application built with Streamlit that transforms raw WhatsApp chat logs into a dashboard of actionable insights. This tool performs everything from statistical analysis to advanced Natural Language Processing (NLP) tasks like sentiment analysis on Hinglish text and automatic topic modeling.

Live Demo: [Your Streamlit App URL Here]

1. Project Overview
WhatsApp chat logs are unstructured text files filled with valuable data. However, manually extracting insights is impossible. This project was built to solve that problem by providing a user-friendly interface to upload a chat file and automatically generate a comprehensive report. The application answers questions like "Who is the most active user?", "What are the main topics we discuss?", and "Is the overall mood of our group positive or negative?".

The project's key challenge and feature is its ability to accurately analyze Hinglish (a mix of Hindi and English), a common language in informal chats where standard NLP tools fail.

2. Key Features
Comprehensive Statistical Dashboard: The main view displays key metrics, including total messages, words, media shared, and links. It also visualizes user activity through timelines, heatmaps, and rankings of the busiest users, days, and months.

Accurate Hinglish Sentiment Analysis: The app goes beyond simple analysis by using a state-of-the-art Hugging Face transformer model (pascalrai/hinglish-twitter-roberta-base-sentiment). This model is specifically fine-tuned on Hinglish social media text, allowing it to accurately determine if messages are positive, negative, or neutral, even with mixed-language slang.

Automatic Topic Modeling: Uses Latent Dirichlet Allocation (LDA) to automatically discover the top 5 underlying themes of the conversation. This provides a high-level summary of what the group talks about most, helping to understand the chat's purpose and focus over time.

In-Depth Word and Emoji Analysis: Identifies and visualizes the most frequently used words and emojis in the chat. This feature uses a custom Hinglish stop-word list to filter out common, non-essential words, ensuring the results are meaningful.

3. Workflow Explained
The project follows a standard data science application workflow, from data ingestion to deployment.

Data Ingestion & Preprocessing (Streamlit & preprocessor.py): The user uploads a .txt file through the Streamlit interface. A dedicated preprocessing module then parses the raw text using regular expressions to handle timestamps, separates users from messages, and converts the data into a clean, structured Pandas DataFrame.

Feature Engineering (preprocessor.py): New, useful columns (like year, month, day, hour) are extracted from the datetime objects to enable time-based analysis.

Backend Analysis (helper.py): This is the core analysis engine. It takes the clean DataFrame and applies various functions to calculate statistics and perform NLP tasks.

For sentiment analysis, it uses the cached transformer model to predict the emotion of each message.

For topic modeling, it runs the text through an NLTK-powered cleaning pipeline (lemmatization, stop-word removal) before feeding it to the Scikit-learn LDA model.

Frontend Visualization (app.py): The main application script takes the processed data and results from the helper functions and uses Matplotlib and Seaborn to generate plots, charts, and tables, which are then displayed to the user in an organized layout.

4. Folder Structure
├── app.py                  # Main Streamlit application script
├── helper.py               # All analysis and NLP functions
├── preprocessor.py         # Data cleaning and preparation function
├── requirements.txt        # Required Python libraries for deployment
├── stop_hinglish.txt       # Custom Hinglish/English stop words list
├── screenshots/            # Folder for README images
└── README.md
