<h1><img src="https://yt3.googleusercontent.com/ytc/AGIKgqPOqJk6sdPnH7SatHqQl2B1A9VTKzfREgMJpqNf=s900-c-k-c0x00ffffff-no-rj" style="width:30px">&nbsp;Welcome to billiez's Profile!<h1>
<img src="https://billiez.tk/banner.png" style="width:100%">
<h3>Craftguy's YouTube Channel:<h3>
    <h5>
    <ul>
        <li><a href="https://www.youtube.com/@Craftguy" target="_blank">Go to Chinese Channel</a></li>
        <li><a href="https://www.youtube.com/@Craftguy2" target="_blank">Go to English Channel</a></li>
    </ul>
    </h5>

<h3>Craftguy's Bilibili Channel:</h3>
    <h5>
    <ul>
        <li><a href="https://space.bilibili.com/1507548366" target="_blank">Go to Bilibili Channel</a></li>
    </ul>
    </h5>

<h2>Recent Project: Scoring System by Appearance - HTML Code</h2>

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.14.7/dist/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@4.3.1/dist/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.3.1/dist/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

<meta name="viewport" content="initial-scale=1.0,width=device-width">

<style>

html,body{
    margin-left:10px;
    margin-top:10px;
    background-color: #f9fade;
}
input[type="range"]{
    width:60vw;
}
</style>

<h2>Scoring System by Appearance</h2><br>

Face: <input type="range" id="face" step="2.5" min="0" max="50" onchange="display()"><br><span id="v1"></span>/100<br>
Body shape: <input type="range" id="body" step="1.5" min="0" max="15" onchange="display()" style="width:50vw"><br><span id="v2"></span>/100<br>
Skin: <input type="range" id="skin" step="1.5" min="0" max="15" onchange="display()"><br><span id="v4"></span>/100<br>
Temperament: <input type="range" id="temperament" step="2" min="0" max="20" onchange="display()" style="width:50vw"><br><span id="v3"></span>/100<br>

Extra body: <input type="checkbox" id="eb" onchange="valid()"><br><br>

<input type="button" class="btn btn-success" value="Predict!" id="submit" onclick="predict()" onload="display()" style="height:50px;font-size:26px;margin-right:10px;">
<input type="button" class="btn btn-info" value="Reset" id="reset" onclick="reset()" style="height:50px;font-size:26px;margin-right:10px;">

<div id="calculate"></div>

<div id="predict"></div>

<script>
window.addEventListener("load",function(){
    display();
})

function reset(){
    var face = document.getElementById("face");
    var body = document.getElementById("body");
    var skin = document.getElementById("skin");
    var temperament = document.getElementById("temperament");

    face.value = 25;
    body.value = 7.5;
    skin.value = 7.5;
    temperament.value = 10;

    display();
}

function valid(){
    var body = document.getElementById("body").value;
    if(body < 15){
        alert("Body not full marks yet!");
        var eb = document.getElementById("eb");
        eb.checked = false;
    }
}

function display(){
    var v1 = document.getElementById("v1");
    var v2 = document.getElementById("v2");
    var v3 = document.getElementById("v3");
    var v4 = document.getElementById("v4");
    var face = document.getElementById("face").value;
    var body = document.getElementById("body").value;
    var skin = document.getElementById("skin").value;
    var temperament = document.getElementById("temperament").value;

    v1.innerHTML = face*100/50;
    v2.innerHTML = body*100/15;
    v4.innerHTML = skin*100/15;
    v3.innerHTML = temperament*100/20;
}

