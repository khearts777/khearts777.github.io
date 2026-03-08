# AI Name: CHKai
import openai
import pyttsx3
import random

# ----------------------------
# Set up APIs and TTS
# ----------------------------
openai.api_key = "YOUR_OPENAI_API_KEY"

engine = pyttsx3.init()

# AI emotions and personality traits
emotions = ["happy", "nonchalant", "excited", "annoyed", "funny"]
personality = "cool, helpful, jokes around but sometimes nonchalant"

# ----------------------------
# Functions
# ----------------------------

# Text-to-Speech
def speak(text):
    engine.say(text)
    engine.runAndWait()

# Generate AI Response
def get_ai_response(user_input, emotion=None):
    if not emotion:
        emotion = random.choice(emotions)
    
    prompt = f"""
    You are an AI named CHKai.
    Personality: {personality}.
    Current emotion: {emotion}.
    User says: "{user_input}"
    Reply accordingly in a casual, cool, sometimes joking way.
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4o-mini",  # powerful chat model
        messages=[{"role": "user", "content": prompt}],
        temperature=0.7,
        max_tokens=250
    )
    return response['choices'][0]['message']['content']

# Generate Image
def generate_image(prompt):
    response = openai.Image.create(
        prompt=prompt,
        n=1,
        size="512x512"
    )
    return response['data'][0]['url']

# ----------------------------
# Main Loop
# ----------------------------
print("CHKai is online! Say 'exit' to quit.")
while True:
    user_input = input("You: ")
    if user_input.lower() == "exit":
        print("CHKai: Later, chill!")
        break

    # Choose emotion randomly
    current_emotion = random.choice(emotions)
    
    # Get AI text response
    ai_response = get_ai_response(user_input, current_emotion)
    
    # Speak response
    speak(ai_response)
    
    # Print response
    print(f"CHKai ({current_emotion}): {ai_response}")
    
    # Optional: Generate image if user asks
    if "draw" in user_input.lower() or "image" in user_input.lower():
        image_url = generate_image(user_input)
        print(f"CHKai generated an image: {image_url}")
