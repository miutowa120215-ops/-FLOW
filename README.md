# -FLOW
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="theme-color" content="#8063c9">
<title>FLOW</title>

<style>
*{box-sizing:border-box}

body{
  margin:0;
  background:#f8f7fb;
  color:#28252d;
  font-family:-apple-system,BlinkMacSystemFont,"Hiragino Sans","Yu Gothic",sans-serif;
}

button,input,select{font:inherit}
button{border:0;cursor:pointer}

.app{
  max-width:650px;
  margin:auto;
  padding:18px 15px 100px;
}

header{
  padding:8px 4px 18px;
}

.logo{
  font-size:34px;
  font-weight:900;
  letter-spacing:.08em;
}

.sub{
  font-size:13px;
  color:#8a8590;
  margin-top:4px;
}

.nav{
  display:flex;
  gap:6px;
  overflow:auto;
  padding:4px;
  background:#eeeaf5;
  border-radius:16px;
  margin-bottom:14px;
}

.nav button{
  white-space:nowrap;
  padding:10px 13px;
  border-radius:12px;
  background:transparent;
  color:#777;
  font-weight:700;
}

.nav button.active{
  background:white;
  color:#694db2;
  box-shadow:0 2px 8px #0001;
}

.card{
  background:white;
  border-radius:20px;
  padding:17px;
  margin-bottom:13px;
  box-shadow:0 3px 16px #00000009;
}

h2{
  font-size:20px;
  margin:0 0 4px;
}

h3{
  margin:0 0 12px;
}

.muted{
  color:#888;
  font-size:13px;
}

.mini{
  font-size:12px;
  color:#999;
}

.grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:9px;
}

.stat{
  background:#f5f2f9;
  border-radius:15px;
  padding:13px;
}

.stat b{
  display:block;
  font-size:20px;
  margin-top:3px;
}

.btn{
  width:100%;
  padding:13px;
  border-radius:14px;
  background:#8063c9;
  color:white;
  font-weight:800;
  margin-top:9px;
}

.btn.light{
  background:#eeeaf5;
  color:#6749a8;
}

.btn.gray{
  background:#eee;
  color:#555;
}

.btn.danger{
  background:#fff0f0;
  color:#a44;
}

.row{
  display:flex;
  gap:8px;
}

.row>*{
  flex:1;
}

.input,
.select{
  width:100%;
  padding:11px;
  border:1px solid #ddd;
  border-radius:12px;
  background:white;
}

.task{
  display:flex;
  align-items:center;
  gap:9px;
  padding:12px 3px;
  border-bottom:1px solid #eee;
}

.task:last-child{
  border-bottom:0;
}

.check{
  width:27px;
  height:27px;
  border-radius:50%;
  border:2px solid #c9c4d1;
  background:white;
  flex:none;
}

.check.done{
  background:#8063c9;
  border-color:#8063c9;
  color:white;
}

.taskname{
  flex:1;
  font-weight:650;
}

.task.done .taskname{
  text-decoration:line-through;
  color:#aaa;
}

.iconbtn{
  background:#f0edf4;
  border-radius:10px;
  padding:7px;
  color:#65509a;
}

.progress{
  height:9px;
  background:#eee;
  border-radius:9px;
  overflow:hidden;
  margin:12px 0;
}

.bar{
  height:100%;
  background:#8063c9;
  width:0%;
  transition:.25s;
}

.timer{
  font-size:48px;
  text-align:center;
  font-weight:900;
  letter-spacing:.04em;
  margin:12px 0;
}

.center{
  text-align:center;
}

.badge{
  display:inline-block;
  padding:5px 9px;
  border-radius:20px;
  background:#eeeaf5;
  color:#694db2;
  font-size:12px;
  font-weight:700;
}

.hidden{
  display:none!important;
}

.routineTabs{
  display:flex;
  gap:7px;
  overflow:auto;
  margin:10px 0;
}

.routineTab{
  min-width:105px;
  padding:11px;
  border-radius:13px;
  background:#f0edf4;
  color:#6a6470;
  text-align:left;
}

.routineTab.active{
  background:#8063c9;
  color:white;
}

.step{
  display:flex;
  align-items:center;
  gap:8px;
  padding:11px 0;
  border-bottom:1px solid #eee;
}

.stepnum{
  width:29px;
  height:29px;
  border-radius:50%;
  background:#eeeaf5;
  color:#6949a8;
  display:grid;
  place-items:center;
  font-weight:800;
}

.stepbody{
  flex:1;
}

