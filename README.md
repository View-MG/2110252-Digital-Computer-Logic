## คำอธิบายเกี่ยวกับ Mini CPU (DigLo Final Project)

ภาพวงจรทั้งหมด

### Opcode Instructions Table

| Opcode  | Command                       | Description                                                                                       |
|---------|-------------------------------|---------------------------------------------------------------------------------------------------|
| 00000   | NOPE                          | Do nothing, skip to the next instruction.                                                       |
| 00001   | accA ← Operand              | Store the 8-bit operand value in accA.                                                          |
| 00010   | accB ← Operand              | Store the 8-bit operand value in accB.                                                          |
| 00011   | accA ← accB                 | Copy the value from accB to accA.                                                               |
| 00100   | accB ← accA                 | Copy the value from accA to accB.                                                               |
| 00101   | regC ← accA                 | Copy the value from accA to regC.                                                               |
| 00110   | accA ← regC                 | Copy the value from regC to accA.                                                               |
| 00111   | regC ← M                   | Store input M in regC.                                                                          |
| 01000   | regC ← N                   | Store input N in regC.                                                                          |
| 01001   | accA ← pRAM_adr[Operand]  | Store the value from pRAM at the specified operand address in accA (rightmost 8 bits only).      |
| 01010   | accA ← rRAM_adr[Operand]  | Store the value from rRAM at the specified operand address in accA.                             |
| 01011   | rRAM_adr[Operand] ← accA   | Store the value from accA in rRAM at the specified operand address.                             |
| 01100   | Jump to address Operand       | Unconditional jump to the specified operand address.                                            |
| 01101   | Jump to address Operand if eq| Jump to the specified operand address if the equal flag is 1.                                   |
| 01110   | Jump to address Operand if gr| Jump to the specified operand address if the greater flag is 1.                                 |
| 01111   | Jump to address Operand if le| Jump to the specified operand address if the lesser flag is 1.                                  |
| 10000   | Jump to address Operand if eq or gr | Jump to the specified operand address if either equal or greater flag is 1.                   |
| 10001   | accA ← accA + accB         | Add accA and accB, store the result in accA (2’s complement, no overflow handling).              |
| 10010   | accA ← accA - accB         | Subtract accB from accA, store the result in accA (2’s complement, no overflow handling).        |
| 10011   | accA ← accA * accB         | Multiply accA[3..0] by accB[3..0], store the 4-bit result in accA.                              |
| 10100   | accA ← accA / accB         | Divide accA by accB (binary, unsigned), store the result in accA.                               |
| 10101   | accA ← accA % accB         | Modulo accA by accB (binary, unsigned), store the result in accA.                               |
| 10110   | accA ← accA ^ accB         | Exponentiate accA[2..0] to accB[2..0], store the result in accA (no overflow handling).         |
| 10111   | accA CMP accB                | Compare accA and accB (2’s complement), set equal, greater, or lesser flags.                   |
| 11000   | accA ← NOT(accA)           | Bitwise NOT of accA, store the result in accA.                                                  |
| 11001   | accA ← accA AND accB       | Bitwise AND of accA and accB, store the result in accA.                                         |
| 11010   | accA ← accA OR accB        | Bitwise OR of accA and accB, store the result in accA.                                          |
| 11011   | accA ← accA XOR accB       | Bitwise XOR of accA and accB, store the result in accA.                                         |
| 11100   | accA ← accA << accB        | Logical shift left of accA by accB[2..0], store the result in accA (max 7 bits shift).          |
| 11101   | isPrime(accA)                | Check if accA is a prime number (binary, unsigned). Set equal flag to 1 if true.               |
| 11110   | rRAM[0x0E:0x0F] ← LCM(m,n) | Compute LCM of m and n from rRAM specified addresses, store in rRAM[0x0E:0x0F].                 |
| 11111   | STOP                         | Halt execution and wait for the result signal.                                                 |
