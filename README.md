# repository.1

<!doctype html>
<html>
<head><meta charset="utf-8"/><title>Calculator</title>
<style>
  body{font-family:Arial;display:flex;align-items:center;justify-content:center;height:100vh;background:#f7fafc}
  .calc{width:300px;background:#fff;padding:12px;border-radius:8px;box-shadow:0 8px 24px rgba(0,0,0,0.08)}
  .display{height:48px;background:#111;color:#fff;border-radius:6px;padding:8px;text-align:right;font-size:18px}
  .keys{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-top:8px}
  button{padding:12px;border-radius:6px;border:0;background:#edf2f7}
</style>
</head>
<body>
<div class="calc">
  <div id="display" class="display">0</div>
  <div class="keys">
    <button data-val="7">7</button><button data-val="8">8</button><button data-val="9">9</button><button data-val="/">/</button>
    <button data-val="4">4</button><button data-val="5">5</button><button data-val="6">6</button><button data-val="*">*</button>
    <button data-val="1">1</button><button data-val="2">2</button><button data-val="3">3</button><button data-val="-">-</button>
    <button data-val="0">0</button><button data-val=".">.</button><button id="clear">C</button><button data-val="+">+</button>
    <button id="equals" style="grid-column:span 4;background:#60a5fa;color:white">=</button>
  </div>
</div>
<script>
  const display = document.getElementById('display');
  let expr = '';
  document.querySelectorAll('button[data-val]').forEach(b=>{
    b.onclick = ()=>{ expr += b.dataset.val; update(); };
  });
  document.getElementById('clear').onclick = ()=>{ expr=''; update(); };
  document.getElementById('equals').onclick = ()=>{ try{ expr = String(eval(expr || '0')); update(); }catch(e){ display.textContent='Error'; setTimeout(()=>{expr='';update();},800)} };
  function update(){ display.textContent = expr || '0'; }
</script>
</body>
</html>