function predict(){
    var v1 = document.getElementById("v1");
    var v2 = document.getElementById("v2");
    var v3 = document.getElementById("v3");
    var v4 = document.getElementById("v4");
    var face = document.getElementById("face").value;
    var body = document.getElementById("body").value;
    var skin = document.getElementById("skin").value;
    var temperament = document.getElementById("temperament").value;
    var total = Number(body) + Number(face) + Number(temperament) + Number(skin);
    var eb = document.getElementById("eb");
    if (eb.checked){
        total = total + 5;
        if(body < 15){
            alert("Body not full marks yet!");
            eb.checked = false;
            total = total - 5;
        }
    }
    if (total > 100){
        total = 100;
    }
    var cal = document.getElementById("calculate");
    var predict = document.getElementById("predict");
    cal.innerHTML = "Score: " + total + "/100";
    if (total >= 86){
        predict.innerHTML = "Grade: S <br> Tell me where she is. I wanna know her!"
    } 
    else if (total >= 79){
        predict.innerHTML = "Grade: A";
    }
    else if (total >= 73){
        predict.innerHTML = "Grade: A-";
    }
    else if (total >= 67){
        predict.innerHTML = "Grade: B+";
    }
    else if (total >= 59){
        predict.innerHTML = "Grade: B";
    }
    else if (total >= 52){
        predict.innerHTML = "Grade: B-";
    }
    else if (total >= 45){
        predict.innerHTML = "Grade: C+";
    }
    else if (total >= 39){
        predict.innerHTML = "Grade: C";
    }
    else if (total >= 34){
        predict.innerHTML = "Grade: C-";
    }
    else if (total >= 29){
        predict.innerHTML = "Grade: D+";
    }
    else if (total >= 22){
        predict.innerHTML = "Grade: D";
    }
    else {
        predict.innerHTML = "Grade: F";
    }
}
</script>
```

<h3>Embed the website to your's:</h3>
    
```html
<style>
body,html{
    margin:0;
    padding:0;
}
</style>
<iframe src="http://photograph.eu.org/rating.php" style="width:100%;height:100vh;border:0;"></iframe>
```
    
<h2>billiez Girls Type Predictor using AI Model</h2>
    
```html
<!DOCTYPE html>
<!--[if lt IE 7]>      <html class="no-js lt-ie9 lt-ie8 lt-ie7"> <![endif]-->
<!--[if IE 7]>         <html class="no-js lt-ie9 lt-ie8"> <![endif]-->
<!--[if IE 8]>         <html class="no-js lt-ie9"> <![endif]-->
<!--[if gt IE 8]>      <html class="no-js"> <!--<![endif]-->
<html>
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>billiez Girls Type</title>
        <meta name="description" content="">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="icon" type="image/x-icon" href="/favicon.ico">
        <link rel="shortcut icon" type="image/x-icon" href="/favicon.ico">
        <meta name="theme-color" content="#9800d4">
        <script src="https://unpkg.com/brain.js@2.0.0-beta.18/dist/browser.js" defer></script>
        <script src="girls.js" defer></script>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-iYQeCzEYFbKjA/T2uDLTpkwGzCiq6soy8tYaI1GyVh/UjpbCx/TYkiZhlZB6+fzT" crossorigin="anonymous">
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-u1OknCvxWvY5kfmNBILK2hRnQC3Pr17a+RTT6rIHI7NnikvbZlHgTPOOmMi466C8" crossorigin="anonymous"></script>
        <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Inconsolata">
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.1/jquery.min.js"></script>
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/anuraghazra/VerlyRangeSlider@v1.0.0/src/style.css" />
        <link rel="stylesheet" href="/style.css" />
        <link rel="stylesheet" href="/overall-style.css" />
        <link id="u-theme-google-font" rel="stylesheet" href="https://fonts.googleapis.com/css?family=Montserrat:100,100i,200,200i,300,300i,400,400i,500,500i,600,600i,700,700i,800,800i,900,900i|Open+Sans:300,300i,400,400i,500,500i,600,600i,700,700i,800,800i">
        <link id="u-page-google-font" rel="stylesheet" href="https://fonts.googleapis.com/css?family=Montserrat:100,100i,200,200i,300,300i,400,400i,500,500i,600,600i,700,700i,800,800i,900,900i|Raleway:100,100i,200,200i,300,300i,400,400i,500,500i,600,600i,700,700i,800,800i,900,900i|Noto+Sans+Modi:400|B612:400,400i,700,700i|Inconsolata:200,300,400,500,600,700,800,900">
        <script src="script.js"></script>
        <style>
            html,body{
                background-image: url(cutie.jpg);
                color: #000;
            }
            input[type="range"]{
                width:50%;
            }
            input[type="range"]:disabled{
                background-color: #cfcfcf;
            }
            @media only screen and (max-width: 768px){
                #st{
                    font-size:22px;
                }
            }
            #st{color:rgb(97, 96, 96)}
            #st:hover{
                cursor: pointer;
                color:#000;
            }
            #accuracy{
                border:#000 1px solid;
                height:20px;
                width:250px;
            }
            #bar{
                height:100%;
            }
        </style>
    </head>
    <body>
        <!--[if lt IE 7]>
            <p class="browsehappy">You are using an <strong>outdated</strong> browser. Please <a href="#">upgrade your browser</a> to improve your experience.</p>
        <![endif]-->

        <div class="container pt-3 mt-3">
            <h1 style="font-family:'Inconsolata'">billiez Girls' Type Predictor using Machine Learning</h1>
            <div class="slider-container" class="pt-3 mt-3 mx-3" style="font-family:'Inconsolata'">
                <span style="font-size:20px;">Long hair? </span><br><input type="range" min="1" max="5" value="3" id="r1" class="range ps6 slider"><br>
                <span style="font-size:20px;">Fat? </span><br><input type="range" min="1" max="5" value="3" id="r2" class="range ps6 slider"><br>
                <span style="font-size:20px;">Tall? </span><br><input type="range" min="1" max="5" value="3" id="r3" class="range ps6 slider"><br>
                <span style="font-size:20px;">Rounded face? </span><br><input type="range" min="1" max="7" value="4" id="r4" class="range ps6 slider"><br>
                <span style="font-size:20px;">Big boobs? </span><br><input type="range" min="1" max="5" value="3" id="r5" class="range ps6 slider"><br>
                <span style="font-size:20px;">Inappropriate face ratio/exceptions? </span><br><input type="range" min="1" max="5" value="3" id="r6" class="range ps6 slider"><br>
                <input type="button" class="mt-2 btn btn-info" id="btn" value="Predict!" style="font-size:28px;">
                <div class="mt-2" id="result" style="font-family:'Inconsolata';display:none"></div>
                <div class="mt-2" id="display" style="font-family:'Inconsolata';font-size:31px;"></div>
                <div id="prediction-index"><span style="font-size:23px;">Accuracy: </span><span id="index" style="font-size:23px;"></span><div class="mt-2" id="accuracy"><div id="bar"></div></div></div>
                <input type="button" class="mt-3 btn btn-success" id="accurate" value="True" style="font-size:24px;display:none">
                <input type="button" class="mt-2 btn btn-danger" id="not-accurate" value="False" style="font-size:24px;display:none">
                <div class="mt-2" style="text-decoration:underline;font-size:27px;font-family:'Inconsolata';" id="st">Inappropriate face ratio explanation 🔽</div>
                <p class="mt-1" id="tc" style="font-size:22px;font-family:'Inconsolata';">
                    <ul class="big">
                        <li>Big face: the face radius is obviously larger than normal girls</li>
                        <li>Eyes distance: the distance between two eyes does not match face shape</li>
                        <li>Concentration: eyes, nose and mouth too concentrated at the middle of the face</li>
                        <li>Size: abnormally small/big eyes/nose/mouth
                            <ul>
                                <li>Major parts of deduction: Small (Flat) eyes, Big nose, Big mouth</li>
                            </ul>
                        </li>
                        <li>Exceptions:
                            <ul>
                                <li>Bad skin: full of acne/skin diseases</li>
                                <li>Untidy appearance: messy hair, dirty face, etc</li>
                                <li>Skin color: dark comparing with normal girls</li>
                            </ul>
                        </li>
                    </ul>
                </p>
                <a href="lstm.html" class="btn btn-info mb-2">Deep Learning using RNN Model</a>
            </div>
        </div>

        <footer class="u-align-center u-clearfix u-footer u-grey-80 u-footer" id="sec-3af1"><div class="u-clearfix u-sheet u-sheet-1">
            <p class="u-small-text u-text u-text-variant u-text-1" style="padding:10px;padding-bottom:5px;;font-family:'Inconsolata';height:33px;">Disclaimer: The machine learning system is still in training process. The results may not be 100% accurate.</p>
            <p class="u-small-text u-text u-text-variant u-text-1" style="padding:10px;font-family:'Inconsolata';height:33px;">©Copyright by billiez™, 2023. All rights reserved.</p>
          </div></footer>

        
        
    </body>
