# 🔐 FlowCode · LCD & Keypad Matrix

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0d1117&height=200&section=header&text=Flowcode%20Master%20Project&fontSize=40&fontColor=38bdf8&animation=fadeIn" width="100%" />
</div>

---

## 🖥️ Sistem u Radu (Simulacija)

Budući da GitHub blokira interaktivni JavaScript u README fajlovima, ispod je vizuelna reprezentacija tvog interfejsa.

<table width="100%">
  <tr>
    <td width="50%" bgcolor="#0a0e14" style="border-radius: 20px; padding: 20px;">
      <div align="center">
        <p><strong>📟 LCD 16x2 DISPLAY</strong></p>
        <img src="https://img.shields.io/badge/SCREEN-%3E_FlowCode_Ready-1c2c2c?style=for-the-badge&logo=microarchitecture&logoColor=adff9e&labelColor=152222" height="40px" />
        <br/>
        <img src="https://img.shields.io/badge/BUFFER-%3E_Waiting_Input...-1c2c2c?style=for-the-badge&labelColor=152222&color=38bdf8" height="30px" />
      </div>
    </td>
    <td width="50%" bgcolor="#10141c" style="border-radius: 20px; padding: 20px;">
      <div align="center">
        <p><strong>🔢 KEYPAD 4x4 MATRIX</strong></p>
        <code>[ 1 ] [ 2 ] [ 3 ] [ A ]</code><br/>
        <code>[ 4 ] [ 5 ] [ 6 ] [ B ]</code><br/>
        <code>[ 7 ] [ 8 ] [ 9 ] [ C ]</code><br/>
        <code>[ * ] [ 0 ] [ # ] [ D ]</code>
      </div>
    </td>
  </tr>
</table>

---

## ✨ Karakteristike Sistema

* **Logic:** Non-blocking scan sa softverskim debouncing-om (20ms).
* **LCD:** HD44780 kontroler u 4-bitnom modu komunikacije.
* **IO Mapping:** * LCD: `PORTB (RB0-RB7)`
    * Keypad: `PORTD (RD0-RD7)`
* **Target:** Optimizovano za PIC16F877A / ATmega328P.

---

## 🛠️ Tehnički Dijagram (Flowchart)

```mermaid
graph TD
    Start(Power ON) --> Init[Inicijalizacija LCD]
    Init --> Scan{Skeniraj Keypad}
    Scan -- Nema unosa --> Scan
    Scan -- Taster Pritisnut --> Debounce[Debounce 20ms]
    Debounce --> Update[Prikaži na LCD]
    Update --> Scan
