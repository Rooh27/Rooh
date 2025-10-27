<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
<title>Rooh — Global Style (Wear. Create. Inspire.)</title>
<meta name="description" content="Rooh — modern lifestyle store. Wear. Create. Inspire.">
<meta name="theme-color" content="#7c3aed">
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
<style>
  :root { --brand:#7c3aed; --brand2:#ec4899; --ink:#0f172a; --bg:#fafafa; }
  body { margin:0; font-family: system-ui, -apple-system, Segoe UI, Roboto, Inter, Arial, sans-serif; background:var(--bg); color:var(--ink); }
  header { position:sticky; top:0; z-index:50; background:rgba(255,255,255,.9); backdrop-filter: blur(8px); border-bottom:1px solid #eee; }
  .hero { background: linear-gradient(135deg, var(--brand) 0%, var(--brand2) 100%); color:white; }
  .card { transition:transform .25s ease, box-shadow .25s ease }
  .card:hover { transform: translateY(-2px); box-shadow: 0 10px 24px rgba(0,0,0,.07); }
  .install-btn { position: fixed; right: 12px; bottom: 12px; }
</style>
</head>
<body>
  <header>
    <div class="max-w-7xl mx-auto px-4 py-3 flex items-center gap-3">
      <div class="w-9 h-9 rounded-md bg-purple-600"></div>
      <strong>Rooh</strong>
      <nav class="ml-auto flex items-center gap-3">
        <a href="#products" class="hover:text-purple-600">Products</a>
        <a href="#contact" class="hover:text-purple-600">Contact</a>
        <select id="currency" class="border rounded px-2 py-1">
          <option value="USD">USD $</option>
          <option value="INR">INR ₹</option>
          <option value="EUR">EUR €</option>
          <option value="GBP">GBP £</option>
        </select>
        <button id="openCart" class="bg-gray-900 text-white px-3 py-1.5 rounded">Cart (<span id="count">0</span>)</button>
      </nav>
    </div>
  </header>

  <section class="hero">
    <div class="max-w-7xl mx-auto px-4 py-14 text-center">
      <h1 class="text-3xl md:text-5xl font-extrabold">Wear. Create. Inspire.</h1>
      <p class="opacity-95 mt-2">Global lifestyle picks — dropshipping, print-on-demand & affiliate — in your currency.</p>
      <a href="#products" class="inline-block mt-6 bg-white text-purple-700 font-semibold px-6 py-3 rounded-lg">Shop now</a>
    </div>
  </section>

  <main class="max-w-7xl mx-auto px-4">
    <section id="products" class="py-10">
      <h3 class="text-2xl font-bold mb-6">Featured</h3>
      <div id="grid" class="grid grid-cols-2 md:grid-cols-4 gap-4"></div>
    </section>

    <!-- Cart Drawer -->
    <div id="drawer" class="fixed left-0 right-0 bottom-0 bg-white rounded-t-2xl shadow-2xl transform translate-y-full transition-transform duration-200">
      <div class="p-4 flex justify-between items-center border-b">
        <strong>Order Summary</strong>
        <button id="closeCart" class="bg-gray-800 text-white px-3 py-1 rounded">Close</button>
      </div>
      <div id="clist" class="max-h-64 overflow-auto p-4 space-y-2"></div>
      <div class="p-4 space-y-2">
        <div class="flex justify-between items-center"><span>Country</span>
          <select id="country" class="border rounded px-2 py-1">
            <option value="US">United States</option><option value="IN">India</option><option value="GB">United Kingdom</option>
            <option value="DE">Germany</option><option value="AE">UAE</option><option value="AU">Australia</option><option value="OTHER">Other</option>
          </select>
        </div>
        <div class="flex justify-between"><span>Subtotal</span><span id="sSub">—</span></div>
        <div class="flex justify-between"><span>Tax <em id="tLabel"></em></span><span id="sTax">—</span></div>
        <div class="flex justify-between"><span>Shipping</span><span id="sShip">—</span></div>
        <div class="flex justify-between text-lg font-bold"><span>Total</span><span id="sTotal">—</span></div>
        <button id="checkout" class="w-full bg-purple-600 text-white px-4 py-2 rounded">Pay Securely</button>
        <p class="text-xs text-gray-500">Checkout opens Stripe Payment Pages.</p>
      </div>
    </div>

    <section id="contact" class="py-12">
      <div class="max-w-xl bg-white rounded-xl shadow p-6 mx-auto">
        <h3 class="text-2xl font-bold mb-4">Contact us</h3>
        <p class="text-sm text-gray-600 mb-4">Email: <a class="text-purple-600" href="mailto:rohini27panchal@gmail.com">rohini27panchal@gmail.com</a></p>
        <p class="text-xs text-gray-500">This GitHub Pages version uses a mailto link. (Your full Render site will have a backend contact form.)</p>
      </div>
    </section>
  </main>

  <button id="install" class="install-btn hidden bg-purple-600 text-white px-4 py-2 rounded shadow">Install Rooh App</button>

  <footer class="py-10 text-center text-sm text-gray-500">
    © 2025 Rooh • Global lifestyle brand
  </footer>

<script>
  // ===== PWA manifest + simple offline SW (inline via Blob so Pages can install) =====
  const manifest = {
    name: 'Rooh — Global Style',
    short_name: 'Rooh',
    display: 'standalone',
    start_url: '.',
    background_color: '#ffffff',
    theme_color: '#7c3aed',
    icons: [
      { src: 'data:image/svg+xml;base64,' + btoa("<svg xmlns=\'http://www.w3.org/2000/svg\' viewBox=\'0 0 64 64\'><rect width=\'64\' height=\'64\' rx=\'12\' fill=\'#7c3aed\'/></svg>"), sizes: '192x192', type: 'image/svg+xml' },
      { src: 'data:image/svg+xml;base64,' + btoa("<svg xmlns=\'http://www.w3.org/2000/svg\' viewBox=\'0 0 64 64\'><rect width=\'64\' height=\'64\' rx=\'12\' fill=\'#7c3aed\'/></svg>"), sizes: '512x512', type: 'image/svg+xml' }
    ]
  };
  const mBlob = new Blob([JSON.stringify(manifest)], {type:'application/json'});
  const mURL = URL.createObjectURL(mBlob);
  const mLink = document.createElement('link'); mLink.rel='manifest'; mLink.href=mURL; document.head.appendChild(mLink);

  const swCode = `
    const C='rooh-pages-v1';
    self.addEventListener('install',e=>{self.skipWaiting()});
    self.addEventListener('activate',e=>{e.waitUntil(self.clients.claim())});
    self.addEventListener('fetch',e=>{
      e.respondWith(fetch(e.request).catch(()=>new Response('<!doctype html><title>Rooh</title><body style="font-family:sans-serif;padding:20px"><h1>Rooh</h1><p>Offline.</p>',{headers:{'Content-Type':'text/html'}})));
    });
  `;
  if('serviceWorker' in navigator){
    const swBlob = new Blob([swCode], {type:'text/javascript'});
    const swURL = URL.createObjectURL(swBlob);
    navigator.serviceWorker.register(swURL);
  }

  // ===== Install prompt =====
  let deferredPrompt=null; const installBtn=document.getElementById('install');
  window.addEventListener('beforeinstallprompt', e=>{ e.preventDefault(); deferredPrompt=e; installBtn.classList.remove('hidden'); });
  installBtn.addEventListener('click', async ()=>{ if(!deferredPrompt) return; deferredPrompt.prompt(); await deferredPrompt.userChoice; installBtn.classList.add('hidden'); });

  // ===== Store logic (client-only with Stripe Payment Links) =====
  const grid = document.getElementById('grid');
  const cartItems = document.getElementById('clist');
  const sumSub = document.getElementById('sSub');
  const sumTax = document.getElementById('sTax');
  const sumShip = document.getElementById('sShip');
  const sumTotal = document.getElementById('sTotal');
  const taxLabel = document.getElementById('tLabel');
  const currencySel = document.getElementById('currency');
  const countrySel = document.getElementById('country');
  const SYMBOL = { USD:'$', INR:'₹', EUR:'€', GBP:'£' };
  let FX = { USD:1 };
  let CART = [];
  const PRODUCTS = [
    { id: 1, type:'affiliate', name:'Eco Yoga Mat', desc:'Grippy & eco-friendly', price:24.99, img:'https://images.unsplash.com/photo-1599050751791-5f1f64e56810?q=80&w=800', link:'https://example.com/eco-mat' },
    { id: 2, type:'dropshipping', name:'Canvas Tote (POD)', desc:'Printed on demand', price:19.50, img:'https://images.unsplash.com/photo-1544441893-675973e31985?q=80&w=800', payment_link:'' },
    { id: 3, type:'affiliate', name:'Insulated Bottle', desc:'Keeps drinks cold', price:29.00, img:'https://images.unsplash.com/photo-1602143407151-7111542de6e8?q=80&w=800', link:'https://example.com/bottle' },
    { id: 4, type:'dropshipping', name:'Printed Tee', desc:'Soft cotton tee', price:22.00, img:'https://images.unsplash.com/photo-1512436991641-6745cdb1723f?q=80&w=800', payment_link:'' }
  ];

  (async function init(){
    try {
      const fx = await fetch('https://api.exchangerate.host/latest?base=USD').then(r=>r.json());
      FX = fx.rates || FX;
    } catch {}
    renderProducts();
    updateCart();
  })();

  function fxv(usd){ const cur = currencySel.value || 'USD'; return usd * (FX[cur] || 1); }
  function fmt(usd){ const cur = currencySel.value || 'USD'; return (SYMBOL[cur]||'$') + fxv(usd).toFixed(2); }

  function renderProducts(){
    grid.innerHTML = '';
    PRODUCTS.forEach(p=>{
      const card = document.createElement('article');
      card.className = 'card bg-white rounded-xl p-3 flex flex-col';
      card.innerHTML = `
        <img src="${p.img}" alt="${p.name}" class="w-full h-40 object-cover rounded-lg mb-3">
        <div class="text-xs text-gray-500 mb-1">${'★'.repeat(4)}${'☆'.repeat(1)}</div>
        <h4 class="font-semibold">${p.name}</h4>
        <p class="text-gray-600 text-sm mb-3">${p.desc||''}</p>
        <div class="flex items-center justify-between mt-auto">
          <span class="font-bold">${fmt(p.price)}</span>
          ${p.type==='affiliate'
            ? `<a class="px-3 py-2 text-sm rounded bg-indigo-600 text-white" href="${p.link}" target="_blank" rel="noopener">Buy</a>`
            : `<button class="px-3 py-2 text-sm rounded bg-purple-600 text-white" onclick="add(${p.id})">Add</button>`}
        </div>`;
      grid.appendChild(card);
    });
  }

  function add(id){
    const p = PRODUCTS.find(x=>x.id===id);
    const ex = CART.find(x=>x.id===id);
    if(ex){ ex.qty += 1; } else { CART.push({...p, qty:1}); }
    updateCart();
  }

  function updateCart(){
    const count = CART.reduce((a,b)=>a+b.qty,0);
    document.getElementById('count').textContent = count;

    cartItems.innerHTML = '';
    let sub=0;
    CART.forEach((it,i)=>{
      sub += it.price*it.qty;
      const li = document.createElement('div');
      li.className = 'flex items-center justify-between bg-gray-100 rounded-lg p-3';
      li.innerHTML = `
        <div>
          <div class="font-medium">${it.name}</div>
          <div class="text-xs text-gray-500">${fmt(it.price)} × ${it.qty}</div>
        </div>
        <div class="flex items-center gap-2">
          <button class="px-2 border rounded" onclick="chg(${i},-1)">-</button>
          <span>${it.qty}</span>
          <button class="px-2 border rounded" onclick="chg(${i},1)">+</button>
          <button class="ml-2 text-red-600" onclick="delIndex(${i})">Remove</button>
        </div>`;
      cartItems.appendChild(li);
    });

    const TAX = { IN:{label:'GST 18%',rate:.18}, US:{label:'Sales Tax 0%',rate:0}, GB:{label:'VAT 20%',rate:.20}, DE:{label:'VAT 19%',rate:.19}, AE:{label:'VAT 5%',rate:.05}, AU:{label:'GST 10%',rate:.10}, OTHER:{label:'Tax 0%',rate:0} };
    const SHIP = { IN:0, US:7.5, GB:6.5, DE:6.5, AE:8, AU:9, OTHER:10 };
    const cc = countrySel.value || 'US';
    const tax = (TAX[cc]?.rate||0) * sub;
    const ship = SHIP[cc] || 0;
    const total = sub + tax + ship;

    taxLabel.textContent = '(' + (TAX[cc]?.label||'Tax 0%') + ')';
    sumSub.textContent = fmt(sub);
    sumTax.textContent = fmt(tax);
    sumShip.textContent = fmt(ship);
    sumTotal.textContent = fmt(total);
  }

  function chg(i,d){ CART[i].qty = Math.max(1, CART[i].qty + d); updateCart(); }
  function delIndex(i){ CART.splice(i,1); updateCart(); }

  document.getElementById('checkout').addEventListener('click', ()=>{
    const dropship = CART.filter(i=>i.type==='dropshipping');
    if(dropship.length===0){ alert('Cart has affiliate items only. Use Buy buttons.'); return; }
    for(const it of dropship){
      const p = PRODUCTS.find(x=>x.id===it.id);
      if(!p.payment_link){ alert('Add Stripe Payment Link for '+p.name+' in the code.'); return; }
    }
    for(const it of dropship){
      const p = PRODUCTS.find(x=>x.id===it.id);
      const url = p.payment_link + (p.payment_link.includes('?')?'&':'?') + 'quantity=' + encodeURIComponent(it.qty);
      window.open(url,'_blank');
    }
  });

  // Drawer open/close
  const drawer = document.getElementById('drawer');
  document.getElementById('openCart').addEventListener('click', ()=>drawer.style.transform='translateY(0)');
  document.getElementById('closeCart').addEventListener('click', ()=>drawer.style.transform='translateY(100%)');
  currencySel.addEventListener('change', ()=>{ renderProducts(); updateCart(); });
  countrySel.addEventListener('change', updateCart);
</script>
</body>
</html>