</html>
```
    
<h3>Javascript Code - girls.js:</h3>
    
```javascript
    
//Javascript for Training Neural Network Model for billiez Girls Type.

//Copyright by billiez, 2023. All rights reserved.

const net = new brain.NeuralNetwork();

$("#prediction-index").css("display","none");

const data = [
    {"input":[2,0,1,4,2,0],"output":["1"]},
    {"input":[1,0,0,3,2,0],"output":["1"]},
    {"input":[4,4,0,4,4,1],"output":["0"]},
    {"input":[2,2,0,4,2,0],"output":["1"]},
    {"input":[4,1,0,4,2,0],"output":["1"]},
    {"input":[4,0,0,0,0,0],"output":["0"]},
    {"input":[0,0,4,0,4,0],"output":["0"]},
    {"input":[4,3,3,2,2,2],"output":["0"]},
    {"input":[3,0,4,0,4,0],"output":["0"]},
    {"input":[4,1,2,4,3,0],"output":["1"]},
    {"input":[2,1,0,3,2,0],"output":["1"]},
    {"input":[4,0,2,3.3333333333333335,2,0],"output":["1"]},
    {"input":[4,0,3,0.6666666666666666,1,0],"output":["0"]},
    {"input":[4,0,4,0,2,0],"output":["0"]},
    {"input":[4,0,0,3.3333333333333335,0,2],"output":["0"]},
    {"input":[4,1,3,2.6666666666666665,0,0],"output":["0"]},
    {"input":[4,0,2,2.6666666666666665,1,1],"output":["0"]},
    {"input":[4,0,2,2,0,0],"output":["0"]},
    {"input":[3,0,0,2.6666666666666665,0,0],"output":["1"]},
    {"input":[3,0,0,1.3333333333333333,0,0],"output":["0"]},
    {"input":[3,0,0,2,0,0],"output":["0"]},
    {"input":[0,4,0,4,4,0],"output":["0"]},
    {"input":[4,0,0,4,4,3],"output":["0"]},
    {"input":[4,0,1,2.6666666666666665,0,0],"output":["1"]},
    {"input":[4,1,0,3.3333333333333335,0,0],"output":["1"]},
    {"input":[3,1,0,4,1,1],"output":["1"]},
    {"input":[0,3,2,3.3333333333333335,1,1],"output":["0"]},
    {"input":[4,2,0,4,1,1],"output":["0"]},
    {"input":[4,1,0,4,1,1],"output":["0"]},
    {"input":[1,0,0,3.3333333333333335,2,0],"output":["1"]},
    {"input":[1,0,3,2,4,0],"output":["0"]},
    {"input":[4,0,1,2.6666666666666665,2,0],"output":["1"]}
];

