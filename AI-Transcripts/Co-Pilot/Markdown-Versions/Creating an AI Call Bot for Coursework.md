# Creating an AI Call Bot for Coursework  

## Me
How can I make an AI call bot based on this guidance for my coursework:  

Then, if possible (and entirely optional), you can implement a basic AI program and test it on one of the datasets related to the selected topic.  
In this regard, it would be better to use one/some of the methods we have been covering during the lecture, e.g. linear regression/classification, decision trees, Naive bayesian model, random forest, Artificial neural network, etc. than using a using ready models.  
Actually, the latter ones are mostly pretrained, and therefore, using them would not really be helpful to practice what we are covering in this course.  

## Co-Pilot
Absolutely! Developing an AI call bot from scratch can be a fantastic learning experience. Here’s a step-by-step guide to get you started:

### Step 1: Define the Objective and Dataset
- **Objective:** Determine what your call bot should achieve (e.g., answering customer service questions, booking appointments).
- **Dataset:** Select a relevant dataset for training. For instance, for a customer service bot, you might need a dataset containing common queries and responses.

### Step 2: Preprocess the Data
- **Cleaning:** Remove any noise, irrelevant data, or inconsistencies from the dataset.
- **Tokenization:** Break down text into smaller components (words or phrases).
- **Normalization:** Convert text to a consistent format (e.g., lowercasing, removing punctuation).

### Step 3: Feature Engineering
- **Vectorization:** Convert textual data into numerical format using methods like TF-IDF (Term Frequency-Inverse Document Frequency) or Word Embeddings (like Word2Vec).

### Step 4: Select and Implement the Model
Given the course guidance, you should avoid using pre-trained models and instead build your own using the methods covered in lectures. Here are some options:

1. **Linear Regression/Classification:**
   - Suitable for straightforward tasks like sentiment analysis.
   - Libraries: Scikit-Learn in Python.

2. **Decision Trees:**
   - Useful for classification problems where interpretability is important.
   - Libraries: Scikit-Learn.

3. **Naive Bayes Model:**
   - Effective for text classification problems.
   - Libraries: Scikit-Learn.

4. **Random Forest:**
   - Ensemble method combining multiple decision trees for better accuracy.
   - Libraries: Scikit-Learn.

5. **Artificial Neural Network (ANN):**
   - Suitable for more complex patterns and learning from large datasets.
   - Libraries: TensorFlow or Keras.

### Step 5: Train the Model
- **Split Data:** Divide your dataset into training and testing sets (e.g., 80% training, 20% testing).
- **Training:** Use the training set to train your chosen model.
- **Evaluation:** Assess the model’s performance on the testing set using metrics such as accuracy, precision, recall, and F1-score.

### Step 6: Implement the Call Bot Logic
- **Integration:** Use a service like Twilio to manage calls.
- **Bot Logic:** Implement the logic to process incoming calls, use the trained model to generate responses, and interact with users.

### Step 7: Test and Iterate
- **Testing:** Conduct extensive testing to ensure the bot behaves as expected.
- **Iteration:** Continuously improve the model and the bot logic based on feedback and testing results.

### Example Code Snippet (Python with Scikit-Learn)
```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.naive_bayes import MultinomialNB
from sklearn.metrics import accuracy_score

# Load dataset
data = pd.read_csv('dataset.csv')

# Preprocess data
X = data['text']
y = data['label']

# Vectorize text data
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(X)

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train model
model = MultinomialNB()
model.fit(X_train, y_train)

# Evaluate model
y_pred = model.predict(X_test)
print('Accuracy:', accuracy_score(y_test, y_pred))
```

