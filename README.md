<!DOCTYPE html>
<html lang="en">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>AI Tools for Creators</title>

<style>

body{
font-family:Arial, sans-serif;
background:#f4f6fb;
margin:0;
padding:40px 20px;
color:#333;
}

header{
text-align:center;
margin-bottom:40px;
}

h1{
color:#0d47a1;
margin-bottom:5px;
}

.subtitle{
color:#666;
font-size:14px;
}

.container{
max-width:900px;
margin:auto;
display:grid;
grid-template-columns:1fr 1fr;
gap:20px;
}

.tool-card{
background:white;
padding:20px;
border-radius:10px;
box-shadow:0 4px 14px rgba(0,0,0,0.08);
transition:0.2s;
}

.tool-card:hover{
transform:translateY(-4px);
box-shadow:0 8px 20px rgba(0,0,0,0.12);
}

h2{
margin-top:0;
color:#1565c0;
font-size:18px;
}

input,textarea{
width:100%;
padding:10px;
margin-top:8px;
border:1px solid #ccc;
border-radius:6px;
font-size:14px;
box-sizing:border-box;
}

textarea{
min-height:90px;
}

button{
width:100%;
padding:10px;
margin-top:10px;
background:#0d47a1;
color:white;
border:none;
border-radius:6px;
font-size:14px;
cursor:pointer;
}

button:hover{
background:#1565c0;
}

.output{
margin-top:12px;
background:#f7f7f7;
border:1px solid #ddd;
padding:12px;
border-radius:6px;
white-space:pre-wrap;
font-size:14px;
}

footer{
text-align:center;
margin-top:40px;
font-size:13px;
color:#777;
}

@media(max-width:700px){
.container{
grid-template-columns:1fr;
}
}

</style>
</head>

<body>

<header>
<h1>AI Tools for Creators</h1>
<div class="subtitle">Free tools for captions, hashtags, prompts and rap lyrics</div>
</header>

<div class="container">

<div class="tool-card">
<h2># Hashtag Generator</h2>

<input id="topic" placeholder="Example: fitness">

<button onclick="generateHashtags()">Generate Hashtags</button>

<div class="output" id="hashtagOutput"></div>
</div>


<div class="tool-card">
<h2>Clickbait Title Generator</h2>

<input id="clickbaitTopic" placeholder="Example: AI tools">

<button onclick="generateTitle()">Generate Title</button>

<div class="output" id="titleOutput"></div>
</div>


<div class="tool-card">
<h2>Emoji Enhancer</h2>

<textarea id="emojiText" placeholder="Write text here..."></textarea>

<button onclick="addEmojis()">Add Emojis</button>

<div class="output" id="emojiOutput"></div>
</div>


<div class="tool-card">
<h2>Word Counter</h2>

<textarea id="wordText" placeholder="Paste your text..."></textarea>

<button onclick="countWords()">Count Words</button>

<div class="output" id="wordOutput"></div>
</div>


<div class="tool-card">
<h2>Prompt Generator</h2>

<button onclick="generatePrompt()">Generate Prompt</button>

<div class="output" id="promptOutput"></div>
</div>


<div class="tool-card">
<h2>AI Rap Song Generator</h2>

<textarea id="rapInput" placeholder="Write your idea, story or lyrics..."></textarea>

<button onclick="generateRapSong()">Generate Rap Song</button>

<div class="output" id="rapSongOutput"></div>
</div>

</div>

<footer>
Free AI tools for content creators
</footer>


<script>

const hashtagDb={
fitness:["#Fitness","#Gym","#Workout","#Health","#FitLife"],
travel:["#Travel","#Adventure","#Explore","#Wanderlust","#TravelLife"],
food:["#Food","#Foodie","#Delicious","#InstaFood","#Yummy"],
tech:["#Tech","#AI","#Innovation","#Future","#Startup"]
};

function generateHashtags(){

const topic=document.getElementById("topic").value.toLowerCase();

const list=hashtagDb[topic]||["#Content","#Creator","#Trending","#Viral","#Ideas"];

document.getElementById("hashtagOutput").innerText=list.join(" ");

}



const titles=[
"You won't believe what happened with {topic}",
"5 secrets about {topic} nobody tells you",
"How {topic} changed everything",
"The truth about {topic}",
"Top tricks creators use for {topic}"
];

function generateTitle(){

const topic=document.getElementById("clickbaitTopic").value||"this";

const template=titles[Math.floor(Math.random()*titles.length)];

document.getElementById("titleOutput").innerText=template.replace("{topic}",topic);

}



const emojiMap={
love:"❤️",
coffee:"☕",
travel:"🌍",
happy:"😊",
food:"🍔",
star:"⭐"
};

function addEmojis(){

let txt=document.getElementById("emojiText").value;

for(const word in emojiMap){

const re=new RegExp("\\b"+word+"\\b","gi");

txt=txt.replace(re,emojiMap[word]+" "+word);

}

document.getElementById("emojiOutput").innerText=txt;

}



function countWords(){

const txt=document.getElementById("wordText").value.trim();

const words=txt?txt.split(/\s+/).length:0;

const chars=txt.length;

document.getElementById("wordOutput").innerText="Words: "+words+"\nCharacters: "+chars;

}



const subjects=["AI","Fitness","Marketing","Travel","Food"];
const actions=["ideas","tips","strategies","guides"];
const formats=["for TikTok","for Instagram","for YouTube","for blogs"];

function generatePrompt(){

const s=subjects[Math.floor(Math.random()*subjects.length)];
const a=actions[Math.floor(Math.random()*actions.length)];
const f=formats[Math.floor(Math.random()*formats.length)];

document.getElementById("promptOutput").innerText="Create "+a+" about "+s+" "+f;

}



function generateRapSong(){

const text=document.getElementById("rapInput").value.trim();

if(text===""){
document.getElementById("rapSongOutput").innerText="Write some text first.";
return;
}

const intros=[
"Late night grind in the city lights",
"Cold streets moving through the neon glow",
"Dark trap drums while the bassline hits",
"Another night chasing bigger dreams"
];

const hooks=[
"Started from the bottom now the vision clear",
"Hustle every night while the world don't hear",
"Dreams getting closer every single year",
"Turn the pain to power that's the life right here"
];

const lines=text.split(/\n|\.|,/).filter(l=>l.trim()!="");

let verse="";

for(let i=0;i<Math.min(4,lines.length);i++){
verse+=lines[i].trim()+"\n";
}

const intro=intros[Math.floor(Math.random()*intros.length)];
const hook=hooks[Math.floor(Math.random()*hooks.length)];

const song=
"INTRO\n"+intro+"\n\n"+
"VERSE\n"+verse+"\n"+
"HOOK\n"+hook+"\n"+hook;

document.getElementById("rapSongOutput").innerText=song;

}

</script>

</body>
</html>
