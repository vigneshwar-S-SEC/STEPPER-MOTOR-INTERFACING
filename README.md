# STEPPER MOTOR INTERFACING

## AIM
To write an assembly language program in 8086 to rotate the motor at different speeds.

---

## APPARATUS REQUIRED

| S. No | Item                        | Specification   | Quantity |
|-------|-----------------------------|-----------------|----------|
| 1     | Microprocessor kit          | 8086            | 1        |
| 2     | Power Supply                | +5 V DC, +12 V DC | 1      |
| 3     | Stepper Motor Interface board | -             | 1        |
| 4     | Stepper Motor               | -               | 1        |

---

## THEORY
A motor in which the rotor is able to assume only discrete stationary angular positions is a **stepper motor**. The rotary motion occurs in a stepwise manner from one equilibrium position to the next.  

**Two-phase scheme:** Any two adjacent stator windings are energized. There are two magnetic fields active in quadrature and none of the rotor pole faces can be in direct alignment with the stator poles. A partial but symmetric alignment of the rotor poles is of course possible.

---

## ALGORITHM
For running the stepper motor in clockwise and anticlockwise directions:

1. Get the first data from the lookup table.  
2. Initialize the counter and move data into the accumulator.  
3. Drive the stepper motor circuitry and introduce delay.  
4. Decrement the counter. If not zero, repeat from step (iii).  
5. Repeat the above procedure both for backward and forward directions.  

---

## SWITCHING SEQUENCE OF STEPPER MOTOR

| Memory Location | A1 | A2 | B1 | B2 | Hex Code |
|-----------------|----|----|----|----|----------|
| 1200            | 1  | 0  | 0  | 0  | 09H      |
| 1201            | 0  | 1  | 0  | 1  | 05H      |
| 1202            | 0  | 1  | 1  | 0  | 06H      |
| 1203            | 1  | 0  | 1  | 0  | 0AH      |

---

## PROGRAM

```asm
; Stepper Motor Interfacing Program in 8086 Assembly

START:   MOV DI, 1200H        ; Initialize memory location to store array
         MOV CX, 0004H        ; Initialize array size

DOWN1:   MOV AL, [DI]         ; Copy the first data into AL
         OUT C0, AL           ; Send it through port address

         MOV DX, 1010H        ; Delay subroutine
L1:      DEC DX
         JNZ L1

         INC DI               ; Go to next memory location
         LOOP DOWN1           ; Repeat until all data is sent

         JMP START            ; Continuous rotation

         HLT                  ; Stop

DATA:    DB 09H, 05H, 06H, 0AH ; Array of data
```
## OUTPUT OF THE PROGRAM:
<img width="330" height="440" alt="WhatsApp Image 2026-05-13 at 11 09 14 AM (1)" src="https://github.com/user-attachments/assets/5e47fdc7-7b4f-4c26-8b04-e8a10348e002" /><img width="330" height="440" alt="WhatsApp Image 2026-05-13 at 11 09 15 AM" src="https://github.com/user-attachments/assets/909d2b8d-ec2f-4c37-9a88-f2f1acac4f84" />
<img width="330" height="440" alt="WhatsApp Image 2026-05-13 at 11 09 14 AM" src="https://github.com/user-attachments/assets/b2fe9f25-52f0-4564-96c1-5c17964b1d88" />



## RESULT

Thus, the assembly language program for rotating the stepper motor in both clockwise and anticlockwise directions was written and verified.