.empty{
  padding:20px 5px;
  text-align:center;
  color:#999;
}

.suggest{
  background:#f5f0ff;
  border-radius:16px;
  padding:14px;
  margin-top:10px;
}

.schedule{
  display:flex;
  gap:9px;
  align-items:center;
  padding:10px 0;
  border-bottom:1px solid #eee;
}

.scheduleTime{
  font-weight:800;
  width:52px;
}

.pillrow{
  display:flex;
  gap:7px;
  flex-wrap:wrap;
}

.pill{
  padding:8px 11px;
  border-radius:20px;
  background:#eeeaf5;
  color:#67509a;
}

.pill.active{
  background:#8063c9;
  color:white;
}

.modal{
  position:fixed;
  inset:0;
  background:#0007;
  display:flex;
  align-items:flex-end;
  z-index:20;
}

.modalbox{
  background:white;
  width:100%;
  max-width:650px;
  margin:auto 0 0;
  padding:20px;
  border-radius:23px 23px 0 0;
  max-height:85vh;
  overflow:auto;
}

.choice{
  width:100%;
  padding:14px;
  border:1px solid #ddd;
  background:white;
  border-radius:13px;
  text-align:left;
  margin:5px 0;
}

.toast{
  position:fixed;
  left:50%;
  bottom:22px;
  transform:translateX(-50%);
  background:#28252d;
  color:white;
  padding:11px 16px;
  border-radius:20px;
  z-index:50;
  font-size:13px;
}
</style>
</head>

<body>

<div class="app">

<header>
  <div class="logo">FLOW</div>
  <div class="sub">今やることを、ひとつずつ。</div>
</header>

<nav class="nav">
  <button id="nHome" class="active" onclick="page('home')">🏠 ホーム</button>
  <button id="nMin" onclick="page('minimum')">🌱 最低限</button>
  <button id="nRun" onclick="page('routine')">⏱️ ルーティン</button>
  <button id="nLog" onclick="page('log')">📊 記録</button>
  <button id="nSet" onclick="page('settings')">⚙️ 設定</button>
</nav>

<!-- HOME -->
<section id="home">

<div class="card">
<h2>今日のFLOW</h2>
<div class="muted" id="todayText"></div>

<div class="grid" style="margin-top:12px">
<div class="stat">
FLOW TIME
<b id="homeTime">0:00</b>
</div>

<div class="stat">
達成率
<b id="homeRate">0%</b>
</div>
</div>

<div class="progress">
<div id="homeBar" class="bar"></div>
</div>

<div id="conditionBox"></div>

<button class="btn" onclick="flowDecide()">
✨ FLOWに任せる
</button>
</div>

<div class="card">
<h2>今やること</h2>
<div id="nowBox"></div>
</div>

<div class="card">
<h2>今日の予定</h2>
<div id="scheduleList"></div>

<button class="btn light" onclick="openSchedule()">
＋ 予定を追加
</button>
</div>

<div class="card">
<h2>今日の活動</h2>
<div id="categoryStats"></div>
</div>

</section>


<!-- MINIMUM -->
<section id="minimum" class="hidden">

<div class="card">

<h2>🌱 最低限モード</h2>
<div class="muted">
今日は全部やらなくていい。できることから。
</div>

<div id="minTasks"></div>

<div class="progress">
<div id="minBar" class="bar"></div>
</div>

<div class="center muted" id="minRate"></div>

<div class="row">

<button class="btn" onclick="addTask()">
＋ 追加
</button>

<button class="btn light" onclick="fiveMinute()">
🆘 5分だけ
</button>

</div>

<button class="btn gray" onclick="resetToday()">
今日をリセット
</button>

</div>

<div class="card">

<h2>⏱️ 今の計測</h2>

<div id="activeTimer">
<div class="empty">
今は計測していません。
</div>
</div>

</div>

</section>


<!-- ROUTINE -->
<section id="routine" class="hidden">

<div class="card">

<h2>⏱️ ルーティン</h2>

<div class="muted">
3つまで自由に作れます。
</div>

<div class="routineTabs" id="routineTabs"></div>

<div class="row">

<button class="btn light" onclick="editRoutine()">
✏️ 名前を編集
</button>

<button class="btn light" onclick="duplicateRoutine()">
📋 複製
</button>

</div>

<div id="routineSteps"></div>

<button class="btn" onclick="addStep()">
＋ 項目を追加
</button>

<div class="grid">

<button class="btn light" onclick="startRoutine()">
▶ 開始
</button>

