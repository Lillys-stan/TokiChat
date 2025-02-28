<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login - Meu App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            color: #ff7f00;
            margin: 0;
            padding: 20px;
            text-align: center;
            background-color: #000; /* Fundo preto como backup */
            /* Adicione a imagem local ou online aqui */
            background-image: url(file:///C:/Users/DESKTOP/Desktop/Projeto%20∞/site%20da%20minha%20Namorada/background.jpg.jpg); /* Substitua por 'background.jpg' se a imagem estiver na mesma pasta */
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            min-height: 100vh;
        }
        .container, .app-container, .chat-container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background: rgba(30, 30, 30, 0.9); /* Fundo semi-transparente para legibilidade */
            border-radius: 8px;
        }
        .chat-container {
            max-width: 600px;
        }
        .input-box {
            width: 80%;
            padding: 8px;
            margin: 10px 0;
        }
        .btn {
            padding: 10px 15px;
            background: #ff7f00;
            color: #000;
            border: none;
            cursor: pointer;
            margin-top: 10px;
        }
        .app-container {
            display: none;
        }
        .chat-container {
            display: none;
            background: rgba(30, 30, 30, 0.9);
        }
        .chat-header {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }
        .chat-header img {
            width: 50px;
            height: 50px;
        }
        .chat-box {
            height: 300px;
            overflow-y: auto;
            background: #2e2e2e;
            padding: 10px;
            border-radius: 8px;
            margin-bottom: 10px;
            display: flex;
            flex-direction: column;
        }
        .message {
            padding: 10px;
            border-radius: 8px;
            margin: 5px 0;
            max-width: 80%;
            word-wrap: break-word;
            align-self: flex-start;
        }
        .sent {
            background: #ff7f00;
            color: #000;
            align-self: flex-end;
        }
        .received {
            background: #555;
            color: #fff;
        }
        .chat-input {
            display: flex;
            justify-content: space-between;
        }
        .chat-input input {
            width: 80%;
            padding: 8px;
        }
    </style>
</head>
<body>
    <div class="container" id="login-container">
        <h1>Login</h1>
        <input type="text" id="username" class="input-box" placeholder="Usuário">
        <input type="password" id="password" class="input-box" placeholder="Senha">
        <button class="btn" onclick="login()">Entrar</button>
    </div>

    <div class="app-container" id="app-container">
        <h1>Meu App</h1>
        <div class="friends">
            <h2>Amigos</h2>
            <div id="friends-list">
                <div class="friend" onclick="openChat('Amigo 1')">
                    <img src="profile1.jpg" alt="Amigo 1">
                    <span>Amigo 1</span>
                </div>
                <div class="friend" onclick="openChat('Amigo 2')">
                    <img src="profile2.jpg" alt="Amigo 2">
                    <span>Amigo 2</span>
                </div>
            </div>
        </div>
    </div>
    
    <div class="chat-container" id="chat-container">
        <div class="chat-header">
            <img src="cat_ears.png" alt="Orelhas de gato">
            <h2>Chat</h2>
            <h3 id="chat-name"></h3>
        </div>
        <div class="chat-box" id="chat-box"></div>
        <div class="chat-input">
            <input type="text" id="message" class="input-box" placeholder="Digite uma mensagem...">
            <button class="btn" onclick="sendMessage()">Enviar</button>
        </div>
    </div>
    
    <script>
        let currentChat = "";

        function login() {
            let username = document.getElementById("username").value;
            let password = document.getElementById("password").value;
            
            if (username && password) {
                document.getElementById("login-container").style.display = "none";
                document.getElementById("app-container").style.display = "block";
            } else {
                alert("Preencha todos os campos!");
            }
        }

        function openChat(friendName) {
            document.getElementById("chat-container").style.display = "block";
            document.getElementById("chat-name").textContent = friendName;
            currentChat = friendName;
            document.getElementById("chat-box").innerHTML = "";
        }
        
        function sendMessage() {
            let message = document.getElementById("message").value;
            if (message.trim() !== "") {
                let chatBox = document.getElementById("chat-box");
                let msgElement = document.createElement("div");
                msgElement.classList.add("message", "sent");
                msgElement.textContent = "Você: " + message;
                chatBox.appendChild(msgElement);
                document.getElementById("message").value = "";
                chatBox.scrollTop = chatBox.scrollHeight;
            }
        }
    </script>
</body>
</html>
