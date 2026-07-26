<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover">
<title>스페이스 디펜더</title>
<style>
  :root {
    --bg-deep: #05060f;
    --bg-panel: #0d1024;
    --line: #232748;
    --gold: #ffcc33;
    --heart: #ff4d6d;
    --text-dim: #7d84b0;
  }

  * { box-sizing: border-box; }

  html, body {
    margin: 0;
    min-height: 100vh;
    /* iOS 관성 스크롤/바운스가 게임 조작을 방해하지 않도록 */
    overscroll-behavior: none;
    touch-action: none;
  }

  body {
    display: flex;
    align-items: center;
    justify-content: center;
    background:
      radial-gradient(circle at 20% 10%, rgba(0, 85, 255, 0.15), transparent 40%),
      radial-gradient(circle at 80% 90%, rgba(255, 0, 255, 0.12), transparent 40%),
      var(--bg-deep);
    font-family: 'Segoe UI', 'Malgun Gothic', sans-serif;
    color: #e8eaf7;
    padding: 10px;
  }

  .game-wrap {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    width: 100%;
    max-width: 500px;
  }

  .hud {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: var(--bg-panel);
    border: 1px solid var(--line);
    border-radius: 10px;
    padding: 8px 12px;
    font-size: 13px;
  }

  .hud-stat { display: flex; flex-direction: column; align-items: center; min-width: 42px; }
  .hud-label { font-size: 9px; color: var(--text-dim); text-transform: uppercase; letter-spacing: 0.08em; }
  .hud-value { font-size: 15px; font-weight: 700; margin-top: 2px; }
  #goldDisplay { color: var(--gold); }
  #stageDisplay { color: #00ffcc; }
  #killDisplay { color: #ff00ff; font-size: 11px; }
  #heartsDisplay { color: var(--heart); }
  #skillDisplay { color: #ffd166; font-size: 20px; }

  canvas {
    background: linear-gradient(180deg, #060814 0%, #0a0d1f 100%);
    border: 1px solid var(--line);
    border-radius: 10px;
    display: block;
    width: 100%;
    max-width: 500px;
    height: auto;
    touch-action: none; /* 캔버스 위 드래그/탭이 화면 스크롤로 이어지지 않도록 */
  }
  canvas:focus { outline: none; box-shadow: 0 0 0 2px #00ffcc; }



  .shop-bar { width: 100%; display: flex; flex-wrap: wrap; gap: 6px; justify-content: center; }
  .shop-key { flex: 1 1 30%; min-width: 90px; background: var(--bg-panel); border: 1px solid var(--line); border-radius: 8px; padding: 6px 8px; font-size: 10.5px; text-align: center; color: var(--text-dim); }
  .shop-key b { display: block; font-size: 12px; color: #e8eaf7; margin-bottom: 1px; }
  .shop-key span.cost { display:block; color: var(--gold); font-size: 10px; margin-top:2px; }
  .shop-key.owned { border-color: #00ffcc; color: #00ffcc; }
  .shop-key.owned b, .shop-key.owned span.cost { color: #00ffcc; }

  .overlay { position: absolute; inset: 0; display: none; align-items: center; justify-content: center; flex-direction: column; gap: 10px; background: rgba(5,6,15,0.92); border-radius: 10px; text-align: center; padding: 18px; }
  .overlay.show { display: flex; }
  .overlay h2 { font-size: 22px; margin: 0; letter-spacing: 0.04em; }
  #gameOverOverlay h2 { color: #ff4d6d; }
  #startOverlay h2 { color: #00ffcc; }
  #cardOverlay h2 { color: #ffd166; font-size: 18px; }
  .overlay p { margin: 0; color: var(--text-dim); font-size: 12px; max-width: 360px; line-height: 1.7; }
  .overlay button.primary-btn { margin-top: 6px; padding: 10px 22px; background: #00ffcc; border: none; border-radius: 8px; font-weight: 700; cursor: pointer; color: #05060f; font-size: 14px; }

  .canvas-stack { position: relative; width: 100%; }

  .fire-btn {
    position: absolute; right: 16px; bottom: 16px; width: 66px; height: 66px; border-radius: 50%;
    border: 2px solid #ff00ff; background: radial-gradient(circle at 35% 30%, #ff6fe0, #ff00ff 70%);
    color: #fff; font-weight: 700; font-size: 12px; cursor: pointer; user-select: none; -webkit-user-select: none;
    touch-action: none; box-shadow: 0 0 14px rgba(255,0,255,0.5); transition: transform .08s ease;
  }
  .fire-btn:active { transform: scale(0.92); }

  .boss-banner { position: absolute; top: 10px; left: 50%; transform: translateX(-50%); background: rgba(255,34,85,0.15); border: 1px solid #ff2255; color: #ff8fa8; font-size: 11px; font-weight: 700; letter-spacing: 0.08em; padding: 4px 12px; border-radius: 20px; display: none; white-space: nowrap; }
  .boss-banner.show { display: block; }

  .card-row { display: flex; gap: 10px; flex-wrap: wrap; justify-content: center; }
  .skill-card {
    width: 110px; background: var(--bg-panel); border: 1px solid var(--line); border-radius: 10px;
    padding: 12px 8px; cursor: pointer; transition: border-color .15s, transform .1s;
  }
  .skill-card:hover { border-color: #ffd166; transform: translateY(-3px); }
  .skill-icon { font-size: 26px; }
  .skill-name { font-size: 12px; font-weight: 700; margin-top: 4px; color: #e8eaf7; }
  .skill-desc { font-size: 9.5px; color: var(--text-dim); margin-top: 4px; line-height: 1.4; }
  .skip-btn { background: transparent; border: 1px solid var(--line); color: var(--text-dim); padding: 8px 18px; border-radius: 8px; cursor: pointer; font-size: 12px; margin-top: 4px; }
</style>
</head>
<body>

<div class="game-wrap">
  <div class="hud">
    <div class="hud-stat"><span class="hud-label">Gold</span><span class="hud-value" id="goldDisplay">0</span></div>
    <div class="hud-stat"><span class="hud-label">Stage</span><span class="hud-value" id="stageDisplay">1</span></div>
    <div class="hud-stat"><span class="hud-label">Boss까지</span><span class="hud-value" id="killDisplay">0/20</span></div>
    <div class="hud-stat"><span class="hud-label">Hearts</span><span class="hud-value" id="heartsDisplay">❤️❤️</span></div>
    <div class="hud-stat"><span class="hud-label">Skill[Enter]</span><span class="hud-value" id="skillDisplay">-</span></div>
  </div>

  <div class="canvas-stack">
    <canvas id="gameCanvas" width="500" height="700" tabindex="0"></canvas>
    <div class="boss-banner" id="bossBanner"></div>

    <div class="overlay show" id="startOverlay">
      <h2>스페이스 디펜더</h2>
      <p>
        방향키/WASD 이동 · 스페이스바(또는 화면/발사버튼)로 발사<br>
        숫자 1~5로 우주선 구매(각기 다른 특성)<br>
        일반 몬스터 20마리 처치 시 보스 등장 · 3번째 보스 디자인부터 고유 스킬 보유<br>
        보스 처치 시 하트가 떨어지니 받으면 회복, 스킬카드 1장도 선택 가능<br>
        보유 스킬은 ENTER로 사용 · 하트를 잃으면 잠깐 멈추고 파괴 연출이 재생됩니다
      </p>
      <button class="primary-btn" id="startBtn">게임 시작</button>
    </div>

    <div class="overlay" id="gameOverOverlay">
      <h2>GAME OVER</h2>
      <p id="finalStats">스테이지 1 · 골드 0</p>
      <button class="primary-btn" id="restartBtn">다시 시작</button>
    </div>

    <div class="overlay" id="cardOverlay">
      <h2>보스 격파! 스킬 카드를 선택하세요</h2>
      <div class="card-row" id="cardRow"></div>
      <button class="skip-btn" id="skipCardBtn">선택 안 함</button>
    </div>

    <button id="fireBtn" class="fire-btn" type="button">발사</button>
  </div>

  <div class="shop-bar">
    <div class="shop-key owned" id="shopKey1"><b>[1] 기본</b>균형형<span class="cost">무료</span></div>
    <div class="shop-key" id="shopKey2"><b>[2] 고속</b>이동·연사↑<span class="cost">50G</span></div>
    <div class="shop-key" id="shopKey3"><b>[3] 하이퍼</b>3방향 확산탄<span class="cost">150G</span></div>
    <div class="shop-key" id="shopKey4"><b>[4] 탱커</b>보스 2배피해·하트+1<span class="cost">300G</span></div>
    <div class="shop-key" id="shopKey5"><b>[5] 스텔스</b>관통탄<span class="cost">500G</span></div>
  </div>
</div>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
const goldDisplay = document.getElementById('goldDisplay');
const stageDisplay = document.getElementById('stageDisplay');
const killDisplay = document.getElementById('killDisplay');
const heartsDisplay = document.getElementById('heartsDisplay');
const skillDisplay = document.getElementById('skillDisplay');
const bossBanner = document.getElementById('bossBanner');
const startOverlay = document.getElementById('startOverlay');
const gameOverOverlay = document.getElementById('gameOverOverlay');
const cardOverlay = document.getElementById('cardOverlay');
const cardRow = document.getElementById('cardRow');
const skipCardBtn = document.getElementById('skipCardBtn');
const finalStats = document.getElementById('finalStats');
const startBtn = document.getElementById('startBtn');
const restartBtn = document.getElementById('restartBtn');
const fireBtn = document.getElementById('fireBtn');
const shopKeyEls = [1,2,3,4,5].map(n => document.getElementById('shopKey'+n));

// --- 게임 상태: ready | playing | cardSelect | over ---
let gameState = 'ready';

let gold = 0;
let stage = 1;
let killCount = 0;
const killsToBoss = 20;

const baseMaxHearts = 2;
let hearts = baseMaxHearts;

let bossActive = false;
let boss = null;
let wingmenCount = 0;
let cardSelectPendingAt = null;

let lastShotTime = 0;
let frameCount = 0;
let isFiring = false;
let timeFactor = 1;

let isPaused = false;
let pauseUntil = 0;
let pendingGameOver = false;

let heldSkill = null;
let invincibleUntil = 0;
let rapidUntil = 0;
let slowUntil = 0;

const player = {
  x: canvas.width / 2 - 25, y: canvas.height - 90, width: 50, height: 54,
  speed: 5, color: '#0055ff', bulletColor: '#ffff00', level: 1,
  fireInterval: 150, trait: 'normal'
};

const shipUpgrades = [
  { level:1, cost:0,   name:'기본 우주선',   color:'#0055ff', speed:5, bulletColor:'#ffff00', fireInterval:150, trait:'normal' },
  { level:2, cost:50,  name:'고속 우주선',   color:'#00ffcc', speed:8, bulletColor:'#00ffcc', fireInterval:100, trait:'rapid'  },
  { level:3, cost:150, name:'하이퍼 우주선', color:'#ff00ff', speed:6, bulletColor:'#ff00ff', fireInterval:170, trait:'spread' },
  { level:4, cost:300, name:'탱커 우주선',   color:'#ffaa00', speed:4, bulletColor:'#ffaa00', fireInterval:220, trait:'heavy'  },
  { level:5, cost:500, name:'스텔스 우주선', color:'#8a2be2', speed:6, bulletColor:'#c9a0ff', fireInterval:140, trait:'pierce' }
];

const skillPool = [
  { id:'bomb',   name:'궤멸 폭탄',   icon:'💣', desc:'화면의 일반 몬스터 전부 제거 + 보스 피해', kind:'bomb'  },
  { id:'shield', name:'무적 쉴드',   icon:'🛡️', desc:'3초간 모든 피해 무효화',                 kind:'shield'},
  { id:'rapid',  name:'속사 모드',   icon:'⚡', desc:'5초간 연사 속도 2배',                     kind:'rapid' },
  { id:'heal',   name:'긴급 수리',   icon:'💚', desc:'하트 1개 즉시 회복',                       kind:'heal'  },
  { id:'slow',   name:'타임 슬로우', icon:'⏳', desc:'4초간 적/보스 속도 절반',                  kind:'slow'  }
];

const bossTemplates = [
  { id:'mothership', name:'레드 마더십',   color:'#ff2255', baseHp:30,  hpPerStage:10, baseSpeed:2,   spdPerStage:0.3,  baseShoot:65, shootPerStage:-5, minShoot:35, hasSkill:false },
  { id:'cruiser',     name:'트윈 크루저',   color:'#ff8800', baseHp:45,  hpPerStage:12, baseSpeed:1.5, spdPerStage:0.25, baseShoot:70, shootPerStage:-5, minShoot:40, hasSkill:false },
  { id:'spider',      name:'스파이더 드론', color:'#aa33ff', baseHp:60,  hpPerStage:15, baseSpeed:3,   spdPerStage:0.3,  baseShoot:80, shootPerStage:-5, minShoot:45, hasSkill:true, skillName:'차지 레이저' },
  { id:'crystal',     name:'크리스탈 이터', color:'#33ffaa', baseHp:75,  hpPerStage:18, baseSpeed:2,   spdPerStage:0.3,  baseShoot:75, shootPerStage:-5, minShoot:40, hasSkill:true, skillName:'미사일 확산' },
  { id:'obsidian',    name:'옵시디언 로드', color:'#7755dd', baseHp:100, hpPerStage:22, baseSpeed:2.5, spdPerStage:0.3,  baseShoot:70, shootPerStage:-5, minShoot:38, hasSkill:true, skillName:'실드 배리어' }
];

const bullets = [];
const enemies = [];
const enemyBullets = [];
const heartDrops = [];
const shatterParticles = [];
const keys = {};

const stars = Array.from({ length: 70 }, () => ({
  x: Math.random()*canvas.width, y: Math.random()*canvas.height, r: Math.random()*1.6+0.3,
  twinkleSpeed: Math.random()*0.05+0.01, phase: Math.random()*Math.PI*2
}));

function effectiveMaxHearts() { return baseMaxHearts + (player.trait === 'heavy' ? 1 : 0); }

// --- 입력 ---
window.addEventListener('keydown', (e) => {
  keys[e.code] = true; keys[e.key] = true;
  if (e.code === 'Space' || e.key === ' ' || e.key === 'Spacebar') e.preventDefault();
  if (e.repeat) return;
  if (gameState !== 'playing') return;
  if (e.key === '1') buyShip(0);
  if (e.key === '2') buyShip(1);
  if (e.key === '3') buyShip(2);
  if (e.key === '4') buyShip(3);
  if (e.key === '5') buyShip(4);
  if (e.key === 'Enter') useSkill();
});
window.addEventListener('keyup', (e) => { keys[e.code] = false; keys[e.key] = false; });

canvas.addEventListener('click', () => canvas.focus());
function startFiring(e) { if (e) e.preventDefault(); canvas.focus(); isFiring = true; }
function stopFiring(e) { if (e) e.preventDefault(); isFiring = false; }
canvas.addEventListener('mousedown', startFiring);
canvas.addEventListener('mouseup', stopFiring);
canvas.addEventListener('mouseleave', stopFiring);
canvas.addEventListener('touchstart', startFiring, { passive:false });
canvas.addEventListener('touchend', stopFiring, { passive:false });
canvas.addEventListener('touchcancel', stopFiring, { passive:false });
fireBtn.addEventListener('mousedown', startFiring);
fireBtn.addEventListener('mouseup', stopFiring);
fireBtn.addEventListener('mouseleave', stopFiring);
fireBtn.addEventListener('touchstart', startFiring, { passive:false });
fireBtn.addEventListener('touchend', stopFiring, { passive:false });
fireBtn.addEventListener('touchcancel', stopFiring, { passive:false });

// --- 모바일/태블릿: 캔버스를 터치(또는 클릭 드래그)해서 우주선을 손가락 위치로 이동 ---
// 캔버스는 CSS로 화면 크기에 맞춰 축소/확대되므로, 실제 캔버스 내부 좌표계(500x700)로 변환해준다.
function getCanvasPos(e) {
  const rect = canvas.getBoundingClientRect();
  const point = (e.touches && e.touches[0]) ? e.touches[0] : e;
  const scaleX = canvas.width / rect.width;
  const scaleY = canvas.height / rect.height;
  return {
    x: (point.clientX - rect.left) * scaleX,
    y: (point.clientY - rect.top) * scaleY
  };
}
function moveShipTo(pos) {
  if (gameState !== 'playing') return;
  player.x = Math.min(canvas.width - player.width, Math.max(0, pos.x - player.width / 2));
  player.y = Math.min(canvas.height - player.height, Math.max(0, pos.y - player.height / 2));
}
canvas.addEventListener('touchstart', (e) => moveShipTo(getCanvasPos(e)), { passive:false });
canvas.addEventListener('touchmove', (e) => { e.preventDefault(); moveShipTo(getCanvasPos(e)); }, { passive:false });
canvas.addEventListener('mousedown', (e) => moveShipTo(getCanvasPos(e)));
canvas.addEventListener('mousemove', (e) => { if (isFiring) moveShipTo(getCanvasPos(e)); });

// --- 윙맨 위치 ---
function getWingmenPositions() {
  const positions = [];
  for (let i = 0; i < wingmenCount; i++) {
    const side = i % 2 === 0 ? 1 : -1;
    const rank = Math.floor(i/2) + 1;
    positions.push({ x: player.x + side*player.width*0.95*rank, y: player.y + 14*rank });
  }
  return positions;
}

// --- 발사 ---
function shootBullet() {
  const dmg = player.trait === 'heavy' ? 2 : 1;
  const pierce = player.trait === 'pierce';

  if (player.trait === 'spread') {
    [-0.22, 0, 0.22].forEach(angle => {
      bullets.push({ x: player.x+player.width/2-3, y: player.y-6, width:6, height:14,
        vx: Math.sin(angle)*10, vy: -Math.cos(angle)*10, color: player.bulletColor, damage:dmg, pierce });
    });
  } else {
    bullets.push({ x: player.x+player.width/2-3, y: player.y-6, width:6, height:16,
      speed:10, color: player.bulletColor, damage:dmg, pierce });
  }

  getWingmenPositions().forEach(pos => {
    bullets.push({ x: pos.x+player.width*0.35-3, y: pos.y-6, width:6, height:14,
      speed:10, color: player.bulletColor, damage:1, pierce:false });
  });
}

// --- 상점 ---
function buyShip(index) {
  const upgrade = shipUpgrades[index];
  if (player.level >= upgrade.level) return;
  if (gold < upgrade.cost) { flashInsufficientGold(index); return; }

  gold -= upgrade.cost;
  const prevMax = effectiveMaxHearts();
  player.level = upgrade.level;
  player.color = upgrade.color;
  player.speed = upgrade.speed;
  player.bulletColor = upgrade.bulletColor;
  player.fireInterval = upgrade.fireInterval;
  player.trait = upgrade.trait;
  const newMax = effectiveMaxHearts();
  if (newMax > prevMax) hearts += (newMax - prevMax);
  else if (hearts > newMax) hearts = newMax;

  goldDisplay.textContent = gold;
  renderHearts();
  updateShopUI();
}
function updateShopUI() { shopKeyEls.forEach((el,i) => { if (player.level >= shipUpgrades[i].level) el.classList.add('owned'); }); }
function flashInsufficientGold(index) { const el = shopKeyEls[index]; el.style.borderColor = '#ff4d6d'; setTimeout(() => { el.style.borderColor = ''; }, 300); }

// --- 일반 몬스터 스폰 ---
let enemySpawnTimer = null;
function startEnemySpawner() {
  clearInterval(enemySpawnTimer);
  enemySpawnTimer = setInterval(() => {
    if (gameState !== 'playing' || bossActive) return;
    const enemyWidth = 38;
    enemies.push({ x: Math.random()*(canvas.width-enemyWidth), y: -40, width: enemyWidth, height: 38,
      speed: 2 + stage*0.5, color: '#ff0055', wobble: Math.random()*Math.PI*2 });
  }, 1000);
}

function isColliding(a, b) { return a.x < b.x+b.width && a.x+a.width > b.x && a.y < b.y+b.height && a.y+a.height > b.y; }

function updateKillDisplay() { killDisplay.textContent = bossActive ? '보스전!' : `${killCount}/${killsToBoss}`; }
function renderHearts() {
  const max = effectiveMaxHearts();
  heartsDisplay.textContent = '❤️'.repeat(Math.max(0,hearts)) + '🖤'.repeat(Math.max(0,max-hearts));
}
function updateSkillHud() { skillDisplay.textContent = heldSkill ? heldSkill.icon : '-'; }

// --- 하트 소멸: 잠깐 정지 + 파괴 연출 ---
function loseHeart() {
  if (Date.now() < invincibleUntil) { spawnSpark('#66ddff'); return; }
  hearts--; renderHearts(); spawnSpark('#ff4d6d');
  isPaused = true; pauseUntil = Date.now() + 1400;
  if (hearts <= 0) pendingGameOver = true;
}
function spawnSpark(color) {
  const cx = player.x+player.width/2, cy = player.y+player.height/2;
  const n = color === '#ff4d6d' ? 12 : 6;
  for (let i=0;i<n;i++){
    const ang = Math.random()*Math.PI*2, spd = 1+Math.random()*3;
    shatterParticles.push({ x:cx, y:cy, vx:Math.cos(ang)*spd, vy:Math.sin(ang)*spd-1, life:40, maxLife:40, size:3+Math.random()*4, color });
  }
}
function updateShatterParticles() {
  for (let i=shatterParticles.length-1;i>=0;i--){
    const p = shatterParticles[i];
    p.x+=p.vx; p.y+=p.vy; p.vy+=0.12; p.life--;
    if (p.life<=0) shatterParticles.splice(i,1);
  }
}

// --- 스킬 카드 ---
function openCardSelect() {
  gameState = 'cardSelect';
  const shuffled = [...skillPool].sort(() => Math.random()-0.5).slice(0,3);
  cardRow.innerHTML = '';
  shuffled.forEach(skill => {
    const el = document.createElement('div');
    el.className = 'skill-card';
    el.innerHTML = `<div class="skill-icon">${skill.icon}</div><div class="skill-name">${skill.name}</div><div class="skill-desc">${skill.desc}</div>`;
    el.addEventListener('click', () => chooseSkill(skill));
    cardRow.appendChild(el);
  });
  cardOverlay.classList.add('show');
}
function chooseSkill(skill) { heldSkill = skill; updateSkillHud(); closeCardSelect(); }
skipCardBtn.addEventListener('click', closeCardSelect);
function closeCardSelect() { cardOverlay.classList.remove('show'); gameState = 'playing'; canvas.focus(); }

function useSkill() {
  if (!heldSkill || gameState !== 'playing') return;
  switch (heldSkill.kind) {
    case 'bomb':
      gold += enemies.length*5; goldDisplay.textContent = gold; enemies.length = 0;
      if (bossActive && boss) { boss.hp -= 15; if (boss.hp <= 0) defeatBoss(); }
      break;
    case 'shield': invincibleUntil = Date.now()+3000; break;
    case 'rapid': rapidUntil = Date.now()+5000; break;
    case 'heal': hearts = Math.min(hearts+1, effectiveMaxHearts()); renderHearts(); break;
    case 'slow': slowUntil = Date.now()+4000; break;
  }
  heldSkill = null; updateSkillHud();
}

// --- 보스 ---
function spawnBoss() {
  bossActive = true; enemies.length = 0; updateKillDisplay();
  const template = bossTemplates[(stage-1) % bossTemplates.length];
  bossBanner.textContent = `⚠ ${template.name} 출현 ⚠`;
  bossBanner.classList.add('show');
  boss = {
    templateId: template.id, name: template.name, color: template.color,
    x: canvas.width/2-60, y: -140, width: 120, height: 90,
    hp: template.baseHp + template.hpPerStage*(stage-1),
    maxHp: template.baseHp + template.hpPerStage*(stage-1),
    speed: template.baseSpeed + template.spdPerStage*(stage-1),
    dir: 1, entering: true, targetY: 55,
    shootTimer: 0, shootInterval: Math.max(template.minShoot, template.baseShoot + template.shootPerStage*(stage-1)),
    hasSkill: template.hasSkill, skillTimer: 0, skillInterval: 240,
    skillState: 'idle', skillStateTimer: 0, shieldActive: false, telegraphX: 0, moveT: 0, dashTimer: 0, dashTarget: undefined
  };
}
function bossShoot() {
  const bx = boss.x+boss.width/2, by = boss.y+boss.height;
  const dx = (player.x+player.width/2)-bx, dy = (player.y+player.height/2)-by;
  const dist = Math.hypot(dx,dy) || 1, spd = 4.5;
  enemyBullets.push({ x:bx-5, y:by-5, width:10, height:10, vx:(dx/dist)*spd, vy:(dy/dist)*spd, color:'#ff5566' });
}
function activateBossSkill(b) {
  if (b.templateId === 'crystal') {
    const bx = b.x+b.width/2, by = b.y+b.height;
    for (let a=-0.6;a<=0.61;a+=0.3) enemyBullets.push({ x:bx-5, y:by-5, width:10, height:10, vx:Math.sin(a)*4.5, vy:Math.cos(a)*4.5, color:'#33ffaa' });
  } else if (b.templateId === 'obsidian') {
    b.shieldActive = true;
  }
}
function updateBossMovement(b) {
  const centerX = canvas.width/2 - b.width/2, range = canvas.width/2 - b.width/2 - 10;
  switch (b.templateId) {
    case 'mothership':
      b.x += b.speed*b.dir*timeFactor;
      if (b.x <= 0 || b.x+b.width >= canvas.width) b.dir *= -1;
      break;
    case 'cruiser':
      b.moveT += 0.015*timeFactor; b.x = centerX + Math.sin(b.moveT)*range;
      break;
    case 'spider':
      b.dashTimer += timeFactor;
      if (b.dashTimer > 70) { b.dashTarget = Math.random()*(canvas.width-b.width); b.dashTimer = 0; }
      if (b.dashTarget !== undefined) b.x += (b.dashTarget-b.x)*0.06*timeFactor;
      break;
    case 'crystal':
      b.moveT += 0.02*timeFactor; b.x = centerX + Math.sin(b.moveT)*range; b.y = b.targetY + Math.sin(b.moveT*2)*18;
      break;
    case 'obsidian':
      b.moveT += 0.012*timeFactor; b.x = centerX + Math.sin(b.moveT)*range*0.7 + Math.sin(b.moveT*3)*range*0.3;
      break;
  }
}
function updateBossSkill(b) {
  if (!b.hasSkill) return;
  if (b.skillState === 'idle') {
    b.skillTimer += timeFactor;
    if (b.skillTimer >= b.skillInterval) {
      b.skillState = 'telegraph'; b.skillStateTimer = 0;
      if (b.templateId === 'spider') b.telegraphX = player.x + player.width/2;
    }
  } else if (b.skillState === 'telegraph') {
    b.skillStateTimer += timeFactor;
    const len = b.templateId === 'spider' ? 55 : 25;
    if (b.skillStateTimer >= len) { activateBossSkill(b); b.skillState = 'active'; b.skillStateTimer = 0; }
  } else if (b.skillState === 'active') {
    b.skillStateTimer += timeFactor;
    const activeLen = b.templateId === 'obsidian' ? 120 : (b.templateId === 'spider' ? 22 : 10);
    if (b.templateId === 'spider' && b.skillStateTimer < 2) {
      if (Math.abs((player.x+player.width/2) - b.telegraphX) < 24) loseHeart();
    }
    if (b.skillStateTimer >= activeLen) {
      if (b.templateId === 'obsidian') b.shieldActive = false;
      b.skillState = 'idle'; b.skillTimer = 0;
    }
  }
}
function defeatBoss() {
  gold += 100 + stage*20; goldDisplay.textContent = gold;
  heartDrops.push({ x: boss.x+boss.width/2-14, y: boss.y+boss.height/2, width:28, height:28, speed:2.5 });

  bossActive = false; boss = null; enemyBullets.length = 0; bossBanner.classList.remove('show');

  stage++; killCount = 0; wingmenCount = stage-1;
  stageDisplay.textContent = stage; updateKillDisplay();

  cardSelectPendingAt = frameCount + 90; // 하트를 받을 시간을 준 뒤 카드 선택 오픈
}

// --- 메인 갱신 ---
function update() {
  timeFactor = (Date.now() < slowUntil) ? 0.5 : 1;

  if ((keys['ArrowLeft']||keys['KeyA']) && player.x>0) player.x -= player.speed;
  if ((keys['ArrowRight']||keys['KeyD']) && player.x+player.width<canvas.width) player.x += player.speed;
  if ((keys['ArrowUp']||keys['KeyW']) && player.y>0) player.y -= player.speed;
  if ((keys['ArrowDown']||keys['KeyS']) && player.y+player.height<canvas.height) player.y += player.speed;

  const curInterval = (Date.now() < rapidUntil) ? player.fireInterval/2 : player.fireInterval;
  if ((keys['Space']||isFiring) && Date.now()-lastShotTime>curInterval) { shootBullet(); lastShotTime = Date.now(); }

  for (let i=bullets.length-1;i>=0;i--){
    const b = bullets[i];
    if (b.vx !== undefined) { b.x+=b.vx; b.y+=b.vy; } else { b.y -= b.speed; }
    if (b.y < -30 || b.y > canvas.height+30 || b.x < -30 || b.x > canvas.width+30) bullets.splice(i,1);
  }

  for (let i=enemies.length-1;i>=0;i--){
    enemies[i].y += enemies[i].speed*timeFactor;
    if (isColliding(enemies[i], player)) { enemies.splice(i,1); loseHeart(); continue; }
    if (enemies[i].y > canvas.height) { enemies.splice(i,1); loseHeart(); }
  }

  for (let i=bullets.length-1;i>=0;i--){
    const b = bullets[i]; let consumed = false;
    for (let j=enemies.length-1;j>=0;j--){
      if (enemies[j] && isColliding(b, enemies[j])) {
        enemies.splice(j,1); gold += 10; goldDisplay.textContent = gold;
        if (!bossActive) { killCount++; updateKillDisplay(); if (killCount >= killsToBoss) spawnBoss(); }
        if (!b.pierce) { consumed = true; break; }
      }
    }
    if (consumed) bullets.splice(i,1);
  }

  if (bossActive && boss) {
    if (boss.entering) {
      boss.y += 2*timeFactor;
      if (boss.y >= boss.targetY) { boss.y = boss.targetY; boss.entering = false; }
    } else {
      updateBossMovement(boss); updateBossSkill(boss);
      boss.shootTimer += timeFactor;
      if (boss.shootTimer >= boss.shootInterval && boss.skillState !== 'telegraph') { bossShoot(); boss.shootTimer = 0; }
    }
    for (let i=bullets.length-1;i>=0;i--){
      if (bullets[i] && isColliding(bullets[i], boss)) {
        const dmg = bullets[i].damage || 1; bullets.splice(i,1);
        if (!boss.shieldActive) { boss.hp -= dmg; if (boss.hp <= 0) { defeatBoss(); break; } }
      }
    }
  }

  for (let i=enemyBullets.length-1;i>=0;i--){
    const eb = enemyBullets[i];
    eb.x += eb.vx*timeFactor; eb.y += eb.vy*timeFactor;
    if (eb.y>canvas.height+20 || eb.y<-20 || eb.x<-20 || eb.x>canvas.width+20) { enemyBullets.splice(i,1); continue; }
    if (isColliding(eb, player)) { enemyBullets.splice(i,1); loseHeart(); }
  }

  for (let i=heartDrops.length-1;i>=0;i--){
    const hd = heartDrops[i]; hd.y += hd.speed;
    if (isColliding(hd, player)) { heartDrops.splice(i,1); hearts = Math.min(hearts+1, effectiveMaxHearts()); renderHearts(); continue; }
    if (hd.y > canvas.height) heartDrops.splice(i,1);
  }
}

// --- 드로잉 ---
function drawStars() {
  stars.forEach(s => {
    const tw = 0.5+0.5*Math.sin(frameCount*s.twinkleSpeed+s.phase);
    ctx.globalAlpha = 0.3+tw*0.5; ctx.fillStyle = '#c9d2ff';
    ctx.beginPath(); ctx.arc(s.x,s.y,s.r,0,Math.PI*2); ctx.fill();
  });
  ctx.globalAlpha = 1;
}
function drawShip(p, isPlayer) {
  const w2=p.width/2, h2=p.height/2;
  ctx.save(); ctx.translate(p.x+w2, p.y+h2);
  const shape = [[0,-1.0],[0.18,-0.4],[0.95,0.15],[0.55,0.35],[0.28,0.25],[0.32,0.85],[0.08,0.6],[0,0.72],[-0.08,0.6],[-0.32,0.85],[-0.28,0.25],[-0.55,0.35],[-0.95,0.15],[-0.18,-0.4]];
  const flicker = 0.6+0.4*Math.sin(frameCount*0.5), flameLen = h2*(0.35+flicker*0.35);
  [-0.08,0.08].forEach(fx => {
    const g = ctx.createLinearGradient(0,h2*0.55,0,h2*0.55+flameLen);
    g.addColorStop(0,'rgba(255,220,120,0.95)'); g.addColorStop(1,'rgba(255,80,40,0)');
    ctx.fillStyle = g; ctx.beginPath();
    ctx.moveTo(fx*p.width-4,h2*0.55); ctx.lineTo(fx*p.width+4,h2*0.55); ctx.lineTo(fx*p.width,h2*0.55+flameLen);
    ctx.closePath(); ctx.fill();
  });
  const bodyGrad = ctx.createLinearGradient(0,-h2,0,h2);
  bodyGrad.addColorStop(0,'#ffffff'); bodyGrad.addColorStop(0.25,p.color); bodyGrad.addColorStop(1,'#05060f');
  ctx.beginPath();
  shape.forEach(([sx,sy],i) => { const px=sx*w2, py=sy*h2; if(i===0) ctx.moveTo(px,py); else ctx.lineTo(px,py); });
  ctx.closePath(); ctx.fillStyle = bodyGrad;
  ctx.shadowColor = p.color; ctx.shadowBlur = isPlayer?10:6; ctx.fill(); ctx.shadowBlur=0;
  ctx.lineWidth=1.2; ctx.strokeStyle='rgba(255,255,255,0.5)'; ctx.stroke();
  ctx.beginPath(); ctx.ellipse(0,-h2*0.15,w2*0.16,h2*0.22,0,0,Math.PI*2);
  const cg = ctx.createRadialGradient(0,-h2*0.25,1,0,-h2*0.15,w2*0.2);
  cg.addColorStop(0,'#ffffff'); cg.addColorStop(1,'#7fdcff'); ctx.fillStyle=cg; ctx.fill();
  ctx.restore();
}
function drawEnemy(e) {
  const w2=e.width/2, h2=e.height/2, bob=Math.sin(frameCount*0.15+e.wobble)*2;
  ctx.save(); ctx.translate(e.x+w2, e.y+h2+bob);
  ctx.beginPath(); ctx.moveTo(0,-h2); ctx.lineTo(w2,0); ctx.lineTo(0,h2); ctx.lineTo(-w2,0); ctx.closePath();
  const g = ctx.createLinearGradient(0,-h2,0,h2); g.addColorStop(0,'#ff8fb3'); g.addColorStop(1,e.color);
  ctx.fillStyle=g; ctx.shadowColor=e.color; ctx.shadowBlur=8; ctx.fill(); ctx.shadowBlur=0;
  ctx.beginPath(); ctx.arc(0,0,w2*0.28,0,Math.PI*2); ctx.fillStyle='#1a0010'; ctx.fill();
  ctx.beginPath(); ctx.arc(0,0,w2*0.14,0,Math.PI*2); ctx.fillStyle='#ffe1ec'; ctx.fill();
  ctx.restore();
}
function drawBullet(b) {
  ctx.save(); ctx.shadowColor=b.color; ctx.shadowBlur=8; ctx.fillStyle=b.color;
  ctx.beginPath(); ctx.moveTo(b.x+b.width/2,b.y); ctx.lineTo(b.x+b.width,b.y+b.height*0.7);
  ctx.lineTo(b.x+b.width/2,b.y+b.height); ctx.lineTo(b.x,b.y+b.height*0.7); ctx.closePath(); ctx.fill();
  ctx.restore();
}
function drawEnemyBullet(b) {
  ctx.save(); ctx.shadowColor=b.color; ctx.shadowBlur=10; ctx.fillStyle=b.color;
  ctx.beginPath(); ctx.arc(b.x+b.width/2,b.y+b.height/2,b.width/2,0,Math.PI*2); ctx.fill(); ctx.restore();
}
function drawHeartDrop(hd) {
  const pulse = 1+0.15*Math.sin(frameCount*0.2);
  ctx.save(); ctx.translate(hd.x+hd.width/2, hd.y+hd.height/2); ctx.scale(pulse,pulse);
  ctx.font='26px sans-serif'; ctx.textAlign='center'; ctx.textBaseline='middle';
  ctx.shadowColor='#ff4d6d'; ctx.shadowBlur=12; ctx.fillText('❤️',0,2);
  ctx.restore();
}
function drawShatterParticles() {
  shatterParticles.forEach(p => {
    const a = Math.max(0,p.life/p.maxLife);
    ctx.save(); ctx.globalAlpha=a; ctx.fillStyle=p.color||'#ff4d6d';
    ctx.beginPath(); ctx.moveTo(p.x,p.y-p.size); ctx.lineTo(p.x+p.size,p.y); ctx.lineTo(p.x,p.y+p.size); ctx.lineTo(p.x-p.size,p.y);
    ctx.closePath(); ctx.fill(); ctx.restore();
  });
}
function roundRectPath(x,y,w,h,r) {
  ctx.beginPath(); ctx.moveTo(x+r,y);
  ctx.arcTo(x+w,y,x+w,y+h,r); ctx.arcTo(x+w,y+h,x,y+h,r); ctx.arcTo(x,y+h,x,y,r); ctx.arcTo(x,y,x+w,y,r);
  ctx.closePath();
}
function drawBoss(b) {
  const cx=b.x+b.width/2, cy=b.y+b.height/2, w2=b.width/2, h2=b.height/2;
  ctx.save(); ctx.translate(cx,cy);

  if (b.templateId === 'mothership') {
    const g = ctx.createRadialGradient(0,-h2*0.2,4,0,0,w2*0.6);
    g.addColorStop(0,'#ff6688'); g.addColorStop(1,'#5a0018');
    ctx.beginPath(); ctx.ellipse(0,0,w2,h2,0,0,Math.PI*2); ctx.fillStyle=g;
    ctx.shadowColor='#ff2255'; ctx.shadowBlur=18; ctx.fill(); ctx.shadowBlur=0;
    ctx.lineWidth=2; ctx.strokeStyle='rgba(255,255,255,0.4)'; ctx.stroke();
    ctx.beginPath(); ctx.ellipse(0,-h2*0.15,w2*0.22,h2*0.22,0,Math.PI,Math.PI*2); ctx.fillStyle='rgba(140,220,255,0.85)'; ctx.fill();
    [-1,1].forEach(s => { ctx.beginPath(); ctx.arc(s*w2*0.28,h2*0.05,6,0,Math.PI*2); ctx.fillStyle='#ffe14d'; ctx.shadowColor='#ffe14d'; ctx.shadowBlur=8; ctx.fill(); ctx.shadowBlur=0; });
  } else if (b.templateId === 'cruiser') {
    ctx.translate(-w2,-h2*0.4);
    const g = ctx.createLinearGradient(0,0,b.width,0);
    g.addColorStop(0,'#5a2a00'); g.addColorStop(0.5,'#ff8800'); g.addColorStop(1,'#5a2a00');
    roundRectPath(0,0,b.width,h2*0.8,14); ctx.fillStyle=g; ctx.shadowColor='#ff8800'; ctx.shadowBlur=16; ctx.fill(); ctx.shadowBlur=0;
    ctx.strokeStyle='rgba(255,255,255,0.4)'; ctx.lineWidth=2; ctx.stroke();
    ctx.translate(w2,h2*0.4);
    [-1,1].forEach(s => { ctx.beginPath(); ctx.arc(s*w2*0.85,0,h2*0.32,0,Math.PI*2); ctx.fillStyle='#ffb84d'; ctx.shadowColor='#ffdd88'; ctx.shadowBlur=10; ctx.fill(); ctx.shadowBlur=0; });
  } else if (b.templateId === 'spider') {
    ctx.strokeStyle=b.color; ctx.lineWidth=4; ctx.lineCap='round';
    [[1,1],[1,-1],[-1,1],[-1,-1]].forEach(([sx,sy]) => {
      ctx.beginPath(); ctx.moveTo(sx*w2*0.3,sy*h2*0.2); ctx.lineTo(sx*w2*1.05,sy*h2*0.95); ctx.stroke();
      ctx.beginPath(); ctx.arc(sx*w2*1.05,sy*h2*0.95,5,0,Math.PI*2); ctx.fillStyle=b.color; ctx.fill();
    });
    ctx.beginPath(); ctx.moveTo(0,-h2*0.55); ctx.lineTo(w2*0.5,0); ctx.lineTo(0,h2*0.55); ctx.lineTo(-w2*0.5,0); ctx.closePath();
    const g2 = ctx.createRadialGradient(0,0,4,0,0,w2*0.5); g2.addColorStop(0,'#e6b3ff'); g2.addColorStop(1,b.color);
    ctx.fillStyle=g2; ctx.shadowColor=b.color; ctx.shadowBlur=14; ctx.fill(); ctx.shadowBlur=0;
  } else if (b.templateId === 'crystal') {
    const pts=[[0,-1],[0.87,-0.5],[0.87,0.5],[0,1],[-0.87,0.5],[-0.87,-0.5]];
    ctx.beginPath();
    pts.forEach(([px,py],i) => { const x=px*w2, y=py*h2; if(i===0) ctx.moveTo(x,y); else ctx.lineTo(x,y); });
    ctx.closePath();
    const g3 = ctx.createLinearGradient(0,-h2,0,h2); g3.addColorStop(0,'#c6fff0'); g3.addColorStop(1,b.color);
    ctx.fillStyle=g3; ctx.shadowColor=b.color; ctx.shadowBlur=16; ctx.fill(); ctx.shadowBlur=0;
    ctx.strokeStyle='rgba(255,255,255,0.5)'; ctx.lineWidth=2; ctx.stroke();
  } else if (b.templateId === 'obsidian') {
    ctx.beginPath(); ctx.ellipse(0,0,w2,h2,0,0,Math.PI*2);
    const g4 = ctx.createRadialGradient(0,-h2*0.2,4,0,0,w2); g4.addColorStop(0,'#6655aa'); g4.addColorStop(1,'#12081f');
    ctx.fillStyle=g4; ctx.shadowColor='#8855ff'; ctx.shadowBlur=20; ctx.fill(); ctx.shadowBlur=0;
    ctx.strokeStyle='rgba(180,140,255,0.6)'; ctx.lineWidth=2; ctx.stroke();
    for (let i=0;i<6;i++){
      const ang=(i/6)*Math.PI*2, sx=Math.cos(ang)*w2, sy=Math.sin(ang)*h2;
      ctx.beginPath(); ctx.moveTo(sx*0.85,sy*0.85); ctx.lineTo(sx*1.2,sy*1.2);
      ctx.lineTo(Math.cos(ang+0.15)*w2*0.85, Math.sin(ang+0.15)*h2*0.85); ctx.closePath();
      ctx.fillStyle='#3d2a66'; ctx.fill();
    }
    if (b.shieldActive) {
      ctx.beginPath(); ctx.ellipse(0,0,w2+14,h2+14,0,0,Math.PI*2);
      ctx.strokeStyle='rgba(120,180,255,0.85)'; ctx.lineWidth=4; ctx.shadowColor='#66aaff'; ctx.shadowBlur=16; ctx.stroke();
      ctx.shadowBlur=0;
    }
  }
  ctx.restore();

  ctx.fillStyle='#ffffff'; ctx.font='11px sans-serif'; ctx.textAlign='left';
  ctx.fillText(b.name, b.x, b.y-26);
  const barW=b.width, barX=b.x, barY=b.y-14;
  ctx.fillStyle='rgba(255,255,255,0.15)'; ctx.fillRect(barX,barY,barW,7);
  const pct = Math.max(0,b.hp/b.maxHp);
  ctx.fillStyle = pct>0.3 ? '#ff2255' : '#ff8844'; ctx.fillRect(barX,barY,barW*pct,7);
  ctx.strokeStyle='rgba(255,255,255,0.4)'; ctx.strokeRect(barX,barY,barW,7);

  if (b.templateId === 'spider' && (b.skillState === 'telegraph' || b.skillState === 'active')) {
    const flashing = b.skillState === 'telegraph';
    ctx.save();
    ctx.globalAlpha = flashing ? (0.3+0.3*Math.sin(frameCount*0.8)) : 0.85;
    ctx.fillStyle = flashing ? '#ff5566' : '#ffdd55';
    ctx.fillRect(b.telegraphX-22, b.y+b.height, 44, canvas.height-(b.y+b.height));
    ctx.restore();
  }
}

function draw() {
  ctx.clearRect(0,0,canvas.width,canvas.height);
  drawStars();
  drawShip(player, true);
  getWingmenPositions().forEach(pos => drawShip({ x:pos.x, y:pos.y, width:player.width*0.72, height:player.height*0.72, color:player.color }, false));
  bullets.forEach(drawBullet);
  enemies.forEach(drawEnemy);
  enemyBullets.forEach(drawEnemyBullet);
  heartDrops.forEach(drawHeartDrop);
  if (bossActive && boss) drawBoss(boss);
  drawShatterParticles();

  if (isPaused) {
    const remain = Math.max(0,(pauseUntil-Date.now())/1400);
    ctx.save(); ctx.globalAlpha = 0.18*remain; ctx.fillStyle = '#ff0033'; ctx.fillRect(0,0,canvas.width,canvas.height); ctx.restore();
  }
}

function triggerGameOver() {
  gameState = 'over'; clearInterval(enemySpawnTimer); bossBanner.classList.remove('show');
  finalStats.textContent = `스테이지 ${stage} · 골드 ${gold}`;
  gameOverOverlay.classList.add('show');
}

function beginRun() {
  gameState = 'playing';
  gold = 0; stage = 1; killCount = 0; hearts = baseMaxHearts;
  bossActive = false; boss = null; wingmenCount = 0; cardSelectPendingAt = null;
  heldSkill = null; invincibleUntil = 0; rapidUntil = 0; slowUntil = 0;
  isPaused = false; pendingGameOver = false;

  bullets.length = 0; enemies.length = 0; enemyBullets.length = 0; heartDrops.length = 0; shatterParticles.length = 0;

  player.x = canvas.width/2-25; player.y = canvas.height-90; player.level = 1;
  player.color = shipUpgrades[0].color; player.speed = shipUpgrades[0].speed;
  player.bulletColor = shipUpgrades[0].bulletColor; player.fireInterval = shipUpgrades[0].fireInterval; player.trait = shipUpgrades[0].trait;

  goldDisplay.textContent = gold; stageDisplay.textContent = stage;
  updateKillDisplay(); renderHearts(); updateSkillHud();
  shopKeyEls.forEach((el,i) => el.classList.toggle('owned', i===0));

  startOverlay.classList.remove('show'); gameOverOverlay.classList.remove('show'); cardOverlay.classList.remove('show'); bossBanner.classList.remove('show');
  canvas.focus(); startEnemySpawner();
}
startBtn.addEventListener('click', beginRun);
restartBtn.addEventListener('click', beginRun);

function gameLoop() {
  frameCount++;
  updateShatterParticles();

  if (gameState === 'playing') {
    if (isPaused) {
      if (Date.now() >= pauseUntil) { isPaused = false; if (pendingGameOver) { pendingGameOver = false; triggerGameOver(); } }
    } else {
      update();
      if (cardSelectPendingAt !== null && frameCount >= cardSelectPendingAt) { cardSelectPendingAt = null; openCardSelect(); }
    }
  }
  draw();
  requestAnimationFrame(gameLoop);
}
gameLoop();
</script>

</body>
</html>
