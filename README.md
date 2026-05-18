# Napredni Embedded Sistem za Unos i Prikaz Podataka (Flowcode)

Profesionalna implementacija i optimizacija matrične tastature (4x4 Keypad) i alfanumeričkog displeja (HD44780 LCD) unutar Flowcode razvojnog okruženja. Projekat se fokusira na efikasno upravljanje resursima mikrokontrolera kroz softverski debouncing i modularnu arhitekturu.

---

## 🔄 Algoritam i Logika Sistema

Sistem koristi stanja (State Machine) i skeniranje matrica u realnom vremenu kako bi detektovao unos bez blokiranja glavne izvršne petlje.

```mermaid
graph TD
    A[Start: Power-On Reset] --> B[Inicijalizacija: LCD & Portovi]
    B --> C[Prikaz Početnog Ekrana]
    C --> D[Skeniranje Redova Tastature]
    D --> E{Detektovan Pritisak?}
    E -- Ne --> D
    E -- Da --> F[Softverski Debounce Tajmer ~20ms]
    F --> G[Validacija i Konverzija u ASCII]
    G --> H[Upis u LCD Bafer & Osvežavanje Ekrana]
    H --> D
