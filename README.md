
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TAQI | Write Your Opinion</title>

<style>
body{
    margin:0;
    font-family:Arial,sans-serif;
    background:#121212;
    color:white;
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
}

.container{
    background:#1e1e1e;
    width:90%;
    max-width:500px;
    padding:25px;
    border-radius:15px;
    text-align:center;
    box-shadow:0 0 15px rgba(0,0,0,.5);
}

h1{
    color:#00bfff;
    margin-bottom:5px;
}

h2{
    font-size:20px;
    margin-bottom:5px;
}

p{
    color:#ccc;
    margin-bottom:20px;
}

textarea{
    width:100%;
    height:150px;
    border:none;
    border-radius:10px;
    padding:10px;
    font-size:16px;
    resize:none;
}

button{
    margin-top:15px;
    width:100%;
    padding:12px;
    border:none;
    border-radius:10px;
    background:#00bfff;
    color:white;
    font-size:18px;
    cursor:pointer;
}

button:hover{
    background:#0099cc;
}

.footer{
    margin-top:20px;
    font-size:13px;
    color:#888;
}
</style>
</head>

<body>

<div class="container">

<h1>TAQI</h1>

<h2>Write your opinion about me</h2>

<p>اكتب رأيك عني</p>

<textarea placeholder="Write your message here... | اكتب رسالتك هنا..."></textarea>

<button>Send | إرسال</button>

<div class="footer">
Thank you for visiting ❤️<br>
شكراً لزيارتك ❤️
</div>

</div>
<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/12.18.0/firebase-app.js";
import { getFirestore, collection, addDoc, serverTimestamp } from "https://www.gstatic.com/firebasejs/12.18.0/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyBIhlERF0_2HXE58lms4qMBMgZdH6aLjOM",
  authDomain: "taki-efdfa.firebaseapp.com",
  projectId: "taki-efdfa",
  storageBucket: "taki-efdfa.firebasestorage.app",
  messagingSenderId: "430185667838",
  appId: "1:430185667838:web:23bc24a8ba84f6fa4ed9af"
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

const textarea = document.querySelector("textarea");
const button = document.querySelector("button");

button.addEventListener("click", async () => {
  const message = textarea.value.trim();

  if (message === "") {
    alert("Please write a message.");
    return;
  }

  try {
    await addDoc(collection(db, "messages"), {
      text: message,
      createdAt: serverTimestamp()
    });

    alert("Thank you! Your message has been sent.");
    textarea.value = "";
  } catch (error) {
    alert("Error sending message.");
    console.error(error);
  }
});
</script>
</body>
</html>
