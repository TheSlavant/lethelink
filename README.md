![Lethelink Logo](public/logo_with_footnote.png)

# Lethelink

Lethelink is an interface to create grounding messages for people who suffer from anterograde amnesia. The messages can be delivered to the person's hearing aid on a schedule to prevent episodes of disorientation.

## Introduction

Caregivers can use Lethelink to create messages (anchors) that ground their Patient in reality, remind them they are safe, and help them orient in time and space. 

🌿 Anchors are context-aware. They are created based on the context about the Patient and their daily schedule, which can be provided by the Caregiver, and the current time. For example, if the Caregiver mentioned that "lunch is at 12pm" and it's 11:45am, an anchor may notify the Patient that lunch is coming up.
🌿 With one voice sample, Lethelink can send anchors in the Caregiver's voice, which is more familiar to the Patient. 
🌿 (coming soon) Prevent the onset of disorientation by selecting what causes an anchor to send: time, Patient's voice, or increased heartbeat.

The Caregiver can set the context for the anchor through a UI that looks like this:

![Lethlink UI](public/ui.png) 

## Demo
 
In this demo video, we show how an anchor generated from the voice of our teammate Paul could help his elderly mother avoid the state of disorientation. 

[![Video thumbnail](public/demo.png)](https://youtu.be/kUsAV1t3ieg)

## Opportunities

Engineering
- Add new anchor triggers: time, heart rate, voice.
- Build a more streamlined hearing aid integration.
- Create an end-to-end UI that connects all the pieces together.

Research
- Stduy the effect of reality anchors on people with Alzheimer's. Can it be an evidence-based clinical practice?
- Can people with amnesia learn to anticipate Lethelink and rely on it?

## Getting Started

**Note:** We walk through every step in this guide, but if you don't code and are not sure what to do, reach out to [Yaroslav](https://twitter.com/TheSlavant) to get help with the setup.

### Prerequisites

- An account at [ElevenLabs](https://elevenlabs.io/)
- An account at [OpenAI](https://platform.openai.com/overview)

### Installation & Setup

1. **Environment Variables Setup**
   Clone the Lethelink repository to your local machine. Inside the project directory, you need to set up your environment variables:

   - `ELEVEN_LABS_API_KEY`: API key generated from Eleven Labs.
   - `OPENAI_API_KEY`: API key generated from OpenAI.

   Use a `.env` file to store these variables and `python-dotenv` to load them.

2. **Set Voice Preference**
   In `app.py`, a default `VOICE_ID` for "Emily" is provided. This voice ID is specific to Eleven Labs. 
   Optional: If you want to fine-tune on the Caregiver's voice, go to [this page](https://elevenlabs.io/voice-lab), add a clear voice sample, and train the voice. Then update the `VOICE_ID` variable with the new ID.

3. **Install Dependencies**
   Use the provided command to install the required dependencies:
   ```bash
   pip install openai streamlit mutagen requests python-dotenv
   ```

4. **Run the Application**
   With Streamlit, run the app using the following command:
   ```bash
   streamlit run app.py
   ```

   By default, the application will be accessible at [http://localhost:8501](http://localhost:8501). 

   Because we expect most users to first experiment with promts and voices, Lethelink will help you save credits by caching generated text and audio to your local directory. So if you send the same prompt with the same voice, you will get an immediate, free response.

## Adapting for Your Use Case

- **Custom Prompts**: Modify the `generate_nudge` function in `app.py` to customize the prompting mechanism.
- **Voice Options**: Check Eleven Labs' documentation for different voice options and update the `VOICE_ID` accordingly.
- **Integrate with Other Models**: The application is currently set up for OpenAI's GPT-4 model. If you have access to different models, adjust the `call_chatgpt` function in the `utils` module.

## License

- License: MIT (feel free to use, modify, and distribute this code as you see fit).

## Contributing

Lethelink is fully open-source, and we welcome contributions! See [Opportunities](#opportunities) for ideas on what to contribute.