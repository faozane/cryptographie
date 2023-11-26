# cryptographie faite par AMOUSSA Faozane Bidemi
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cryptographie</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background-color: #1a1a1a;
      color: white;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .container {
      max-width: 400px;
      width: 100%;
      text-align: center;
      background-color: #333;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
      border-radius: 10px;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.5s, transform 0.5s;
    }

    .hr-style {
      height: 5px;
      background-color: #45a049;
      margin: 15px 0;
    }

    h2 {
      color: #45a049;
    }

    textarea {
      width: calc(100% - 30px);
      padding: 15px;
      margin-bottom: 10px;
      border: 1px solid #45a049;
      border-radius: 5px;
      background-color: #1a1a1a;
      color: white;
    }

    button {
      padding: 10px;
      background-color: #45a049;
      color: white;
      border: none;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    button:hover {
      background-color: #1a1a1a;
    }

    p {
      font-size: 18px;
      margin-top: 10px;
      white-space: pre-wrap;
    }

    .fadeIn {
      opacity: 1;
      transform: translateY(0);
    }
  </style>
</head>
<body>

<div class="container" id="cryptoContainer">
  <hr class="hr-style">
  <h2>CRYPTOGRAPHIE</h2>

  <textarea id="inputText" rows="4" placeholder="Entrez votre texte..."></textarea>
  <button id="encryptBtn" onclick="encrypt()">Crypter</button>
  <button id="decryptBtn" onclick="decrypt()" style="display: none;">Décrypter</button>
  <p id="encryptedText"></p>
  <hr class="hr-style">
</div>

<script>
  const container = document.getElementById('cryptoContainer');
  container.classList.add('fadeIn');

  function crypto(textArray, shift) {
    const alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    return textArray.map(char => {
      const index = alphabet.indexOf(char);
      if (index !== -1) {
        const newIndex = (index + shift) % 26;
        return alphabet[newIndex];
      } else {
        return char;
      }
    }).join('');
  }

  function encrypt() {
    const inputText = document.getElementById('inputText').value.toUpperCase();
    const encryptedText = crypto(Array.from(inputText), 3);
    document.getElementById('encryptedText').innerText = `Message crypté : ${encryptedText}`;
    document.getElementById('inputText').value = '';
    toggleButtons();
  }

  function decrypt() {
    const inputText = document.getElementById('encryptedText').innerText.split(':')[1].trim();
    const decryptedText = crypto(Array.from(inputText), -3);
    document.getElementById('encryptedText').innerText = `Message décrypté : ${decryptedText}`;
    toggleButtons();
  }

  function toggleButtons() {
    const encryptBtn = document.getElementById('encryptBtn');
    const decryptBtn = document.getElementById('decryptBtn');
    encryptBtn.style.display = encryptBtn.style.display === 'none' ? 'block' : 'none';
    decryptBtn.style.display = decryptBtn.style.display === 'none' ? 'block' : 'none';
  }
</script>

</body>
</html>
