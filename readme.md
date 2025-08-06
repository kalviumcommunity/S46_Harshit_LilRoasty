# 🔥 LilRoasty – Your Friendly AI Roasting Assistant

**LilRoasty** is a playful and compact AI project that roasts users in a light-hearted, personalized way using cutting-edge generative AI. Whether it's your bio, mood, or just your name, LilRoasty delivers a spicy burn with a smile 😄🔥.

This project combines four powerful GenAI concepts:

* Prompting
* Structured Output
* Function Calling
* Retrieval-Augmented Generation (RAG)

Each concept is implemented with a clear and practical role in the app.

---

## 🌟 Project Overview

LilRoasty takes simple user input (like name and bio) and now also includes an optional selfie upload for extra roasting accuracy. The system returns a fun, personalized roast. Under the hood, it uses:

* AI prompting to generate the roast
* RAG to make it culturally relevant
* Structured output to make the data usable
* Function calling to modularize features like spice rating, comebacks, and meme suggestions
* Vision analysis (if selfie provided) to enhance roast personalization

LilRoasty takes simple user input (like name and bio) and returns a fun, personalized roast. Under the hood, it uses:

* AI prompting to generate the roast
* RAG to make it culturally relevant
* Structured output to make the data usable
* Function calling to modularize features like spice rating, comebacks, and meme suggestions

---

## 🚀 GenAI Concepts Breakdown

🖼️ **Bonus: Image + Text Input Support**

If a selfie is uploaded, LilRoasty uses Gemini Vision or CLIP to extract visual context (like facial expressions, accessories, mood). This info is added to the prompt so the AI can tailor the roast more accurately.

Example Prompt:

> "Analyze the person's photo and description, then roast them in a witty, sarcastic tone. Follow it with a light compliment."

---

### 🧠 Prompting

**Prompting** is how we tell the AI what we want.

In LilRoasty:

* We create dynamic prompts like:

  > "Roast a developer who says they drink 4 coffees a day but still miss deadlines."
* These prompts are fed to the LLM (like GPT-4), which returns a roast
* Prompts are also enhanced using retrieved meme content (from RAG)

### 🗃️ Structured Output

**Structured Output** means getting information back in a clean, usable format.

LilRoasty returns all roast content as a JSON object:

```json
{
  "roast": "You're like semicolons in Python — unnecessary and still causing errors.",
  "spice_level": "high",
  "theme": "techie",
  "meme_reference": "https://i.imgflip.com/devfail.jpg",
  "comeback_suggestion": "At least I don’t write JavaScript with print statements."
}
```

This structure is perfect for UI rendering, sharing, or exporting.

### ⚙️ Function Calling

**Function calling** lets GPT automatically trigger pre-defined logic in your code.

In LilRoasty, we use:

* `rateSpiceLevel(text)` – To analyze how spicy the roast is
* `generateComeback(roast)` – To suggest a funny reply
* `getTrendingMemes(theme)` – To recommend a meme that fits the roast

These are modular Python functions and are called when GPT detects they’re needed.

### 🔍 RAG (Retrieval-Augmented Generation)

**RAG** makes the AI smarter by feeding it real-world, external context.

In LilRoasty:

* We store a dataset of memes and funny lines in a vector database (like FAISS)
* When generating a roast, we fetch related content based on the user's input
* This content is inserted into the prompt so the AI stays up to date and meme-savvy

### 🧠 Why We Use a Vector Database

A vector database lets us search **semantically**, meaning the AI can find content that's similar in **meaning**, not just in words.
This makes roast generation funnier and more personalized.

### 🔎 What Is FAISS or ChromaDB?

You can choose between **FAISS** or **ChromaDB** for meme retrieval in RAG:

#### 🧠 FAISS

* Open-source library by Meta (Facebook)
* Extremely fast vector search engine
* Great for large-scale datasets and production

#### 💡 ChromaDB

* Open-source, easy-to-use vector store built in Python
* User-friendly and great for small to mid-size GenAI apps
* Integrated well with LangChain

**Whichever you choose**, the flow remains:

```
User bio ➝ Embed ➝ Vector Search ➝ Retrieve best memes ➝ Add to Prompt ➝ GPT Roasts
```

**Example:**
User says: “I’m a coffee addict who avoids parties.”
RAG retrieves: Memes about caffeine and introversion.
Prompt: “Roast this dev using this meme line: 'You live on coffee and avoid more calls than a scammer.'”

**Example:**
User says: “I’m a coffee addict who avoids parties.”
FAISS retrieves: Memes about caffeine and introversion.
Prompt: “Roast this dev using this meme line: 'You live on coffee and avoid more calls than a scammer.'”

---

## 🧪 Example Flow

**Input:**

```json
{
  "name": "Harshit",
  "bio": "I'm a software dev who drinks 4 cups of coffee and still misses deadlines."
}
```

**Process:**

1. Create prompt using bio
2. RAG fetches a relevant meme quote
3. GPT generates roast
4. GPT optionally calls functions (e.g., spice rating, comeback)

**Output:**

```json
{
  "roast": "You commit code like you commit to diets — full of hope and empty results.",
  "spice_level": "medium",
  "theme": "techie",
  "meme_reference": "https://i.imgflip.com/techfail.jpg",
  "comeback_suggestion": "Better flaky code than flaky people."
}
```

---

## 🛠 Tech Stack (Updated with Frontend & Hosting)

| Component      | Tech                           |
| -------------- | ------------------------------ |
| GenAI Model    | OpenAI GPT-4 + Gemini Vision   |
| Backend        | Node.js + Express (or FastAPI) |
| Vector DB      | FAISS or ChromaDB              |
| Dataset        | JSON/CSV with memes/roasts     |
| Image Analysis | CLIP / BLIP / Gemini Vision    |
| Output Format  | JSON                           |
| Frontend       | React + Tailwind               |
| Hosting        | Vercel / Netlify               |

---

## 💡 Future Features

* Roast battles with leaderboard
* Text-to-speech roast delivery
* Roast templates for fictional characters or celebrities
* Roast me from history (e.g., Einstein roasting you)

---

## 📜 License

MIT License — fork, remix, and roast responsibly.

---

## 👨‍💻 Made with humor by Harshit