<button class="btn gray" onclick="skipStep()">
⏭️ 次へ
</button>

</div>

<div id="routineTimer"></div>

</div>

</section>


<!-- LOG -->
<section id="log" class="hidden">

<div class="card">

<h2>📊 FLOW TIME</h2>

<div class="pillrow">

<button class="pill active"
onclick="logRange(1,this)">
今日
</button>

<button class="pill"
onclick="logRange(7,this)">
7日
</button>

<button class="pill"
onclick="logRange(30,this)">
30日
</button>

</div>

<div id="logContent" style="margin-top:14px"></div>

</div>

<div class="card">

<h2>🧠 コンディション</h2>

<div class="muted">
今日の状態
</div>

<div id="conditionChoices"
class="pillrow"
style="margin-top:10px">
</div>

</div>

</section>


<!-- SETTINGS -->
<section id="settings" class="hidden">

<div class="card">

<h2>💾 データ</h2>

<div class="muted">
スマホを変えるときなどにバックアップできます。
</div>

<button class="btn" onclick="exportData()">
📤 データを書き出す
</button>

<button class="btn light"
onclick="document.getElementById('importFile').click()">
📥 データを読み込む
</button>

<input
id="importFile"
type="file"
accept=".json"
class="hidden"
onchange="importData(event)"
>

</div>

<div class="card">

<h2>📝 FLOWについて</h2>

<div class="muted">
FLOWは「全部やる」ためではなく、
今の自分にできる次の一歩を見つけるためのアプリ。
</div>

</div>

</section>

</div>


<div id="modal" class="modal hidden">
<div class="modalbox" id="modalBox"></div>
</div>

<div id="toast" class="toast hidden"></div>


<script>

const KEY="FLOW_DATA_V3";

const cats=[
"📚 勉強",
"💃 運動",
"💄 美容",
"🧹 家事",
"🎀 自分時間",
"📝 その他"
];

let data;
let activeTask=null;
let taskInterval=null;

let selectedRoutine=0;
let routineInterval=null;
let routineRunning=false;
let routineIndex=0;
let routineRemaining=0;

let currentLogRange=1;


/* =========================
   DATA
========================= */

function defaultData(){

return {

tasks:[
{
name:"英単語",
cat:"📚 勉強",
done:false
},
{
name:"英文法",
cat:"📚 勉強",
done:false
},
{
name:"運動",
cat:"💃 運動",
done:false
},
{
name:"明日の準備",
cat:"📝 その他",
done:false
}
],

routines:[
{
name:"ルーティン1",
steps:[
{name:"準備",min:5},
{name:"メイン",min:20},
{name:"片付け",min:5}
]
},
{
name:"ルーティン2",
steps:[
{name:"準備",min:5},
{name:"メイン",min:20}
]
},
{
name:"ルーティン3",
steps:[
{name:"準備",min:5},
{name:"メイン",min:20}
]
}
],

records:{},

schedule:[],

condition:"😐 普通"

};

}


function loadData(){

try{

const old=localStorage.getItem(KEY);

if(old){

const parsed=JSON.parse(old);

if(parsed.tasks && parsed.routines){

return parsed;

}

}

}catch(e){}

return defaultData();

}


data=loadData();


function saveData(){

localStorage.setItem(
KEY,
JSON.stringify(data)
);

}


function todayKey(date=new Date()){

return date.toISOString().slice(0,10);

}


function dayRecord(key=todayKey()){

if(!data.records[key]){

data.records[key]={
total:0,
cats:{},
tasks:{}
};

}

return data.records[key];

}


function addRecord(cat,seconds,taskName){

if(seconds<=0)return;

const record=dayRecord();

record.total+=seconds;

record.cats[cat]=
(record.cats[cat]||0)+seconds;

if(taskName){

record.tasks[taskName]=
(record.tasks[taskName]||0)+seconds;

}

saveData();

}


function formatTime(seconds){

seconds=Math.max(
0,
Math.floor(seconds||0)
);

const h=Math.floor(seconds/3600);

const m=Math.floor(
(seconds%3600)/60
);

const s=seconds%60;

if(h){

return `${h}:${String(m).padStart(2,"0")}:${String(s).padStart(2,"0")}`;

}

return `${m}:${String(s).padStart(2,"0")}`;

}


function esc(text){

return String(text)
.replaceAll("&","&amp;")
.replaceAll("<","&lt;")
.replaceAll(">","&gt;")
.replaceAll('"',"&quot;")
.replaceAll("'","&#039;");

}


