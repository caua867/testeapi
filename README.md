```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chat TerraGuia</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f3fdf3;
      padding: 40px;
    }
    .chatbox {
      max-width: 450px;
      margin: auto;
      background: white;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
    }
    .messages {
      height: 300px;
      overflow-y: auto;
      margin-bottom: 10px;
      padding-right: 10px;
      font-size: 18px;
    }
    .msg {
      margin-bottom: 12px;
    }
    .msg.user {
      text-align: right;
      color: #006400;
    }
    .msg.bot {
      text-align: left;
      color: #333;
    }
    input {
      width: calc(100% - 70px);
      padding: 12px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      padding: 12px 15px;
      background: #2e7d32;
      color: white;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-left: 5px;
    }
  </style>
</head>
<body>
  <div class="chatbox">
    <h2>💬 Chat TerraGuia</h2>
    <div class="messages" id="chat"></div>
    <div style="display: flex;">
      <input type="text" id="input" placeholder="Digite sua dúvida...">
      <button onclick="send()">Enviar</button>
    </div>
  </div>
  <script>
    const chat = document.getElementById("chat");

    function send() {
      const input = document.getElementById("input");
      const question = input.value.trim();
      if (!question) return;

      appendMessage("Você", question, "user");
      input.value = "";

      setTimeout(() => {
        const answer = getAnswer(question.toLowerCase());
        appendMessage("TerraGuia IA", answer, "bot");
      }, 3000);
    }

    function appendMessage(sender, text, type) {
      const div = document.createElement("div");
      div.className = "msg " + type;
      div.innerHTML = <strong>${sender}:</strong> ${text};
      chat.appendChild(div);
      chat.scrollTop = chat.scrollHeight;
    }

    function getAnswer(q) {
      if (q.includes("oi") || q.includes("olá") || q.includes("bom dia")) return "Olá! 👋 Sou a IA da TerraGuia. Como posso te ajudar com sua lavoura hoje?";
      if (q.includes("como funciona")) return "A TerraGuia envia orientações diárias sobre sua lavoura com base no clima e tipo de cultura.";
      if (q.includes("preço") || q.includes("valor")) return "A plataforma completa custa R$ 99,90 por mês.";
      if (q.includes("gratuito")) return "Sim! Temos uma versão gratuita com recursos limitados.";
      if (q.includes("offline")) return "Sim, a TerraGuia funciona mesmo com internet limitada.";
      if (q.includes("culturas")) return "Milho, feijão, mandioca, hortaliças e outras culturas já estão disponíveis.";
      return "Desculpe, ainda estou aprendendo. Reformule sua pergunta, por favor.";
    }
  </script>
</body>
</html>
