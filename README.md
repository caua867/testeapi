<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Chat TerraGuia</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0fdf4;
      margin: 0;
      padding: 40px 10px;
    }
    .chat-container {
      max-width: 500px;
      background: #ffffff;
      margin: auto;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      color: #2e7d32;
    }
    #chat {
      height: 300px;
      overflow-y: auto;
      background: #f9f9f9;
      padding: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
      font-size: 16px;
      margin-bottom: 10px;
    }
    input {
      flex: 1;
      padding: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      padding: 10px 15px;
      background: #2e7d32;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .input-area {
      display: flex;
      gap: 5px;
    }
  </style>
</head>
<body>
  <div class="chat-container">
    <h2>💬 Chat TerraGuia</h2>
    <div id="chat"></div>
    <div class="input-area">
      <input id="input" type="text" placeholder="Digite sua dúvida..." />
      <button onclick="send()">Enviar</button>
    </div>
  </div>

  <script>
    const chat = document.getElementById("chat");

    function send() {
      const input = document.getElementById("input");
      const question = input.value.trim();
      if (!question) return;

      appendMessage("Você", question, "right");
      input.value = "";

      setTimeout(() => {
        const answer = getAnswer(question.toLowerCase());
        appendMessage("TerraGuia IA", answer, "left");
      }, 3000);
    }

    function appendMessage(sender, text, align) {
      const div = document.createElement("div");
      div.style.textAlign = align;
      div.style.marginBottom = "8px";
      div.innerHTML = `<strong>${sender}:</strong> ${text}`;
      chat.appendChild(div);
      chat.scrollTop = chat.scrollHeight;
    }

    function getAnswer(q) {
      if (q.includes("oi") || q.includes("olá") || q.includes("bom dia")) return "Olá! 👋 Sou a IA da TerraGuia. Como posso te ajudar com sua lavoura hoje?";
      if (q.includes("como funciona")) return "A TerraGuia envia orientações diárias com base no clima e tipo de cultura.";
      if (q.includes("preço") || q.includes("valor")) return "A plataforma completa custa R$ 99,90 por mês.";
      if (q.includes("gratuito")) return "Sim! Temos uma versão gratuita com recursos limitados.";
      if (q.includes("offline")) return "Sim, funciona mesmo com internet limitada.";
      if (q.includes("culturas")) return "Milho, feijão, mandioca, hortaliças e muito mais.";
      return "Desculpe, ainda estou aprendendo. Reformule sua pergunta, por favor.";
    }
  </script>
</body>
</html>
