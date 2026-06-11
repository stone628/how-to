# AGENTS.md

Electronics lecture series — Korean-language content only. All material is static markdown; no code, no tooling. Target audience: middle school to high school students.

Goal: understand digital circuits at the logical level with minimal electronics engineering depth. The final project is a simple computer built from flip-flops (memory), an adder (CPU), and an LED (output).

- `index.md` is the table of contents. Each lecture links back to `index.md` via relative markdown links. Renaming/moving a file requires updating links in every other lecture file.

## Content scope

| File | Topic |
|------|-------|
| `lecture01.md` | Switch, battery, multimeter, Ohm's law |
| `lecture02.md` | LED, current-limiting resistor, diode behavior |
| `lecture03.md` | PNP/NPN transistor as a digital switch |
| `lecture04.md` | MOSFET as a digital switch, BJT comparison |
| `lecture05.md` | NOT, NAND, NOR gates from MOSFETs (CMOS) |
| `lecture06.md` | AND, OR, XOR gates from primitive gate composition |
| `lecture07.md` | NAND as universal gate, why NAND is the gate of choice |

Each lecture follows the same structure: 목표 (goals) → 실습 (practice) → 결론 (conclusion) → 심화 주제 (advanced topics).

## Content constraints (from reviews)

- **EE depth**: minimal by design. Saturation/cut-off regions, detailed transistor physics, and complex circuit analysis are intentionally excluded as distracting.
- **심화 주제**: practical skills and questions that extend the experiment (e.g. LED forward voltage / resistor calculation, multimeter usage tips, real-vs-ideal Ohm's law deviation).
- **실습 (practice)**: schematic diagrams and detailed build instructions are deferred — planned for a future update. Current text describes the experiment at a high level.
- **Digital vs analog framing**: lectures emphasize the *logical* switching behavior (ON/OFF = 1/0). Line between mechanical switch (no power needed to stay closed) and transistor switch (continuous base current needed) is a key concept introduced in lecture03.
