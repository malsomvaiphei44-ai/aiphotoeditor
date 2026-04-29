index.html
<!DOCTYPE html>
<html>
<head><link rel="stylesheet" href="styles.css">
  <title>AI Photo Editor</title>
  <link rel="stylesheet" href="styles.css">
</head>

<body>

  <div class="container">
    <h1>AI Photo Editor</h1>

    <input type="file" id="fileInput" accept="image/*">
    <br>

    <button onclick="processImage()">Remove Background</button>

    <div id="loader" class="loader"></div>

    <img id="previewImage">

    <a id="downloadBtn" download="edited.png">Download Image</a>
  </div>

  <script src="script.js"></script>

<script src="script.js"></script></body>
</html>
CSS
body {
  font-family: Arial;
  background: linear-gradient(to right, #1e1e2f, #3a3a5a);
  color: white;
  text-align: center;
}

.container {
  margin-top: 50px;
}

input {
  margin: 20px;
}

button {
  padding: 12px 25px;
  border: none;
  background: #ff4b2b;
  color: white;
  border-radius: 25px;
  cursor: pointer;
}

img {
  max-width: 300px;
  margin-top: 20px;
  border-radius: 15px;
}

.loader {
  display: none;
  margin: 20px auto;
  border: 5px solid #fff;
  border-top: 5px solid transparent;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  100% { transform: rotate(360deg); }
}

#downloadBtn {
  display: none;
  margin-top: 15px;
  padding: 10px 20px;
  background: limegreen;
  color: white;
  border-radius: 20px;
  text-decoration: none;
}

/* ✨ AI effect styles */
.processed {
  filter: blur(4px) brightness(1.1);
}

.cutout {
  filter: drop-shadow(0 0 15px rgba(0,255,150,0.7));
}
script.js
Javascript 
function processImage() {
  const fileInput = document.getElementById("fileInput");
  const file = fileInput.files[0];

  if (!file) {
    alert("Please upload an image first!");
    return;
  }

  const loader = document.getElementById("loader");
  const preview = document.getElementById("previewImage");
  const downloadBtn = document.getElementById("downloadBtn");

  loader.style.display = "block";
  preview.style.display = "none";
  downloadBtn.style.display = "none";

  setTimeout(() => {
    const imageURL = URL.createObjectURL(file);

    preview.src = imageURL;
    preview.style.display = "block";

    // ✨ Apply AI-like effect
    preview.classList.add("processed", "cutout");

    downloadBtn.href = imageURL;
    downloadBtn.style.display = "inline-block";

    loader.style.display = "none";
  }, 800);
}