/* =========================
   PAGE
========================= */

function page(name){

const pages=[
"home",
"minimum",
"routine",
"log",
"settings"
];

pages.forEach(p=>{

document
.getElementById(p)
.classList.toggle(
"hidden",
p!==name
);

});


const navs={
home:"nHome",
minimum:"nMin",
routine:"nRun",
log:"nLog",
settings:"nSet"
};

Object.values(navs).forEach(id=>{

document
.getElementById(id)
.classList.remove("active");

});

document
.getElementById(navs[name])
.classList.add("active");

renderAll();

}


/* =========================
   RENDER
========================= */

function renderAll(){

renderHome();
renderMinimum();
renderRoutine();
renderLog();
renderCondition();

saveData();

}


function renderHome(){

const record=dayRecord();

const done=data.tasks.filter(
t=>t.done
).length;

const rate=data.tasks.length
?Math.round(done/data.tasks.length*100)
:0;

document.getElementById(
"todayText"
).textContent=
new Date().toLocaleDateString(
"ja-JP",
{
weekday:"long",
month:"long",
day:"numeric"
}
);

document.getElementById(
"homeTime"
).textContent=
formatTime(record.total);

document.getElementById(
"homeRate"
).textContent=
rate+"%";

document.getElementById(
"homeBar"
).style.width=
rate+"%";

document.getElementById(
"conditionBox"
).innerHTML=
`<span class="badge">${esc(data.condition)}</span>`;


const now=document.getElementById("nowBox");


if(activeTask){

const seconds=getActiveSeconds();

now.innerHTML=`

<div class="suggest">

<b>${esc(activeTask.name)}</b>

<div class="mini">
${esc(activeTask.cat)}
</div>

<div class="timer" id="homeTimer">
${formatTime(seconds)}
</div>

<div class="row">

<button class="btn light"
onclick="pauseTask()">
⏸️ 中断
</button>

<button class="btn"
onclick="finishTask()">
✓ 終了
</button>

</div>

</div>

`;

}else{

const task=data.tasks.find(
t=>!t.done
);

if(task){

const index=data.tasks.indexOf(task);

now.innerHTML=`

<div class="suggest">

<b>${esc(task.name)}</b>

<div class="mini">
${esc(task.cat)}
</div>

<button class="btn"
onclick="startTask(${index})">
▶ 今これをやる
</button>

</div>

`;

}else{

now.innerHTML=`
<div class="empty">
今日の最低限は全部クリア！🎉
</div>
`;

}

}


renderSchedule();

const catBox=
document.getElementById(
"categoryStats"
);

const catsData=
record.cats||{};

catBox.innerHTML=
cats.map(cat=>`

<div class="schedule">

<span style="flex:1">
${cat}
</span>

<b>
${formatTime(catsData[cat]||0)}
</b>

</div>

`).join("");

}


function renderMinimum(){

const box=
document.getElementById("minTasks");

if(!data.tasks.length){

box.innerHTML=
`<div class="empty">
タスクを追加してね。
</div>`;

}else{

box.innerHTML=
data.tasks.map((task,index)=>{

const seconds=
dayRecord().tasks?.[task.name]||0;

return `

<div class="task ${task.done?"done":""}">

<button
class="check ${task.done?"done":""}"
onclick="toggleTask(${index})">

${task.done?"✓":""}

</button>

<div class="taskname">

${esc(task.name)}

<div class="mini">

${esc(task.cat)}
・${formatTime(seconds)}

</div>

</div>

<button
class="iconbtn"
onclick="editTask(${index})">
✏️
</button>

<button
class="iconbtn"
onclick="deleteTask(${index})">
×
</button>

</div>

`;

}).join("");

}


const done=data.tasks.filter(
t=>t.done
).length;

const rate=data.tasks.length
?Math.round(done/data.tasks.length*100)
:0;

document.getElementById(
"minBar"
).style.width=rate+"%";

document.getElementById(
"minRate"
).textContent=
`${done}/${data.tasks.length} 完了 ・ ${rate}%`;


const timerBox=
document.getElementById("activeTimer");

if(activeTask){

timerBox.innerHTML=`

<div class="center">

<span class="badge">
${esc(activeTask.name)}
</span>

<div class="timer" id="taskTimer">
${formatTime(getActiveSeconds())}
</div>

<div class="row">

<button class="btn light"
onclick="pauseTask()">
⏸️ 中断
</button>

<button class="btn"
onclick="finishTask()">
✓ 終了
</button>

</div>

</div>

`;

}else{

timerBox.innerHTML=
`<div class="empty">
今は計測していません。
</div>`;

}

}


