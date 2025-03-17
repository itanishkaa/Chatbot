# Chatbot

This is an AI-powered chatbot built using a combination of **Speech-to-Text**, **Text-to-Speech**, and **Natural Language Processing (NLP)**. It can listen to user queries via voice input, process text input, and respond using voice output. The chatbot uses the **Google Text-to-Speech (gTTS)** API for speech synthesis, **SpeechRecognition** for speech-to-text, and a **DialoGPT** model for conversational AI. Additionally, it uses **NLTK** and **scikit-learn** for further processing of textual input and generating meaningful responses.

## Requirements
To run the chatbot, you will need the following libraries:

- `speech_recognition`: For speech-to-text functionality.
- `gTTS (Google Text-to-Speech)`: For text-to-speech output.
- `transformers`: For working with conversational AI models (e.g., DialoGPT).
- `nltk`: For text processing and tokenization.
- `numpy`: For numerical operations.
- `sklearn`: For text vectorization and similarity scoring.

You can install the required libraries using:
```bash
pip install speechrecognition gtts transformers nltk numpy scikit-learn
```

## Overview

`chatbot_ai.py`

This is the main Python script that performs the following functions:
- **Speech-to-Text:** Listens to the user's speech input using the microphone and converts it to text using the Google Speech Recognition API.
- **Text-to-Speech:** Converts the chatbot's text responses into speech using the Google Text-to-Speech (gTTS) API.
- **Wake-up Functionality:** The chatbot wakes up when its name (e.g., "Dev") is mentioned in the user's speech.
- **Chatbot Responses:** It uses the **DialoGPT-medium** model from Hugging Face's Transformers library for generating responses to user queries. The chatbot can also answer simple queries like telling the current time.
- **Text Processing:** Uses NLTK to process and normalize input text for generating more meaningful responses. It also handles greetings and thanks messages.
- **Exit Command:** The chatbot stops running when the user says "exit" or "close".

`chatbot_nltk.ipynb`

This Jupyter notebook focuses on the NLP-related aspects of the chatbot. It demonstrates
- Tokenizing text data into sentences and words using NLTK.
- Lemmatization of words.
- Using **TF-IDF** vectorization to compute similarity between user input and pre-stored responses.
- Handling greetings and generating appropriate responses based on input text.

`data.txt`

This file contains text data that the chatbot uses for processing and generating responses. The text is processed and tokenized into sentences and words, which the chatbot uses to understand and generate replies.

## How it Works
### Speech-to-Text
- The `speech_to_text()` function listens for audio input from the microphone and converts it into text using the Google Web Speech API.
- It prints the recognized text or displays an error message if it couldn't recognize anything.
### Text-to-Speech
- The `text_to_speech()` function takes a string input and converts it to speech using the `gTTS` API. The generated audio is saved to a file (`res.mp3`), played, and then deleted after the speech is played.
### Chatbot Conversation
- The chatbot uses a mix of **DialoGPT** for general conversations and **cosine similarity** to find the most appropriate responses from pre-stored text data.
- The conversation is driven by text commands and is further enriched by responses generated from the chatbot model.
### Wake-up Command
The `wake_up()` function listens for the chatbot's name in the speech input to wake up and activate the conversational mode.
### Greetings & Responses
- The chatbot recognizes common greetings such as "hello", "hi", and "how are you?" and responds accordingly. It also understands when the user says "thank you" or "thanks".
### Exiting the Chat
- The chatbot stops the conversation when the user types or says commands like "exit" or "close", and responds with various farewell messages like "Goodbye" or "Have a good day".

## Usage
- Run the chatbot using
``` bash
python chatbot_ai.py
```
Start interacting with the bot. Say "Dev" to wake it up, or type your message to start the conversation.
- The bot will respond using text-to-speech and show the text responses.
- Say "exit" or "close" to end the conversation.


## Example Interaction
```vbnet
User: "Dev, what can you do?"
Bot: "Hello, I am Dev the AI, what can I do for you?"
User: "What time is it?"
Bot: "The time is 10:45 AM."
User: "Thank you!"
Bot: "You're welcome!"
User: "Exit"
Bot: "Goodbye!"
```
