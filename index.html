<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>芽芽的 3D 梦核生存：幻音觉醒</title>
    <!-- 引入 Three.js 核心库 -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        body { margin: 0; overflow: hidden; background-color: #2a2035; touch-action: none; font-family: 'Courier New', monospace; }
        canvas { display: block; width: 100vw; height: 100vh; }
        
        #ui-layer {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none; display: flex; flex-direction: column; justify-content: space-between;
            padding: env(safe-area-inset-top, 20px) 20px 30px 20px; box-sizing: border-box;
            transition: box-shadow 1s ease;
        }

        .top-bar { display: flex; justify-content: space-between; pointer-events: auto; }
        
        .glass-box {
            background: rgba(42, 32, 53, 0.4); backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 12px;
            padding: 10px 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            color: #d8c8e3; font-weight: bold; font-size: 13px; letter-spacing: 1px;
        }
        
        .sanity-bar-bg { 
            width: 120px; height: 6px; background: rgba(0, 0, 0, 0.5); 
            border-radius: 3px; margin-top: 6px; overflow: hidden; border: 1px solid rgba(255,255,255,0.1);
        }
        .sanity-bar-fill { 
            width: 100%; height: 100%; background: linear-gradient(90deg, #d48bb5, #7d96b3); 
            transition: width 0.2s, background 0.5s;
        }
        .sanity-bar-fill.danger { background: linear-gradient(90deg, #c0392b, #e74c3c); }

        .build-menu {
            position: absolute; right: 20px; top: 50%; transform: translateY(-50%);
            display: flex; flex-direction: column; gap: 15px; pointer-events: auto;
        }
        
        .build-btn {
            width: 50px; height: 50px; border-radius: 50%;
            background: rgba(20, 15, 25, 0.5); backdrop-filter: blur(10px);
            border: 2px solid rgba(150, 150, 150, 0.3); 
            display: flex; align-items: center; justify-content: center; font-size: 20px; 
            box-shadow: 0 0 10px rgba(0,0,0,0.5); position: relative; transition: all 0.3s; opacity: 0.5;
        }
        .build-btn.can-build { opacity: 1; transform: scale(1.05); background: rgba(255, 255, 255, 0.1); border-color: rgba(255,255,255,0.5); }
        .build-btn:active { transform: scale(0.85); }
        
        .build-cost {
            position: absolute; bottom: -18px; width: 180%; text-align: center; left: -40%;
            background: rgba(20, 15, 25, 0.85); font-size: 9px; padding: 3px 0; border-radius: 6px;
            color: #d8c8e3; font-weight: bold; letter-spacing: 0.5px;
        }

        .text-frag { color: #ffeaa7; text-shadow: 0 0 5px rgba(255,177,66,0.5); } 
        .text-wood { color: #fd79a8; } 
        .text-hint-day { color: #00cec9; } 
        .text-hint-night { color: #ff0044; text-shadow: 0 0 8px rgba(255,0,68,0.8); } 
        .text-hint-warn { color: #ffb142; }

        #msg-box {
            position: absolute; top: 15%; left: 50%; transform: translateX(-50%);
            color: #e8dcf5; font-size: 14px; letter-spacing: 2px;
            background: rgba(20, 15, 25, 0.7); padding: 8px 20px; border-radius: 20px;
            opacity: 0; transition: opacity 0.5s; pointer-events: none; border: 1px solid rgba(255,255,255,0.1);
        }

        /* 入梦弹窗 */
        #start-screen {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(26, 16, 37, 0.95); display: flex; flex-direction: column;
            align-items: center; justify-content: center; color: #d8c8e3;
            z-index: 200; transition: opacity 0.5s; pointer-events: auto;
        }
        .start-title {
            font-size: 28px; color: #a29bfe; letter-spacing: 6px; font-weight: bold;
            text-shadow: 0 0 15px rgba(162, 155, 254, 0.6); margin-bottom: 20px;
        }
        .start-content {
            background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(162, 155, 254, 0.3);
            padding: 15px; border-radius: 15px; text-align: left; line-height: 1.8; font-size: 12px;
            max-width: 85%; letter-spacing: 1px;
        }
        .start-btn {
            margin-top: 30px; padding: 12px 40px; background: rgba(162, 155, 254, 0.1);
            border: 2px solid #a29bfe; border-radius: 25px; color: #a29bfe; font-family: 'Courier New', monospace;
            font-size: 18px; font-weight: bold; cursor: pointer; transition: all 0.3s;
        }
        .start-btn:active { background: #a29bfe; color: #1a1025; transform: scale(0.95); }

        /* 死亡与胜利屏幕 */
        #game-over {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(10, 5, 15, 0.95); display: flex; flex-direction: column;
            align-items: center; justify-content: center; color: #ff0044; font-size: 24px;
            z-index: 100; opacity: 0; pointer-events: none; transition: opacity 1s; letter-spacing: 5px; text-align: center;
        }
        #game-over.active { opacity: 1; pointer-events: auto; }
        
        #victory-screen {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(255, 255, 255, 0.95); display: flex; flex-direction: column;
            align-items: center; justify-content: center; color: #a29bfe; font-size: 28px;
            z-index: 100; opacity: 0; pointer-events: none; transition: opacity 3s; letter-spacing: 8px; text-align: center;
            font-weight: bold; text-shadow: 0 0 20px #fff;
        }
        #victory-screen.active { opacity: 1; pointer-events: auto; }

        .restart-btn {
            margin-top: 30px; padding: 12px 35px; background: transparent; border: 2px solid currentColor;
            border-radius: 20px; font-size: 16px; font-weight: bold; font-family: 'Courier New', monospace;
            cursor: pointer; transition: all 0.3s;
        }
        .restart-btn:active { background: currentColor; color: #fff; }
    </style>
</head>
<body>

    <div id="start-screen">
        <div class="start-title">梦核边缘</div>
        <div class="start-content">
            ✦ 滑动左侧移动。收集 <span class="text-frag">金色碎片</span> 与木材。<br>
            ✦ <b style="color:#00cec9">📺电视机：阻挡怪物，理智缓慢流失（临时保命）</b><br>
            ✦ <b style="color:#fd79a8">⛺帐篷：阻挡怪物，安全恢复理智（真正据点）</b><br>
            ✦ <b style="color:#ffeaa7">🕸️捕梦网：全自动生产碎片！</b><br>
            ✦ <b style="color:#fff; text-shadow: 0 0 5px #fff;">🚪唤醒之门：终极目标，逃离梦境。</b><br>
            <div style="text-align: center; margin-top:10px; color:#00cec9;">🎧 建议佩戴耳机游玩</div>
        </div>
        <button class="start-btn" onclick="startGame()">入梦</button>
    </div>

    <div id="ui-layer">
        <div class="top-bar">
            <div class="glass-box">
                <div style="margin-bottom: 6px;">✨ 碎片: <span id="frag-count" class="text-frag">0</span></div>
                <div>🪵 木材: <span id="wood-count" class="text-wood">0</span></div>
            </div>
            <div class="glass-box" style="text-align: right;">
                <div id="time-hint" class="text-hint-day" style="font-size: 10px; opacity: 0.8;">白天 (收集)</div>
                <div class="sanity-bar-bg"><div id="sanity-fill" class="sanity-bar-fill"></div></div>
            </div>
        </div>

        <div class="build-menu">
            <!-- 添加了关于建筑分工的 tooltip 暗示 -->
            <div class="build-btn" id="btn-tv" onclick="build('tv')" title="临时阻挡怪物，理智仍会流失">📺<div class="build-cost">10碎</div></div>
            <div class="build-btn" id="btn-tent" onclick="build('tent')" title="安全恢复理智">⛺<div class="build-cost">25碎 15木</div></div>
            <div class="build-btn" id="btn-net" onclick="build('net')" title="自动生产碎片">🕸️<div class="build-cost">40碎 30木</div></div>
            <div class="build-btn" id="btn-door" onclick="build('door')" style="border-color: #fff; box-shadow: 0 0 15px #fff;" title="逃离梦境">🚪<div class="build-cost">100碎 80木</div></div>
        </div>
        
        <div id="msg-box"></div>
    </div>

    <div id="game-over">
        <div>梦境已崩塌。</div>
        <div id="survival-record" style="font-size: 14px; margin-top: 10px; color: #666;"></div>
        <button class="restart-btn" style="color:#6e8a9f" onclick="location.reload()">重新入梦</button>
    </div>

    <div id="victory-screen">
        <div>你醒了。</div>
        <div style="font-size: 14px; margin-top: 20px; color: #666; letter-spacing: 2px;">理智与音乐共存。</div>
        <button class="restart-btn" style="color:#a29bfe; margin-top: 50px;" onclick="location.reload()">再次入睡</button>
    </div>

    <script>
        // --- 0. 游戏核心状态 ---
        const state = {
            gameStarted: false, gameTime: 0, 
            frags: 0, wood: 0, sanity: 100, isDead: false, victory: false,
            safeZones: [], nightCount: 0, isCurrentlyNight: false,
            nets: [], lastFragGenTime: 0 
        };

        // --- 🎵 A. 生成式音频引擎 ---
        const audioEngine = {
            ctx: null, masterGain: null, dayDrone: null, nightDrone: null, nightGain: null,
            init: function() {
                const AudioContext = window.AudioContext || window.webkitAudioContext;
                this.ctx = new AudioContext();
                this.masterGain = this.ctx.createGain();
                this.masterGain.gain.value = 0.5; 
                
                const delay = this.ctx.createDelay();
                delay.delayTime.value = 0.5;
                const feedback = this.ctx.createGain();
                feedback.gain.value = 0.3;
                delay.connect(feedback); feedback.connect(delay);
                this.masterGain.connect(delay); delay.connect(this.ctx.destination);
                this.masterGain.connect(this.ctx.destination);

                this.dayDrone = this.ctx.createOscillator();
                this.dayDrone.type = 'sine'; this.dayDrone.frequency.value = 110; 
                const dayGain = this.ctx.createGain(); dayGain.gain.value = 0.15;
                this.dayDrone.connect(dayGain).connect(this.masterGain); this.dayDrone.start();

                this.nightDrone = this.ctx.createOscillator();
                this.nightDrone.type = 'sawtooth'; this.nightDrone.frequency.value = 55; 
                this.nightGain = this.ctx.createGain(); this.nightGain.gain.value = 0; 
                const filter = this.ctx.createBiquadFilter();
                filter.type = 'lowpass'; filter.frequency.value = 200; 
                this.nightDrone.connect(filter).connect(this.nightGain).connect(this.masterGain);
                this.nightDrone.start();

                setInterval(() => this.playEtherealNote(), 2000);
            },
            playEtherealNote: function() {
                if (!state.gameStarted || state.isDead || state.victory || !this.ctx) return;
                const osc = this.ctx.createOscillator(); const gain = this.ctx.createGain();
                const notes = [220, 246.94, 277.18, 329.63, 369.99, 440, 493.88, 554.37, 659.25];
                osc.frequency.value = notes[Math.floor(Math.random() * notes.length)];
                osc.type = 'sine';
                const now = this.ctx.currentTime;
                gain.gain.setValueAtTime(0, now); gain.gain.linearRampToValueAtTime(0.05 + Math.random()*0.05, now + 1.5); gain.gain.linearRampToValueAtTime(0, now + 5);
                osc.connect(gain).connect(this.masterGain); osc.start(now); osc.stop(now + 5);
            },
            playVictoryChord: function() {
                if (!this.ctx) return;
                this.nightGain.gain.linearRampToValueAtTime(0, this.ctx.currentTime + 2);
                [440, 554.37, 659.25, 880].forEach((freq, idx) => {
                    const osc = this.ctx.createOscillator(); const gain = this.ctx.createGain();
                    osc.frequency.value = freq; osc.type = 'sine'; const now = this.ctx.currentTime;
                    gain.gain.setValueAtTime(0, now); gain.gain.linearRampToValueAtTime(0.1, now + 2 + idx*0.5); 
                    osc.connect(gain).connect(this.masterGain); osc.start(now);
                });
            },
            stopAll: function() {
                if(this.masterGain) this.masterGain.gain.linearRampToValueAtTime(0, this.ctx.currentTime + 2);
            }
        };

        // --- 1. 梦境架构 ---
        const scene = new THREE.Scene();
        const dayColor = new THREE.Color('#c8bce5'); const nightColor = new THREE.Color('#1a1025');
        scene.background = dayColor.clone(); scene.fog = new THREE.FogExp2(dayColor.clone(), 0.025); 

        const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.shadowMap.enabled = true; renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        renderer.toneMapping = THREE.ACESFilmicToneMapping; renderer.toneMappingExposure = 0.9; 
        document.body.appendChild(renderer.domElement);

        const ambientLight = new THREE.AmbientLight('#ffffff', 0.8); scene.add(ambientLight);
        const dirLight = new THREE.DirectionalLight('#ffe0ec', 0.8);
        dirLight.position.set(20, 50, -20); dirLight.castShadow = true;
        dirLight.shadow.mapSize.width = 1024; dirLight.shadow.mapSize.height = 1024;
        dirLight.shadow.camera.near = 0.5; dirLight.shadow.camera.far = 100;
        const d = 40; dirLight.shadow.camera.left = -d; dirLight.shadow.camera.right = d; dirLight.shadow.camera.top = d; dirLight.shadow.camera.bottom = -d;
        scene.add(dirLight);

        function createCheckerBoard() {
            const canvas = document.createElement('canvas'); canvas.width = 512; canvas.height = 512; const ctx = canvas.getContext('2d');
            ctx.fillStyle = '#b6a6d3'; ctx.fillRect(0, 0, 512, 512); ctx.fillStyle = '#c5b6e0'; ctx.fillRect(0, 0, 256, 256); ctx.fillRect(256, 256, 256, 256);
            return new THREE.CanvasTexture(canvas);
        }
        const groundTex = createCheckerBoard(); groundTex.wrapS = THREE.RepeatWrapping; groundTex.wrapT = THREE.RepeatWrapping; groundTex.repeat.set(100, 100); 
        const ground = new THREE.Mesh(new THREE.PlaneGeometry(500, 500), new THREE.MeshStandardMaterial({ map: groundTex, roughness: 0.4, metalness: 0.1 }));
        ground.rotation.x = -Math.PI / 2; ground.receiveShadow = true; scene.add(ground);

        // --- 2. 玩家烟雾 ---
        const playerGroup = new THREE.Group(); playerGroup.position.y = 0; scene.add(playerGroup);
        const playerLight = new THREE.PointLight('#ffb3d9', 1.5, 15); playerLight.position.set(0, 1, 0); playerGroup.add(playerLight);
        const smokeParticles = [];
        const smokeGeo = new THREE.SphereGeometry(0.4, 8, 8); const smokeMat = new THREE.MeshBasicMaterial({ color: '#ffffff', transparent: true, opacity: 0.4, blending: THREE.AdditiveBlending });
        for(let i=0; i<15; i++) {
            const particle = new THREE.Mesh(smokeGeo, smokeMat);
            particle.userData = { yOffset: Math.random() * 2, speed: 0.02 + Math.random() * 0.02, angle: Math.random() * Math.PI * 2, radius: Math.random() * 0.3 };
            playerGroup.add(particle); smokeParticles.push(particle);
        }

        const eyeTrees = [];
        for(let i=0; i<35; i++) {
            const treeGroup = new THREE.Group();
            const trunkMat = new THREE.MeshStandardMaterial({ color: '#e0d5dd', roughness: 0.2, transparent: true, opacity: 0.35, depthWrite: false });
            const trunk = new THREE.Mesh(new THREE.CylinderGeometry(0.3, 0.5, 5, 8), trunkMat); trunk.position.y = 2.5; treeGroup.add(trunk);
            const eyeGroup = new THREE.Group(); eyeGroup.position.y = 4.5; 
            const sclera = new THREE.Mesh(new THREE.SphereGeometry(0.8, 16, 16), new THREE.MeshStandardMaterial({ color: '#fff9c4' })); eyeGroup.add(sclera);
            const pupil = new THREE.Mesh(new THREE.SphereGeometry(0.35, 16, 16), new THREE.MeshStandardMaterial({ color: '#111', emissive: '#4d0000', emissiveIntensity: 2 }));
            pupil.position.z = 0.6; pupil.scale.set(1, 1.5, 0.4); eyeGroup.add(pupil); treeGroup.add(eyeGroup);
            const r = 10 + Math.random() * 70; const theta = Math.random() * Math.PI * 2;
            treeGroup.position.set(r * Math.cos(theta), 0, r * Math.sin(theta)); scene.add(treeGroup); eyeTrees.push({ group: eyeGroup, pupil: pupil }); 
        }

        // --- 3. 资源生成逻辑 ---
        const floatingResources = [];
        function spawnResource(type, x, z) {
            let mesh;
            if (type === 'frag') {
                mesh = new THREE.Mesh(new THREE.OctahedronGeometry(0.45), new THREE.MeshStandardMaterial({ color: '#ffeaa7', emissive: '#ffb142', emissiveIntensity: 0.8, transparent: true, opacity: 0.9, roughness: 0.1 }));
                mesh.userData = { type: 'frag', baseY: 0.8, offset: Math.random()*Math.PI*2 };
            } else {
                mesh = new THREE.Mesh(new THREE.CylinderGeometry(0.12, 0.25, 1.5, 5), new THREE.MeshStandardMaterial({ color: '#fd79a8', emissive: '#6c5ce7', emissiveIntensity: 0.3, roughness: 0.5 }));
                mesh.rotation.set(Math.random()*Math.PI, Math.random()*Math.PI, Math.random()*Math.PI);
                mesh.userData = { type: 'wood', baseY: 0.8, offset: Math.random()*Math.PI*2 };
            }
            mesh.position.set(x, 0.8, z); mesh.castShadow = true; scene.add(mesh); floatingResources.push(mesh);
        }
        for(let i=0; i<150; i++) spawnResource('frag', (Math.random()-0.5)*140, (Math.random()-0.5)*140);
        for(let i=0; i<80; i++) spawnResource('wood', (Math.random()-0.5)*140, (Math.random()-0.5)*140);

        // --- 4. 庇护所工厂 (引入 Type 分化) ---
        const staticTexCanvas = document.createElement('canvas'); staticTexCanvas.width = 128; staticTexCanvas.height = 128;
        const staticCtx = staticTexCanvas.getContext('2d'); const staticTex = new THREE.CanvasTexture(staticTexCanvas);
        function updateStatic() {
            const imgData = staticCtx.createImageData(128, 128);
            for (let i=0; i<imgData.data.length; i+=4) { const v=Math.random()*255; imgData.data[i]=imgData.data[i+1]=imgData.data[i+2]=v; imgData.data[i+3]=255; }
            staticCtx.putImageData(imgData, 0, 0); staticTex.needsUpdate = true;
        }
        function createGlowTex(colorRGB) {
            const canvas = document.createElement('canvas'); canvas.width=128; canvas.height=128; const ctx=canvas.getContext('2d');
            const grd = ctx.createRadialGradient(64,64,0,64,64,64); grd.addColorStop(0, `rgba(${colorRGB}, 0.8)`); grd.addColorStop(0.4, `rgba(${colorRGB}, 0.3)`); grd.addColorStop(1, `rgba(${colorRGB}, 0)`);
            ctx.fillStyle=grd; ctx.fillRect(0,0,128,128); return new THREE.CanvasTexture(canvas);
        }
        const tvGlowTex = createGlowTex('0, 206, 201'); 
        const tentGlowTex = createGlowTex('255, 158, 205');

        function createTV(x, z) {
            const group = new THREE.Group();
            const shell = new THREE.Mesh(new THREE.BoxGeometry(2.5, 2, 1.5), new THREE.MeshStandardMaterial({ color: '#2d3436' })); shell.position.y=2.5; shell.castShadow=true; group.add(shell);
            const screen = new THREE.Mesh(new THREE.PlaneGeometry(2, 1.5), new THREE.MeshBasicMaterial({ map: staticTex })); screen.position.set(0,2.5,0.76); group.add(screen);
            const light = new THREE.PointLight('#00cec9', 5, 30); light.position.set(0,2.5,1); group.add(light);
            const aura = new THREE.Sprite(new THREE.SpriteMaterial({ map: tvGlowTex, color: '#00cec9',
