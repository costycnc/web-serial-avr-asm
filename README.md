Web Serial API + AVR Assembly Control 🔌
This project demonstrates how to bridge the gap between a modern web browser and low-level hardware. You can control an Arduino (ATmega328P) directly from a webpage using the Web Serial API, without any intermediate server or software.

🚀 What's Inside
Frontend: HTML5 and JavaScript implementation of the Web Serial API.

Backend (Firmware): High-performance AVR Assembly (ASM) code for UART communication and LED control.

Direct Register Access: Learn how to manipulate UDR0, UBRR0, and PORTB for maximum efficiency.

💻 Core Logic
JavaScript (Browser Side)
The core logic to connect and handle the serial stream:

JavaScript
// 🔌 CONNECT AND READ
async function connect() {
  port = await navigator.serial.requestPort();
  await port.open({ baudRate: 115200 });
  
  writer = port.writable.getWriter();
  reader = port.readable.getReader();

  while (keepReading) {
    const { value, done } = await reader.read();
    if (done) break;
    let text = new TextDecoder().decode(value);
    console.log(&quot;From Arduino:&quot;, text);
  }
}
AVR Assembly (Hardware Side)
A snippet of how the ATmega328P handles incoming bytes:

Snippet di codice
; 📥 RECEIVE BYTE (ASM)
USART_Receive:
    lds r16, UCSR0A           ; Load Status Register
    sbrs r16, RXC0            ; Skip if Receive Complete flag is set
    rjmp USART_Receive        ; Wait for data
    lds r16, UDR0             ; Get byte from Data Register
    ret
📖 Live Documentation
You can read the full step-by-step tutorial in two languages:

🇺🇸 English Version (Mirror)

🇮🇹 Versione Italiana (Mirror)

🔗 Official Project Page
For the complete guide, more CNC projects, and advanced AVR tutorials, visit my official website:
👉 costycnc.it - Web Serial API Guide

🛠️ How to Test
Connect your Arduino to a USB port.

Open the Live Demo.

Click "Connect", select your COM port, and start sending commands!

Developed by CostyCNC. Dedicated to high-precision hardware control.


