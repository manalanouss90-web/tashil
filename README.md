[موقع_مدرسي_شخصي (2).html](https://github.com/user-attachments/files/24172790/_._.2.html)
<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>تسهيل الدراسة</title>
<style>
* { box-sizing: border-box; }
body {
  margin:0;
  font-family: "Segoe UI", Tahoma, Arial, sans-serif;
  direction: rtl;
  color:#333;
  background: linear-gradient(135deg, #e3f2fd, #fce4ec);
  min-height: 100vh;
}
header { background: linear-gradient(135deg,#3f51b5,#5c6bc0); color:white; padding:40px 20px; text-align:center; }
header h1 { margin:0; font-size:32px; }
header p { font-size:18px; opacity:0.9; }
nav { background-color:#283593; display:flex; justify-content:center; gap:20px; padding:12px 0; flex-wrap:wrap; }
nav a { color:white; text-decoration:none; font-weight:bold; transition:color 0.3s; }
nav a:hover { color:#ffeb3b; }
.container { max-width:1000px; margin:auto; padding:20px; }
section { background-color:white; margin-bottom:20px; padding:25px; border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.08); }
section h2 { margin-top:0; color:#3f51b5; }
ul { padding-right:20px; }
.btn { display:inline-block; margin-top:10px; padding:10px 20px; background-color:#3f51b5; color:white; border-radius:6px; text-decoration:none; transition:background 0.3s; cursor:pointer; }
.btn:hover { background-color:#303f9f; }
footer { background-color:#1a237e; color:white; text-align:center; padding:15px; font-size:14px; }
@media (max-width:600px){ header h1{font-size:24px;} nav{flex-direction:column;} }
select,input,textarea{margin-top:10px; padding:10px; border-radius:6px; width:100%; }
textarea{resize:none;}
</style>
</head>
<body>

<header>
<h1>تسهيل الدراسة</h1>
<p>أضف الدروس، واحصل على ملخصات ذكية لجميع المستويات</p>
</header>

<nav>
<a href="#addLesson">إضافة درس</a>
<a href="#summary">تلخيص الدروس</a>
</nav>

<div class="container">

<section id="addLesson">
<h2>إضافة درس جديد</h2>
<select id="levelAdd">
<option value="">-- اختر المستوى --</option>
<option value="second">الثانية إعدادي</option>
<option value="third">الثالثة إعدادي</option>
</select>
<select id="subjectAdd">
<option value="">-- اختر المادة --</option>
<option value="history">التاريخ</option>
<option value="geography">الجغرافيا</option>
<option value="arabic">اللغة العربية</option>
<option value="math">الرياضيات</option>
<option value="science">علوم الحياة والأرض</option>
<option value="islamic">التربية الإسلامية</option>
</select>
<input type="text" id="lessonTitleAdd" placeholder="اكتب عنوان الدرس">
<textarea id="lessonContent" rows="5" placeholder="اكتب نص الدرس أو ملخصه"></textarea>
<button class="btn" onclick="addLesson()">إضافة الدرس</button>
<p id="addMessage" style="margin-top:10px; font-weight:bold;"></p>
</section>

<section id="summary">
<h2>تلخيص الدروس حسب المستوى والمادة</h2>
<select id="level">
<option value="">-- اختر المستوى --</option>
<option value="second">الثانية إعدادي</option>
<option value="third">الثالثة إعدادي</option>
</select>
<select id="subject">
<option value="">-- اختر المادة --</option>
<option value="history">التاريخ</option>
<option value="geography">الجغرافيا</option>
<option value="arabic">اللغة العربية</option>
<option value="math">الرياضيات</option>
<option value="science">علوم الحياة والأرض</option>
<option value="islamic">التربية الإسلامية</option>
</select>
<input type="text" id="lessonTitle" placeholder="اكتب عنوان الدرس">
<button class="btn" onclick="summarizeByLevel()">لخّص الدرس</button>
<p id="result" style="margin-top:15px; font-weight:bold;"></p>
</section>

</div>
<footer>
<p>© 2025 - تسهيل الدراسة</p>
</footer>

<script>
let lessons = {
  second: { history:{}, geography:{}, arabic:{}, math:{}, science:{}, islamic:{} },
  third: { history:{}, geography:{}, arabic:{}, math:{}, science:{}, islamic:{} }
};

function addLesson(){
  const level = document.getElementById('levelAdd').value;
  const subject = document.getElementById('subjectAdd').value;
  const title = document.getElementById('lessonTitleAdd').value.trim();
  const content = document.getElementById('lessonContent').value.trim();
  if(!level || !subject || !title || !content){
    document.getElementById('addMessage').innerText = '❌ الرجاء تعبئة جميع الحقول.';
    return;
  }
  lessons[level][subject][title] = content;
  document.getElementById('addMessage').innerText = '✅ تم إضافة الدرس بنجاح!';
  document.getElementById('lessonTitleAdd').value = '';
  document.getElementById('lessonContent').value = '';
}

function summarizeByLevel(){
  const level = document.getElementById('level').value;
  const subject = document.getElementById('subject').value;
  const title = document.getElementById('lessonTitle').value.trim();
  if(!level || !subject || !lessons[level][subject][title]){
    document.getElementById('result').innerText = '❌ لم يتم العثور على الدرس. تأكد من المستوى والمادة والعنوان.';
    return;
  }
  const content = lessons[level][subject][title];
  const sentences = content.split('.');
  const summary = sentences.slice(0,2).join('.') + (sentences.length>2?'. . .':'');
  document.getElementById('result').innerText = '📘 ملخص الدرس: ' + summary;
}
</script>

</body>
</html>