net.train(data);

$(function(){
    $("ul.big").slideToggle(0);
})

$("#st").click(function(){
    $("ul.big").slideToggle(1000);
    const st = document.getElementById("st");
    if(st.innerHTML == "Inappropriate face ratio explanation 🔼"){
        st.innerHTML = "Inappropriate face ratio explanation 🔽";
    }
    else{
        st.innerHTML = "Inappropriate face ratio explanation 🔼";
    }
})

const btn = document.getElementById("btn");
btn.addEventListener("click",function(){
    const r1 = document.getElementById("r1").value - 1;
    const r2 = document.getElementById("r2").value - 1;
    const r3 = document.getElementById("r3").value - 1;
    const r4 = (document.getElementById("r4").value - 1) / 1.5;
    const r5 = document.getElementById("r5").value - 1;
    const r6 = document.getElementById("r6").value - 1;

    const result = document.getElementById("result");
    const guess = net.run([r1,r2,r3,r4,r5,r6])[0];

    $("#prediction-index").css("display","block");

    result.innerHTML = guess > 0.5 ? "1" : "0";
    if(result.innerHTML == "1"){
        const display = document.getElementById("display");
        display.innerHTML = "Billy should love this girl! (" + Math.floor(guess * 100) + "%)";
        display.style.color = "#000";
        const index = document.getElementById("index");
        $("#bar").css("width", Math.floor(guess * 100) + "%");
        if(Math.floor(guess * 100) < 72){
            $("#bar").css("background-color","red");
            index.innerHTML = "Low";
        }
        else if(Math.floor(guess * 100) < 82){
            $("#bar").css("background-color","yellow");
            index.innerHTML = "Normal";
        }
        else{
            $("#bar").css("background-color","green");
            index.innerHTML = "High";
        }
    }
    else{
        const display = document.getElementById("display");
        display.innerHTML = "Billy should not love this girl! (" + Math.floor(100 - guess * 100) + "%)";
        display.style.color = "#9c2017";
        const index = document.getElementById("index");
        $("#bar").css("width", Math.floor(100 - guess * 100) + "%");
        if(Math.floor(100 - guess * 100) < 72){
            $("#bar").css("background-color","red");
            index.innerHTML = "Low";
        }
        else if(Math.floor(100 - guess * 100) < 82){
            $("#bar").css("background-color","yellow");
            index.innerHTML = "Normal";
        }
        else{
            $("#bar").css("background-color","green");
            index.innerHTML = "High";
        }
    }

    $(".range").prop('disabled','true');

    $(".btn").css("display","block");
})

