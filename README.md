# nicegames.com
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Always Hi Chatbot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
        }
        #chat-container {
            border: 1px solid #ccc;
            height: 400px;
            overflow-y: scroll;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
        }
        #user-input {
            width: 80%;
            padding: 8px;
        }
        #send-btn {
            padding: 8px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .user-message {
            text-align: right;
            margin: 5px;
            color: #333;
        }
        .bot-message {
            text-align: left;
            margin: 5px;
            color: #4CAF50;
        }
    </style>
</head>
<body>
    <h1>Always Hi Chatbot</h1>
    <div id="chat-container"></div>
    <div>
        <input type="text" id="user-input" placeholder="Type your message here...">
        <button id="send-btn">Send</button>
    </div>

    <script>
        const chatContainer = document.getElementById('chat-container');
        const userInput = document.getElementById('user-input');
        const sendBtn = document.getElementById('send-btn');

        function addMessage(sender, message) {
            const messageDiv = document.createElement('div');
            messageDiv.classList.add(sender + '-message');
            messageDiv.textContent = message;
            chatContainer.appendChild(messageDiv);
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }

        function handleUserInput() {
            const message = userInput.value.trim();
            if (message) {
                addMessage('user', message);
                userInput.value = '';
                
                // The bot always responds with "Hi!"
                setTimeout(() => {
                    addMessage('bot', 'Hi!');
                }, 500);
            }
        }

        sendBtn.addEventListener('click', handleUserInput);
        userInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                handleUserInput();
            }
        });

        // Initial greeting
        setTimeout(() => {
            addMessage('bot', 'Hi! I will always say "Hi!" no matter what you say.');
        }, 500);
    </script>
</body>
</html>

