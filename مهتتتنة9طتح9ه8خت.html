<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>تطبيق المهام الدراسية المتطور – نسخة عالمية</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<style>
:root{
  --bg:#f5f5f5;
  --card:#ffffff;
  --text:#1e293b;
  --accent:#3b82f6;
  --done:#16a34a;
  --pending:#ef4444;
}
body{font-family:"Cairo",sans-serif;margin:0;padding:20px;background:var(--bg);color:var(--text);transition:all 0.3s;}
body.dark{--bg:#1a1c2c;--card:#2a2c3c;--text:#f5f5f5;--accent:#38bdf8;}
h1{text-align:center;font-size:30px;background:var(--accent);-webkit-background-clip:text;color:transparent;font-weight:800;}
.container{display:grid;grid-template-columns:repeat(auto-fit,minmax(350px,1fr));gap:20px;margin-top:20px;}
.card{background:var(--card);padding:20px;border-radius:18px;box-shadow:0 10px 25px rgba(0,0,0,0.15);transition:0.4s;}
.card:hover{transform:translateY(-6px) scale(1.02);}
.card h3{text-align:center;margin-bottom:12px;}
input, select{width:100%;padding:8px;margin:4px 0;border-radius:8px;border:1px solid #ccc;background:rgba(0,0,0,0.03);color:var(--text);}
input:focus, select:focus{outline:none;border-color:var(--accent);}
button{padding:8px 12px;border:none;border-radius:8px;background:var(--accent);color:white;cursor:pointer;margin:4px 0;width:100%;transition:0.3s;font-weight:600;}
button:hover{opacity:0.9;transform:scale(1.03);}
.task{border-radius:12px;padding:10px;margin:6px 0;background:rgba(0,0,0,0.05);display:flex;flex-direction:column;gap:4px;}
.task span{display:flex;justify-content:space-between;align-items:center;}
.task a{color:var(--accent);text-decoration:none;}
.task.done{background:#16a34a20;}
.task.pending{background:#ef444420;}

/* لوحة التحكم الجانبية */
.control-panel{
  position:fixed;
  top:50%;
  left:10px;
  transform:translateY(-50%);
  background:var(--card);
  padding:12px;
  border-radius:20px;
  box-shadow:0 8px 20px rgba(0,0,0,0.3);
  display:flex;
  flex-direction:column;
  gap:8px;
  z-index:1000;
}
.control-panel button, .control-panel select{
  width:140px;
  cursor:pointer;
}
.control-panel select{padding:6px;}

/* الرسم البياني */
.chart-container{width:100%;height:250px;margin-top:12px;}
</style>
</head>
<body>

<div class="control-panel">
  <button onclick="toggleDark()">🌙/☀️ الوضع الداكن</button>
  <select id="themeSelect" onchange="changeTheme(this.value)">
    <option value="default">🎨 السيمة الافتراضية</option>
    <option value="blue">🔵 أزرق</option>
    <option value="green">🟢 أخضر</option>
    <option value="pink">🌸 وردي</option>
    <option value="orange">🟠 برتقالي</option>
  </select>
  <button onclick="exportData()">📤 تصدير</button>
  <button onclick="importData()">📥 استيراد</button>
</div>

<h1>📝 تطبيق المهام الدراسية المتطور – نسخة عالمية</h1>
<div class="container" id="subjectsContainer"></div>

<input type="file" id="fileInput" style="display:none">

<script>
// المواد
const subjects=[
  {name:"التشريح",color:"#FF6B6B"},
  {name:"الفسلجة",color:"#f7b731"},
  {name:"الأنسجة",color:"#54a0ff"},
  {name:"الأجنة",color:"#0abde3"},
  {name:"الكيمياء",color:"#10ac84"},
  {name:"التشريح الأولى",color:"#8854d0"},
  {name:"الكيمياء الأولى",color:"#ee5253"},
  {name:"الجرائم",color:"#f368e0"},
  {name:"الأخلاقيات الطبية",color:"#ff9ff3"}
];

const container=document.getElementById("subjectsContainer");

// إنشاء بطاقات المواد
subjects.forEach((subj,i)=>{
  const card=document.createElement("div");
  card.className="card";
  card.style.borderTop=`6px solid ${subj.color}`;
  card.innerHTML=`<h3>${subj.name}</h3>
  <input type="text" id="taskName${i}" placeholder="اسم المهمة">
  <input type="datetime-local" id="taskTime${i}" placeholder="وقت المهمة">
  <select id="taskPriority${i}">
    <option value="عادي">⭐ عادي</option>
    <option value="مهم">⭐⭐ مهم</option>
    <option value="ضروري">⭐⭐⭐ ضروري</option>
  </select>
  <select id="taskDifficulty${i}">
    <option value="سهل">💪 سهل</option>
    <option value="متوسط">💪💪 متوسط</option>
    <option value="صعب">💪💪💪 صعب</option>
  </select>
  <input type="text" id="taskLocation${i}" placeholder="المكان">
  <input type="text" id="taskVideo${i}" placeholder="رابط فيديو">
  <button onclick="addTask(${i})">➕ إضافة مهمة</button>
  <div id="tasks${i}"></div>
  <div class="chart-container"><canvas id="chart${i}"></canvas></div>`;
  container.appendChild(card);
  loadTasks(i);
});

// إضافة مهمة
function addTask(i){
  const name=document.getElementById(`taskName${i}`).value.trim();
  if(!name) return;
  const time=document.getElementById(`taskTime${i}`).value;
  const priority=document.getElementById(`taskPriority${i}`).value;
  const difficulty=document.getElementById(`taskDifficulty${i}`).value;
  const location=document.getElementById(`taskLocation${i}`).value;
  const video=document.getElementById(`taskVideo${i}`).value;
  const tasks=JSON.parse(localStorage.getItem(`tasks${i}`)||"[]");
  tasks.push({name,time,priority,difficulty,location,video,status:"pending"});
  localStorage.setItem(`tasks${i}`,JSON.stringify(tasks));
  renderTasks(i);
  clearInputs(i);
  scheduleNotification(name,time);
  updateChart(i);
}

// إشعارات المهام
function scheduleNotification(name,time){
  if(!("Notification" in window)) return;
  if(Notification.permission==="default") Notification.requestPermission();
  const now=new Date();
  const taskTime=new Date(time);
  const delay=taskTime-now;
  if(delay>0 && Notification.permission==="granted"){
    setTimeout(()=>new Notification("تذكير بالمهمة", {body:name} ), delay);
  }
}

// عرض المهام
function renderTasks(i){
  const tasksDiv=document.getElementById(`tasks${i}`);
  const tasks=JSON.parse(localStorage.getItem(`tasks${i}`)||"[]");
  tasksDiv.innerHTML="";
  tasks.forEach((t,idx)=>{
    const div=document.createElement("div");
    div.className="task "+t.status;
    div.innerHTML=`<span><b>${t.name}</b> (${t.time?new Date(t.time).toLocaleString():""}) - ${t.priority} - ${t.difficulty} - ${t.location} ${t.video?`- <a href="${t.video}" target="_blank">🎥</a>`:""}</span>
      <span>
        <button onclick="toggleStatus(${i},${idx})">✔️</button>
        <button onclick="deleteTask(${i},${idx})">🗑️</button>
      </span>`;
    tasksDiv.appendChild(div);
  });
  updateChart(i);
}

function toggleStatus(i,idx){
  const tasks=JSON.parse(localStorage.getItem(`tasks${i}`)||"[]");
  tasks[idx].status=tasks[idx].status==="pending"?"done":"pending";
  localStorage.setItem(`tasks${i}`,JSON.stringify(tasks));
  renderTasks(i);
}

function deleteTask(i,idx){
  const tasks=JSON.parse(localStorage.getItem(`tasks${i}`)||"[]");
  tasks.splice(idx,1);
  localStorage.setItem(`tasks${i}`,JSON.stringify(tasks));
  renderTasks(i);
}

function loadTasks(i){renderTasks(i);}
function clearInputs(i){
  document.getElementById(`taskName${i}`).value="";
  document.getElementById(`taskTime${i}`).value="";
  document.getElementById(`taskLocation${i}`).value="";
  document.getElementById(`taskVideo${i}`).value="";
}

// حفظ واستيراد وتصدير
function exportData(){
  const data={};
  subjects.forEach((s,i)=>{data[i]=JSON.parse(localStorage.getItem(`tasks${i}`)||"[]");});
  const blob=new Blob([JSON.stringify(data,null,2)],{type:"application/json"});
  const url=URL.createObjectURL(blob);
  const a=document.createElement("a");
  a.href=url;
  a.download="tasks.json";
  a.click();
  URL.revokeObjectURL(url);
}

function importData(){
  const input=document.getElementById("fileInput");
  input.click();
  input.onchange=()=>{
    const file=input.files[0];
    const reader=new FileReader();
    reader.onload=function(e){
      const data=JSON.parse(e.target.result);
      for(let i in data){localStorage.setItem(`tasks${i}`,JSON.stringify(data[i])); renderTasks(i);}
    };
    reader.readAsText(file);
  }
}

// الوضع الداكن
function toggleDark(){document.body.classList.toggle("dark");}

// تغيير السيمات
function changeTheme(val){
  const root=document.documentElement;
  if(val=="default"){root.style.setProperty('--accent','#3b82f6');}
  else if(val=="blue"){root.style.setProperty('--accent','#54a0ff');}
  else if(val=="green"){root.style.setProperty('--accent','#10ac84');}
  else if(val=="pink"){root.style.setProperty('--accent','#ff9ff3');}
  else if(val=="orange"){root.style.setProperty('--accent','#f19066');}
}

// الرسوم البيانية
function updateChart(i){
  const ctx=document.getElementById(`chart${i}`).getContext('2d');
  const tasks=JSON.parse(localStorage.getItem(`tasks${i}`)||"[]");
  const done=tasks.filter(t=>t.status==="done").length;
  const pending=tasks.filter(t=>t.status==="pending").length;
  if(window[`chartInstance${i}`]) window[`chartInstance${i}`].destroy();
  window[`chartInstance${i}`]=new Chart(ctx,{
    type:'doughnut',
    data:{
      labels:['مكتملة','غير مكتملة'],
      datasets:[{
        label:'حالة المهام',
        data:[done,pending],
        backgroundColor:['#16a34a','#ef4444'],
      }]
    },
    options:{
      responsive:true,
      plugins:{legend:{position:'bottom'}}
    }
  });
}

</script>
</body>
</html>
