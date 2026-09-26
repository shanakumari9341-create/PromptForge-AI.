<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PromptForge AI — Intelligent Prompt Engineering</title>
<style>
:root{--bg:#07111f;--panel:#0d1b2e;--panel2:#10233b;--text:#eef5ff;--muted:#9db0c9;--accent:#6ea8fe;--accent2:#8b7cff;--border:#1d3553;--good:#39d98a;--warn:#ffcc66;--bad:#ff6b7a}
*{box-sizing:border-box} body{margin:0;font-family:Inter,Segoe UI,Arial,sans-serif;background:linear-gradient(135deg,#07111f,#0a1424 55%,#10182b);color:var(--text);min-height:100vh}
button,input,textarea,select{font:inherit} button{cursor:pointer}
.app{display:grid;grid-template-columns:245px 1fr;min-height:100vh}.sidebar{border-right:1px solid var(--border);background:rgba(7,17,31,.92);padding:22px;position:sticky;top:0;height:100vh}
.logo{font-size:21px;font-weight:800;margin-bottom:30px}.logo span{color:var(--accent)}
.nav button{width:100%;text-align:left;background:transparent;border:0;color:var(--muted);padding:12px 13px;border-radius:10px;margin:3px 0}.nav button:hover,.nav button.active{background:var(--panel2);color:#fff}
.side-bottom{position:absolute;bottom:20px;color:var(--muted);font-size:12px}
main{padding:28px;max-width:1450px;width:100%;margin:auto}.top{display:flex;justify-content:space-between;align-items:center;margin-bottom:25px}.badge{border:1px solid var(--border);padding:7px 11px;border-radius:20px;color:var(--good);font-size:12px;background:#0b1b18}
h1{font-size:34px;margin:0 0 8px} h2{margin:0 0 12px} p{color:var(--muted);line-height:1.6}.grid{display:grid;grid-template-columns:1.1fr .9fr;gap:18px}.card{background:rgba(13,27,46,.92);border:1px solid var(--border);border-radius:16px;padding:20px;box-shadow:0 15px 45px rgba(0,0,0,.18)}
textarea{width:100%;min-height:175px;background:#081525;border:1px solid var(--border);border-radius:12px;color:#fff;padding:15px;resize:vertical;outline:none}textarea:focus,input:focus,select:focus{border-color:var(--accent)}
.row{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:12px}select,input{width:100%;background:#081525;color:#fff;border:1px solid var(--border);padding:11px;border-radius:10px}
label{font-size:12px;color:var(--muted);display:block;margin-bottom:6px}.btn{border:0;border-radius:10px;padding:11px 15px;background:var(--accent);color:#06101c;font-weight:700}.btn.secondary{background:#162b47;color:#dceaff;border:1px solid var(--border)}.btn.danger{background:#3a1720;color:#ffb8c0}.actions{display:flex;gap:9px;flex-wrap:wrap;margin-top:13px}
.output{white-space:pre-wrap;background:#081525;border:1px solid var(--border);border-radius:12px;padding:15px;min-height:250px;line-height:1.65;color:#e8f1ff}.score{font-size:38px;font-weight:800}.meter{height:9px;background:#15263c;border-radius:10px;overflow:hidden;margin:6px 0 14px}.meter i{display:block;height:100%;background:linear-gradient(90deg,var(--accent),var(--accent2));width:0}
.metrics{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}.metric{background:#0a192b;border:1px solid var(--border);padding:12px;border-radius:12px}.metric b{display:block;font-size:19px;margin-bottom:4px}.metric span{font-size:12px;color:var(--muted)}
.section{margin-top:18px}.hidden{display:none}.history-item{padding:12px;border:1px solid var(--border);border-radius:10px;margin:8px 0;background:#0a192b}.history-item small{color:var(--muted)}.empty{color:var(--muted);padding:30px;text-align:center}
.notice{padding:12px;border-radius:10px;background:#0b1b30;border:1px solid var(--border);color:var(--muted);font-size:13px}.risk{font-weight:700}.risk.low{color:var(--good)}.risk.medium{color:var(--warn)}.risk.high{color:var(--bad)}
@media(max-width:900px){.app{grid-template-columns:1fr}.sidebar{position:relative;height:auto;border-right:0;border-bottom:1px solid var(--border)}.side-bottom{position:static;margin-top:20px}.grid{grid-template-columns:1fr}.row{grid-template-columns:1fr}main{padding:18px}}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar">
  <div class="logo">⚡ Prompt<span>Forge</span> AI</div>
  <div class="nav">
    <button class="active" onclick="show('optimizer',this)">✨ Prompt Optimizer</button>
    <button onclick="show('analyzer',this)">🔍 Prompt Analyzer</button>
    <button onclick="show('library',this)">📚 Prompt Library</button>
    <button onclick="show('history',this)">🕘 History</button>
    <button onclick="show('analytics',this)">📊 Analytics</button>
  </div>
  <div class="side-bottom">Demo AI Mode • Single Page Edition</div>
</aside>

<main>
  <div class="top">
    <div><h1>PromptForge AI</h1><p>Turn ordinary human language into structured, high-quality AI prompts.</p></div>
    <div class="badge">● Demo AI Ready</div>
  </div>

  <section id="optimizer">
    <div class="grid">
      <div class="card">
        <h2>✨ Smart Prompt Optimizer</h2>
        <p>Describe what you want in normal language. The engine extracts intent, requirements and constraints, then creates a structured prompt.</p>
        <textarea id="input" placeholder="Example: I want to build an impressive machine learning project for college using Python..."></textarea>
        <div class="row">
          <div><label>Category</label><select id="category"><option>Auto Detect</option><option>Coding</option><option>Education</option><option>Machine Learning</option><option>Career</option><option>Business</option><option>Writing</option><option>Research</option></select></div>
          <div><label>Tone</label><select id="tone"><option>Professional</option><option>Educational</option><option>Friendly</option><option>Technical</option><option>Creative</option></select></div>
          <div><label>Output</label><select id="format"><option>Structured</option><option>Step-by-Step</option><option>Table</option><option>Bullet Points</option><option>JSON</option></select></div>
        </div>
        <div class="actions">
          <button class="btn" onclick="generate()">✨ Generate Smart Prompt</button>
          <button class="btn secondary" onclick="loadExample()">Try Example</button>
          <button class="btn secondary" onclick="clearAll()">Clear</button>
        </div>
      </div>

      <div class="card">
        <h2>🧠 Intent & Requirements</h2>
        <div id="intentBox" class="notice">Enter a requirement and generate a prompt to see the analysis.</div>
        <div class="section">
          <h2>📊 Prompt Quality</h2>
          <div class="score" id="score">—</div>
          <div class="metrics">
            <div class="metric"><b id="clarity">—</b><span>Clarity</span><div class="meter"><i id="m1"></i></div></div>
            <div class="metric"><b id="specificity">—</b><span>Specificity</span><div class="meter"><i id="m2"></i></div></div>
            <div class="metric"><b id="context">—</b><span>Context</span><div class="meter"><i id="m3"></i></div></div>
            <div class="metric"><b id="completeness">—</b><span>Completeness</span><div class="meter"><i id="m4"></i></div></div>
          </div>
        </div>
      </div>
    </div>

    <div class="grid section">
      <div class="card"><h2>📝 Generated Prompt</h2><div id="promptOutput" class="output">Your optimized prompt will appear here.</div><div class="actions"><button class="btn secondary" onclick="copyText('promptOutput')">Copy</button><button class="btn secondary" onclick="savePrompt()">Save</button></div></div>
      <div class="card"><h2>🤖 Demo AI Response</h2><div id="aiOutput" class="output">The demo AI response will appear here.</div><div class="actions"><button class="btn secondary" onclick="copyText('aiOutput')">Copy Response</button></div></div>
    </div>

    <div class="card section"><h2>🛡️ Security Check</h2><div id="security" class="notice">Security status will appear after generation.</div></div>
  </section>

  <section id="analyzer" class="hidden">
    <div class="card"><h2>🔍 Prompt Analyzer</h2><p>Paste an existing prompt and get transparent quality feedback.</p>
      <textarea id="analyzeInput" placeholder="Example: Create a website."></textarea>
      <div class="actions"><button class="btn" onclick="analyze()">Analyze Prompt</button><button class="btn secondary" onclick="improveExisting()">Improve This Prompt</button></div>
      <div id="analysisResult" class="section output">Analysis will appear here.</div>
    </div>
  </section>

  <section id="library" class="hidden">
    <div class="card"><h2>📚 Prompt Library</h2><p>Your saved prompts are stored locally in this single-page demo.</p><div id="libraryList"></div></div>
  </section>

  <section id="history" class="hidden">
    <div class="card"><h2>🕘 History</h2><div id="historyList"></div></div>
  </section>

  <section id="analytics" class="hidden">
    <div class="grid">
      <div class="card"><h2>📊 Analytics</h2><div class="metrics">
        <div class="metric"><b id="totalPrompts">0</b><span>Total prompts</span></div>
        <div class="metric"><b id="savedPrompts">0</b><span>Saved prompts</span></div>
        <div class="metric"><b id="avgScore">—</b><span>Average quality</span></div>
        <div class="metric"><b id="sessions">1</b><span>Demo sessions</span></div>
      </div></div>
      <div class="card"><h2>🎯 What this demo contains</h2><div class="notice">Natural-language understanding • Requirement extraction • Prompt optimization • Quality scoring • Security checks • Demo AI responses • Local history • Prompt library • Analytics</div></div>
    </div>
  </section>
</main>
</div>

<script>
const KEY='promptforge_single_page_v1';
let db=JSON.parse(localStorage.getItem(KEY)||'{"history":[],"saved":[]}');

function persist(){localStorage.setItem(KEY,JSON.stringify(db));renderAll();}
function show(id,btn){
  document.querySelectorAll('main section').forEach(s=>s.classList.add('hidden'));
  document.getElementById(id).classList.remove('hidden');
  document.querySelectorAll('.nav button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active'); renderAll();
}
function loadExample(){
  document.getElementById('input').value='I am a third year computer science student. I want to build an impressive machine learning project for college using Python. It should solve a real-world problem, use a dataset, have a dashboard, and be deployable.';
}
function clearAll(){['input','analyzeInput'].forEach(id=>document.getElementById(id).value='');document.getElementById('promptOutput').textContent='Your optimized prompt will appear here.';document.getElementById('aiOutput').textContent='The demo AI response will appear here.';document.getElementById('intentBox').textContent='Enter a requirement and generate a prompt to see the analysis.';document.getElementById('security').textContent='Security status will appear after generation.'}
function detect(text){
  const t=text.toLowerCase(); let domain='General'; let intent='Task Request';
  if(/machine learning|ml|model|dataset|classification|prediction/.test(t)){domain='Machine Learning';intent='ML Project / Model Development'}
  else if(/python|javascript|java|c\+\+|code|program|website|app|software/.test(t)){domain='Programming / Software Development';intent='Technical Development'}
  else if(/learn|study|roadmap|course|exam|interview/.test(t)){domain='Education / Career';intent='Learning or Preparation'}
  else if(/resume|cv|job|placement/.test(t)){domain='Career';intent='Career Assistance'}
  else if(/marketing|instagram|post|campaign|brand/.test(t)){domain='Marketing / Content';intent='Content Creation'}
  const duration=(t.match(/\b\d+\s*(day|days|week|weeks|month|months|year|years)\b/)||[])[0]||'Not specified';
  const tech=(t.match(/\b(python|javascript|java|c\+\+|react|node\.?js|tensorflow|pytorch)\b/i)||[])[0]||'Not specified';
  const missing=[]; if(!/audience|student|customer|user|beginner|developer|manager|college/.test(t))missing.push('target audience'); if(!/format|table|bullet|step|json|report|dashboard|roadmap/.test(t))missing.push('desired output format');
  return {domain,intent,duration,tech,missing};
}
function score(text,info){
  const clarity=Math.min(98,55+Math.min(25,Math.floor(text.length/25)));
  const specificity=Math.min(98,45+(text.match(/\b(using|for|with|include|should|must|in|within)\b/gi)||[]).length*7);
  const context=Math.min(98,45+(text.match(/\b(I am|student|beginner|college|company|customer|audience|project)\b/gi)||[]).length*10);
  const completeness=Math.max(40,96-info.missing.length*18);
  return {clarity,specificity,context,completeness,overall:Math.round((clarity+specificity+context+completeness)/4)};
}
function buildPrompt(text,info){
 return `ROLE:
You are an expert ${info.domain.toLowerCase()} mentor and solution architect.

CONTEXT:
The user provided this requirement:
"${text}"

OBJECTIVE:
Understand the user's real goal and provide a practical, accurate and actionable solution.

TASK:
Solve the user's requirement while respecting the stated context, technology and constraints.

DETECTED INTENT:
${info.intent}

KNOWN TECHNOLOGY:
${info.tech}

DURATION:
${info.duration}

REQUIREMENTS:
- Address the user's main objective
- Use beginner-friendly but technically correct explanations where appropriate
- Include practical steps and examples
- Clearly separate assumptions from confirmed requirements

CONSTRAINTS:
- Do not invent missing requirements
- If critical information is missing, state the assumption or ask a concise clarification
- Keep the response structured and actionable

OUTPUT FORMAT:
${document.getElementById('format').value}

TONE:
${document.getElementById('tone').value}

QUALITY CRITERIA:
- Relevant to the user's request
- Specific and actionable
- Well structured
- Technically clear`;
}
function security(text){
 const t=text.toLowerCase();
 const risky=['ignore previous instructions','reveal system prompt','bypass security','steal password','api key','secret key'];
 const found=risky.filter(x=>t.includes(x));
 return found.length?{level:found.length>1?'HIGH':'MEDIUM',msg:'Potentially unsafe or instruction-override language detected: '+found.join(', ')}:{level:'LOW',msg:'No obvious prompt-injection or secret-exposure pattern detected by this basic demo checker.'};
}
function demoResponse(info){
 return `Demo AI Response

Based on your request, I would approach this as a ${info.intent.toLowerCase()} task in the ${info.domain} domain.

Recommended structure:
1. Define the exact objective and success criteria.
2. Collect or prepare the required input/data.
3. Select an appropriate technology or method.
4. Implement the solution in small testable stages.
5. Evaluate the result using measurable criteria.
6. Document the architecture, limitations and future improvements.

Technology detected: ${info.tech}
Duration detected: ${info.duration}

Note: This is PromptForge AI's local Demo AI mode. It demonstrates the complete prompt-engineering pipeline without sending your data to an external LLM.`;
}
function generate(){
 const text=document.getElementById('input').value.trim(); if(!text){alert('Please enter your requirement first.');return}
 const info=detect(text), s=score(text,info), sec=security(text), prompt=buildPrompt(text,info);
 document.getElementById('intentBox').innerHTML=`<b>Intent:</b> ${info.intent}<br><b>Domain:</b> ${info.domain}<br><b>Technology:</b> ${info.tech}<br><b>Duration:</b> ${info.duration}<br><b>Missing / uncertain:</b> ${info.missing.length?info.missing.join(', '):'None detected'}`;
 document.getElementById('promptOutput').textContent=prompt;
 document.getElementById('aiOutput').textContent=demoResponse(info);
 document.getElementById('security').innerHTML=`<span class="risk ${sec.level.toLowerCase()}">Risk: ${sec.level}</span> — ${sec.msg}`;
 setScore(s);
 db.history.unshift({text,prompt,score:s.overall,date:new Date().toLocaleString()}); db.history=db.history.slice(0,50); persist();
}
function setScore(s){
 document.getElementById('score').textContent=s.overall+'/100';
 [['clarity',s.clarity,'m1'],['specificity',s.specificity,'m2'],['context',s.context,'m3'],['completeness',s.completeness,'m4']].forEach(([id,v,m])=>{document.getElementById(id).textContent=v+'%';document.getElementById(m).style.width=v+'%'});
}
function analyze(){
 const text=document.getElementById('analyzeInput').value.trim(); if(!text){alert('Paste a prompt first.');return}
 const info=detect(text),s=score(text,info);
 document.getElementById('analysisResult').textContent=`OVERALL SCORE: ${s.overall}/100

Clarity: ${s.clarity}%
Specificity: ${s.specificity}%
Context: ${s.context}%
Completeness: ${s.completeness}%

Detected intent: ${info.intent}
Domain: ${info.domain}

Suggestions:
${info.missing.length?info.missing.map(x=>'• Add '+x).join('\\n'):'• Your prompt contains the main detectable components.'}
• Consider adding explicit constraints and success criteria.
• Specify the desired output format if it matters.`;
}
function improveExisting(){
 const text=document.getElementById('analyzeInput').value.trim(); if(!text){alert('Paste a prompt first.');return}
 document.getElementById('input').value=text; show('optimizer',document.querySelector('.nav button')); generate();
}
function copyText(id){navigator.clipboard.writeText(document.getElementById(id).textContent).then(()=>alert('Copied!'))}
function savePrompt(){
 const p=document.getElementById('promptOutput').textContent;if(!p||p.startsWith('Your optimized')){alert('Generate a prompt first.');return}
 db.saved.unshift({prompt:p,date:new Date().toLocaleString()});db.saved=db.saved.slice(0,50);persist();alert('Prompt saved to Library.');
}
function renderAll(){
 document.getElementById('libraryList').innerHTML=db.saved.length?db.saved.map((x,i)=>`<div class="history-item"><b>Saved Prompt ${db.saved.length-i}</b><br><small>${x.date}</small><p>${escapeHtml(x.prompt.slice(0,300))}...</p><button class="btn secondary" onclick="navigator.clipboard.writeText(${JSON.stringify(x.prompt)})">Copy</button></div>`).join(''):'<div class="empty">No saved prompts yet.</div>';
 document.getElementById('historyList').innerHTML=db.history.length?db.history.map((x,i)=>`<div class="history-item"><b>${escapeHtml(x.text.slice(0,90))}</b><br><small>${x.date} • Score ${x.score}/100</small><div class="actions"><button class="btn secondary" onclick="reuse(${i})">Reuse</button></div></div>`).join(''):'<div class="empty">No history yet.</div>';
 document.getElementById('totalPrompts').textContent=db.history.length;document.getElementById('savedPrompts').textContent=db.saved.length;
 document.getElementById('avgScore').textContent=db.history.length?Math.round(db.history.reduce((a,b)=>a+b.score,0)/db.history.length)+'/100':'—';
}
function reuse(i){document.getElementById('input').value=db.history[i].text;show('optimizer',document.querySelector('.nav button'));generate()}
function escapeHtml(s){return s.replace(/[&<>"']/g,m=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#039;'}[m]))}
renderAll();
</script>
</body>
</html>
