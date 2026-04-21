<!DOCTYPE html>
<html>
<head>
    <title>Ellipse Coordinate Studio</title>
    <style>
        /* White Mode Theme Variables */
        :root {
            --bg: #ffffff;
            --grid: #e9ecef;
            --axis: #6c757d;
            --text-dark: #212529;
            --accent: #0d6efd;
            --handle-w: #dc3545; /* Red */
            --handle-h: #198754; /* Green */
            --header-bg: #f8f9fa;
            --border: #dee2e6;
        }

        body { margin: 0; background: var(--bg); color: var(--text-dark); font-family: 'Segoe UI', Tahoma, sans-serif; display: flex; flex-direction: column; height: 100vh; overflow: hidden; }
        
        header { background: var(--header-bg); border-bottom: 2px solid var(--border); padding: 15px 30px; display: flex; flex-direction: column; gap: 15px; }
        .top-row { display: flex; justify-content: space-between; align-items: center; }
        .bottom-row { display: flex; justify-content: space-between; align-items: center; }
        
        .data-panel { display: flex; align-items: center; gap: 15px; font-weight: bold; font-family: 'Consolas', monospace; font-size: 0.9rem; }
        .data-point { color: var(--accent); }
        
        canvas { background: var(--bg); cursor: crosshair; touch-action: none; flex-grow: 1; display: block; }
        
        /* Action Buttons */
        .btn-group { display: flex; gap: 8px; }
        .action-btn { background: #e9ecef; color: var(--text-dark); border: 1px solid #ced4da; padding: 6px 14px; font-weight: bold; cursor: pointer; border-radius: 6px; transition: all 0.2s; font-size: 0.9rem; display: flex; align-items: center; justify-content: center;}
        .action-btn:hover { background: #dee2e6; }
        .action-btn.primary { background: var(--accent); color: #fff; border-color: var(--accent); }
        .action-btn.primary:hover { background: #0b5ed7; }
        .action-btn.secondary { background: #6c757d; color: #fff; border-color: #6c757d; }
        .action-btn.secondary:hover { background: #5c636a; }
        .action-btn.success { background: #198754; color: #fff; border-color: #198754; }
        .action-btn.success:hover { background: #157347; }
        
        .copy-btn { font-size: 1.2rem; padding: 6px 10px; }

        /* Equation Formatting CSS */
        .equation-wrapper { display: flex; align-items: center; gap: 8px; }
        .equation-box { font-family: 'Times New Roman', Times, serif; font-size: 1.4rem; background: #fff; padding: 8px 20px; border-radius: 8px; border: 1px solid var(--border); display: flex; align-items: center; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        .fraction { display: inline-flex; flex-direction: column; align-items: center; margin: 0 8px; }
        .numerator { border-bottom: 1.5px solid var(--text-dark); padding: 0 5px; }
        .denominator { padding: 0 5px; }
        .math-sign { margin: 0 5px; font-weight: bold; }
    </style>
</head>
<body>

<header>
    <div class="top-row">
        <div style="font-weight: 800; letter-spacing: 1px; font-size: 1.2rem; color: var(--accent);">ELLIPSE_GEOMETRY_ENGINE <span style="font-size: 0.8rem; color: #6c757d; font-weight: normal;">(Snaps to 1 cm Grid)</span></div>
        <div class="btn-group">
            <button id="btnSave" class="action-btn success">💾 Save Graph</button>
            <button id="btnZoomOut" class="action-btn">➖ Zoom Out</button>
            <button id="btnZoomIn" class="action-btn">➕ Zoom In</button>
            <button id="btnCenter" class="action-btn">🎯 Center</button>
            <button id="btnEllipse" class="action-btn secondary">Make Ellipse</button>
            <button id="btnCircle" class="action-btn primary">Make Circle</button>
        </div>
    </div>
    <div class="bottom-row">
        <div class="data-panel">
            <div>CENTER: (<span id="outX" class="data-point">0</span>, <span id="outY" class="data-point">0</span>) cm</div>
            <div>A (Width): <span id="outA" class="data-point">0</span> cm</div>
            <div>B (Height): <span id="outB" class="data-point">0</span> cm</div>
        </div>
        <div class="equation-wrapper">
            <div id="equation-container" class="equation-box"></div>
            <button id="btnCopy" class="action-btn copy-btn" title="Copy Equation to Clipboard">📋</button>
        </div>
    </div>
</header>

<canvas id="canvas"></canvas>

<script>
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');

// State Variables (Values are now exactly in Centimeters)
let el = { x: 0, y: 0, a: 4, b: 3 }; 
let dragMode = null;
let zoom = 1.0; 
let currentEquationText = ""; // Holds the plain-text string for clipboard

// Standard CSS mapping: 1 inch = 96px, 1 inch = 2.54cm -> 1cm = 37.795px
const PPCM = 37.795; 

function init() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight - document.querySelector('header').offsetHeight;
    render();
}

function updateEquation() {
    const h = el.x;
    const k = -el.y; 
    const aSq = el.a * el.a;
    const bSq = el.b * el.b;

    // 1. Build the HTML visual equation
    const numX_HTML = h === 0 ? `x<sup>2</sup>` : (h > 0 ? `(x - ${h})<sup>2</sup>` : `(x + ${Math.abs(h)})<sup>2</sup>`);
    const numY_HTML = k === 0 ? `y<sup>2</sup>` : (k > 0 ? `(y - ${k})<sup>2</sup>` : `(y + ${Math.abs(k)})<sup>2</sup>`);

    const eqHtml = `
        <div class="fraction">
            <div class="numerator">${numX_HTML}</div>
            <div class="denominator">${aSq}</div>
        </div>
        <div class="math-sign">+</div>
        <div class="fraction">
            <div class="numerator">${numY_HTML}</div>
            <div class="denominator">${bSq}</div>
        </div>
        <div class="math-sign">=</div>
        <div style="margin-left:5px;">1</div>
    `;
    document.getElementById('equation-container').innerHTML = eqHtml;

    // 2. Build the Plain-Text equation for the clipboard
    const numX_Text = h === 0 ? "x^2" : (h > 0 ? `(x - ${h})^2` : `(x + ${Math.abs(h)})^2`);
    const numY_Text = k === 0 ? "y^2" : (k > 0 ? `(y - ${k})^2` : `(y + ${Math.abs(k)})^2`);
    currentEquationText = `${numX_Text} / ${aSq} + ${numY_Text} / ${bSq} = 1`;
}

function render() {
    // Fill background with solid white so saved PNGs aren't transparent
    ctx.fillStyle = "#ffffff";
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    
    const midX = canvas.width / 2;
    const midY = canvas.height / 2;
    const zStep = PPCM * zoom; // Grid square size dynamically scales

    // 1. DRAW GLOBAL GRID
    ctx.strokeStyle = "#e9ecef";
    ctx.lineWidth = 1;
    ctx.beginPath();
    for(let x = midX; x < canvas.width; x += zStep) { ctx.moveTo(x, 0); ctx.lineTo(x, canvas.height); }
    for(let x = midX; x > 0; x -= zStep) { ctx.moveTo(x, 0); ctx.lineTo(x, canvas.height); }
    for(let y = midY; y < canvas.height; y += zStep) { ctx.moveTo(0, y); ctx.lineTo(canvas.width, y); }
    for(let y = midY; y > 0; y -= zStep) { ctx.moveTo(0, y); ctx.lineTo(canvas.width, y); }
    ctx.stroke();

    // 2. DRAW FIXED GLOBAL AXES
    ctx.strokeStyle = "#6c757d";
    ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.moveTo(0, midY); ctx.lineTo(canvas.width, midY); // X-Axis
    ctx.moveTo(midX, 0); ctx.lineTo(midX, canvas.height); // Y-Axis
    ctx.stroke();

    // 3. DRAW AXIS NOTATION (In Centimeters)
    ctx.fillStyle = "#6c757d";
    ctx.font = "12px Arial";
    let unitSpacing = zoom < 0.6 ? 2 : 1; 
    
    for(let i = -50; i <= 50; i += unitSpacing) {
        if(i === 0) continue;
        let px = midX + (i * zStep);
        let py = midY + (i * zStep);
        
        // X labels (1, 2, 3 cm)
        if (px > 0 && px < canvas.width) ctx.fillText(i, px + 5, midY + 16); 
        // Y labels (-1, -2, -3 cm)
        if (py > 0 && py < canvas.height) ctx.fillText(-i, midX + 5, py - 5); 
    }
    // Origin
    ctx.fillStyle = "#0d6efd";
    ctx.fillText("(0,0)", midX + 5, midY + 16);

    // Convert Logical cm to Screen Pixels
    const worldX = midX + (el.x * PPCM * zoom);
    const worldY = midY + (el.y * PPCM * zoom);
    const pxA = el.a * PPCM * zoom;
    const pxB = el.b * PPCM * zoom;

    // 4. DRAW ELLIPSE LOCAL ALIGNMENT
    ctx.strokeStyle = "rgba(108, 117, 125, 0.4)";
    ctx.lineWidth = 1.5;
    ctx.setLineDash([6, 4]);
    ctx.beginPath();
    ctx.moveTo(0, worldY); ctx.lineTo(canvas.width, worldY); 
    ctx.moveTo(worldX, 0); ctx.lineTo(worldX, canvas.height); 
    ctx.stroke();
    ctx.setLineDash([]);

    // 5. DRAW ELLIPSE
    ctx.beginPath();
    ctx.ellipse(worldX, worldY, pxA, pxB, 0, 0, Math.PI * 2);
    ctx.fillStyle = "rgba(13, 110, 253, 0.1)";
    ctx.fill();
    ctx.strokeStyle = "#0d6efd";
    ctx.lineWidth = 3;
    ctx.stroke();

    // 6. HANDLES
    ctx.fillStyle = "#0d6efd"; // Center
    ctx.fillRect(worldX - 7, worldY - 7, 14, 14);
    
    ctx.fillStyle = "#dc3545"; // Width
    ctx.beginPath(); ctx.arc(worldX + pxA, worldY, 9, 0, Math.PI*2); ctx.fill();
    
    ctx.fillStyle = "#198754"; // Height
    ctx.beginPath(); ctx.arc(worldX, worldY - pxB, 9, 0, Math.PI*2); ctx.fill();

    // Output Data stats
    document.getElementById('outX').innerText = el.x;
    document.getElementById('outY').innerText = -el.y;
    document.getElementById('outA').innerText = el.a;
    document.getElementById('outB').innerText = el.b;
    updateEquation();
}

// === BUTTON LOGIC ===

// Copy Equation Button
document.getElementById('btnCopy').addEventListener('click', (e) => {
    navigator.clipboard.writeText(currentEquationText).then(() => {
        // Visual feedback
        const btn = e.target;
        btn.innerText = "✅";
        setTimeout(() => { btn.innerText = "📋"; }, 1500);
    }).catch(err => {
        console.error('Failed to copy: ', err);
    });
});

document.getElementById('btnSave').addEventListener('click', () => {
    const link = document.createElement('a');
    link.download = 'ellipse-graph.png';
    link.href = canvas.toDataURL('image/png');
    link.click();
});

document.getElementById('btnCircle').addEventListener('click', () => {
    const maxRadius = Math.max(el.a, el.b);
    el.a = maxRadius; 
    el.b = maxRadius;
    render();
});

document.getElementById('btnEllipse').addEventListener('click', () => {
    if (el.a === el.b) {
        el.b = Math.max(1, Math.round(el.a * 0.5));
    } else {
        el.a = 4;
        el.b = 2;
    }
    render();
});

document.getElementById('btnCenter').addEventListener('click', () => {
    el.x = 0; el.y = 0;
    render();
});

document.getElementById('btnZoomIn').addEventListener('click', () => {
    zoom = Math.min(3.0, zoom + 0.2); 
    render();
});

document.getElementById('btnZoomOut').addEventListener('click', () => {
    zoom = Math.max(0.4, zoom - 0.2); 
    render();
});

// === MOUSE INTERACTION (Snap perfectly to Grid Intersections) ===
canvas.onmousedown = (e) => {
    const rect = canvas.getBoundingClientRect();
    const mx = e.clientX - rect.left; 
    const my = e.clientY - rect.top;
    
    const wx = (canvas.width/2) + (el.x * PPCM * zoom);
    const wy = (canvas.height/2) + (el.y * PPCM * zoom);
    const pxA = el.a * PPCM * zoom;
    const pxB = el.b * PPCM * zoom;

    // Hit detection (15 pixels leeway)
    if (Math.hypot(mx - (wx + pxA), my - wy) < 15) {
        dragMode = 'a';
    } else if (Math.hypot(mx - wx, my - (wy - pxB)) < 15) {
        dragMode = 'b';
    } else if (Math.hypot(mx - wx, my - wy) < 20) {
        dragMode = 'move';
    }
};

window.onmousemove = (e) => {
    if (!dragMode) return;
    const rect = canvas.getBoundingClientRect();
    const mx = e.clientX - rect.left; 
    const my = e.clientY - rect.top;
    const midX = canvas.width/2; 
    const midY = canvas.height/2;

    if (dragMode === 'move') { 
        // Calculate raw cm from center, and snap EXACTLY to whole numbers
        let rawX = (mx - midX) / (PPCM * zoom); 
        let rawY = (my - midY) / (PPCM * zoom); 
        el.x = Math.round(rawX); 
        el.y = Math.round(rawY); 
    }
    else if (dragMode === 'a') { 
        // Calculate width in cm, snap EXACTLY to whole numbers, minimum 1
        let rawA = Math.abs(((mx - midX) / (PPCM * zoom)) - el.x);
        el.a = Math.max(1, Math.round(rawA)); 
    }
    else if (dragMode === 'b') { 
        // Calculate height in cm, snap EXACTLY to whole numbers, minimum 1
        let rawB = Math.abs(((my - midY) / (PPCM * zoom)) - el.y);
        el.b = Math.max(1, Math.round(rawB)); 
    }
    render();
};

window.onmouseup = () => dragMode = null;
window.onresize = init;

// Initialize
init();
</script>
</body>
</html>
