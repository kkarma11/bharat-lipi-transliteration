<!doctype html>

<html lang="en">

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width,initial-scale=1" />

<title>Bharat Signboard Transliterations — Prototype</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700\\\&display=swap" rel="stylesheet">

<style>

\&nbsp; :root{

\&nbsp;   --bg:#0f1724; --card:#0b1220; --muted:#93a0b6; --accent:#7c3aed; --glass: rgba(255,255,255,0.03);

\&nbsp;   color-scheme: dark;

\&nbsp; }

\&nbsp; \\\*{box-sizing:border-box}

\&nbsp; body{

\&nbsp;   margin:0; font-family:Inter, system-ui, Arial; background:

\&nbsp;   radial-gradient(1000px 400px at 10% 10%, rgba(124,58,237,0.08), transparent 8%),

\&nbsp;   linear-gradient(180deg,#051229 0%, #071424 100%);

\&nbsp;   color:#e6eef8; -webkit-font-smoothing:antialiased; -moz-osx-font-smoothing:grayscale;

\&nbsp;   padding:28px;

\&nbsp; }

\&nbsp; header{display:flex;align-items:center;gap:18px;margin-bottom:18px}

\&nbsp; header h1{font-size:20px;margin:0}

\&nbsp; header p{margin:0;color:var(--muted);font-size:13px}

\&nbsp; .wrap{display:grid;grid-template-columns:1fr 420px;gap:18px;align-items:start}

\&nbsp; .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); padding:16px;border-radius:12px;box-shadow: 0 6px 24px rgba(2,6,23,0.6); border:1px solid rgba(255,255,255,0.03)}

\&nbsp; .left{min-height:520px}

\&nbsp; textarea{width:100%;min-height:200px;background:transparent;border:1px dashed rgba(255,255,255,0.06);padding:12px;border-radius:8px;color:inherit;font-size:16px;resize:vertical}

\&nbsp; .controls{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px;align-items:center}

\&nbsp; select, button, input\\\[type=file]{padding:10px 12px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:var(--glass);color:inherit;font-size:14px}

\&nbsp; button.primary{background:linear-gradient(90deg,var(--accent),#5b21b6);border:none;color:white;font-weight:600}

\&nbsp; .small{font-size:13px;color:var(--muted)}

\&nbsp; .right img{max-width:100%;border-radius:8px;margin-bottom:8px}

\&nbsp; .preview{background:rgba(255,255,255,0.02);padding:12px;border-radius:8px;min-height:120px;white-space:pre-wrap;font-size:18px}

\&nbsp; .row{display:flex;gap:8px;align-items:center;margin-top:10px}

\&nbsp; .meta{display:flex;gap:8px;flex-direction:column;margin-top:10px}

\&nbsp; .actions{display:flex;gap:8px;margin-top:10px}

\&nbsp; .hint{font-size:13px;color:var(--muted);margin-top:8px}

\&nbsp; footer{margin-top:18px;color:var(--muted);font-size:13px}

\&nbsp; .result-block{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:12px}

\&nbsp; .result-card{background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);padding:12px;border-radius:8px;font-size:18px;min-height:120px;white-space:pre-wrap}

\&nbsp; .badge{font-size:12px;padding:6px 8px;border-radius:999px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03)}

\&nbsp; .status{font-size:13px;color:var(--muted)}

\&nbsp; .topbar{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:12px}

\&nbsp; .logo{display:flex;gap:8px;align-items:center}

