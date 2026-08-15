<!DOCTYPE html>
<html>
<head>
  <title>My Robot</title>
</head>

<body>
  <h1>🤖 My Robot</h1>

  <div id="chat"></div>

  <input id="message" placeholder="Type to your robot...">
  <button onclick="sendMessage()">Send</button>

  <script>
    function sendMessage() {
      const input = document.getElementById("message");
      const message = input.value.trim();

      if (!message) return;

      document.getElementById("chat").innerHTML +=
        "<p><b>You:</b> " + message + "</p>";

      let reply = "I heard you say: " + message;

      if (message.toLowerCase().includes("hello")) {
        reply = "Hello! 👋";
      }

      if (message.toLowerCase().includes("name")) {
        reply = "I'm your robot!";
      }

      document.getElementById("chat").innerHTML +=
        "<p><b>Robot:</b> " + reply + "</p>";

      input.value = "";
    }
  </script>
</body>
</html>