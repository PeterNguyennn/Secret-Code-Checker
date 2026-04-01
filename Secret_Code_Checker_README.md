# Secret Code Checker

A 4-bit combinational logic circuit built entirely from discrete gate ICs. Set the correct binary code on a DIP switch — the circuit triggers an LED alarm via a transistor. No microcontroller, no code.

![TinkerCAD Circuit](tinkercad.png)

🔗 [View & Simulate on TinkerCAD](https://www.tinkercad.com/things/63q92yzz8nq-a-secret-code-checker) · 🎥 [Demo Video](https://drive.google.com/file/d/1YtCvv6Mga-zqozHSLAAdKCUKDyExCcgd/view?usp=drive_link)

---

## How It Works

The circuit compares a 4-bit DIP switch input against a hardwired secret code (**1001**) using AND and NOT gates. Bits that must be `1` feed directly into an AND gate; bits that must be `0` are first inverted by a NOT gate. All four conditioned signals chain into a final AND gate — output goes HIGH only when every bit matches simultaneously. That HIGH signal drives the base of an NPN transistor, switching on the alarm LED.

> Boolean expression: `Q = A AND NOT(B) AND NOT(C) AND D`

---

## Specs

| Property | Value |
|---|---|
| Input | 4-bit DIP switch |
| Secret code | 1001 (hardwired) |
| Gate ICs | 74HC04 (NOT), 74HC08 (AND) |
| Output stage | NPN transistor + LED |
| Supply | 5V |
| Logic family | 74HC CMOS |

---

## Components

- AND gate IC (74HC08)
- NOT gate IC (74HC04)
- NPN transistor (2N2222 or BC547)
- 4-position DIP switch
- Resistors: 1kΩ ×4 (pull-down), 220Ω (LED)
- LED, breadboard, jumper wires, 5V supply

---

## Lessons Learned

- 74HC series is strictly 5V — running it at 9V causes ICs to overheat immediately
- Pull-down resistors on DIP switch outputs are mandatory; without them, "off" switches float and logic behaves unpredictably
- Working out the Boolean expression on paper before wiring made the gate connections much clearer
- Transistor pinout varies by part number — always check the datasheet before inserting

---

## Future Improvements

- Extend to 8-bit code using an 8-position DIP switch for a more secure lock
- Add a second DIP switch to make the secret code reprogrammable without rewiring
- Add a buzzer in parallel with the LED for audible alarm output
- Replace discrete gates with a dedicated 74HC85 4-bit comparator IC
