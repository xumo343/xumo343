<!-- index.html -->
<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Full Translator</title>
<style>
body { font-family: Arial; display:flex; justify-content:center; align-items:center; height:100vh; background:#f0f0f0;}
.container { background:white; padding:30px; border-radius:15px; box-shadow:0 0 15px rgba(0,0,0,0.2); text-align:center; width:400px;}
textarea, button { width:80%; padding:10px; margin:10px 0; font-size:16px; border-radius:8px; border:1px solid #ccc;}
button { cursor:pointer; background-color:#4CAF50; color:white; border:none;}
button:hover { background-color:#45a049; }
#output { margin-top:20px; font-weight:bold;}
</style>
</head>
<body>
<div class="container">
<h2>Full Translator</h2>
<textarea id="inputText" rows="4" placeholder="Matn kiriting..."></textarea><br>
<button onclick="translateText()">Tarjima qilish</button>
<div id="output"></div>
</div>

<script>
const dictionary = {
    "salom":"hello",
    "kitob":"book",
    "dunyo":"world",
    "yaxshi":"good",
    "men":"I",
    "sen":"",
    "o‘qish":"study",
    "maktab":"school",
    "do‘st":"friend",
    "osh":"pilaf",
    "olma":"apple",
    "uzum":"zilola",
    "qizil":"farangiz",
    "kok":"xumoyun",
    "yashil":"soliha"
};

function translateText(){
    let text = document.getElementById('inputText').value.toLowerCase().trim();
    if(!text){ document.getElementById('output').innerText=""; return; }

    let words = text.split(/\s+/);

    let translatedWords = words.map(word=>{
        if(dictionary[word]) return dictionary[word];
        for(let key in dictionary){
            if(dictionary[key] === word) return key;
        }
        return "";
    }).filter(w => w !== "");

    document.getElementById('output').innerText = translatedWords.join(" ");
}
</script>
</body>
</html>