/* =========================
   TASKS
========================= */

function toggleTask(index){

data.tasks[index].done=
!data.tasks[index].done;

saveData();
renderAll();

}


function addTask(){

openModal(`

<h3>🌱 タスクを追加</h3>

<input
id="taskNameInput"
class="input"
placeholder="例：英単語"
>

<select
id="taskCatInput"
class="select"
style="margin-top:8px">

${cats.map(cat=>
`<option>${cat}</option>`
).join("")}

</select>

<button
class="btn"
onclick="saveNewTask()">
追加
</button>

<button
class="btn light"
onclick="closeModal()">
キャンセル
</button>

`);

}


function saveNewTask(){

const name=
document
.getElementById("taskNameInput")
.value.trim();

if(!name){

toast("タスク名を入れてね");

return;

}

data.tasks.push({

name:name,

cat:
document
.getElementById("taskCatInput")
.value,

done:false

});

closeModal();
renderAll();

}


function editTask(index){

const task=data.tasks[index];

openModal(`

<h3>✏️ タスクを編集</h3>

<input
id="taskNameInput"
class="input"
value="${esc(task.name)}"
>

<select
id="taskCatInput"
class="select"
style="margin-top:8px">

${cats.map(cat=>
`<option ${cat===task.cat?"selected":""}>
${cat}
</option>`
).join("")}

</select>

<button
class="btn"
onclick="saveEditTask(${index})">
保存
</button>

`);

}


function saveEditTask(index){

const name=
document
.getElementById("taskNameInput")
.value.trim();

if(name){

data.tasks[index].name=name;

}

data.tasks[index].cat=
document
.getElementById("taskCatInput")
.value;

closeModal();
renderAll();

}


function deleteTask(index){

if(!confirm("このタスクを削除する？"))return;

data.tasks.splice(index,1);

saveData();
renderAll();

}


/* =========================
   TASK TIMER
========================= */

function getActiveSeconds(){

if(!activeTask)return 0;

if(activeTask.paused){

return activeTask.elapsed;

}

return activeTask.elapsed+
Math.floor(
(Date.now()-activeTask.started)/1000
);

}


function startTask(index){

if(activeTask){

toast("まず今の計測を終えてね");

return;

}

const task=data.tasks[index];

activeTask={

index:index,

name:task.name,

cat:task.cat,

started:Date.now(),

elapsed:0,

paused:false

};

clearInterval(taskInterval);

taskInterval=
setInterval(updateTaskTimer,1000);

renderAll();

}


function updateTaskTimer(){

if(!activeTask)return;

const seconds=getActiveSeconds();

const ids=[
"taskTimer",
"homeTimer"
];

ids.forEach(id=>{

const el=
document.getElementById(id);

if(el){

el.textContent=
formatTime(seconds);

}

});

}


function pauseTask(){

if(!activeTask)return;

if(!activeTask.paused){

activeTask.elapsed=
getActiveSeconds();

activeTask.paused=true;

clearInterval(taskInterval);

toast("一旦休憩しよう🌱");

}else{

activeTask.started=Date.now();

activeTask.paused=false;

clearInterval(taskInterval);

taskInterval=
setInterval(updateTaskTimer,1000);

toast("再開！");

}

renderAll();

}


function finishTask(){

if(!activeTask)return;

const seconds=
getActiveSeconds();

addRecord(
activeTask.cat,
seconds,
activeTask.name
);

const index=activeTask.index;

if(data.tasks[index]){

data.tasks[index].done=true;

}

activeTask=null;

clearInterval(taskInterval);

taskInterval=null;

saveData();
renderAll();

toast("記録したよ ✨");

}


/* =========================
   5 MINUTE
========================= */

function fiveMinute(){

const task=
data.tasks.find(t=>!t.done);

if(!task){

toast("今日は最低限クリア！🎉");

return;

}

if(activeTask){

toast("まず今の計測を終えてね");

return;

}

startTask(
data.tasks.indexOf(task)
);

toast("5分だけやってみよう🌱");

setTimeout(()=>{

if(activeTask){

toast(
"5分できた！続ける？今日はここまででもOK🌱"
);

}

},300000);

}


/* =========================
   RESET
========================= */

function resetToday(){

if(!confirm(
"今日の完了状態と記録をリセットする？"
))return;

data.tasks.forEach(
task=>task.done=false
);

delete data.records[todayKey()];

saveData();
renderAll();

}


