---

# Web Serial API + AVR Assembly Control 🔌

This project demonstrates how to bridge the gap between a modern web browser and low-level hardware. You can control an Arduino (ATmega328P) directly from a webpage using the **Web Serial API**, without any intermediate server or software.

## 🚀 What's Inside

* **Frontend:** HTML5 and JavaScript implementation of the Web Serial API.
* **Backend (Firmware):** High-performance AVR Assembly (ASM) code for UART communication and LED control.
* **Direct Register Access:** Learn how to manipulate `UDR0`, `UBRR0`, and `PORTB` for maximum efficiency.

---

## 💻 Core Logic

### JavaScript (Browser Side)

The core logic to connect and handle the serial stream:

```javascript
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
    console.log("From Arduino:", text);
  }
}

```

### AVR Assembly (Hardware Side)

A snippet of how the ATmega328P handles incoming bytes at the register level:

```asm
; 📥 RECEIVE BYTE (ASM)
USART_Receive:
    lds r16, UCSR0A           ; Load Status Register
    sbrs r16, RXC0            ; Skip if Receive Complete flag is set
    rjmp USART_Receive        ; Wait for data
    lds r16, UDR0             ; Get byte from Data Register
    ret

```

---

## 📖 Live Documentation

You can read the full step-by-step tutorial in two languages:

* 🇺🇸 **[English Version (Mirror)](https://costycnc.github.io/web-serial-avr-asm/)**
* 🇮🇹 **[Versione Italiana (Mirror)](https://costycnc.github.io/web-serial-avr-asm/it.html)**

---

## 🔗 Official Project Page

For the complete guide, more CNC projects, and advanced AVR tutorials, visit my official website:
👉 **[costycnc.it - Web Serial API Guide](https://www.costycnc.it/avr1/serial-port/en.html)**

## 🛠️ How to Test

1. Connect your Arduino to a USB port.
2. Open the [Live Demo](https://costycnc.github.io/web-serial-avr-asm/).
3. Click "Connect", select your COM port, and start sending commands!

---

*Developed by CostyCNC. Dedicated to high-precision hardware control.*

---



