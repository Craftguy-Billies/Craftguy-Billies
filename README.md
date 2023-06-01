<h1>Welcome to billiez's Profile<h1>
    
<h3>Craftguy's YouTube Channel:<h3>
    <div>
    <ul>
        <li><a href="www.youtube.com/@Craftguy">Go to Chinese Channel</a></li>
        <li><a href="www.youtube.com/@Craftguy2">Go to Chinese Channel</a></li>
    </ul>
    </div>

<h3>Craftguy's Bilibili Channel:</h3>
    <div>
    <ul>
        <li><a href="https://space.bilibili.com/1507548366">Go to Bilibili Channel</a></li>
    </ul>
    </div>

<h2>Recent Project: Scoring System by Appearance - HTML Code</h2>

```js
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