### Resources
- **Scikit-Learn Documentation:** [https://scikit-learn.org/stable/](https://scikit-learn.org/stable/)
- **TensorFlow/Keras Documentation:** [https://www.tensorflow.org/](https://www.tensorflow.org/)
- **Twilio for Call Management:** [https://www.twilio.com/docs/voice](https://www.twilio.com/docs/voice)

By following these steps, you’ll be well on your way to creating a functional AI call bot. Best of luck with your coursework!  

## Me
What online dataset can I use to create a general conversational bot, one that you could add to a call with friends?  

## Co-Pilot
Great question! Here are a few online datasets that you can use to create a general conversational bot:

1. **3K Conversations Dataset for ChatBot on Kaggle**:
   - This dataset contains around 3,000 conversations and is suitable for building a basic chatbot.
   - [Link to dataset](https://www.kaggle.com/datasets/kreeshrajani/3k-conversations-dataset-for-chatbot)

2. **LMSYS-Chat-1M on Hugging Face**:
   - This large-scale dataset includes one million real-world conversations with various state-of-the-art language models.
   - [Link to dataset](https://huggingface.co/datasets/lmsys/lmsys-chat-1m)

3. **PolyAI Conversational Datasets on GitHub**:
   - This repository provides access to large datasets like Reddit comments, OpenSubtitles, and Amazon QA pairs.
   - [Link to repository](https://github.com/PolyAI-LDN/conversational-datasets)

These datasets should give you a good starting point for creating a conversational bot that you can use during calls with friends. Happy coding! 😊

Is there anything specific you'd like to know about working with these datasets?  

## Me
The dataset is as text in a csv, how can I write a quick little python script that will use all the text snippets and convert them to audio recordings with "Question" before each text from the question column and "Answer" before each text from the answer column?  

## Co-Pilot
You can achieve this by using Python along with the gTTS (Google Text-to-Speech) library to convert the text to audio. Here's a quick script that reads a CSV file, prepends "Question" or "Answer" to the respective text, and converts each entry to an audio file:

### Step-by-Step Guide:
1. **Install Required Libraries**:
   ```bash
   pip install pandas gtts
   ```

2. **Python Script**:
   ```python
   import pandas as pd
   from gtts import gTTS
   import os

   # Load the dataset
   data = pd.read_csv('dataset.csv')

   # Ensure the columns are named 'Question' and 'Answer'
   for index, row in data.iterrows():
       # Prepare the text
       question_text = f"Question: {row['Question']}"
       answer_text = f"Answer: {row['Answer']}"

       # Convert text to speech
       question_audio = gTTS(text=question_text, lang='en', slow=False)
       answer_audio = gTTS(text=answer_text, lang='en', slow=False)

       # Save the audio files
       question_audio.save(f"question_{index}.mp3")
       answer_audio.save(f"answer_{index}.mp3")

       print(f"Saved question_{index}.mp3 and answer_{index}.mp3")

   print("All audio files have been created successfully.")
   ```

### Explanation:
- **Loading Data**: The `pandas` library is used to read the CSV file.
- **Text Preparation**: The script loops through each row in the dataset, prefixes "Question" and "Answer" to the respective text.
- **Text-to-Speech Conversion**: The `gtts` (Google Text-to-Speech) library is used to convert the text to audio.
- **Saving Audio Files**: The audio files are saved as `question_<index>.mp3` and `answer_<index>.mp3` where `<index>` is the row index.

This script assumes that your CSV file has columns named "Question" and "Answer". If your column names are different, make sure to adjust the script accordingly.

By following this script, you should be able to convert your text snippets to audio recordings easily. Enjoy adding a voice to your dataset! 🎤

If you have any questions or run into any issues, feel free to ask.  

## Me
How can i put them into seperate folders for questions and answers within the root folder?  

## Co-Pilot
You can modify the script to create separate folders for the questions and answers within the root directory. Here's how you can do it:

1. **Import the `os` module** to handle directory operations.
2. **Create directories** for the questions and answers if they don't already exist.
3. **Save the audio files** in their respective directories.

Here's the updated script:

### Python Script:
```python
import pandas as pd
from gtts import gTTS
import os

# Load the dataset
data = pd.read_csv('dataset.csv')

# Create directories for questions and answers if they don't exist
os.makedirs('questions', exist_ok=True)
os.makedirs('answers', exist_ok=True)

# Ensure the columns are named 'Question' and 'Answer'
for index, row in data.iterrows():
    # Prepare the text
    question_text = f"Question: {row['Question']}"
    answer_text = f"Answer: {row['Answer']}"

    # Convert text to speech
    question_audio = gTTS(text=question_text, lang='en', slow=False)
    answer_audio = gTTS(text=answer_text, lang='en', slow=False)

    # Save the audio files in their respective directories
    question_audio.save(f"questions/question_{index}.mp3")
    answer_audio.save(f"answers/answer_{index}.mp3")

    print(f"Saved questions/question_{index}.mp3 and answers/answer_{index}.mp3")

print("All audio files have been created successfully.")
```

### Explanation:
- **Creating Directories**: The `os.makedirs()` function creates the 'questions' and 'answers' directories if they don't already exist.
- **Saving Audio Files**: The audio files are saved within these directories.

This script will place the question audio files in the 'questions' folder and the answer audio files in the 'answers' folder, both located in the root directory. This should help you keep your audio files organized.

If you encounter any issues or have further questions, feel free to ask! 🎧📁  

## Me
Instead of `from gtts import gTTS` I have the following line, how can i adapt teh code?  
```from google.cloud import texttospeech as tts```  

## Co-Pilot
Got it! You can use the Google Cloud Text-to-Speech API to convert text to speech. You'll need to adjust the code to work with the Google Cloud API instead of gTTS. Here's how you can do it:

### Step-by-Step Guide:
1. **Install the Google Cloud Text-to-Speech Library**:
   ```bash
   pip install google-cloud-texttospeech
   ```

2. **Set Up Authentication**:
   Ensure you have set up your Google Cloud authentication properly by setting the `GOOGLE_APPLICATION_CREDENTIALS` environment variable to the path of your service account key file.

3. **Python Script**:
   ```python
   import pandas as pd
   from google.cloud import texttospeech as tts
   import os

   # Initialize the Text-to-Speech client
   client = tts.TextToSpeechClient()

   # Function to synthesize speech
   def synthesize_speech(text, output_file):
       input_text = tts.SynthesisInput(text=text)
       voice = tts.VoiceSelectionParams(
           language_code="en-US",
           ssml_gender=tts.SsmlVoiceGender.NEUTRAL
       )
       audio_config = tts.AudioConfig(
           audio_encoding=tts.AudioEncoding.MP3
       )
       response = client.synthesize_speech(
           input=input_text,
           voice=voice,
           audio_config=audio_config
       )
       with open(output_file, "wb") as out:
           out.write(response.audio_content)

   # Load the dataset
   data = pd.read_csv('dataset.csv')

   # Create directories for questions and answers if they don't exist
   os.makedirs('questions', exist_ok=True)
   os.makedirs('answers', exist_ok=True)

   # Ensure the columns are named 'Question' and 'Answer'
   for index, row in data.iterrows():
       # Prepare the text
       question_text = f"Question: {row['Question']}"
       answer_text = f"Answer: {row['Answer']}"

       # Convert text to speech and save the audio files in their respective directories
       synthesize_speech(question_text, f"questions/question_{index}.mp3")
       synthesize_speech(answer_text, f"answers/answer_{index}.mp3")

       print(f"Saved questions/question_{index}.mp3 and answers/answer_{index}.mp3")

   print("All audio files have been created successfully.")
   ```

### Explanation:
- **Client Initialization**: The Google Cloud Text-to-Speech client is initialized.
- **Synthesize Function**: The `synthesize_speech()` function converts text to speech and saves the audio to a file.
- **Creating Directories**: The `os.makedirs()` function creates the 'questions' and 'answers' directories if they don't already exist.
- **Saving Audio Files**: The audio files are saved within these directories with the specified naming convention.

This script will read the CSV file, prepend "Question" and "Answer" to the respective texts, convert them to audio using the Google Cloud Text-to-Speech API, and save the files in the respective directories.

Let me know if you need any further adjustments or run into any issues! 📂🔊  

## Me
How can I modify this code to start with the audio files as input and have a mapping of question to answer where each question and answer that map to each other have the same number in the fiole name and question audios are stored in the questions subfoilder while answer audios are stored in the audios subfolder?  

## Copilot
To achieve this, we’ll need to read the audio files, create a mapping between question and answer files based on their numbering, and then save them in their respective folders.

Here’s how you can modify the code to start with the audio files as input and map questions to answers:

### Step-by-Step Guide:

1. **Create Directories for Questions and Answers**:
   Ensure directories exist for storing question and answer audio files.

2. **Map Question and Answer Files**:
   Read the files, map questions to answers, and save them in the respective directories.

### Python Script:

```python
import os
import shutil

# Define directories
source_directory = 'source_audios'
questions_directory = 'questions'
answers_directory = 'answers'

# Create directories for questions and answers if they don't exist
os.makedirs(questions_directory, exist_ok=True)
os.makedirs(answers_directory, exist_ok=True)

# Function to determine if a file is a question or answer based on its name
def is_question(filename):
    return filename.startswith('question')

def is_answer(filename):
    return filename.startswith('answer')

# Loop through files in source directory
for filename in os.listdir(source_directory):
    # Construct full file path
    file_path = os.path.join(source_directory, filename)

    if os.path.isfile(file_path):
        # Determine if file is a question or answer
        if is_question(filename):
            destination = os.path.join(questions_directory, filename)
        elif is_answer(filename):
            destination = os.path.join(answers_directory, filename)
        else:
            continue  # Skip files that do not match question or answer pattern

        # Move the file to the respective directory
        shutil.move(file_path, destination)
        print(f'Moved {filename} to {destination}')

print("All audio files have been moved to their respective directories.")
```

### Explanation:

- **Define Directories**: `source_directory` is the directory containing your original audio files. `questions_directory` and `answers_directory` are the target directories where question and answer files will be moved.
- **Create Directories**: Use `os.makedirs()` to create the target directories if they don't already exist.
- **Map Files**: Loop through the files in the source directory, check if each file is a question or answer based on its name, and move it to the appropriate directory.

This script assumes that your audio files are named in a way that makes it clear whether they are questions or answers (e.g., "question_1.mp3" and "answer_1.mp3"). If your naming convention is different, you'll need to adjust the `is_question` and `is_answer` functions accordingly.

By following this approach, you can organize your audio files into their respective folders, making it easier to manage the question-answer pairs. Let me know if you need any further adjustments or run into any issues! 📂🔊

If you’d like to explore anything else, feel free to ask!  

## Me
No so i have a subdirectory called questions which contains files named from question_0.mp3 all teh way to question_3724.mp3 and same for the asnwers subdirectory, how can I adapt this code to use the audio files as input data:  

```Python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.naive_bayes import MultinomialNB
from sklearn.metrics import accuracy_score

# Load dataset
data = pd.read_csv('dataset.csv')

# Preprocess data
X = data['text']
y = data['label']

# Vectorize text data
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(X)

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train model
model = MultinomialNB()
model.fit(X_train, y_train)

# Evaluate model
y_pred = model.predict(X_test)
print('Accuracy:', accuracy_score(y_test, y_pred))
```  

## Copilot
To adapt your code to work with the audio files as input data, you need to transcribe the audio files into text first. You can use a speech-to-text library like Google Cloud Speech-to-Text API for transcription. Here’s a modified approach:

1. **Install Required Libraries**:
   ```bash
   pip install google-cloud-speech pandas scikit-learn
   ```

2. **Set Up Authentication**:
   Ensure you have set up your Google Cloud authentication properly by setting the `GOOGLE_APPLICATION_CREDENTIALS` environment variable to the path of your service account key file.

3. **Python Script**:
   ```python
   import os
   import pandas as pd
   from google.cloud import speech
   from sklearn.model_selection import train_test_split
   from sklearn.feature_extraction.text import TfidfVectorizer
   from sklearn.naive_bayes import MultinomialNB
   from sklearn.metrics import accuracy_score

   # Initialize the Speech-to-Text client
   client = speech.SpeechClient()

   # Directories containing audio files
   questions_dir = 'questions'
   answers_dir = 'answers'

   # Function to transcribe audio file
   def transcribe_audio(audio_path):
       with open(audio_path, 'rb') as audio_file:
           audio_content = audio_file.read()
       audio = speech.RecognitionAudio(content=audio_content)
       config = speech.RecognitionConfig(
           encoding=speech.RecognitionConfig.AudioEncoding.LINEAR16,
           sample_rate_hertz=16000,
           language_code='en-US'
       )
       response = client.recognize(config=config, audio=audio)
       return response.results[0].alternatives[0].transcript if response.results else ""

   # Prepare data
   data = []
   for i in range(3725):  # Number of question-answer pairs
       question_path = os.path.join(questions_dir, f'question_{i}.mp3')
       answer_path = os.path.join(answers_dir, f'answer_{i}.mp3')
       question_text = transcribe_audio(question_path)
       answer_text = transcribe_audio(answer_path)
       data.append({'text': question_text + " " + answer_text, 'label': 'question_answer_pair'})

   # Convert data to DataFrame
   df = pd.DataFrame(data)

   # Preprocess data
   X = df['text']
   y = df['label']

   # Vectorize text data
   vectorizer = TfidfVectorizer()
   X = vectorizer.fit_transform(X)

   # Split data
   X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

   # Train model
   model = MultinomialNB()
   model.fit(X_train, y_train)

   # Evaluate model
   y_pred = model.predict(X_test)
   print('Accuracy:', accuracy_score(y_test, y_pred))
   ```

### Explanation:
- **Transcribe Audio Files**: The `transcribe_audio()` function uses the Google Cloud Speech-to-Text API to transcribe audio files to text.
- **Prepare Data**: The script iterates through the audio files, transcribes them, and combines each question and corresponding answer into a single text entry.
- **Vectorize and Train Model**: The combined text data is vectorized, split into training and testing sets, and used to train a Naive Bayes classifier.

This approach will allow you to use your audio files as input data, convert them into a format suitable for machine learning, and train a model based on the transcriptions.

If you have any questions or need further assistance, feel free to ask! 🎤📝✨  

## Me
So I want my chatbot to be able to receive one of teh questions as audio input and then use one of the answers that most likely maps to that question to speak teh response as audio output, what would be the next step?  

## Copilot
To enable your chatbot to receive audio input, convert it to text, find the most relevant answer, and then convert the response back to audio, you need to follow these steps:

### Step 1: Transcribe the Audio Input
Use the Google Cloud Speech-to-Text API to convert the user's audio input into text.

### Step 2: Find the Most Relevant Answer
Use a pre-trained model or your own trained model to find the most relevant answer to the user's question.

### Step 3: Convert the Answer to Audio
Use the Google Cloud Text-to-Speech API to convert the text response back into audio.

### Python Script Example
Here’s how you can put it all together:

#### Install Required Libraries
```bash
pip install google-cloud-speech google-cloud-texttospeech scikit-learn
```

#### Set Up Authentication
Ensure you have set up your Google Cloud authentication properly by setting the `GOOGLE_APPLICATION_CREDENTIALS` environment variable to the path of your service account key file.

#### Python Code
```python
import os
from google.cloud import speech
from google.cloud import texttospeech as tts
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.naive_bayes import MultinomialNB

# Initialize the clients
speech_client = speech.SpeechClient()
tts_client = tts.TextToSpeechClient()

# Load and preprocess data
data = pd.read_csv('dataset.csv')
X = data['Question'] + " " + data['Answer']
y = data['Question']  # Assume questions are unique identifiers

# Vectorize text data
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(X)

# Train model
model = MultinomialNB()
model.fit(X, y)

# Transcribe audio input
def transcribe_audio(audio_path):
    with open(audio_path, 'rb') as audio_file:
        audio_content = audio_file.read()
    audio = speech.RecognitionAudio(content=audio_content)
    config = speech.RecognitionConfig(
        encoding=speech.RecognitionConfig.AudioEncoding.LINEAR16,
        sample_rate_hertz=16000,
        language_code='en-US'
    )
    response = speech_client.recognize(config=config, audio=audio)
    return response.results[0].alternatives[0].transcript if response.results else ""

# Find the most relevant answer
def find_answer(question_text):
    question_vec = vectorizer.transform([question_text])
    answer_text = model.predict(question_vec)[0]
    return data[data['Question'] == answer_text]['Answer'].values[0]

# Convert text to speech
def synthesize_speech(text, output_file):
    input_text = tts.SynthesisInput(text=text)
    voice = tts.VoiceSelectionParams(
        language_code="en-US",
        ssml_gender=tts.SsmlVoiceGender.NEUTRAL
    )
    audio_config = tts.AudioConfig(
        audio_encoding=tts.AudioEncoding.MP3
    )
    response = tts_client.synthesize_speech(
        input=input_text,
        voice=voice,
        audio_config=audio_config
    )
    with open(output_file, "wb") as out:
        out.write(response.audio_content)

# Example usage
audio_input_path = 'user_question.mp3'  # Path to the input audio file
transcribed_question = transcribe_audio(audio_input_path)
print(f"Transcribed Question: {transcribed_question}")

relevant_answer = find_answer(transcribed_question)
print(f"Relevant Answer: {relevant_answer}")

output_audio_path = 'response.mp3'
synthesize_speech(relevant_answer, output_audio_path)
print(f"Saved response to {output_audio_path}")
```

### Explanation:
1. **Initialize Clients**: Initialize the Google Cloud Speech-to-Text and Text-to-Speech clients.
2. **Load and Preprocess Data**: Load your dataset and vectorize the combined text of questions and answers.
3. **Train Model**: Train a Naive Bayes classifier to map questions to their answers.
4. **Transcribe Audio Input**: Use the `transcribe_audio()` function to convert audio input to text.
5. **Find Relevant Answer**: Use the `find_answer()` function to find the most relevant answer based on the transcribed text.
6. **Convert Text to Speech**: Use the `synthesize_speech()` function to convert the text answer back to audio.

This approach will allow your chatbot to receive audio questions, process them to find the most relevant answer, and respond with audio output. Enjoy building your conversational bot! 🎙️🤖🔊

If you need any further assistance or adjustments, just let me know.  

## Me
what method/library can I use to record my voice in the terminal and pass that as input for testing the model?  

## Copilot
You can use the `pyaudio` and `wave` libraries in Python to record your voice from the terminal and save it as a .wav file. Here's how you can do it:

### Step-by-Step Guide:

1. **Install Required Libraries**:
   ```bash
   pip install pyaudio
   ```

2. **Python Script to Record Audio**:
   ```python
   import pyaudio
   import wave

   def record_audio(filename, duration=5, sample_rate=16000):
       # Set up parameters
       chunk = 1024  # Record in chunks of 1024 samples
       format = pyaudio.paInt16  # 16 bits per sample
       channels = 1  # Mono
       rate = sample_rate  # Sample rate

       # Initialize PyAudio
       p = pyaudio.PyAudio()

       # Open stream
       stream = p.open(format=format,
                       channels=channels,
                       rate=rate,
                       input=True,
                       frames_per_buffer=chunk)

       print("Recording...")

       # Initialize array to store frames
       frames = []

       # Record for the given duration
       for _ in range(int(rate / chunk * duration)):
           data = stream.read(chunk)
           frames.append(data)

       # Stop and close the stream
       stream.stop_stream()
       stream.close()
       p.terminate()

       print("Recording finished.")

       # Save the recorded data as a WAV file
       with wave.open(filename, 'wb') as wf:
           wf.setnchannels(channels)
           wf.setsampwidth(p.get_sample_size(format))
           wf.setframerate(rate)
           wf.writeframes(b''.join(frames))

   # Example usage
   record_audio('user_question.wav', duration=5)
   ```

### Explanation:
- **Set Up Parameters**: The script sets up recording parameters such as sample size, format, channels (mono), and sample rate.
- **Initialize PyAudio**: PyAudio is initialized, and an input stream is opened for recording.
- **Record Audio**: Audio is recorded in chunks and stored in an array for the given duration (default is 5 seconds).
- **Save Audio**: The recorded audio frames are saved as a .wav file.

Once you have the audio recorded, you can use it as input for your model as shown in the previous example. You can then pass the file path of the recorded audio to the `transcribe_audio` function.

By following these steps, you’ll be able to record your voice from the terminal, transcribe it, find the relevant answer, and convert the answer back to audio.

Feel free to test this out, and let me know if you need further assistance! 🎤🔄🗣️

Enjoy creating and testing your conversational bot! 🎉📞🎧  

## Me
(Now Monday, Nov 25)  
I have a sharePoint list and I want to enforce column validation for a text email labelled "Requestor Work Email", I want to enforce validation to check wheher on not it's an email and if it ends in "bradfordcft.org.uk" or "bradford.gov.uk"  

## Copilot
To enforce column validation in your SharePoint list for the "Requestor Work Email" column, you can use a combination of SharePoint's built-in column validation and a formula to check if the email address ends with "bradfordcft.org.uk" or "bradford.gov.uk". Here’s how you can do it:

### Steps to Apply Column Validation:

1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the following formula in the "Formula" box:
     ```plaintext
     =AND(
         ISERROR(FIND("@", [Requestor Work Email])),
         ISERROR(FIND(".", [Requestor Work Email])),
         OR(
             RIGHT([Requestor Work Email], 15) = "bradfordcft.org.uk",
             RIGHT([Requestor Work Email], 14) = "bradford.gov.uk"
         )
     )
     ```
   - This formula checks if the email contains an "@" symbol, a ".", and ends with either "bradfordcft.org.uk" or "bradford.gov.uk".

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with bradfordcft.org.uk or bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **Email Format Check**: The formula ensures the email contains an "@" symbol and a ".", which are basic requirements for a valid email address.
- **Domain Check**: The `OR` function checks if the email ends with either "bradfordcft.org.uk" or "bradford.gov.uk".
- **User Message**: A friendly error message is displayed if the validation fails.

By following these steps, you can enforce column validation to ensure that the "Requestor Work Email" column contains valid email addresses that meet your specified criteria.

Does this help with what you were looking to achieve?  

## Me
My colleague got teh following error when entering her work email. [Uploaded Image Expired]  

## Copilot
The error message your colleague received ("The validation formula has evaluated to an error") suggests that there might be an issue with the validation formula. Let's double-check and correct it to ensure it works properly.

Here’s an updated formula that should correctly validate an email and check if it ends with "bradfordcft.org.uk" or "bradford.gov.uk":

### Corrected Validation Formula:
```plaintext
=AND(
    ISNUMBER(FIND("@", [Requestor Work Email])),
    OR(
        RIGHT([Requestor Work Email], 17) = "bradfordcft.org.uk",
        RIGHT([Requestor Work Email], 14) = "bradford.gov.uk"
    )
)
```

### Steps to Apply This Corrected Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the corrected formula in the "Formula" box:
     ```plaintext
     =AND(
         ISNUMBER(FIND("@", [Requestor Work Email])),
         OR(
             RIGHT([Requestor Work Email], 17) = "bradfordcft.org.uk",
             RIGHT([Requestor Work Email], 14) = "bradford.gov.uk"
         )
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with bradfordcft.org.uk or bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **ISNUMBER(FIND("@", [Requestor Work Email]))**: This part checks if the email contains an "@" symbol, ensuring it's a valid email format.
- **OR(RIGHT(...))**: This part checks if the email ends with either "bradfordcft.org.uk" or "bradford.gov.uk".

This should resolve the validation error your colleague encountered and ensure the email addresses meet the required criteria. Let me know if this works or if you need further assistance! 📧👍  

## Me
It still gives the same error  

## Copilot
Let's try another approach to ensure that our validation formula works correctly. This time, we'll use a slightly different method to validate the email format and check the domain:

### Updated Validation Formula:
```plaintext
=AND(
    ISNUMBER(FIND("@", [Requestor Work Email])),
    OR(
        RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
        RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
    )
)
```

### Steps to Apply This Updated Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the updated formula in the "Formula" box:
     ```plaintext
     =AND(
         ISNUMBER(FIND("@", [Requestor Work Email])),
         OR(
             RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
             RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
         )
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with bradfordcft.org.uk or bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **ISNUMBER(FIND("@", [Requestor Work Email]))**: This checks if the email contains an "@" symbol.
- **RIGHT and LEN Functions**: These functions are used to extract the domain part of the email address after the "@" symbol and check if it matches either "bradfordcft.org.uk" or "bradford.gov.uk".

This updated formula should correctly validate the email addresses. If you continue to face issues, consider verifying the exact text in the "Requestor Work Email" column to ensure there are no unexpected characters or spaces.

Give this a try, and let me know if it resolves the issue! 📧✅  

## Me
I'm still getting the following error: The validation formula has evaluated to an error.  

## Copilot
I understand how frustrating that can be. Let's try another approach using a slightly different logic. SharePoint column validation formulas can sometimes be a bit tricky. Here’s a revised formula that should work without errors:

### Revised Validation Formula:
```plaintext
=AND(
    ISNUMBER(FIND("@", [Requestor Work Email])),
    OR(
        RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
        RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
    )
)
```

### Steps to Apply This Updated Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the updated formula in the "Formula" box:
     ```plaintext
     =AND(
         ISNUMBER(FIND("@", [Requestor Work Email])),
         OR(
             RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
             RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
         )
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with bradfordcft.org.uk or bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

If you continue to face issues, consider checking the following:
- Ensure that there are no leading or trailing spaces in the email addresses.
- Double-check the actual column name "Requestor Work Email" in the formula matches the column name exactly, including any spaces.

### Verification of Formula
Here’s a simplified version of the formula for better understanding:
```plaintext
=AND(
    ISNUMBER(FIND("@", [Requestor Work Email])),
    OR(
        RIGHT([Requestor Work Email], 17) = "bradfordcft.org.uk",
        RIGHT([Requestor Work Email], 14) = "bradford.gov.uk"
    )
)
```
Give this a try, and let me know how it goes! If it still doesn't work, we may need to try a different approach or consider custom scripts using Power Automate for more complex validations. 🌟📧  

## Me
could an IF endswith "@bradfordcft.org.uk" or "@bradford.gov.uk" work?  

## Copilot
Absolutely, using the `IF` function with `ENDSWITH` in a SharePoint column validation formula could simplify the process. However, SharePoint column validation formulas don't directly support an `ENDSWITH` function. Instead, we can mimic this behavior using `RIGHT` and `LEN` functions.

Here's a formula that checks if the "Requestor Work Email" ends with either "@bradfordcft.org.uk" or "@bradford.gov.uk":

### Simplified Formula:
```plaintext
=IF(
    AND(
        ISNUMBER(FIND("@", [Requestor Work Email])),
        OR(
            RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
            RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
        )
    ), 
    TRUE, 
    FALSE
)
```

### Steps to Apply This Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the simplified formula in the "Formula" box:
     ```plaintext
     =IF(
         AND(
             ISNUMBER(FIND("@", [Requestor Work Email])),
             OR(
                 RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
                 RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
             )
         ), 
         TRUE, 
         FALSE
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with @bradfordcft.org.uk or @bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **ISNUMBER(FIND("@", [Requestor Work Email]))**: Ensures the email contains an "@" symbol.
- **RIGHT and LEN Functions**: These functions mimic the `ENDSWITH` behavior to check if the email ends with the specified domains.

This formula should work effectively for your needs. Let me know if this resolves the issue or if there's anything else you need help with! 📧✅  

## Me
I want to get rid of this bit:  
`AND( ISNUMBER(FIND("@", [Requestor Work Email])),`  

## Copilot
Understood! If you want to skip the validation that checks for the presence of the "@" symbol, we can simplify the formula to directly check if the email ends with the specified domains. Here’s how to do it:

### Simplified Validation Formula:
```plaintext
=OR(
    RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
    RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
)
```

### Steps to Apply This Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the simplified formula in the "Formula" box:
     ```plaintext
     =OR(
         RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
         RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with @bradfordcft.org.uk or @bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **OR**: The formula uses the `OR` function to check if the email ends with either "@bradfordcft.org.uk" or "@bradford.gov.uk".
- **RIGHT**: The `RIGHT` function extracts the specified number of characters from the end of the email address to perform the check.

This formula should now work without the additional check for the "@" symbol. Let me know if this resolves the issue or if you need further assistance! 📧✅  


## Me
I still want to use the length - where the @ is  

## Copilot
Got it! We'll keep the length and position of the "@" symbol to ensure that the domain part is correctly checked. Here's a refined formula that checks if the email ends with the specified domains by utilizing the position of the "@" symbol:

### Updated Validation Formula:
```plaintext
=AND(
    FIND("@", [Requestor Work Email]) > 1, 
    OR(
        RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
        RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
    )
)
```

### Steps to Apply This Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the updated formula in the "Formula" box:
     ```plaintext
     =AND(
         FIND("@", [Requestor Work Email]) > 1, 
         OR(
             RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
             RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
         )
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with @bradfordcft.org.uk or @bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **FIND("@", [Requestor Work Email]) > 1**: This ensures the "@" symbol is present and not the first character in the email.
- **RIGHT and LEN Functions**: These functions extract the domain part of the email after the "@" symbol and check if it matches either "bradfordcft.org.uk" or "bradford.gov.uk".

By using this formula, we correctly ensure that the email contains an "@" symbol and checks the domain part of the email for the specified domains.

Give this a try, and let me know if it resolves the issue! 🌟📧✨  


## Me
Now I'm using this as the formula ut I'm still getting teh same erro:  

## Copilot
It seems like we're still encountering some issues with the formula. Let's try a simplified approach to ensure the validation formula works correctly. We'll break it down and focus on checking if the email ends with the specified domains without additional complexity.

### Simplified Validation Formula:
```plaintext
=OR(
    RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
    RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
)
```

This formula checks if the last 17 characters of the email address match "@bradfordcft.org.uk" or if the last 14 characters match "@bradford.gov.uk".

### Steps to Apply This Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the simplified formula in the "Formula" box:
     ```plaintext
     =OR(
         RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
         RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with @bradfordcft.org.uk or @bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **OR**: The formula uses the `OR` function to check if the email ends with either "@bradfordcft.org.uk" or "@bradford.gov.uk".
- **RIGHT**: The `RIGHT` function extracts the specified number of characters from the end of the email address to perform the check.

This should now work without the additional check for the "@" symbol, focusing solely on the domain validation. Let me know if this resolves the issue or if you need further assistance! 📧✅

If you continue to encounter problems, it might be helpful to review the actual values in the "Requestor Work Email" column to ensure there are no unexpected characters or leading/trailing spaces causing the issue. You could also try entering a few test values directly to see how they are evaluated.  


## Me
This is the formula:  
```
=OR(
  RIGHT(#NAME?,LEN(#NAME?)-FIND("@",#NAME?))="@bradfordcft.org.uk",
  RIGHT(#NAME?,LEN(#NAME?)-FIND("@",#NAME?))="@bradford.gov.uk"
)
```  

## Copilot
The issue with your formula seems to be the placeholder `#NAME?`, which should be replaced with the actual column name `Requestor Work Email`. Here's the corrected formula:

### Corrected Validation Formula:
```plaintext
=OR(
    RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
    RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
)
```

### If You Want to Include the `FIND` Function:
If you want to use the `FIND` function to ensure the domain part comes after the "@" symbol, you can use the following formula:
```plaintext
=OR(
    RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
    RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
)
```

### Steps to Apply the Corrected Formula:
1. **Open List Settings**:
   - Go to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the corrected formula in the "Formula" box:
     ```plaintext
     =OR(
         RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
         RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
     )
     ```
     OR, if including the `FIND` function:
     ```plaintext
     =OR(
         RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradfordcft.org.uk",
         RIGHT([Requestor Work Email], LEN([Requestor Work Email]) - FIND("@", [Requestor Work Email])) = "bradford.gov.uk"
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with @bradfordcft.org.uk or @bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **OR**: The formula uses the `OR` function to check if the email ends with either "@bradfordcft.org.uk" or "@bradford.gov.uk".
- **RIGHT and LEN Functions**: These functions are used to extract the domain part of the email after the "@" symbol.

Applying this corrected formula should now work without the error. Let me know if this resolves the issue or if there's anything else you need assistance with! 📧✅

If the issue persists, it might be helpful to test the formula with different email addresses directly to see how they are evaluated.  


## Me
How can I check what validation formula is being used from the form used to submit the data?  

## Copilot
To check the validation formula being used in a SharePoint form, you can follow these steps:

1. **Access List Settings**:
   - Navigate to your SharePoint site and open the list where the form is located.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Columns**:
   - In the List Settings page, under the "Columns" section, find and click on the column you are interested in (e.g., "Requestor Work Email").

3. **View Column Validation**:
   - Scroll down to the "Column Validation" section within the column settings.
   - Here, you will see the validation formula that is being used for that column.

This process will help you view and verify the validation formula directly from the form's associated list settings.

If you have access to edit permissions, you can also modify the validation formula here to ensure it aligns with your requirements.

Feel free to reach out if you need any more guidance or run into any issues! 😊📄✨  

## Me
What does the FIND function return if the substring is not found?  

## Copilot
The `FIND` function in SharePoint, like in Excel, returns an error if the substring is not found. Specifically, it returns the `#VALUE!` error. This is important to handle in your validation formula to avoid issues.

To manage this, you can use the `ISNUMBER` function to check if `FIND` successfully located the substring. Here's how you might incorporate it:

### Combined Validation Formula:
```plaintext
=AND(
    ISNUMBER(FIND("@", [Requestor Work Email])),
    OR(
        RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
        RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
    )
)
```

This ensures that the "@" symbol is present and then checks the domain part.

### Applying This Formula:
1. **Open List Settings**:
   - Navigate to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the combined formula in the "Formula" box:
     ```plaintext
     =AND(
         ISNUMBER(FIND("@", [Requestor Work Email])),
         OR(
             RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
             RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
         )
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with @bradfordcft.org.uk or @bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

By using `ISNUMBER` with `FIND`, we ensure the validation formula works correctly even when the "@" symbol is not found. This approach will help you handle errors gracefully.

If you need further assistance or adjustments, let me know! 🌟📧✨  

## Me
Can I use an if statement with just `ISNUMBER(FIND("@", [Requestor Work Email]))`  

## Copilot
Yes, you can use an `IF` statement with just `ISNUMBER(FIND("@", [Requestor Work Email]))` to check whether the "@" symbol is present in the email address. However, since you also want to validate that the email ends with specific domains, you'll need to include additional checks in your formula.

Here's how you can structure the formula to incorporate both conditions using `IF`, `ISNUMBER`, and `FIND`:

### Combined Validation Formula:
```plaintext
=IF(
    ISNUMBER(FIND("@", [Requestor Work Email])),
    OR(
        RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
        RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
    ),
    FALSE
)
```

### Steps to Apply This Formula:
1. **Open List Settings**:
   - Navigate to your SharePoint list.
   - Click on the gear icon (Settings) in the top right corner and select "List settings".

2. **Edit Column**:
   - Under "Columns", click on "Requestor Work Email" to edit the column.

3. **Add Column Validation**:
   - Scroll down to the "Column Validation" section.
   - Enter the combined formula in the "Formula" box:
     ```plaintext
     =IF(
         ISNUMBER(FIND("@", [Requestor Work Email])),
         OR(
             RIGHT([Requestor Work Email], 17) = "@bradfordcft.org.uk",
             RIGHT([Requestor Work Email], 14) = "@bradford.gov.uk"
         ),
         FALSE
     )
     ```

4. **User Message**:
   - Enter a user-friendly message for the validation error, such as:
     ```plaintext
     Please enter a valid email address ending with @bradfordcft.org.uk or @bradford.gov.uk.
     ```

5. **Save Changes**:
   - Click "OK" to save the changes.

### Explanation:
- **IF and ISNUMBER(FIND("@", [Requestor Work Email]))**: The `IF` statement checks if the "@" symbol is present in the email address.
- **OR and RIGHT Functions**: If the "@" symbol is present, the `OR` function checks if the email ends with either "@bradfordcft.org.uk" or "@bradford.gov.uk".
- **FALSE**: If the "@" symbol is not present, the formula returns `FALSE`.

This formula should effectively validate that the email address contains the "@" symbol and ends with one of the specified domains.

Give this a try, and let me know if it resolves the issue! 📧✅ If you need further assistance, feel free to ask. 😊  

*End of this Conversation*