/* =========================
   ROUTINE
========================= */

function renderRoutine(){

const tabs=
document.getElementById(
"routineTabs"
);

tabs.innerHTML=
data.routines.map(
(r,index)=>`

<button
class="routineTab ${index===selectedRoutine?"active":""}"
onclick="selectRoutine(${index})">

<b>${esc(r.name)}</b>

<div class="mini">
${r.steps.length}項目
・
${r.steps.reduce(
(a,s)=>a+Number(s.min),0
)}分
</div>

</button>

`).join("");


const routine=
data.routines[selectedRoutine];

const steps=
document.getElementById(
"routineSteps"
);

if(!routine.steps.length){

steps.innerHTML=
`<div class="empty">
項目を追加してね。
</div>`;

}else{

steps.innerHTML=
routine.steps.map(
(step,index)=>`

<div class="step">

<div class="stepnum">
${index+1}
</div>

<div class="stepbody">

<b>${esc(step.name)}</b>

<div class="mini">
${step.min}分
</div>

</div>

<button
class="iconbtn"
onclick="moveStep(${index},-1)">
↑
</button>

<button
class="iconbtn"
onclick="moveStep(${index},1)">
↓
</button>

<button
class="iconbtn"
onclick="editStep(${index})">
✏️
</button>

<button
class="iconbtn"
onclick="removeStep(${index})">
×
</button>

</div>

`).join("");

}

renderRoutineTimer();

}


function selectRoutine(index){

stopRoutine();

selectedRoutine=index;

routineIndex=0;
routineRemaining=0;

renderAll();

}


function editRoutine(){

const routine=
data.routines[selectedRoutine];

openModal(`

<h3>✏️ ルーティン名</h3>

<input
id="routineNameInput"
class="input"
value="${esc(routine.name)}"
>

<button
class="btn"
onclick="saveRoutineName()">
保存
</button>

`);

}


function saveRoutineName(){

const name=
document
.getElementById("routineNameInput")
.value.trim();

if(name){

data.routines[selectedRoutine].name=
name;

}

closeModal();
renderAll();

}


function duplicateRoutine(){

if(data.routines.length>=3){

toast("ルーティンは3つまでだよ");

return;

}

const copy=
JSON.parse(
JSON.stringify(
data.routines[selectedRoutine]
)
);

copy.name=
copy.name+" コピー";

data.routines.push(copy);

selectedRoutine=
data.routines.length-1;

saveData();
renderAll();

toast("複製したよ✨");

}


function addStep(){

openModal(`

<h3>＋ 項目を追加</h3>

<input
id="stepNameInput"
class="input"
placeholder="例：英単語"
>

<input
id="stepMinInput"
class="input"
type="number"
min="1"
value="5"
style="margin-top:8px"
placeholder="分"
>

<button
class="btn"
onclick="saveStep()">
追加
</button>

`);

}


function saveStep(){

const name=
document
.getElementById("stepNameInput")
.value.trim();

const min=
Math.max(
1,
Number(
document
.getElementById("stepMinInput")
.value
)||5
);

if(!name){

toast("項目名を入れてね");

return;

}

data.routines[
selectedRoutine
].steps.push({

name:name,

min:min

});

closeModal();
renderAll();

}


function editStep(index){

const step=
data.routines[
selectedRoutine
].steps[index];

openModal(`

<h3>✏️ 項目を編集</h3>

<input
id="stepNameInput"
class="input"
value="${esc(step.name)}"
>

<input
id="stepMinInput"
class="input"
type="number"
min="1"
value="${step.min}"
style="margin-top:8px"
>

<button
class="btn"
onclick="saveEditedStep(${index})">
保存
</button>

`);

}


function saveEditedStep(index){

const name=
document
.getElementById("stepNameInput")
.value.trim();

const min=
Math.max(
1,
Number(
document
.getElementById("stepMinInput")
.value
)||1
);

if(name){

data.routines[
selectedRoutine
].steps[index]={
name:name,
min:min
};

}

closeModal();
renderAll();

}


function removeStep(index){

if(!confirm(
"この項目を削除する？"
))return;

data.routines[
selectedRoutine
].steps.splice(index,1);

renderAll();

}


function moveStep(index,direction){

const steps=
data.routines[
selectedRoutine
].steps;

const newIndex=
index+direction;

if(
newIndex<0||
newIndex>=steps.length
)return;

[
steps[index],
steps[newIndex]
]=[
steps[newIndex],
steps[index]
];

renderAll();

}


