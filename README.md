<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Language Translator</title>

<style>

body{
    font-family: Arial;
    background: #dfe3e8;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container{
    width: 500px;
    background: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0px 0px 10px gray;
}

h1{
    text-align: center;
}

textarea{
    width: 100%;
    height: 100px;
    padding: 10px;
    margin-top: 20px;
    font-size: 18px;
}

select{
    width: 100%;
    padding: 10px;
    margin-top: 20px;
    font-size: 18px;
}

button{
    width: 100%;
    padding: 12px;
    margin-top: 20px;
    background: blue;
    color: white;
    border: none;
    font-size: 18px;
    cursor: pointer;
}

button:hover{
    background: darkblue;
}

#result{
    margin-top: 20px;
    padding: 15px;
    background: #f1f1f1;
    border-radius: 10px;
    font-size: 20px;
}

</style>

</head>

<body>

<div class="container">

    <h1>Language Translator</h1>

    <textarea id="text" placeholder="Enter text"></textarea>

    <select id="language">
        <option value="ta">Tamil</option>
        <option value="hi">Hindi</option>
        <option value="fr">French</option>
        <option value="es">Spanish</option>
    </select>

    <button onclick="translateText()">Translate</button>

    <div id="result">Translation appears here</div>

</div>

<script>

async function translateText(){

    let text = document.getElementById("text").value;

    let language = document.getElementById("language").value;

    let url =
    `https://api.mymemory.translated.net/get?q=${text}&langpair=en|${language}`;

    let response = await fetch(url);

    let data = await response.json();

    document.getElementById("result").innerHTML =
    data.responseData.translatedText;
}

</script>

</body>
</html>
