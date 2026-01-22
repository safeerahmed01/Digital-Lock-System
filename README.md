🔐 Digital Lock System Using 74xx ICs
A hardware-based digital combination lock designed using classic TTL 74xx logic ICs.
The system accepts decimal input from a keypad, encodes it into BCD, stores each digit, compares it with preset values, and unlocks only when all digits match correctly.

This project demonstrates digital logic design, combinational + sequential circuits, and practical hardware interfacing using encoders, decoders, registers, comparators, and flip-flops.

🧠 How the System Works

:) Input Encoding
----> A numeric keypad is connected to the 74147 Priority Encoder.
----> Since 74147 outputs active-LOW BCD, a 7404 inverter is used to convert it into true BCD.

:) Display
----> The BCD output is sent to a 7447 BCD-to-7 Segment Decoder.
----> The entered digit is shown on a 7-segment display.

:) Data Storage
----> Each digit is stored using a 74195 Universal Shift Register (parallel load mode).
----> Separate registers are used for each digit.

:) Comparison
----> Stored digits (from 74195) are compared with preset values using 7485 4-bit Magnitude Comparators.
----> The A = B output becomes HIGH when a correct digit is entered.

:) Decision Latching
----> Each comparator’s output is latched using a 7474 D Flip-Flop.
----> This prevents glitches and stores the match result.

:) Final Unlock Logic
----> The three DFF outputs are combined using an AND gate.
----> The lock opens only when all three digits are correct.

🧩 Components Used
IC	Description
----> 74147	Priority Encoder (Decimal to BCD)
----> 7404	Hex Inverter
----> 7447	BCD to 7-Segment Decoder
----> 74195	4-bit Universal Shift Register
----> 7485	4-bit Magnitude Comparator
----> 7474	Dual D Flip-Flop
----> AND Gate	Final unlock logic
----> 7-Segment Display	Visual output
----> Keypad	User input
----> 10kΩ Resistors	Pull-downs for encoder
----> 1µF Capacitors + Pull-ups	Clock debouncing

🔄 System Flow
   Keypad → 74147 → 7404 → 7447 → 7-Segment
                      ↓
                   74195
                      ↓
                    7485
                      ↓
                    7474
                      ↓
                 AND Gate
                      ↓
                    LOCK

🎯 Features

----> Fully hardware-based (no microcontroller)
----> Noise-free clock using RC debounce
----> Secure 3-digit comparison
----> Visual digit feedback
----> Modular and expandable design

🛠️ Applications
----> Digital door locks
----> Security panels
----> Safe lock systems
----> Educational digital logic labs
