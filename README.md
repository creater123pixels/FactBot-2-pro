<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FactBot 2 Pro - Your Daily Dose of Knowledge & Fun!</title>
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap" rel="stylesheet">
    <style>
        /* Base Styles */
        body {
            font-family: 'Open Sans', Arial, sans-serif;
            background: linear-gradient(to right, #6dd5ed, #2193b0);
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            min-height: 100vh;
            color: #333;
            box-sizing: border-box;
        }

        .chat-container {
            width: 450px;
            max-width: 90%;
            background-color: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            margin-bottom: auto; /* Pushes the chat container to the top */
        }

        .chat-header {
            background-color: #4CAF50;
            color: white;
            padding: 15px 20px;
            border-top-left-radius: 10px;
            border-top-right-radius: 10px;
            margin: -25px -25px 20px -25px;
            font-size: 1.2em;
            font-weight: 700;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .chat-box {
            max-height: 380px;
            overflow-y: auto;
            margin-bottom: 20px;
            padding-right: 10px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            scroll-behavior: smooth;
        }

        /* Scrollbar styles */
        .chat-box::-webkit-scrollbar {
            width: 8px;
        }

        .chat-box::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }

        .chat-box::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 10px;
        }

        .chat-box::-webkit-scrollbar-thumb:hover {
            background: #555;
        }

        .input-container {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
        }

        input[type="text"] {
            flex-grow: 1;
            padding: 12px 15px;
            border-radius: 25px;
            border: 1px solid #ddd;
            font-size: 1em;
            outline: none;
            transition: border-color 0.3s ease;
        }

        input[type="text"]:focus {
            border-color: #2193b0;
        }

        button {
            padding: 12px 25px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1em;
            font-weight: 700;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            white-space: nowrap;
        }

        button:hover {
            background-color: #45a049;
            transform: translateY(-2px);
        }

        button:active {
            transform: translateY(0);
        }

        .action-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-top: 10px;
        }

        .action-buttons button {
            background-color: #2193b0;
            padding: 10px 18px;
            font-size: 0.95em;
        }

        .action-buttons button:hover {
            background-color: #1a7b92;
        }

        .message {
            padding: 12px 18px;
            border-radius: 20px;
            max-width: 80%;
            line-height: 1.5;
            word-wrap: break-word;
        }

        .user-message {
            background: linear-gradient(to right, #3498db, #2980b9);
            color: white;
            align-self: flex-end;
            border-bottom-right-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .bot-message {
            background-color: #ecf0f1;
            color: #2c3e50;
            align-self: flex-start;
            border-bottom-left-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
        }

        .bot-typing {
            background-color: #f0f3f4;
            color: #7f8c8d;
            font-style: italic;
            align-self: flex-start;
            padding: 10px 15px;
            border-radius: 20px;
            max-width: fit-content;
        }

        footer {
            text-align: center;
            margin-top: 30px;
            font-size: 0.85em;
            color: #ecf0f1;
            text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
            width: 100%;
            padding: 10px 0;
        }

        /* --- MEDIA QUERIES for Mobile Responsiveness --- */
        @media (max-width: 900px) {
            .chat-container {
                width: 90%;
                padding: 20px;
            }

            .chat-header {
                margin: -20px -20px 15px -20px;
            }

            .chat-box {
                max-height: 350px;
            }

            input[type="text"], button {
                font-size: 0.95em;
                padding: 10px 20px;
            }

            .action-buttons button {
                padding: 9px 15px;
            }
        }

        @media (max-width: 600px) {
            body {
                padding: 15px;
            }

            .chat-container {
                width: 100%;
                max-width: 95%;
                padding: 15px;
                border-radius: 10px;
            }

            .chat-header {
                margin: -15px -15px 10px -15px;
                font-size: 1.1em;
                padding: 12px 15px;
            }

            .chat-box {
                max-height: 300px;
                margin-bottom: 15px;
            }

            .input-container {
                flex-direction: column;
                gap: 8px;
            }

            input[type="text"] {
                width: 100%;
                padding: 10px 12px;
                font-size: 0.9em;
            }

            button {
                width: 100%;
                padding: 10px;
                font-size: 0.95em;
            }

            .action-buttons {
                flex-direction: column;
                gap: 8px;
            }

            .action-buttons button {
                width: 100%;
                padding: 10px;
            }

            .message {
                max-width: 90%;
                padding: 10px 15px;
                font-size: 0.95em;
            }

            footer {
                margin-top: 20px;
                font-size: 0.8em;
            }
        }
    </style>
</head>
<body>

<div class="chat-container">
    <div class="chat-header">FactBot 2 Pro</div>
    <div class="chat-box" id="chatBox">
    </div>
    <div class="input-container">
        <input type="text" id="userInput" placeholder="Ask me something or click a button..." />
        <button onclick="sendMessage()">Send</button>
    </div>
    <div class="action-buttons">
        <button id="factButton" onclick="askForCategory()">Tell me a fact</button>
        <button id="jokeButton" onclick="tellRandomJoke()">Tell me a joke</button>
        <button id="quoteButton" onclick="tellRandomQuote()">Tell me a quote</button>
        <button id="createJokeButton" onclick="createJoke()">Create a joke</button>
        <button id="resetButton" onclick="resetChat()">Reset Chat</button>
    </div>
</div>

<footer>
    <p>Created by: G. Kavi Siva Murugan</p>
</footer>

<script>
    let factCategory = null;
    let awaitingJokeQuestion = false;
    let awaitingJokeAnswer = false;
    let jokeQuestion = "";
    let jokeAnswer = "";
    let botTypingTimeout;

    // --- Fact Categories & Facts ---
    const factCategories = {
        "science": [
            "Did you know that honey never spoils? Archaeologists have found pots of honey in ancient tombs that are over 3000 years old!",
            "The human brain uses about 20% of the body's oxygen and calories.",
            "A lightning bolt is five times hotter than the surface of the sun.",
            "Sound travels about 4.3 times faster in water than in air.",
            "There are more possible iterations of a game of chess than there are atoms in the known universe."
        ],
        "math": [
            "The number Pi (p) is infinite and non-repeating. It's a transcendental number that never ends!",
            "The only number that is spelled with the same number of letters as itself is 'four'.",
            "Zero is the only number that cannot be represented by Roman numerals.",
            "A 'googol' is the number 1 followed by 100 zeros. A 'googolplex' is 10 to the power of a googol."
        ],
        "history": [
            "The Great Wall of China is over 13,000 miles long! It's not visible from space with the naked eye, despite popular belief.",
            "Cleopatra lived closer in time to the invention of the iPhone than to the building of the Great Pyramid of Giza.",
            "The shortest war in history was between Britain and Zanzibar on August 27, 1896. It lasted only 38 minutes.",
            "The first recorded use of the word 'hello' as a greeting was in 1827.",
            "The national animal of Scotland is the unicorn."
        ],
        "fun": [
            "A group of flamingos is called a 'flamboyance'! Isn't that fun?",
            "It is impossible for most people to lick their own elbow.",
            "A 'jiffy' is an actual unit of time: 1/100th of a second.",
            "The longest English word without a vowel (excluding 'y') is 'rhythm'.",
            "The average person walks the equivalent of three times around the world in their lifetime."
        ],
        "animals": [
            "A group of owls is called a parliament.",
            "The heart of a shrimp is in its head!",
            "Octopuses have three hearts: two pump blood through the gills and one circulates it to the rest of the body.",
            "A snail can sleep for three years.",
            "Butterflies taste with their feet."
        ],
        "space": [
            "There are more stars in the universe than grains of sand on all the beaches on Earth.",
            "A full NASA space suit costs around $12 million.",
            "One day on Venus is longer than one year on Venus.",
            "The highest mountain known to man is on Mars, called Olympus Mons, and it's three times taller than Mount Everest.",
            "Footprints on the moon will stay there for 100 million years because there is no wind to erode them."
        ],
        "nature": [
            "The Amazon rainforest produces over 20% of the world's oxygen.",
            "The largest living structure on Earth is the Great Barrier Reef.",
            "Hot water freezes faster than cold water (known as the Mpemba effect).",
            "Diamonds are the hardest natural substance on Earth.",
            "The Earth's deepest point is the Mariana Trench, nearly 7 miles deep."
        ],
        "technology": [
            "The first computer mouse was made of wood.",
            "The QWERTY keyboard layout was designed to slow down typing to prevent typewriters from jamming.",
            "More than 90% of the world's currency is digital.",
            "The first website ever created is still online: info.cern.ch.",
            "The average smartphone has more computing power than the computers used for the Apollo 11 moon landing."
        ]
    };

    // --- Pre-defined jokes (NOW as objects with Question and Answer) ---
    const jokes = [
        { question: "Why don't scientists trust atoms?", answer: "Because they make up everything!" },
        { question: "What do you call a fish with no eyes?", answer: "Fsh!" },
        { question: "Why did the scarecrow win an award?", answer: "Because he was outstanding in his field!" },
        { question: "I told my wife she was drawing her eyebrows too high.", answer: "She looked surprised." },
        { question: "What do you call cheese that isn't yours?", answer: "Nacho cheese!" },
        { question: "Why don't skeletons fight each other?", answer: "They don't have the guts." },
        { question: "What do you call a boomerang that won't come back?", answer: "A stick." },
        { question: "Why did the old man fall in the well?", answer: "Because he couldn't see that well!" },
        { question: "I'm reading a book about anti-gravity.", answer: "It's impossible to put down!" },
        { question: "What's orange and sounds like a parrot?", answer: "A carrot!" },
        { question: "What do you call a lazy kangaroo?", answer: "Pouch potato!" },
        { question: "Why did the invisible man turn down the job offer?", answer: "He couldn't see himself doing it." },
        { question: "What's a vampire's favorite fruit?", answer: "A neck-tarine!" },
        { question: "Did you hear about the two guys who stole a calendar?", answer: "They each got six months." },
        { question: "Why was the math book sad?", answer: "Because it had too many problems." }
    ];

    // --- Pre-defined quotes ---
    const quotes = [
        {
            text: "The only way to do great work is to love what you do.",
            author: "Steve Jobs"
        },
        {
            text: "Believe you can and you're halfway there.",
            author: "Theodore Roosevelt"
        },
        {
            text: "The future belongs to those who believe in the beauty of their dreams.",
            author: "Eleanor Roosevelt"
        },
        {
            text: "It is during our darkest moments that we must focus to see the light.",
            author: "Aristotle"
        },
        {
            text: "Strive not to be a success, but rather to be of value.",
            author: "Albert Einstein"
        },
        {
            text: "The best way to predict the future is to create it.",
            author: "Peter Drucker"
        },
        {
            text: "The mind is everything. What you think you become.",
            author: "Buddha"
        },
        {
            text: "Innovation distinguishes between a leader and a follower.",
            author: "Steve Jobs"
        },
        {
            text: "The purpose of our lives is to be happy.",
            author: "Dalai Lama"
        },
        {
            text: "Life is what happens when you're busy making other plans.",
            author: "John Lennon"
        }
    ];

    // Helper function to add messages to the chat box
    function addMessage(text, type) {
        const chatBox = document.getElementById("chatBox");
        const messageDiv = document.createElement("div");
        messageDiv.classList.add("message", type);
        messageDiv.innerHTML = text; // Use innerHTML to allow for bold text in responses
        chatBox.appendChild(messageDiv);
        chatBox.scrollTop = chatBox.scrollHeight; // Scroll to bottom
    }

    // Function to show typing indicator
    function showTypingIndicator() {
        const chatBox = document.getElementById("chatBox");
        let typingDiv = document.getElementById("typing-indicator");
        if (!typingDiv) {
            typingDiv = document.createElement("div");
            typingDiv.classList.add("bot-typing");
            typingDiv.id = "typing-indicator";
            typingDiv.textContent = "FactBot 2 Pro is typing...";
            chatBox.appendChild(typingDiv);
            chatBox.scrollTop = chatBox.scrollHeight;
        }
    }

    // Function to remove typing indicator
    function removeTypingIndicator() {
        const typingDiv = document.getElementById("typing-indicator");
        if (typingDiv) {
            typingDiv.remove();
        }
    }

    // Initial welcome message on load
    document.addEventListener("DOMContentLoaded", () => {
        addMessage("Hello! I'm **FactBot 2 Pro**. How can I help you today? You can ask for a _fact_, a _joke_, a _quote_, or _create your own joke_!", "bot-message");
    });

    // Ask for fact category (used when button is clicked or "fact" is typed)
    function askForCategory() {
        factCategory = "awaiting"; // Set a temporary state to indicate waiting for category
        const categoriesList = Object.keys(factCategories).map(cat => `*${cat.charAt(0).toUpperCase() + cat.slice(1)}*`).join(', ');
        showTypingIndicator();
        setTimeout(() => {
            removeTypingIndicator();
            addMessage(`What type of fact would you like? You can choose from: ${categoriesList}.`, "bot-message");
        }, 800);
        // Clear any other pending states
        awaitingJokeQuestion = false;
        awaitingJokeAnswer = false;
    }

    // Handle fact category input (when bot is awaiting category specifically)
    function handleCategoryInput(input) {
        input = input.toLowerCase().trim();
        const categoriesList = Object.keys(factCategories).map(cat => `*${cat.charAt(0).toUpperCase() + cat.slice(1)}*`).join(', ');

        if (factCategories[input]) {
            factCategory = null; // Reset fact category state
            const facts = factCategories[input];
            const randomFact = facts[Math.floor(Math.random() * facts.length)]; // Get a random fact from the category
            showTypingIndicator();
            setTimeout(() => {
                removeTypingIndicator();
                addMessage(randomFact, "bot-message");
            }, 1000); // Simulate typing delay
        } else {
            showTypingIndicator();
            setTimeout(() => {
                removeTypingIndicator();
                addMessage(`I'm sorry, I don't have facts for that category. Please choose from: ${categoriesList}.`, "bot-message");
            }, 1000);
        }
    }

    // Tell a random pre-defined joke
    function tellRandomJoke() {
        const randomIndex = Math.floor(Math.random() * jokes.length);
        const randomJoke = jokes[randomIndex];
        showTypingIndicator();
        setTimeout(() => {
            removeTypingIndicator();
            // Format the joke with "Question:" and "Answer:"
            addMessage(`Question: ${randomJoke.question}<br>Answer: ${randomJoke.answer}`, "bot-message");
        }, 1200);
        // Clear any other pending states
        factCategory = null;
        awaitingJokeQuestion = false;
        awaitingJokeAnswer = false;
    }

    // Tell a random pre-defined quote
    function tellRandomQuote() {
        const randomIndex = Math.floor(Math.random() * quotes.length);
        const randomQuote = quotes[randomIndex];
        showTypingIndicator();
        setTimeout(() => {
            removeTypingIndicator();
            addMessage(`"${randomQuote.text}" - _${randomQuote.author}_`, "bot-message");
        }, 1200);
        // Clear any other pending states
        factCategory = null;
        awaitingJokeQuestion = false;
        awaitingJokeAnswer = false;
    }

    // Start creating a new joke
    function createJoke() {
        showTypingIndicator();
        setTimeout(() => {
            removeTypingIndicator();
            addMessage("Great! Let's create a new joke. First, please tell me the joke question (the setup).", "bot-message");
        }, 800);
        awaitingJokeQuestion = true;
        // Clear any other pending states
        factCategory = null;
        awaitingJokeAnswer = false;
    }

    // Handle questions about the bot's creator
    function handleAboutCreator() {
        const creatorInfo = "I was created by **G. Kavi Siva Murugan** in **May 2025** as a fun project to provide facts, jokes, and quotes, and to demonstrate interactive chatbot capabilities using simple JavaScript.";
        showTypingIndicator();
        setTimeout(() => {
            removeTypingIndicator();
            addMessage(creatorInfo, "bot-message");
        }, 1200);
    }

    // Send message based on user input
    function sendMessage() {
        const userInput = document.getElementById("userInput").value;
        document.getElementById("userInput").value = ""; // Clear input immediately

        if (userInput.trim() === "") {
            return; // Don't send empty messages
        }

        addMessage(userInput, "user-message"); // Display user's message

        const lowerInput = userInput.toLowerCase().trim();

        // --- High-priority commands (should always execute if matched) ---
        if (lowerInput === "reset chat" || lowerInput === "reset") {
            resetChat();
            return; // Stop further processing
        } else if (lowerInput.includes("create a joke") || lowerInput === "create joke") {
            createJoke();
            return; // Stop further processing
        }

        // --- Handle specific AWAITING states (joke creation or explicit fact category request) ---
        // These take precedence if the bot is in a conversational flow
        if (awaitingJokeQuestion) {
            jokeQuestion = userInput;
            awaitingJokeQuestion = false;
            awaitingJokeAnswer = true;
            showTypingIndicator();
            setTimeout(() => {
                removeTypingIndicator();
                addMessage("Got it! Now please provide the answer (the punchline) to your joke.", "bot-message");
            }, 800);
            return; // Stop further processing
        } else if (awaitingJokeAnswer) {
            jokeAnswer = userInput;
            awaitingJokeAnswer = false; // Reset state
            showTypingIndicator();
            setTimeout(() => {
                removeTypingIndicator();
                // Format the user-created joke as Question and Answer
                addMessage(`Here's your custom joke:<br>Question: ${jokeQuestion}<br>Answer: ${jokeAnswer}`, "bot-message");
            }, 1000);
            return; // Stop further processing
        } else if (factCategory === "awaiting") { // ONLY if bot explicitly asked for category (e.g., after "tell me a fact")
            handleCategoryInput(userInput); // This function will handle showing typing/response
            return; // Stop further processing
        }

        // --- If no specific state or high-priority command is active, handle general conversation via keywords ---
        handleGeneralConversation(userInput);
    }

    // Handle general conversation or unrecognized input, now heavily keyword-driven
    function handleGeneralConversation(input) {
        const lowerInput = input.toLowerCase().trim();
        let botResponse = "";
        let handledByFunction = false; // Flag to indicate if a specific function (like tellRandomJoke) was called

        // 1. Check for greetings
        const greetings = ["hello", "hi", "hey", "good morning", "good evening", "how are you"];
        if (greetings.some(greeting => lowerInput.includes(greeting))) {
            botResponse = "Hello there! How can I help you today?";
        }
        // 2. Check for bot's identity
        else if (lowerInput.includes("your name") || lowerInput.includes("who are you")) {
            botResponse = "I am **FactBot 2 Pro**, your friendly knowledge companion!";
        }
        // 3. Check for creator info
        else if (lowerInput.includes("who created you") || lowerInput.includes("who made you") || lowerInput.includes("your creator")) {
            handleAboutCreator(); // Call the specific function for creator info
            handledByFunction = true;
        }
        // 4. Check for thank you
        else if (lowerInput.includes("thank you") || lowerInput.includes("thanks")) {
            botResponse = "You're welcome! Glad I could help.";
        }
        // 5. Check for goodbye
        else if (lowerInput.includes("bye") || lowerInput.includes("goodbye") || lowerInput.includes("see ya")) {
            botResponse = "Goodbye! Come back soon for more facts and jokes!";
        }
        // 6. Check for general "fact" request
        else if (lowerInput.includes("fact")) {
            // If the user just typed "fact" or "tell me a fact", trigger the category prompt
            askForCategory(); // This function already handles typing and message display
            handledByFunction = true; // Mark as handled by a function
        }
        // 7. Check for general "joke" request
        else if (lowerInput.includes("joke") && !lowerInput.includes("create")) { // Exclude "create joke"
            tellRandomJoke(); // This function already handles typing and message display
            handledByFunction = true; // Mark as handled by a function
        }
        // 8. Check for general "quote" request
        else if (lowerInput.includes("quote")) {
            tellRandomQuote(); // This function already handles typing and message display
            handledByFunction = true; // Mark as handled by a function
        }
        // 9. Check for direct fact category keywords (e.g., "science fact", "history fact", or just "science")
        else {
            for (const category in factCategories) {
                // Check for "science fact" or just "science"
                if (lowerInput.includes(category + " fact") || lowerInput === category) {
                    const facts = factCategories[category];
                    const randomFact = facts[Math.floor(Math.random() * facts.length)];
                    botResponse = randomFact;
                    break; // Found a category, no need to check others
                }
            }
        }

        // Display response if `botResponse` was set and no specific function took over
        if (botResponse !== "" && !handledByFunction) {
            showTypingIndicator();
            setTimeout(() => {
                removeTypingIndicator();
                addMessage(botResponse, "bot-message");
            }, 1000);
        } else if (botResponse === "" && !handledByFunction) {
            // Fallback for completely unrecognized input
            botResponse = "I'm not sure how to respond to that. You can ask for a _fact_, a _joke_, a _quote_, or _create a joke_!";
            showTypingIndicator();
            setTimeout(() => {
                removeTypingIndicator();
                addMessage(botResponse, "bot-message");
            }, 1000);
        }
        // If handledByFunction is true, the response was already managed by that function.
    }

    // Reset chat to the initial state
    function resetChat() {
        const chatBox = document.getElementById("chatBox");
        chatBox.innerHTML = ''; // Clear all messages
        showTypingIndicator();
        setTimeout(() => {
            removeTypingIndicator();
            addMessage("Hello! I'm **FactBot 2 Pro**. How can I help you today? You can ask for a _fact_, a _joke_, a _quote_, or _create your own joke_!", "bot-message");
        }, 500); // A small delay for reset message
        document.getElementById("userInput").value = '';
        factCategory = null;
        awaitingJokeQuestion = false;
        awaitingJokeAnswer = false;
        jokeQuestion = "";
        jokeAnswer = "";
    }

    // Trigger the Enter key to send message
    document.getElementById("userInput").addEventListener("keypress", function(event) {
        if (event.key === "Enter") {
            sendMessage();
        }
    });
</script>

</body>
</html>