const accurate = document.getElementById("accurate");
const notAccurate = document.getElementById("not-accurate");

accurate.addEventListener("click",function(){
    const display = document.getElementById("display");
    display.innerHTML = "";

    $("#prediction-index").css("display","none");

    const r1 = document.getElementById("r1").value - 1;
    const r2 = document.getElementById("r2").value - 1;
    const r3 = document.getElementById("r3").value - 1;
    const r4 = (document.getElementById("r4").value - 1) / 1.5;
    const r5 = document.getElementById("r5").value - 1;
    const r6 = document.getElementById("r6").value - 1;
    const result = document.getElementById("result");

    data.push({
        input: [r1,r2,r3,r4,r5,r6],
        output: [result.innerHTML]
    })

    print();

    $(".range").removeAttr('disabled');
    $(".range").val(3);
    $("#r4").val(4);

    result.innerHTML = "";

    accurate.style.display = "none";
    notAccurate.style.display = "none";
})

notAccurate.addEventListener("click",function(){
    const display = document.getElementById("display");
    display.innerHTML = "";

    $("#prediction-index").css("display","none");
    
    const r1 = document.getElementById("r1").value - 1;
    const r2 = document.getElementById("r2").value - 1;
    const r3 = document.getElementById("r3").value - 1;
    const r4 = (document.getElementById("r4").value - 1) / 1.5;
    const r5 = document.getElementById("r5").value - 1;
    const r6 = document.getElementById("r6").value - 1;
    const result = document.getElementById("result");
    const record = result.innerHTML == "1" ? "0" : "1";

    data.push({
        input: [r1,r2,r3,r4,r5,r6],
        output: [record]
    })

    print();

    $(".range").removeAttr('disabled');
    $(".range").val(3);
    $("#r4").val(4);

    result.innerHTML = "";

    accurate.style.display = "none";
    notAccurate.style.display = "none";
})

function print(){
    console.log(JSON.stringify(data));
}
    
```
    
<h3>Embed the website to your's:</h3>
    
```html
<style>
body,html{
    margin:0;
    padding:0;
}
</style>
<iframe src="https://girls.cbu.net" style="width:100%;height:100vh;border:0;"></iframe>
```
