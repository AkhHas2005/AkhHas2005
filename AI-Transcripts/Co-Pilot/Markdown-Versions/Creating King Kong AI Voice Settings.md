# Creating King Kong AI Voice Settings  

## Me
I'm currently trying to make an AI Call bot with the personality of King Kong the gorilla. What should I update these text to speech settings to mimic the voice of Kong:  

```Python
# Convert text to speech
def synthesize_speech(text, output_file):
    input_text = tts.SynthesisInput(text=text)
    voice = tts.VoiceSelectionParams(
        language_code="en-US",
        name="en-US-Wavenet-D",
        ssml_gender=tts.SsmlVoiceGender.MALE
    )
    audio_config = tts.AudioConfig(
        audio_encoding=tts.AudioEncoding.MP3,
        pitch=-5.0,
        speaking_rate=0.75
    )
    response = tts_client.synthesize_speech(
        input=input_text,
        voice=voice,
        audio_config=audio_config
    )
    with open(output_file, "wb") as out:
        out.write(response.audio_content)
```  
        
## Co-Pilot
That’s an awesome concept—King Kong as an AI call bot! To make the voice sound more like the mighty Kong, here are a few adjustments you might consider:

- **Pitch:** Lower it even more, perhaps around **-10.0** or **-15.0**, to give a deep and rumbling effect.
- **Speaking Rate:** Slow it down further, around **0.6**, to make the speech sound more deliberate and primal.
- **Voice Selection:** Instead of "en-US-Wavenet-D," try a voice with a richer and more guttural tone. You may need to experiment with different voices in your text-to-speech engine.
- **Add Effects:** Layer some reverberation or a subtle growl effect to give it a larger-than-life presence.

Since Kong isn’t exactly chatty, consider mixing synthesized speech with sound effects—like grunts, roars, and deep breaths—to make interactions feel more immersive.

Are you planning for it to just speak, or will it have some dynamic vocal responses based on user input?  

## Me
Can you give me the updated code?  

## Co-Pilot
Absolutely! Here’s your updated code with the adjustments for a deeper, slower, more primal King Kong voice:

```python
# Convert text to speech
def synthesize_speech(text, output_file):
    input_text = tts.SynthesisInput(text=text)
    voice = tts.VoiceSelectionParams(
        language_code="en-US",
        name="en-US-Wavenet-D",  # Try experimenting with other voices for a more guttural tone
        ssml_gender=tts.SsmlVoiceGender.MALE
    )
    audio_config = tts.AudioConfig(
        audio_encoding=tts.AudioEncoding.MP3,
        pitch=-12.0,  # Lower pitch for a more monstrous tone
        speaking_rate=0.6  # Slower speech for a powerful, deliberate effect
    )
    response = tts_client.synthesize_speech(
        input=input_text,
        voice=voice,
        audio_config=audio_config
    )
    with open(output_file, "wb") as out:
        out.write(response.audio_content)
```

You might also want to layer some **sound effects** like grunts or deep breath noises between responses, making the interaction feel more beastly.

Is your bot going to respond in full sentences, or will it mostly roar and grunt with a few key phrases? Sounds like an epic project!  

*End of this Conversation*
