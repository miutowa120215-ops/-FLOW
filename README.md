# -FLOW
毎日の生活を、無理なく流れにのせる
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="theme-color" content="#ffffff">
<title>FLOW</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#faf9fc;color:#25232a;font-family:-apple-system,BlinkMacSystemFont,"Hiragino Sans","Yu Gothic",sans-serif}
button,input{font:inherit}
button{border:0;cursor:pointer}
.app{max-width:600px;margin:auto;padding:20px 18px 90px}
header{padding:12px 4px 20px}
.logo{font-size:34px;font-weight:800;letter-spacing:.08em}
.sub{margin-top:5px;color:#777;font-size:14px}
.tabs{display:flex;background:#eeeaf3;border-radius:16px;padding:4px;margin-bottom:18px}
.tabs button{flex:1;padding:12px;border-radius:13px;background:transparent;color:#777;font-weight:700}
.tabs button.active{background:#fff;color:#6d4fc2;box-shadow:0 2px 8px #00000010}
.card{background:#fff;border-radius:22px;padding:18px;margin-bottom:14px;box-shadow:0 3px 15px #00000008}
h2{font-size:21px;margin:0 0 5px}
.desc{font-size:13px;color:#888;margin-bottom:15px}
.task{display:flex;align-items:center;gap:12px;padding:14px 4px;border-bottom:1px solid #eee}
.task:last-child{border-bottom:0}
.check{width:27px;height:27px;border:2px solid #c9c3d3;border-radius:50%;background:white;flex:none}
.check.done{background:#8063c9;border-color:#8063c9;color:white}
.taskname{flex:1;font-weight:600}
.task.done .taskname{text-decoration:line-through;color:#aaa}
.small{font-size:12px;color:#999}
.btn{width:100%;padding:13px;border-radius:14px;background:#8063c9;color:white;font-weight:700;margin-top:10px}
.btn.light{background:#f0edf5;color:#6044a0}
.btn.gray{background:#eee;color:#555}
.row{display:flex;gap:8px}
.row>*{flex:1}
.progress{height:9px;background:#eee;border-radius:10px;overflow:hidden;margin:14px 0}
.progressbar{height:100%;background:#8063c9;width:0%;transition:.3s}
.message{text-align:center;font-weight:700;padding:8px}
.input{width:100%;padding:12px;border:1px solid #ddd;border-radius:12px;background:#fff}
.routineStep{display:flex;gap:12px;align-items:center;padding:15px 5px;border-bottom:1px solid #eee}
.num{width:30px;height:30px;border-radius:50%;background:#eeeaf3;color:#6547a7;display:grid;place-items:center;font-weight:800}
.routineStep.current{background:#f5f0ff;border-radius:15px;padding:15px}
.timer{text-align:center;font-size:52px;font-weight:800;margin:15px 0}
.badge{display:inline-block;background:#eeeaf3;color:#6749a8;padding:5px 9px;border-radius:20px;font-size:12px}
.hidden{display:none}
.notice{background:#fff5dd;padding:14px;border-radius:15px;color:#72571d;margin-top:12px}
.modal{position:fixed;inset:0;background:#0007;display:flex;align-items:flex-end;z-index:10}
.modalbox{background:white;width:100%;max-width:600px;margin:auto 0 0;padding:22px;border-radius:25px 25px 0 0}
.modalbox h3{margin-top:0}
.choice{padding:15px;border:2px solid #eee;border-radius:15px;margin:8px 0;text-align:left;background:white}
.choice:hover{border-color:#8063c9}
</style>
</head>

<body>
<div class="app">

<header>
<div class="logo">FLOW</div>
<div class="sub">毎日の生活を、無理なく流れにのせる</div>
</header>

<div class="tabs">
<button id="minTab" class="active" onclick="showMode('minimum')">🌱 最低限モード</button>
<button id="runTab" onclick="showMode('routine')">⏱️ ルーティンモード</button>
</div>

<section id="minimum">

<div class="card">
<h2>今日の最低限</h2>
<div class="desc">順番は自由。できたものからチェックしよう。</div>

<div class="progress"><div id="minProgress" class="progressbar"></div></div>
<div id="minMessage" class="message">今日はここから。</div>

<div id="tasks"></div>

<div class="row">
<button class="btn light" onclick="addTask()">＋ やることを追加</button>
<button class="btn light" onclick="zeroMode()">🌱 やる気ゼロ</button>
</div>

<button class="btn gray" onclick="resetTasks()">今日をリセット</button>
</div>

<div class="card">
<h2>あとでやる</h2>
<div class="desc">今じゃなくても大丈夫。あとで戻そう。</div>
<div id="later"></div>
</div>

</section>

<section id="routine" class="hidden">

<div class="card">
<h2>ルーティン</h2>
<div class="desc">決めた順番で、時間内に流れよう。</div>

<label class="small">出発時刻</label>
<input id="leaveTime" class="input" type="time" value="08:00" onchange="checkRush()">

<div id="routineInfo" class="notice"></div>
<div id="routineSteps"></div>

<div class="timer" id="timer">00:00</div>
<div id="timerName" class="message">スタートしよう</div>

<div class="row">
<button class="btn" onclick="startTimer()">▶ スタート</button>
<button class="btn light" onclick="nextStep()">次へ →</button>
</div>

<button class="btn gray" onclick="checkRush()">時間を確認する</button>
</div>

</section>

</div>

<div id="rushModal" class="modal hidden">
<div class="modalbox">
<h3>🏃 時間が足りないかも</h3>
<p>通常ルーティンのままだと、出発時刻までに終わらない可能性があります。</p>
<button class="choice" onclick="setRush(true)">🏃 急ぎモードにする</button>
<button class="choice" onclick="setRush(false)">🧘 通常モードのまま</button>
</div>
</div>

<script>
const defaultTasks=[
{name:"英単語",done:false},
{name:"英文法",done:false},
{name:"運動",done:false},
{name:"水分をとる",done:false},
{name:"明日の準備",done:false}
];

const defaultRoutine=[
{name:"着替える",normal:5,rush:3},
{name:"朝ごはん",normal:10,rush:7},
{name:"歯みがき・洗顔",normal:8,rush:5},
{name:"荷物確認",normal:5,rush:3}
];

let tasks=JSON.parse(localStorage.getItem("flowTasks")||"null")||defaultTasks;
let later=JSON.parse(localStorage.getItem("flowLater")||"[]");
let routine=JSON.parse(localStorage.getItem("flowRoutine")||"null")||defaultRoutine;
let rush=false;
let currentStep=0;
let timerId=null;
let remaining=0;

function save(){
localStorage.setItem("flowTasks",JSON.stringify(tasks));
localStorage.setItem("flowLater",JSON.stringify(later));
}

function showMode(mode){
document.getElementById("minimum").classList.toggle("hidden",mode!=="minimum");
document.getElementById("routine").classList.toggle("hidden",mode!=="routine");
document.getElementById("minTab").classList.toggle("active",mode==="minimum");
document.getElementById("runTab").classList.toggle("active",mode==="routine");
if(mode==="routine")renderRoutine();
}

function renderTasks(){
const box=document.getElementById("tasks");
box.innerHTML="";
tasks.forEach((t,i)=>{
const div=document.createElement("div");
div.className="task "+(t.done?"done":"");
div.innerHTML=
'<button class="check '+(t.done?"done":"")+'" onclick="toggleTask('+i+')">'+(t.done?"✓":"")+'</button>'+
'<div class="taskname">'+escapeHtml(t.name)+'</div>'+
'<button class="small" onclick="postpone('+i+')">あとで</button>';
box.appendChild(div);
});
updateProgress();
renderLater();
}

function toggleTask(i){
tasks[i].done=!tasks[i].done;
save();renderTasks();
}

function updateProgress(){
let total=tasks.length;
let done=tasks.filter(t=>t.done).length;
let percent=total?Math.round(done/total*100):0;
document.getElementById("minProgress").style.width=percent+"%";

let msg="";
if(percent===100)msg="全部できた！明日もがんばろう！";
else if(percent>=80)msg="最低限クリア！";
else if(percent>=50)msg="頑張った！！";
else if(percent>0)msg="今日はここまで！明日またやろう";
else msg="今日はここから。";
document.getElementById("minMessage").textContent=msg;
}

function addTask(){
let name=prompt("追加することを入力してね");
if(name&&name.trim()){
tasks.push({name:name.trim(),done:false});
save();renderTasks();
}
}

function postpone(i){
later.push(tasks[i].name);
tasks.splice(i,1);
save();renderTasks();
}

function renderLater(){
const box=document.getElementById("later");
if(!later.length){
box.innerHTML='<div class="small">まだありません。</div>';
return;
}
box.innerHTML=later.map((x,i)=>
'<div class="task"><div class="taskname">'+escapeHtml(x)+'</div>'+
'<button class="small" onclick="restoreLater('+i+')">戻す</button></div>'
).join("");
}

function restoreLater(i){
tasks.push({name:later[i],done:false});
later.splice(i,1);
save();renderTasks();
}

function zeroMode(){
tasks=tasks.map(t=>({
name:t.name+"（ちょっとだけ）",
done:t.done
}));
save();renderTasks();
alert("今日は「ちょっとだけ」でOK🌱");
}

function resetTasks(){
if(confirm("今日のチェックをリセットする？")){
tasks=defaultTasks.map(t=>({...t}));
save();renderTasks();
}
}

function renderRoutine(){
const box=document.getElementById("routineSteps");
box.innerHTML="";
routine.forEach((s,i)=>{
let mins=rush?s.rush:s.normal;
box.innerHTML+=
'<div class="routineStep '+(i===currentStep?"current":"")+'">'+
'<div class="num">'+(i+1)+'</div>'+
'<div style="flex:1"><b>'+escapeHtml(s.name)+'</b><br><span class="small">'+mins+'分'+(rush?"・短縮":"")+'</span></div>'+
'</div>';
});
updateRoutineInfo();
}

function totalMinutes(){
return routine.reduce((a,s)=>a+(rush?s.rush:s.normal),0);
}

function updateRoutineInfo(){
let mins=totalMinutes();
document.getElementById("routineInfo").textContent=
(rush?"🏃 急ぎモード：":"通常モード：")+"必要時間 約"+mins+"分";
}

function checkRush(){
let value=document.getElementById("leaveTime").value;
if(!value)return;

let now=new Date();
let [h,m]=value.split(":").map(Number);
let leave=new Date();
leave.setHours(h,m,0,0);
let diff=Math.round((leave-now)/60000);

if(diff>0 && totalMinutes()>diff && !rush){
document.getElementById("rushModal").classList.remove("hidden");
}
updateRoutineInfo();
}

function setRush(value){
rush=value;
document.getElementById("rushModal").classList.add("hidden");
renderRoutine();
}

function startTimer(){
if(timerId)return;
if(currentStep>=routine.length){
currentStep=0;
renderRoutine();
}
remaining=(rush?routine[currentStep].rush:routine[currentStep].normal)*60;
document.getElementById("timerName").textContent=routine[currentStep].name;

timerId=setInterval(()=>{
remaining--;
renderTimer();
if(remaining<=0){
clearInterval(timerId);
timerId=null;
alert("「"+routine[currentStep].name+"」完了！");
nextStep();
}
},1000);
renderTimer();
}

function renderTimer(){
let m=Math.floor(remaining/60);
let s=remaining%60;
document.getElementById("timer").textContent=
String(m).padStart(2,"0")+":"+String(s).padStart(2,"0");
}

function nextStep(){
if(timerId){
clearInterval(timerId);
timerId=null;
}
if(currentStep<routine.length-1){
currentStep++;
remaining=0;
renderRoutine();
document.getElementById("timer").textContent="00:00";
document.getElementById("timerName").textContent=routine[currentStep].name;
}else{
currentStep=routine.length;
document.getElementById("timer").textContent="00:00";
document.getElementById("timerName").textContent="ルーティン完了！🎉";
document.getElementById("routineSteps").innerHTML=
'<div class="message">全部の流れが終わった！おつかれさま💗</div>';
}
}

function escapeHtml(str){
return String(str).replace(/[&<>"']/g,m=>({
"&":"&amp;","<":"&lt;",">":"&gt;",
'"':"&quot;","'":"&#039;"
}[m]));
}

renderTasks();
renderRoutine();
</script>
</body>
</html>