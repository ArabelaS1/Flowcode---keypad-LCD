# <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Gear.png" width="40" /> FLOWCODE SYSTEM: LCD & MATRIX KEYPAD

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:38bdf8,100:a855f7&height=240&section=header&text=EMBEDDED%20DASHBOARD&fontSize=70&fontAlignY=35&animation=twinkling&desc=Keypad%20Matrix%20%E2%80%A2%20LCD%2016x2%20%E2%80%A2%20Flowcode%20V10&descAlignY=55&descSize=20" width="100%" />

  <br/>

  <p align="center">
    <img src="https://img.shields.io/badge/System-Active-00FF00?style=for-the-badge&logo=cpu&logoColor=white" />
    <img src="https://img.shields.io/badge/Input-4x4_Matrix-38bdf8?style=for-the-badge&logo=pypy&logoColor=white" />
    <img src="https://img.shields.io/badge/Output-LCD_16x2-a855f7?style=for-the-badge&logo=monitor&logoColor=white" />
  </p>
</div>

---

## 🛰️ Real-Time Logic Console
<div align="center">
  <table border="0">
    <tr>
      <td bgcolor="#0d1117">
        <p align="center"><strong>📟 LCD SIMULATOR</strong></p>
        <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=ADFF9E&background=152222&width=435&lines=%3E_Initializing_System...;%3E_Flowcode_v10_Detected;%3E_Keypad_Scanning...;%3E_Input_Buffer_Ready" alt="Typing SVG" />
      </td>
    </tr>
  </table>
</div>

---

## 🧬 Arhitektura Algoritma (Flowchart)
Ovaj dijagram koristi **Mermaid** engine koji GitHub renderuje sa oštrim, modernim linijama.

```mermaid
graph LR
    %% Definisanje stilova
    classDef hardware fill:#1e2a3a,stroke:#38bdf8,stroke-width:2px,color:#fff;
    classDef logic fill:#0f172a,stroke:#a855f7,stroke-width:2px,color:#fff;
    classDef output fill:#1c2c2c,stroke:#adff9e,stroke-width:2px,color:#adff9e;

    A[POWER ON] --> B{SCAN ROWS}
    B -- Pulse --> C[READ COLUMNS]
    C --> D{KEY PRESSED?}
    D -- YES --> E[DEBOUNCE LOGIC]
    E --> F[ASCII CONVERSION]
    F --> G[LCD WRITE]
    G --> B

    class A,B,C hardware;
    class D,E,F logic;
    class G output;