/* =========================
   ROUTINE TIMER
========================= */

function startRoutine(){

const routine=
data.routines[selectedRoutine];

if(!routine.steps.length){

toast("項目を追加してね");

return;

}

if(routineRunning){

toast("もう動いてるよ");

return;

}

if(routineRemaining<=0){

routineIndex=0;

routineRemaining=
Number(
routine.steps[0].min
)*60;

}

routineRunning=true;

clearInterval(routineInterval);

routineInterval=
setInterval(()=>{

if(!routineRunning)return;

routineRemaining--;

if(routineRemaining<=0){

routineIndex++;

if(
routineIndex>=
routine.steps.length
){

stopRoutine();

routineIndex=
routine.steps.length-1;

routineRemaining=0;

renderAll();

toast(
"ルーティン完了！🎉"
);

return;

}

routineRemaining=
Number(
routine.steps[routineIndex].min
)*60;

toast(
"次へ → "+
routine.steps[routineIndex].name
);

}

renderRoutineTimer();

},1000);

renderRoutineTimer();

}


function stopRoutine(){

routineRunning=false;

clearInterval(routineInterval);

routineInterval=null;

renderRoutineTimer();

}


function skipStep(){

const routine=
data.routines[selectedRoutine];

if(!routine.steps.length)return;

routineIndex++;

if(
routineIndex>=routine.steps.length
){

routineIndex=0;

routineRemaining=
routine.steps[0].min*60;

}else{

routineRemaining=
routine.steps[routineIndex].min*60;

}

renderRoutineTimer();

}


function renderRoutineTimer(){

const box=
document.getElementById(
"routineTimer"
);

const routine=
data.routines[selectedRoutine];

if(
!routine||
!routine.steps.length
){

box.innerHTML="";

return;

}

const current=
routine.steps[routineIndex];

let remaining=
routineRemaining;

if(!remaining){

remaining=
current.min*60;

}

const future=
routine.steps
.slice(routineIndex+1)
.reduce(
(total,step)=>
total+Number(step.min)*60,
0
);

const totalRemaining=
remaining+future;

box.innerHTML=`

<div class="card"
style="background:#f7f4fb;margin-top:12px">

<div class="center">

<span class="badge">
今：${esc(current.name)}
</span>

<div class="timer">
${formatTime(remaining)}
</div>

<div class="muted">
全体の残り 約
${Math.ceil(totalRemaining/60)}
分
</div>

<button
class="btn gray"
onclick="stopRoutine()">
${routineRunning?"⏸️ 一時停止":"⏸️ 停止"}
</button>

<button
class="btn light"
onclick="startRoutine()">
▶️ ${routineRunning?"再スタート":"再開"}
</button>

</div>

</div>

`;

}


/* =========================
   SCHEDULE
========================= */

function renderSchedule(){

const box=
document.getElementById(
"scheduleList"
);

if(!data.schedule.length){

box.innerHTML=
`<div class="empty">
予定はまだありません。
</div>`;

return;

}

const sorted=
data.schedule
.map((item,index)=>({
...item,
original:index
}))
.sort(
(a,b)=>
a.time.localeCompare(b.time)
);

box.innerHTML=
sorted.map(
item=>`

<div class="schedule">

<span class="scheduleTime">
${item.time}
</span>

<span style="flex:1">
${esc(item.name)}
</span>

<button
class="iconbtn"
onclick="deleteSchedule(${item.original})">
×
</button>

</div>

`).join("");

}


function openSchedule(){

openModal(`

<h3>📅 今日の予定</h3>

<input
id="scheduleTimeInput"
class="input"
type="time"
>

<input
id="scheduleNameInput"
class="input"
style="margin-top:8px"
placeholder="予定"
>

<button
class="btn"
onclick="saveSchedule()">
追加
</button>

`);

}


function saveSchedule(){

const time=
document
.getElementById("scheduleTimeInput")
.value;

const name=
document
.getElementById("scheduleNameInput")
.value.trim();

if(!time||!name){

toast("時間と予定を入れてね");

return;

}

data.schedule.push({
time:time,
name:name
});

closeModal();
renderAll();

}


function deleteSchedule(index){

data.schedule.splice(index,1);

renderAll();

}


/* =========================
   FLOWに任せる
========================= */

