<!DOCTYPE html>
<html>
<head>
<title>BMI Calculator</title>

<style>
body{
    font-family: Arial;
    background:#f4f4f4;
}

.container{
    width:350px;
    margin:100px auto;
    padding:20px;
    background:white;
    border-radius:10px;
    box-shadow:0 0 10px gray;
    text-align:center;
}

input{
    width:90%;
    padding:10px;
    margin:10px 0;
}

button{
    padding:10px 20px;
    background:#4CAF50;
    color:white;
    border:none;
    cursor:pointer;
}

button:hover{
    background:#45a049;
}

.result{
    margin-top:20px;
    font-size:18px;
}

.error{
    color:red;
}
</style>
</head>

<body>

<div class="container">

<h2>BMI Calculator</h2>

<input type="number" id="height" placeholder="Enter Height (cm)">
<input type="number" id="weight" placeholder="Enter Weight (kg)">

<button onclick="calculateBMI()">Calculate BMI</button>

<div class="result">
<p id="bmi"></p>
<p id="category"></p>
<p id="error" class="error"></p>
</div>

</div>

<script>

function calculateBMI(){

let height = document.getElementById("height").value;
let weight = document.getElementById("weight").value;

document.getElementById("error").innerText="";
document.getElementById("bmi").innerText="";
document.getElementById("category").innerText="";

if(height=="" || weight==""){
    document.getElementById("error").innerText="Please enter height and weight";
    return;
}

if(height<=0 || weight<=0){
    document.getElementById("error").innerText="Values must be positive";
    return;
}

height = height/100;

let bmi = weight/(height*height);
bmi = bmi.toFixed(2);

let category="";

if(bmi<18.5){
    category="Underweight";
}
else if(bmi<24.9){
    category="Normal";
}
else if(bmi<29.9){
    category="Overweight";
}
else{
    category="Obese";
}

document.getElementById("bmi").innerText="BMI: "+bmi;
document.getElementById("category").innerText="Category: "+category;

}

</script>

</body>
</html>
