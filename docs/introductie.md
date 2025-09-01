# Introductie

## Hoofdstuk 1 – Wat is een microcontroller?

### 1.1 Wat is een microcontroller?
Een microcontroller is een kleine computer op een chip. Hij kan drie dingen:

- **Meten** (via ingangen of sensoren)
- **Denken** (programma uitvoeren)
- **Sturen** (via uitgangen, bijvoorbeeld een LED of motor aanzetten)

 **Voorbeelden:**

- Raspberry Pi Pico
- Arduino Uno

![Foto van Raspberry Pi Pico en Arduino UNO naast elkaar](img/pico_arduino.jpg)

### 1.2 Verschil met een computer
Een laptop kan veel dingen tegelijk doen (internet, filmpjes, spelletjes).
Een microcontroller doet meestal één taak, maar kan dat heel betrouwbaar en snel.
Bijvoorbeeld: een wasmachine besturen, lampen automatisch schakelen of een robot laten bewegen.

### 1.3 Veilig werken met elektronica
Microcontrollers werken meestal op 3.3V of 5V. Spanningen tot en met 24V zijn veilig voor mensen.

Dit wil niet zeggen dat mensen veilig zijn voor microcontrollers.
Het vermogen dat een microcontroller bord kan leveren is beperkt. Sluit nooit rechtstreeks een grote motor of lamp aan. Dit kan leiden tot te hoge stromen waardoor de microcontroller of het bord kapot kan gaan.

Zoals in het hoofdstuk over componenten al vermeld werd: altijd een weerstand in serie zetten met een LED, anders kan er iets kapot gaan.

![Schema van LED met serieweerstand](img/ac_source_led_res.png)

---

