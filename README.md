# A-fatimah-albahry <!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>نتيجة الطفل</title>

<style>
body{
    font-family: Arial;
    text-align:center;
    padding:20px;

    /* خلفية تموج ألوان قوس قزح */
    background: linear-gradient(-45deg, #ff0000, #ff7f00, #ffff00, #00ff00, #0000ff, #4b0082, #8f00ff);
    background-size: 400% 400%;
    animation: rainbow 15s ease infinite;
}

@keyframes rainbow {
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
}

/* رأس الصفحة */
.header{
    background:white;
    padding:15px;
    border-radius:12px;
    margin-bottom:15px;
}

.logo{
    width:90px;
    margin-bottom:10px;
}

.header h2{
    margin:0;
    color:#0a6ebd;
}

.header h3{
    margin:5px 0 0;
    font-weight:normal;
    color:#333;
}

.container{
    background:white;
    padding:25px;
    border-radius:15px;
    box-shadow:0 0 15px rgba(0,0,0,0.2);
    max-width:350px;
    margin:auto;
}

h1{
    color:#ff6b6b;
}

input{
    width:90%;
    padding:10px;
    margin:10px 0;
    border-radius:8px;
    border:1px solid #ccc;
    text-align:center;
}

button{
    padding:10px 20px;
    border:none;
    border-radius:8px;
    background:#ff6b6b;
    color:white;
    font-size:16px;
    cursor:pointer;
}

button:hover{
    background:#ff3b3b;
}

.result{
    margin-top:15px;
    font-size:18px;
    color:#333;
    font-weight:bold;
}

.footer{
    margin-top:15px;
    font-size:14px;
    color:#555;
}
</style>
</head>

<body>

<div class="header">
    <img src="logo.png" class="logo">
    <h2>وزارة التعليم</h2>
    <h3>إدارة التعليم بمنطقة نجران</h3>
</div>

<div class="container" id="printArea">

<h1>حساب عمر الطفل</h1>

<input type="date" id="birthDate">

<br>

<button onclick="calculateAge()">عرض النتيجة</button>

<div class="result" id="result"></div>

<div class="footer">
مديرة الروضة ومصممته:<br>
<strong>فاطمه صالح ال بحري</strong>
</div>

</div>

<br>

<button onclick="window.print()">🖨️ طباعة النتيجة</button>

<script>
function calculateAge(){
    const birthDate=document.getElementById("birthDate").value;
    if(!birthDate){
        document.getElementById("result").innerHTML="الرجاء اختيار تاريخ الميلاد";
        return;
    }

    const birth=new Date(birthDate);
    const today=new Date();

    let years=today.getFullYear()-birth.getFullYear();
    let months=today.getMonth()-birth.getMonth();
    if(today.getDate() < birth.getDate()){
        months--;
    }
    if(months<0){
        years--;
        months+=12;
    }

    // تحديد الفصل حسب العمر
    let grade = "";
    if(years < 3) grade = "غير مناسب للروضة بعد";
    else if(years == 3) grade = "براعم المستقبل (3 سنوات)";
    else if(years == 4) grade = "الورود (4 سنوات)";
    else if(years == 5) grade = "المرح (5 سنوات)";
    else grade = "تأهيل للصف الأول الابتدائي (6 سنوات فما فوق)";

    document.getElementById("result").innerHTML=
    "العمر: "+years+" سنة و "+months+" شهر<br>فصل الروضة المناسب: "+grade;
}
</script>

</body>
</html>
