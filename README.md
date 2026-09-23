# dems-defeat-gop-2026-fund
"Fundraising hub for 2026 Democratic candidates — Senate, House, and Governor races, with candidate bios, live polling."
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dems Defeat GOP 2026 — Flip the Toss-Ups</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Archivo+Black&family=Barlow+Condensed:wght@500;600;700&family=Source+Sans+3:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --navy:#131F3B;
    --navy-2:#1D2E52;
    --paper:#F4F0E6;
    --gold:#C8972C;
    --gold-2:#E4B94F;
    --ink:#1A1A18;
    --line:#D8D0BC;
    --toss:#B4451F;
    --lean:#7A8A5A;
  }
  *{box-sizing:border-box;}
  body{margin:0;background:var(--paper);color:var(--ink);font-family:'Source Sans 3',sans-serif;}
  h1,h2,h3,.display{font-family:'Barlow Condensed',sans-serif;text-transform:uppercase;letter-spacing:.01em;}
  .brand-mark{font-family:'Archivo Black',sans-serif;}

  header.top{background:var(--navy);color:var(--paper);padding:18px 24px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:50;border-bottom:4px solid var(--gold);}
  .logo{display:flex;align-items:center;gap:12px;}
  .logo svg{flex:0 0 auto;}
  .logo-text{font-family:'Archivo Black',sans-serif;font-size:20px;line-height:1;letter-spacing:.01em;}
  .logo-text span{display:block;font-family:'Barlow Condensed',sans-serif;font-weight:500;font-size:12px;letter-spacing:.14em;color:var(--gold-2);margin-top:3px;}

  nav.tabs{display:flex;gap:4px;flex-wrap:wrap;}
  nav.tabs button{background:none;border:none;color:var(--paper);font-family:'Barlow Condensed',sans-serif;font-size:17px;font-weight:600;letter-spacing:.03em;padding:10px 16px;cursor:pointer;border-bottom:3px solid transparent;}
  nav.tabs button:hover{color:var(--gold-2);}
  nav.tabs button.active{color:var(--gold-2);border-bottom-color:var(--gold);}

  section.view{display:none;padding:40px 24px 80px;max-width:1180px;margin:0 auto;}
  section.view.active{display:block;}

  .hero{display:grid;grid-template-columns:1.1fr .9fr;gap:36px;align-items:center;padding:56px 0 40px;border-bottom:1px solid var(--line);}
  .hero h1{font-size:56px;line-height:.96;margin:0 0 18px;}
  .hero p{font-size:18px;line-height:1.5;max-width:46ch;margin:0 0 22px;}
  .hero .stat-row{display:flex;gap:28px;margin-top:26px;flex-wrap:wrap;}
  .stat{border-left:3px solid var(--gold);padding-left:12px;}
  .stat b{display:block;font-family:'Barlow Condensed',sans-serif;font-size:34px;line-height:1;color:var(--navy);}
  .stat small{font-size:12px;letter-spacing:.06em;color:#555;}
  .hero-panel{background:var(--navy);color:var(--paper);padding:28px;position:relative;}
  .hero-panel h3{color:var(--gold-2);font-size:22px;margin-top:0;}
  .hero-panel .featured-photo{width:100%;aspect-ratio:1/1;object-fit:cover;border:3px solid var(--gold);margin-bottom:14px;}

  .btn{display:inline-block;background:var(--gold);color:var(--navy);font-family:'Barlow Condensed',sans-serif;font-weight:700;font-size:16px;letter-spacing:.02em;text-transform:uppercase;padding:11px 20px;border:none;cursor:pointer;text-decoration:none;}
  .btn:hover{background:var(--gold-2);}
  .btn.ghost{background:transparent;color:var(--paper);border:2px solid var(--gold);}

  .section-head{display:flex;align-items:baseline;justify-content:space-between;margin:44px 0 20px;border-bottom:2px solid var(--navy);padding-bottom:8px;}
  .section-head h2{font-size:30px;margin:0;color:var(--navy);}
  .section-head .count{font-family:'Barlow Condensed',sans-serif;font-size:15px;color:#666;}

  .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:22px;}

  .card{background:#fff;border:1px solid var(--line);display:flex;flex-direction:column;}
  .card .photo-wrap{position:relative;}
  .card img.photo{width:100%;aspect-ratio:4/3;object-fit:cover;display:block;background:#ddd;}
  .rating{position:absolute;top:10px;left:0;background:var(--toss);color:#fff;font-family:'Barlow Condensed',sans-serif;font-weight:600;font-size:12px;letter-spacing:.05em;padding:4px 10px;text-transform:uppercase;}
  .rating.lean{background:var(--lean);}
  .poll{position:absolute;bottom:10px;right:10px;background:var(--navy);color:var(--gold-2);font-family:'Barlow Condensed',sans-serif;font-weight:700;font-size:15px;padding:4px 9px;}
  .card-body{padding:16px;display:flex;flex-direction:column;gap:8px;flex:1;}
  .card-body h3{margin:0;font-size:22px;color:var(--navy);}
  .card-body .race{font-size:13px;color:#666;margin-top:-6px;}
  .card-body .bio{font-size:14px;line-height:1.45;color:#333;flex:1;}
  .notes{width:100%;border:1px dashed #b8ad8c;background:#fbf9f2;font-family:'Source Sans 3',sans-serif;font-size:13px;padding:8px;resize:vertical;min-height:54px;}
  .notes:focus{outline:2px solid var(--gold);}
  .card-foot{display:flex;gap:8px;margin-top:4px;}
  .donate-btn{flex:1;text-align:center;background:var(--navy);color:var(--paper);font-family:'Barlow Condensed',sans-serif;font-weight:700;letter-spacing:.03em;text-transform:uppercase;padding:10px;border:none;cursor:pointer;text-decoration:none;font-size:14px;}
  .donate-btn:hover{background:var(--navy-2);}

  .articles-intro{max-width:64ch;margin-bottom:24px;color:#333;line-height:1.5;}
  #articleForm{background:#fff;border:1px solid var(--line);padding:20px;margin-bottom:32px;}
  #articleForm input,#articleForm textarea{width:100%;font-family:'Source Sans 3',sans-serif;font-size:14px;padding:9px;border:1px solid var(--line);margin-bottom:10px;}
  #articleForm textarea{min-height:110px;resize:vertical;}
  .article-card{background:#fff;border:1px solid var(--line);padding:18px 20px;margin-bottom:16px;}
  .article-card h4{margin:0 0 4px;color:var(--navy);font-size:20px;font-family:'Barlow Condensed',sans-serif;}
  .article-card .src{font-size:12px;color:#777;margin-bottom:8px;}
  .article-card p{font-size:14px;line-height:1.5;margin:0 0 10px;white-space:pre-wrap;}
  .article-card button{background:none;border:none;color:#a33;font-size:12px;cursor:pointer;padding:0;}

  footer{background:var(--navy);color:#B9BFCF;text-align:center;padding:26px;font-size:13px;}
  .note-banner{background:#fff8e0;border:1px solid var(--gold);padding:12px 16px;font-size:13px;color:#5a4a12;margin-bottom:28px;}

  @media(max-width:820px){
    .hero{grid-template-columns:1fr;}
    header.top{flex-direction:column;align-items:flex-start;gap:12px;}
    nav.tabs{width:100%;justify-content:flex-start;}
    .hero h1{font-size:38px;}
  }
</style>
</head>
<body>

<header class="top">
  <div class="logo">
    <svg width="40" height="40" viewBox="0 0 40 40" aria-hidden="true">
      <rect x="1" y="1" width="38" height="38" fill="#131F3B" stroke="#C8972C" stroke-width="2"/>
      <path d="M8 27 L14 13 L20 27 M10.5 21 H17.5" stroke="#E4B94F" stroke-width="2.4" fill="none" stroke-linecap="square"/>
      <rect x="24" y="13" width="8" height="14" fill="none" stroke="#F4F0E6" stroke-width="2.4"/>
      <line x1="24" y1="20" x2="32" y2="20" stroke="#F4F0E6" stroke-width="2.4"/>
    </svg>
    <div class="logo-text">DEMS DEFEAT GOP<span>2026 TOSS-UP FUND</span></div>
  </div>
  <nav class="tabs">
    <button data-view="home" class="active">Home</button>
    <button data-view="senate">Senate</button>
    <button data-view="house">House</button>
    <button data-view="governor">Governor</button>
    <button data-view="articles">Articles</button>
  </nav>
</header>

<!-- HOME -->
<section class="view active" id="home">
  <div class="hero">
    <div>
      <h1>Every toss-up race<br>needs a closer.</h1>
      <p>One place to track the closest Senate, House, and Governor races of 2026 — real polling, real ratings, and a direct way to back the Democrat in each one.</p>
      <a href="#senate" class="btn" onclick="showView('senate')">See the Senate map</a>
      <div class="stat-row">
        <div class="stat"><b>7</b><small>SENATE TOSS-UPS</small></div>
        <div class="stat"><b>18</b><small>HOUSE TOSS-UPS</small></div>
        <div class="stat"><b>13</b><small>GOVERNOR RACES</small></div>
      </div>
    </div>
    <div class="hero-panel">
      <img class="featured-photo" src="https://ui-avatars.com/api/?name=Abdul+El-Sayed&background=E4B94F&color=131F3B&size=400&bold=true&font-size=0.4" alt="Abdul El-Sayed">
      <h3>Featured: Abdul El-Sayed — Michigan</h3>
      <p style="font-size:14px;line-height:1.5;">Running for Michigan's open Senate seat against Mike Rogers. Every public poll since the primary has been within the margin of error. This is the seat that decides whether Michigan sends a Democrat to the Senate for a fourth straight cycle.</p>
      <a href="#" class="btn ghost" onclick="alert('Add your ActBlue-style donation link here.'); return false;">Donate to El-Sayed</a>
    </div>
  </div>

  <div class="note-banner">
    Photos below are placeholder initials avatars generated automatically — swap in a real photo for any candidate by replacing that card's image URL in the page code, or ask to have specific ones added.
  </div>

  <div class="section-head"><h2>Why these races</h2></div>
  <p style="max-width:70ch;line-height:1.6;">Control of Congress in 2027 comes down to a small number of races where the outcome is genuinely uncertain. This site tracks the ones rated <strong>Toss-Up</strong> by nonpartisan handicappers, plus the governor's races Democrats are most focused on flipping or defending. Use the tabs above to browse each chamber, read the polling, and send a contribution directly to the candidate.</p>
</section>

<!-- SENATE -->
<section class="view" id="senate">
  <div class="section-head"><h2>Senate — Toss-Up Races</h2><span class="count" id="senateCount"></span></div>
  <div class="grid" id="senateGrid"></div>
</section>

<!-- HOUSE -->
<section class="view" id="house">
  <div class="section-head"><h2>House — Toss-Up Races</h2><span class="count" id="houseCount"></span></div>
  <p style="max-width:70ch;color:#444;font-size:14px;margin-top:-8px;">Ratings shift through the fall as new polling and fundraising numbers come in — check back against Cook Political Report for the latest before an event or ad buy.</p>
  <div class="grid" id="houseGrid"></div>
</section>

<!-- GOVERNOR -->
<section class="view" id="governor">
  <div class="section-head"><h2>Governor Races</h2><span class="count" id="govCount"></span></div>
  <div class="grid" id="govGrid"></div>
</section>

<!-- ARTICLES -->
<section class="view" id="articles">
  <div class="section-head"><h2>Articles</h2></div>
  <p class="articles-intro">Paste in general election-coverage articles here — pieces that aren't about one specific candidate. Saved articles stay in this browser until you clear them.</p>
  <form id="articleForm">
    <input type="text" id="artTitle" placeholder="Article title" required>
    <input type="text" id="artSource" placeholder="Source / link (optional)">
    <textarea id="artBody" placeholder="Paste the article text or your notes on it..." required></textarea>
    <button type="submit" class="btn">Add article</button>
  </form>
  <div id="articleList"></div>
</section>

<footer>Dems Defeat GOP — 2026 Toss-Up Fund. Not affiliated with any candidate's official campaign committee.</footer>

<script>
function ratingBadge(rating){
  const cls = rating === 'Toss-Up' ? 'rating' : 'rating lean';
  return `<span class="${cls}">${rating}</span>`;
}
function avatar(name){
  return `https://ui-avatars.com/api/?name=${encodeURIComponent(name)}&background=131F3B&color=E4B94F&size=400&bold=true&font-size=0.38`;
}
function renderCard(c){
  return `<div class="card">
    <div class="photo-wrap">
      <img class="photo" src="${c.photo || avatar(c.name)}" alt="${c.name}">
      ${ratingBadge(c.rating)}
      ${c.poll ? `<span class="poll">${c.poll}</span>` : ''}
    </div>
    <div class="card-body">
      <h3>${c.name}</h3>
      <div class="race">${c.race}</div>
      <div class="bio">${c.bio}</div>
      <textarea class="notes" placeholder="Your notes on this race...">${c.defaultNote || ''}</textarea>
      <div class="card-foot">
        <a href="#" class="donate-btn" onclick="alert('Add this candidate\\'s official donation link here (not a direct ActBlue link).'); return false;">Donate</a>
      </div>
    </div>
  </div>`;
}
function renderGrid(id, countId, data){
  document.getElementById(id).innerHTML = data.map(renderCard).join('');
  document.getElementById(countId).textContent = data.length + (data.length===1 ? ' race' : ' races');
}

const senateData = [
  {name:"Abdul El-Sayed", race:"Michigan — vs. Mike Rogers (R)", rating:"Toss-Up", poll:"~46-47%", bio:"Public health physician and former Wayne County health director. Running for Gary Peters' open seat; would be the first Muslim U.S. Senator."},
  {name:"Jon Ossoff", race:"Georgia — vs. Mike Collins (R)", rating:"Toss-Up", poll:"Lead, low single digits", bio:"Incumbent senator since 2021, seeking a second term in a state Trump carried narrowly in 2024."},
  {name:"Chris Pappas", race:"New Hampshire — vs. John Sununu (R)", rating:"Toss-Up", poll:"Too close to call", bio:"U.S. Representative running for Jeanne Shaheen's open seat against former Senator John Sununu."},
  {name:"Josh Turek", race:"Iowa — vs. Ashley Hinson (R)", rating:"Toss-Up", poll:"Within margin", bio:"State legislator and two-time Paralympic gold medalist running for Joni Ernst's open seat."},
  {name:"Sherrod Brown", race:"Ohio — vs. Jon Husted (R)", rating:"Toss-Up", poll:"Ahead in most polls", bio:"Former three-term senator seeking a return to the seat he lost in 2024."},
  {name:"James Talarico", race:"Texas — vs. Ken Paxton (R)", rating:"Toss-Up", poll:"Ahead in recent polls", bio:"State legislator running in a state Democrats haven't won statewide since 1994."},
  {name:"Roy Cooper", race:"North Carolina — open seat", rating:"Toss-Up", poll:"Competitive", bio:"Former two-term North Carolina governor running for the state's open Senate seat."},
];

const houseData = [
  {name:"Adam Gray", race:"California — incumbent", rating:"Toss-Up", bio:"First-term representative defending a Central Valley swing district."},
  {name:"Derek Tran", race:"California — incumbent", rating:"Toss-Up", bio:"First-term representative defending a competitive Orange County-area seat."},
  {name:"Jared Golden", race:"Maine — incumbent", rating:"Toss-Up", bio:"Independent-minded Democrat defending a district Trump has carried before."},
  {name:"Gabe Vasquez", race:"New Mexico — incumbent", rating:"Toss-Up", bio:"First-term representative in a competitive border district."},
  {name:"Laura Gillen", race:"New York — incumbent", rating:"Toss-Up", bio:"First-term representative defending a Long Island swing seat."},
  {name:"Don Davis", race:"North Carolina — incumbent", rating:"Toss-Up", bio:"Moderate Democrat defending a rural/suburban eastern NC district."},
  {name:"Marcy Kaptur", race:"Ohio — incumbent", rating:"Toss-Up", bio:"Longest-serving woman in House history, defending a Toledo-area district Trump has carried."},
  {name:"Emilia Sykes", race:"Ohio — incumbent", rating:"Toss-Up", bio:"First-term representative defending a competitive Akron-area seat."},
  {name:"Vicente Gonzalez", race:"Texas — incumbent", rating:"Toss-Up", bio:"Defending a South Texas border district that has trended Republican."},
  {name:"Marie Gluesenkamp Perez", race:"Washington — incumbent", rating:"Toss-Up", bio:"Small-business-owner Democrat defending a rural southwest Washington seat."},
  {name:"Democratic challenger", race:"Arizona — vs. David Schweikert (R)", rating:"Toss-Up", bio:"Targeting a longtime Republican incumbent in a competitive Phoenix-area district."},
  {name:"Democratic challenger", race:"Arizona — vs. Juan Ciscomani (R)", rating:"Toss-Up", bio:"Targeting a first-term Republican in a closely divided southern Arizona district."},
  {name:"Democratic challenger", race:"Colorado — vs. Gabe Evans (R)", rating:"Toss-Up", bio:"Targeting a first-term Republican in a swing Denver-suburbs district."},
  {name:"Democratic challenger", race:"Iowa — vs. Mariannette Miller-Meeks (R)", rating:"Toss-Up", bio:"Targeting a longtime top Democratic pickup opportunity in southeast Iowa."},
  {name:"Democratic challenger", race:"Michigan — vs. Tom Barrett (R)", rating:"Toss-Up", bio:"Targeting a first-term Republican in a Lansing-area swing district."},
  {name:"Democratic challenger", race:"Nebraska — vs. Don Bacon's open seat (R)", rating:"Toss-Up", bio:"Targeting the Omaha-area seat left open by a retiring moderate Republican."},
  {name:"Democratic challenger", race:"Pennsylvania — vs. Ryan Mackenzie (R)", rating:"Toss-Up", bio:"Targeting a first-term Republican in the Lehigh Valley."},
  {name:"Democratic challenger", race:"Pennsylvania — vs. Scott Perry (R)", rating:"Toss-Up", bio:"Targeting a longtime Republican incumbent in the Harrisburg area."},
];

const govData = [
  {name:"Jonathan Kreiss-Tomkins", race:"Alaska — Governor", rating:"Lean D", bio:"Former state legislator running to lead Alaska."},
  {name:"Katie Hobbs", race:"Arizona — Governor (incumbent)", rating:"Lean D", bio:"Incumbent governor seeking re-election in a perennial battleground state."},
  {name:"Gina Hinojosa", race:"Texas — Governor", rating:"Toss-Up", bio:"State legislator running for governor in a state Democrats haven't won statewide since 1994."},
  {name:"Amy Acton", race:"Ohio — Governor", rating:"Toss-Up", bio:"Former Ohio Department of Health director, known statewide for her role in the state's COVID-19 response."},
  {name:"Cinde Warmington", race:"New Hampshire — Governor", rating:"Toss-Up", bio:"Executive councilor running for New Hampshire's open governorship."},
  {name:"Aaron Ford", race:"Nevada — Governor", rating:"Toss-Up", bio:"Nevada Attorney General running to flip the governor's office."},
  {name:"Cindy Holscher", race:"Kansas — Governor", rating:"Lean D", bio:"State senator running to keep the governorship in Democratic hands."},
  {name:"Rob Sand", race:"Iowa — Governor", rating:"Toss-Up", bio:"Iowa State Auditor running for governor as one of the state's most visible statewide Democrats."},
  {name:"David Crowley", race:"Wisconsin — Governor", rating:"Toss-Up", bio:"Milwaukee County Executive running for Wisconsin's open governorship."},
  {name:"Jocelyn Benson", race:"Michigan — Governor", rating:"Toss-Up", bio:"Michigan Secretary of State running for the state's open governorship."},
  {name:"Keisha Lance Bottoms", race:"Georgia — Governor", rating:"Toss-Up", bio:"Former Atlanta mayor running for Georgia's open governorship."},
  {name:"David Jolly", race:"Florida — Governor", rating:"Lean R", bio:"Former Republican congressman turned Democrat, running for governor of Florida."},
  {name:"Amanda Janoo", race:"Vermont — Governor", rating:"Toss-Up", bio:"Economic policy advisor running for Vermont's open governorship."},
];

renderGrid('senateGrid','senateCount', senateData);
renderGrid('houseGrid','houseCount', houseData);
renderGrid('govGrid','govCount', govData);

// tab switching
function showView(id){
  document.querySelectorAll('.view').forEach(v=>v.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  document.querySelectorAll('nav.tabs button').forEach(b=>b.classList.toggle('active', b.dataset.view===id));
  window.scrollTo({top:0, behavior:'instant'});
}
document.querySelectorAll('nav.tabs button').forEach(b=>{
  b.addEventListener('click', ()=>showView(b.dataset.view));
});

// articles (stored in-memory + localStorage so it survives reloads on the live site)
let articles = [];
try{ articles = JSON.parse(localStorage.getItem('ddg_articles')||'[]'); }catch(e){ articles = []; }
function saveArticles(){ localStorage.setItem('ddg_articles', JSON.stringify(articles)); }
function renderArticles(){
  const list = document.getElementById('articleList');
  if(!articles.length){ list.innerHTML = '<p style="color:#777;font-size:14px;">No articles added yet.</p>'; return; }
  list.innerHTML = articles.map((a,i)=>`
    <div class="article-card">
      <h4>${a.title}</h4>
      ${a.source ? `<div class="src">${a.source}</div>` : ''}
      <p>${a.body}</p>
      <button onclick="removeArticle(${i})">Remove</button>
    </div>`).join('');
}
function removeArticle(i){ articles.splice(i,1); saveArticles(); renderArticles(); }
document.getElementById('articleForm').addEventListener('submit', function(e){
  e.preventDefault();
  articles.unshift({
    title: document.getElementById('artTitle').value,
    source: document.getElementById('artSource').value,
    body: document.getElementById('artBody').value
  });
  saveArticles();
  this.reset();
  renderArticles();
});
renderArticles();
</script>
</body>
</html>