\&nbsp; .logo .dot{width:36px;height:36px;border-radius:9px;background:linear-gradient(180deg,#9f7aea,#6d28d9);display:flex;align-items:center;justify-content:center;font-weight:700;color:white}

\&nbsp; @media (max-width:960px){

\&nbsp;   .wrap{grid-template-columns:1fr}

\&nbsp;   .right{order:-1}

\&nbsp; }


</head>

<body>

  <header>

    <div class="logo">

      <div class="dot">BT</div>

      <div>

        <h1>Bharat Translit — Signboard Transliterations</h1>

        <p>Transliterate (phonetic rendering) signboards between Indian scripts — prototype</p>

      </div>

    </div>

  </header>



  <main class="wrap">

    <section class="card left">

      <div class="topbar">

        <div>

          <div class="badge">Prototype • Transliteration (not translation)</div>

        </div>

        <div class="status" id="status">Ready</div>

      </div>



      <label class="small">Paste signboard text here (or OCR from image):</label>

      <textarea id="sourceText" placeholder="e.g. హైదరాబాదు రోడ్ (or paste any script)"></textarea>



      <div class="controls">

        <select id="sourceScript">

          <option value="auto">Detect script (auto)</option>

          <option value="devanagari">Devanagari (हिन्दी/Marathi)</option>

          <option value="bengali">Bengali (বাংলা)</option>

          <option value="gurmukhi">Gurmukhi (ਪੰਜਾਬੀ)</option>

          <option value="gujarati">Gujarati (ગુજરાતી)</option>

          <option value="oriya">Odia (ଓଡ଼ିଆ)</option>

          <option value="tamil">Tamil (தமிழ்)</option>

          <option value="telugu">Telugu (తెలుగు)</option>

          <option value="kannada">Kannada (ಕನ್ನಡ)</option>

          <option value="malayalam">Malayalam (മലയാളം)</option>

          <option value="latin">Latin (transliteration target)</option>

        </select>



        <select id="targetScript">

          <option value="devanagari">Devanagari (हिन्दी)</option>

          <option value="gurmukhi">Gurmukhi (ਪੰਜਾਬੀ)</option>

          <option value="telugu">Telugu (తెలుగు)</option>

          <option value="malayalam">Malayalam (മലയാളം)</option>

          <option value="tamil">Tamil (தமிழ்)</option>

          <option value="kannada">Kannada (ಕನ್ನಡ)</option>

          <option value="bengali">Bengali (বাংলা)</option>

          <option value="oriya">Odia (ଓଡ଼ିଆ)</option>

          <option value="gujarati">Gujarati (ગુજરાતી)</option>

          <option value="latin">Latin (ITRANS-like)</option>

        </select>



        <button class="primary" id="transliterateBtn">Transliterate</button>



        <label style="display:flex;align-items:center;gap:8px;">

          <input type="file" id="imageInput" accept="image/\\\*" style="display:none">

          <button id="uploadBtn">Upload Image (OCR)</button>

        </label>



        <button id="clearBtn">Clear</button>

      </div>



      <div class="hint">Tip: For travelling users, select source script as "auto" and choose the target script you can read (e.g., Gurmukhi → Devanagari).</div>



      <div class="result-block" aria-live="polite">

        <div class="result-card" id="origBox"><strong>Original</strong><hr id="hr1"><div id="origText" style="margin-top:8px" class="preview">—</div></div>

        <div class="result-card" id="transBox"><strong>Transliteration</strong><hr id="hr2"><div id="transText" style="margin-top:8px" class="preview">—</div></div>

      </div>



      <div class="actions">

        <button id="copyBtn">Copy Transliteration</button>

        <button id="downloadBtn">Download as TXT</button>

      </div>



      <div class="meta">

        <div class="small">OCR \& Transliteration processing is done in your browser. For best OCR results use clear photos of large, horizontal sign text.</div>

        <div class="small">This prototype uses open-source client libraries for OCR and transliteration. For production-level coverage of all Indic glyph edge-cases, integrate Aksharamukha or a server transliteration service.</div>

      </div>

    </section>



    <aside class="card right">

      <div><strong>Preview / Photo</strong></div>

      <div style="margin-top:8px">

        <img id="previewImage" alt="preview" src="" style="display:none">

        <div class="small" id="ocrProgress">No image uploaded.</div>

      </div>



      <div style="margin-top:14px">

        <strong>Example inputs</strong>

        <div class="hint" style="margin-top:8px">

          Try these examples:

          <ul style="margin:6px 0 0 18px;color:var(--muted)">

            <li>హైదరాబాద్ → Telugu sample</li>

            <li>ਹੈਦਰਾਬਾਦ → Gurmukhi sample</li>

            <li>பெருந்துறை → Tamil sample</li>

            <li>दोपहर रोटी दुकान → Devanagari sample</li>

          </ul>

        </div>

      </div>



      <hr style="margin:12px 0;border:none;border-top:1px solid rgba(255,255,255,0.03)">



      <div>

        <strong>About</strong>

        <p class="small" style="margin-top:6px">Bharat Translit demonstrates the core flow: OCR → script detection/selection → transliteration phonetics. It preserves phonetics (not meaning).</p>

      </div>



      <div style="margin-top:10px">

        <strong>Limitations</strong>

        <ul class="small" style="margin:6px 0 0 18px;color:var(--muted)">

          <li>OCR accuracy depends on photo quality and font.</li>

          <li>Transliteration quality depends on library rules and script-specific conventions.</li>

          <li>Compound/vowel-marker edge cases may require server-side mapping or a more complete library.</li>

        </ul>

      </div>



      <footer>

        <div>Prototype • Not for safety-critical use • Built for demonstration</div>

      </footer>

    </aside>

  </main>



  <!-- CDN: Tesseract.js for OCR -->

  <script src="https://unpkg.com/tesseract.js@2.1.5/dist/tesseract.min.js"></script>



  <!-- CDN: Sanscript (Indic transliteration). If CDN is unavailable, fallback message will show. -->

  <script src="https://unpkg.com/sanscript@1.0.0/sanscript.min.js"></script>



  <script>

  // All logic is client-side. No server required.

  (function(){

    const sourceTextEl = document.getElementById('sourceText');

    const sourceSelect = document.getElementById('sourceScript');

    const targetSelect = document.getElementById('targetScript');

    const transliterateBtn = document.getElementById('transliterateBtn');

    const origTextEl = document.getElementById('origText');

    const transTextEl = document.getElementById('transText');

    const statusEl = document.getElementById('status');

    const copyBtn = document.getElementById('copyBtn');

    const downloadBtn = document.getElementById('downloadBtn');

    const clearBtn = document.getElementById('clearBtn');

    const uploadBtn = document.getElementById('uploadBtn');

    const imageInput = document.getElementById('imageInput');

    const previewImage = document.getElementById('previewImage');

    const ocrProgress = document.getElementById('ocrProgress');



    // check availability of Sanscript

    const hasSanscript = typeof Sanscript !== 'undefined' \&\& typeof Sanscript.t !== 'undefined';

    if(!hasSanscript){

      alert('Warning: transliteration library failed to load. Transliteration actions may not work. You can still OCR text.');

      console.warn('Sanscript not loaded — transliteration will be disabled.');

    }



    // mapping for Sanscript script codes -> Sanscript scheme names

    // Sanscript scheme names: 'devanagari','iast','hk','itrans', etc.

    const schemeMap = {

      devanagari: 'devanagari',

      gurmukhi: 'gurmukhi',

      bengali: 'bengali',

      gujarati: 'gujarati',

      oriya: 'oriya',

      tamil: 'tamil',

      telugu: 'telugu',

      kannada: 'kannada',

      malayalam: 'malayalam',

      latin: 'itrans' // use ITRANS-like Latin fallback

    };



    function setStatus(msg){

      statusEl.textContent = msg;

    }



    // Simple auto-detect script: check Unicode ranges heuristically

    function detectScript(text){

      if(!text) return 'unknown';

      // check for Telugu

      if(/\[\\u0C00-\\u0C7F]/.test(text)) return 'telugu';

      if(/\[\\u0C80-\\u0CFF]/.test(text)) return 'malayalam';

      if(/\[\\u0B80-\\u0BFF]/.test(text)) return 'oriya';

      if(/\[\\u0B00-\\u0B7F]/.test(text)) return 'bengali';

      if(/\[\\u0A00-\\u0A7F]/.test(text)) return 'gurmukhi';

      if(/\[\\u0A80-\\u0AFF]/.test(text)) return 'gujarati';

      if(/\[\\u0B80-\\u0BFF]/.test(text)) return 'tamil'; // overlap caution

      if(/\[\\u0900-\\u097F]/.test(text)) return 'devanagari';

      if(/\[\\u0C80-\\u0CFF]/.test(text)) return 'telugu';

      // fallback latin

      if(/^\[\\u0000-\\u007F\\s0-9,.-:\\/]+$/.test(text)) return 'latin';

      return 'devanagari';

    }



    // Transliterate using Sanscript if available. If not, return same string with note.

    function transliterateText(text, fromScript, toScript){

      if(!text) return '';

      if(!hasSanscript){

        return text + '\\n\\n\[Transliteration library not loaded — showing original]';

      }

      const fromScheme = schemeMap\[fromScript] || 'devanagari';

      const toScheme = schemeMap\[toScript] || 'devanagari';

      try{

        return Sanscript.t(text, fromScheme, toScheme);

      }catch(e){

        console.error('Transliteration error', e);

        return text + '\\n\\n\[Transliteration failed: ' + (e.message || 'error') + ']';

      }

    }



    // basic OCR using Tesseract.js

    async function doOCR(file){

      ocrProgress.textContent = 'OCR: initializing...';

      previewImage.style.display = 'none';

      const worker = Tesseract.createWorker({

        logger: m => {

          if(m.status \&\& m.progress !== undefined){

            const pct = Math.round(m.progress \* 100);

            ocrProgress.textContent = `OCR: ${m.status} ${pct}%`;

          } else {

            ocrProgress.textContent = `OCR: ${m.status || JSON.stringify(m)}`;

          }

        }

      });

      await worker.load();

      await worker.loadLanguage('eng+hin+tel+tam+kan+mal+pan+ben');

      await worker.initialize('eng+hin+tel+tam+kan+mal+pan+ben');

      ocrProgress.textContent = 'OCR: recognizing...';

      const { data } = await worker.recognize(file);

      await worker.terminate();

      ocrProgress.textContent = 'OCR: done';

      return data \&\& data.text ? data.text.trim() : '';

    }



    // Image upload flow

    uploadBtn.addEventListener('click', (e)=>{

      imageInput.click();

    });



    imageInput.addEventListener('change', async (ev)=>{

      const f = ev.target.files \&\& ev.target.files\[0];

      if(!f) return;

      // preview

      const url = URL.createObjectURL(f);

      previewImage.src = url;

      previewImage.style.display = 'block';

      // OCR

      try{

        setStatus('Running OCR...');

        const text = await doOCR(f);

        if(text){

          sourceTextEl.value = text;

          origTextEl.textContent = text;

        } else {

          sourceTextEl.value = '';

          origTextEl.textContent = '\[No text found]';

        }

        setStatus('OCR complete');

      }catch(err){

        console.error(err);

        ocrProgress.textContent = 'OCR failed: ' + (err.message || err);

        setStatus('OCR failed');

      }

    });



    // Transliterate button

    transliterateBtn.addEventListener('click', ()=>{

      const input = sourceTextEl.value.trim();

      if(!input){

        alert('Please paste text or upload an image with sign text first.');

        return;

      }

      setStatus('Transliterating...');

      origTextEl.textContent = input;



      // Determine source script

      let sourceScript = sourceSelect.value;

      if(sourceScript === 'auto'){

        sourceScript = detectScript(input);

      }

      const targetScript = targetSelect.value;



      // do transliteration

      const out = transliterateText(input, sourceScript, targetScript);

      transTextEl.textContent = out;

      setStatus('Done');

    });



    // Also auto transliterate on paste or change

    sourceTextEl.addEventListener('input', ()=>{

      const text = sourceTextEl.value.trim();

      origTextEl.textContent = text || '—';

    });



    // Copy transliteration

    copyBtn.addEventListener('click', async ()=>{

      const txt = transTextEl.textContent || '';

      try{

        await navigator.clipboard.writeText(txt);

        setStatus('Copied to clipboard');

      }catch(e){

        alert('Copy failed — please select and copy manually.');

      }

    });



    // Download transliteration

    downloadBtn.addEventListener('click', ()=>{

      const txt = transTextEl.textContent || '';

      const blob = new Blob(\[txt], {type:'text/plain;charset=utf-8'});

      const a = document.createElement('a');

      a.href = URL.createObjectURL(blob);

      a.download = 'transliteration.txt';

      document.body.appendChild(a);

      a.click();

      a.remove();

      setStatus('Downloaded');

    });



    // Clear

    clearBtn.addEventListener('click', ()=>{

      sourceTextEl.value = '';

      origTextEl.textContent = '—';

      transTextEl.textContent = '—';

      previewImage.style.display = 'none';

      ocrProgress.textContent = 'No image uploaded.';

      setStatus('Ready');

    });



    // initialize sample example

    sourceTextEl.value = 'హైదరాబాద్ రోడ్\\nపార్కింగ్ 200 మీటర్లు';

    origTextEl.textContent = sourceTextEl.value;

    transTextEl.textContent = '—';

    setStatus('Ready');



    // accessibility: keyboard enter on transliterate

    sourceTextEl.addEventListener('keydown', (e)=>{

      if((e.ctrlKey || e.metaKey) \&\& e.key === 'Enter'){

        transliterateBtn.click();

      }

    });

  })();

  </script>

</body>

</html>