function flowDecide(){

const task=
data.tasks.find(
t=>!t.done
);

if(
data.condition==="🫠 しんどい"||
data.condition==="😴 眠い"
){

if(task){

openModal(`

<h3>🌱 今はこれだけ</h3>

<p>
今のコンディションなら、
まず
<strong>
「${esc(task.name)}」
</strong>
を5分だけやってみるのがおすすめ。
</p>

<button
class="btn"
onclick="closeModal();fiveMinute()">
▶ 5分だけ始める
</button>

`);

return;

}

}


if(task){

const index=
data.tasks.indexOf(task);

openModal(`

<h3>✨ FLOWに任せる</h3>

<p>
今は
<strong>
「${esc(task.name)}」
</strong>
から始めるのがおすすめ。
</p>

<button
class="btn"
onclick="closeModal();startTask(${index})">
▶ 今これをやる
</button>

`);

return;

}


if(
data.routines[selectedRoutine] &&
data.routines[selectedRoutine].steps.length
){

openModal(`

<h3>✨ ルーティンを始めよう</h3>

<p>
「${esc(
data.routines[selectedRoutine].name
)}」
が使えそう。
</p>

<button
class="btn"
onclick="closeModal();page('routine');startRoutine()">
▶ 開始
</button>

`);

return;

}


toast("今日は全部クリア！🎉");

}


/* =========================
   LOG
========================= */

function renderLog(){

const now=new Date();

let total=0;

const categoryTotals={};

for(
let i=0;
i<currentLogRange;
i++
){

const date=
new Date(now);

date.setDate(
now.getDate()-i
);

const record=
data.records[todayKey(date)];

if(!record)continue;

total+=record.total||0;

Object.entries(
record.cats||{}
).forEach(
([category,seconds])=>{

categoryTotals[category]=
(categoryTotals[category]||0)
+seconds;

});

}


document.getElementById(
"logContent"
).innerHTML=`

<div class="stat">

<div class="muted">

${
currentLogRange===1
?"今日"
:`過去${currentLogRange}日`
}

</div>

<b>
${formatTime(total)}
</b>

</div>

${
cats.map(
cat=>`

<div class="schedule">

<span style="flex:1">
${cat}
</span>

<b>
${formatTime(
categoryTotals[cat]||0
)}
</b>

</div>

`
).join("")
}

`;

}


function logRange(days,element){

currentLogRange=days;

document
.querySelectorAll("#log .pill")
.forEach(
button=>
button.classList.remove("active")
);

element.classList.add("active");

renderLog();

}


/* =========================
   CONDITION
========================= */

function renderCondition(){

const options=[
"😊 元気",
"😐 普通",
"😴 眠い",
"🫠 しんどい"
];

document.getElementById(
"conditionChoices"
).innerHTML=

options.map(
option=>`

<button
class="pill ${data.condition===option?"active":""}"
onclick="setCondition('${option}')">

${option}

</button>

`).join("");

}


function setCondition(value){

data.condition=value;

saveData();

renderAll();

toast("今日の状態を記録したよ");

}


/* =========================
   MODAL
========================= */

function openModal(html){

document.getElementById(
"modalBox"
).innerHTML=html;

document.getElementById(
"modal"
).classList.remove("hidden");

}


function closeModal(){

document.getElementById(
"modal"
).classList.add("hidden");

}


document
.getElementById("modal")
.addEventListener(
"click",
function(event){

if(
event.target.id==="modal"
){

closeModal();

}

});


/* =========================
   TOAST
========================= */

function toast(message){

const element=
document.getElementById("toast");

element.textContent=message;

element.classList.remove("hidden");

setTimeout(
()=>{
element.classList.add("hidden");
},
2200
);

}


/* =========================
   BACKUP
========================= */

function exportData(){

const blob=
new Blob(
[
JSON.stringify(
data,
null,
2
)
],
{
type:"application/json"
}
);

const url=
URL.createObjectURL(blob);

const link=
document.createElement("a");

link.href=url;

link.download=
"FLOW-backup.json";

document.body.appendChild(link);

link.click();

link.remove();

URL.revokeObjectURL(url);

toast("バックアップを作ったよ");

}


function importData(event){

const file=
event.target.files[0];

if(!file)return;

const reader=
new FileReader();

reader.onload=function(){

try{

const imported=
JSON.parse(
reader.result
);

if(
!imported.tasks||
!imported.routines
){

throw new Error();

}

data=imported;

saveData();

renderAll();

toast("復元したよ！");

}catch(error){

toast(
"このファイルは読み込めないみたい"
);

}

};

reader.readAsText(file);

}


/* =========================
   START
========================= */

renderAll();

setInterval(
()=>{
updateTaskTimer();
},
1000
);

</script>

</body>
</html>