<div _ngcontent-ng-c3856422327="" inline-copy-host="" class="markdown markdown-main-panel enable-updated-hr-color" id="model-response-message-contentr_d51f14ce244ef736" aria-live="polite" aria-busy="false" dir="ltr" style="--animation-duration: 400ms; --fade-animation-function: linear;"><p data-path-to-node="0">Ho capito perfettamente il problema: quando il mio sistema chiude il blocco di codice JavaScript con i tre backtick (```), "rompe" il resto del documento perché GitHub pensa che il README sia finito lì o si confonde con i blocchi successivi.</p><p data-path-to-node="1">Per risolvere questo fastidio tecnico, ecco il trucco: ti incollo il testo <b data-path-to-node="1" data-index-in-node="75">senza usare i blocchi di codice della chat</b>, ma usando una separazione chiara.</p><h3 data-path-to-node="2">Istruzioni per un copia-incolla perfetto:</h3><p data-path-to-node="3">Copia tutto quello che c'è tra le due linee tratteggiate qui sotto.</p><hr data-path-to-node="4"><h1 data-path-to-node="5">Web Serial API + AVR Assembly Control 🔌</h1><p data-path-to-node="6">This project demonstrates how to bridge the gap between a modern web browser and low-level hardware. You can control an Arduino (ATmega328P) directly from a webpage using the <b data-path-to-node="6" data-index-in-node="175">Web Serial API</b>, without any intermediate server or software.</p><h2 data-path-to-node="7">🚀 What's Inside</h2><ul data-path-to-node="8"><li><p data-path-to-node="8,0,0"><b data-path-to-node="8,0,0" data-index-in-node="0">Frontend:</b> HTML5 and JavaScript implementation of the Web Serial API.</p></li><li><p data-path-to-node="8,1,0"><b data-path-to-node="8,1,0" data-index-in-node="0">Backend (Firmware):</b> High-performance AVR Assembly (ASM) code for UART communication and LED control.</p></li><li><p data-path-to-node="8,2,0"><b data-path-to-node="8,2,0" data-index-in-node="0">Direct Register Access:</b> Learn how to manipulate <code data-path-to-node="8,2,0" data-index-in-node="48">UDR0</code>, <code data-path-to-node="8,2,0" data-index-in-node="54">UBRR0</code>, and <code data-path-to-node="8,2,0" data-index-in-node="65">PORTB</code> for maximum efficiency.</p></li></ul><hr data-path-to-node="9"><h2 data-path-to-node="10">💻 Core Logic</h2><h3 data-path-to-node="11">JavaScript (Browser Side)</h3><p data-path-to-node="12">The core logic to connect and handle the serial stream:</p><response-element class="" ng-version="0.0.0-PLACEHOLDER"><!----><!----><!----><!----><!----><!----><code-block _nghost-ng-c26535677="" class="ng-tns-c26535677-342 ng-star-inserted" style=""><!----><!----><div _ngcontent-ng-c26535677="" class="code-block ng-tns-c26535677-342 ng-animate-disabled ng-trigger ng-trigger-codeBlockRevealAnimation" jslog="223238;track:impression,attention;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]]" data-hveid="0" decode-data-ved="1" data-ved="0CAAQhtANahgKEwim8fL9iaSTAxUAAAAAHQAAAAAQzgY" style="display: block;"><div _ngcontent-ng-c26535677="" class="code-block-decoration header-formatted gds-title-s ng-tns-c26535677-342 ng-star-inserted" style=""><span _ngcontent-ng-c26535677="" class="ng-tns-c26535677-342">JavaScript</span><div _ngcontent-ng-c26535677="" class="buttons ng-tns-c26535677-342 ng-star-inserted"><!----><button _ngcontent-ng-c26535677="" aria-label="Copia codice" mat-icon-button="" mattooltip="Copia codice" class="mdc-icon-button mat-mdc-icon-button mat-mdc-button-base mat-mdc-tooltip-trigger copy-button ng-tns-c26535677-342 mat-unthemed ng-star-inserted" mat-ripple-loader-uninitialized="" mat-ripple-loader-class-name="mat-mdc-button-ripple" mat-ripple-loader-centered="" jslog="179062;track:generic_click,impression;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]];mutable:true"><span class="mat-mdc-button-persistent-ripple mdc-icon-button__ripple"></span><mat-icon _ngcontent-ng-c26535677="" role="img" fonticon="content_copy" class="mat-icon notranslate gds-icon-s google-symbols mat-ligature-font mat-icon-no-color" aria-hidden="true" data-mat-icon-type="font" data-mat-icon-name="content_copy"></mat-icon><!----><span class="mat-focus-indicator"></span><span class="mat-mdc-button-touch-target"></span></button><!----><!----></div><!----><!----></div><!----><div _ngcontent-ng-c26535677="" class="formatted-code-block-internal-container ng-tns-c26535677-342"><div _ngcontent-ng-c26535677="" class="animated-opacity ng-tns-c26535677-342"><pre _ngcontent-ng-c26535677="" class="ng-tns-c26535677-342"><code _ngcontent-ng-c26535677="" role="text" data-test-id="code-content" class="code-container formatted ng-tns-c26535677-342"><span class="hljs-comment">// 🔌 CONNECT AND READ</span>
<span class="hljs-keyword">async</span> <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">connect</span>(<span class="hljs-params"></span>) </span>{
  port = <span class="hljs-keyword">await</span> navigator.serial.requestPort();
  <span class="hljs-keyword">await</span> port.open({ <span class="hljs-attr">baudRate</span>: <span class="hljs-number">115200</span> });
  
  writer = port.writable.getWriter();
  reader = port.readable.getReader();

  <span class="hljs-keyword">while</span> (keepReading) {
    <span class="hljs-keyword">const</span> { value, done } = <span class="hljs-keyword">await</span> reader.read();
    <span class="hljs-keyword">if</span> (done) <span class="hljs-keyword">break</span>;
    <span class="hljs-keyword">let</span> text = <span class="hljs-keyword">new</span> TextDecoder().decode(value);
    <span class="hljs-built_in">console</span>.log(<span class="hljs-string">"From Arduino:"</span>, text);
  }
}
</code></pre><!----></div></div></div><!----><!----><!----></code-block><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----></response-element><h3 data-path-to-node="14">AVR Assembly (Hardware Side)</h3><p data-path-to-node="15">A snippet of how the ATmega328P handles incoming bytes at the register level:</p><response-element class="" ng-version="0.0.0-PLACEHOLDER"><!----><!----><!----><!----><!----><!----><code-block _nghost-ng-c26535677="" class="ng-tns-c26535677-343 ng-star-inserted" style=""><!----><!----><div _ngcontent-ng-c26535677="" class="code-block ng-tns-c26535677-343 ng-animate-disabled ng-trigger ng-trigger-codeBlockRevealAnimation" jslog="223238;track:impression,attention;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]]" data-hveid="0" decode-data-ved="1" data-ved="0CAAQhtANahgKEwim8fL9iaSTAxUAAAAAHQAAAAAQzwY" style="display: block;"><div _ngcontent-ng-c26535677="" class="code-block-decoration header-formatted gds-title-s ng-tns-c26535677-343 ng-star-inserted" style=""><span _ngcontent-ng-c26535677="" class="ng-tns-c26535677-343">Snippet di codice</span><div _ngcontent-ng-c26535677="" class="buttons ng-tns-c26535677-343 ng-star-inserted"><!----><button _ngcontent-ng-c26535677="" aria-label="Copia codice" mat-icon-button="" mattooltip="Copia codice" class="mdc-icon-button mat-mdc-icon-button mat-mdc-button-base mat-mdc-tooltip-trigger copy-button ng-tns-c26535677-343 mat-unthemed ng-star-inserted" mat-ripple-loader-uninitialized="" mat-ripple-loader-class-name="mat-mdc-button-ripple" mat-ripple-loader-centered="" jslog="179062;track:generic_click,impression;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]];mutable:true"><span class="mat-mdc-button-persistent-ripple mdc-icon-button__ripple"></span><mat-icon _ngcontent-ng-c26535677="" role="img" fonticon="content_copy" class="mat-icon notranslate gds-icon-s google-symbols mat-ligature-font mat-icon-no-color" aria-hidden="true" data-mat-icon-type="font" data-mat-icon-name="content_copy"></mat-icon><!----><span class="mat-focus-indicator"></span><span class="mat-mdc-button-touch-target"></span></button><!----><!----></div><!----><!----></div><!----><div _ngcontent-ng-c26535677="" class="formatted-code-block-internal-container ng-tns-c26535677-343"><div _ngcontent-ng-c26535677="" class="animated-opacity ng-tns-c26535677-343"><pre _ngcontent-ng-c26535677="" class="ng-tns-c26535677-343"><code _ngcontent-ng-c26535677="" role="text" data-test-id="code-content" class="code-container formatted ng-tns-c26535677-343">; 📥 RECEIVE BYTE (ASM)
USART_Receive:
    lds r16, UCSR0A           ; Load Status Register
    sbrs r16, RXC0            ; Skip if Receive Complete flag is set
    rjmp USART_Receive        ; Wait for data
    lds r16, UDR0             ; Get byte from Data Register
    ret
</code></pre><!----></div></div></div><!----><!----><!----></code-block><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----></response-element><hr data-path-to-node="17"><h2 data-path-to-node="18">📖 Live Documentation</h2><p data-path-to-node="19">You can read the full step-by-step tutorial in two languages:</p><ul data-path-to-node="20"><li><p data-path-to-node="20,0,0">🇺🇸 <b data-path-to-node="20,0,0" data-index-in-node="5"><response-element class="" ng-version="0.0.0-PLACEHOLDER"><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><link-block _nghost-ng-c2055557401="" class="ng-star-inserted"><!----><!----><a _ngcontent-ng-c2055557401="" target="_blank" rel="noopener" externallink="" _nghost-ng-c3446112727="" jslog="197247;track:generic_click,impression,attention;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]]" href="https://costycnc.github.io/web-serial-avr-asm/" class="ng-star-inserted" data-hveid="0" decode-data-ved="1" data-ved="0CAAQ_4QMahgKEwim8fL9iaSTAxUAAAAAHQAAAAAQ0AY">English Version (Mirror)</a><!----></link-block><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----></response-element></b></p></li><li><p data-path-to-node="20,1,0">🇮🇹 <b data-path-to-node="20,1,0" data-index-in-node="5"><response-element class="" ng-version="0.0.0-PLACEHOLDER"><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><link-block _nghost-ng-c2055557401="" class="ng-star-inserted"><!----><!----><a _ngcontent-ng-c2055557401="" target="_blank" rel="noopener" externallink="" _nghost-ng-c3446112727="" jslog="197247;track:generic_click,impression,attention;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]]" href="https://costycnc.github.io/web-serial-avr-asm/it.html" class="ng-star-inserted" data-hveid="0" decode-data-ved="1" data-ved="0CAAQ_4QMahgKEwim8fL9iaSTAxUAAAAAHQAAAAAQ0QY">Versione Italiana (Mirror)</a><!----></link-block><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----></response-element></b></p></li></ul><hr data-path-to-node="21"><h2 data-path-to-node="22">🔗 Official Project Page</h2><p data-path-to-node="23">For the complete guide, more CNC projects, and advanced AVR tutorials, visit my official website:
👉 <b data-path-to-node="23" data-index-in-node="101"><response-element class="" ng-version="0.0.0-PLACEHOLDER"><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><link-block _nghost-ng-c2055557401="" class="ng-star-inserted"><!----><!----><a _ngcontent-ng-c2055557401="" target="_blank" rel="noopener" externallink="" _nghost-ng-c3446112727="" jslog="197247;track:generic_click,impression,attention;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]]" href="https://www.costycnc.it/avr1/serial-port/en.html" class="ng-star-inserted" data-hveid="0" decode-data-ved="1" data-ved="0CAAQ_4QMahgKEwim8fL9iaSTAxUAAAAAHQAAAAAQ0gY">costycnc.it - Web Serial API Guide</a><!----></link-block><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----></response-element></b></p><h2 data-path-to-node="24">🛠️ How to Test</h2><ol start="1" data-path-to-node="25"><li><p data-path-to-node="25,0,0">Connect your Arduino to a USB port.</p></li><li><p data-path-to-node="25,1,0">Open the <response-element class="" ng-version="0.0.0-PLACEHOLDER"><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><link-block _nghost-ng-c2055557401="" class="ng-star-inserted"><!----><!----><a _ngcontent-ng-c2055557401="" target="_blank" rel="noopener" externallink="" _nghost-ng-c3446112727="" jslog="197247;track:generic_click,impression,attention;BardVeMetadataKey:[[&quot;r_d51f14ce244ef736&quot;,&quot;c_de220cc08f9d74fb&quot;,null,&quot;rc_a6f658ccf5c8607b&quot;,null,null,&quot;it&quot;,null,1,null,null,1,0]]" href="https://costycnc.github.io/web-serial-avr-asm/" class="ng-star-inserted" data-hveid="0" decode-data-ved="1" data-ved="0CAAQ_4QMahgKEwim8fL9iaSTAxUAAAAAHQAAAAAQ0wY">Live Demo</a><!----></link-block><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----></response-element>.</p></li><li><p data-path-to-node="25,2,0">Click "Connect", select your COM port, and start sending commands!</p></li></ol><hr data-path-to-node="26"><p data-path-to-node="27"><i data-path-to-node="27" data-index-in-node="0">Developed by CostyCNC. Dedicated to high-precision hardware control.</i></p><hr data-path-to-node="28"><p data-path-to-node="29">Spero che questo formato "nudo" non venga alterato. Se vedi che mancano i tre segnetti (```) prima di <b data-path-to-node="29" data-index-in-node="102">asm</b> o dopo la fine del codice, aggiungili a mano nel redattore di GitHub.</p><p data-path-to-node="30">Una volta salvato questo, il tuo repository sarà un gioiello di chiarezza. Ti serve aiuto per rinominare i file <code data-path-to-node="30" data-index-in-node="112">index.html</code> e <code data-path-to-node="30" data-index-in-node="125">it.html</code> per far combaciare i link?</p></div>

---
*Developed by CostyCNC. Dedicated to high-precision hardware control.*





