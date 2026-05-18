<!-- HEADER SECTION -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=200&section=header&text=Flowcode%20Keypad%20%26%20LCD&fontSize=40&animation=fadeIn" width="100%" />
  
  <p align="center">
    <const badge>
      <img src="https://img.shields.io/badge/Flowcode-v10-blue?style=for-the-badge&logo=microarchitecture" />
    </const>
    <const badge>
      <img src="https://img.shields.io/badge/Hardware-PIC%20%2F%20Arduino-orange?style=for-the-badge&logo=hardware" />
    </const>
    <const badge>
      <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" />
    </const>
  </p>

  <h3>🚀 Napredni Embedded Sistem za Unos i Prikaz Podataka</h3>
  <p>Implementacija matrice tastature (Keypad 4x4) i LCD displeja unutar Flowcode okruženja sa optimizovanim algoritmom za obradu pritiska tastera.</p>
</div>

<br/>

<!-- O PROJEKTU -->
## 📝 O Projektu

Ovaj projekat predstavlja napredno rešenje za komunikaciju između korisnika i mikrokontrolera. Koristeći **Flowcode** grafičko programiranje, uspešno je implementirana kontrola **4x4 Keypad-a** i **16x2 LCD-a** (ili 20x4). Sistem je dizajniran tako da minimizira opterećenje procesora (debouncing tastera je rešen softverski) i omogućava fluidan ispis u realnom vremenu.

### ✨ Ključne Karakteristike:
*   **Dynamic LCD Refresh:** Pametno osvežavanje ekrana bez treperenja (flicker-free).
*   **Debounce Algoritam:** Eliminisan "double-tap" efekat mehaničkih tastera.
*   **Modularni Flowcode Makroi:** Kod je podeljen na jasne celine (Inicijalizacija, Unos, Obrada, Prikaz).
*   **Univerzalna Arhitektura:** Lako se portuje na PIC, AVR (Arduino) ili STM32 mikrokontrolere.

<br/>

<!-- HARDVERSKE KOMPONENTE -->
## 🛠️ Hardverska Arhitektura

Projekat je testiran i simuliran sa sledećim komponentama:

| Komponenta | Tip/Model | Svrha |
| :--- | :--- | :--- |
| **Mikrokontroler** | PIC16F877A / ATmega328P | Glavni kontroler |
| **Displej** | LCD 16x2 (HD44780) | Prikaz korisničkog interfejsa |
| **Unos** | Matrični Keypad 4x4 | Unos karaktera i komandi |
| **Oscilator** | Kristal 19.66MHz / 16MHz | Stabilan takt sistema |

<br/>

<!-- KAKO RADI / ALGORITAM -->
## 🔄 Logika i Algoritam (Flowchart)

Sistem se oslanja na state-mašinu koja konstantno skenira redove i kolone tastature.

```mermaid
graph TD
    A[Start] --> B[Inicijalizacija LCD-a i Keypad-a]
    B --> C[Prikaži Welcome Screen]
    C --> D[Skeniraj Keypad 4x4]
    D --> E{Taster pritisnut?}
    E -- Ne --> D
    E -- Da --> F[Softverski Debounce 20ms]
    F --> G[Konvertuj Matrix Code u ASCII]
    G --> H[Ispiši karakter na LCD]
    H --> D
