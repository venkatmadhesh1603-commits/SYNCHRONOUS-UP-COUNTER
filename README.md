### SYNCHRONOUS-UP&DOWN-COUNTER

**AIM:**

To implement 4 bit synchronous up counter synchronous down counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

### SYNCHRONOUS-DOWN-COUNTER
A Synchronous Down Counter is a digital sequential circuit in which all flip-flops are triggered by a common clock signal and the count decreases by one for each clock pulse. Since all flip-flops change state simultaneously, the operation is faster and more reliable than asynchronous counters. It counts in binary down sequence, usually from the maximum value to zero, and is widely used in timers, countdown circuits, and digital clocks.

![alt text](image-1.png)

![alt text](image.png)

**Procedure**                                                                                                                              
SYNCHRONOUS-UP-COUNTER:                                                                                                                         
Connect Vcc and GND to the counter IC.

Apply clock pulses to the common clock input.

Enable the counter by setting the enable input HIGH.

Observe the output count (Q) after each clock pulse.

Verify that the count increments synchronously in binary.

SYNCHRONOUS-DOWN-COUNTER:                                                                                                                       
Connect Vcc and GND to the counter IC.

Apply clock pulses to the common clock input.

Set the enable input HIGH.

Observe the outputs (Q) for each clock pulse.

Verify that the count decrements synchronously in binary.

**PROGRAM**
```
SYNCHRONOUS-UP-COUNTER:
module exp11(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out+1;
end
endmodule

SYNCHRONOUS-DOWN-COUNTER:
module exp11(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out-1;
end
endmodule

```

Developed by: Sangeeth J RegisterNumber: 25016967

**RTL LOGIC UP COUNTER**
SYNCHRONOUS-UP-COUNTER:
![alt text](<Screenshot 2025-12-15 142812.png>)
SYNCHRONOUS-DOWN-COUNTER:
![alt text](<Screenshot 2025-12-15 212318.png>)

**TIMING DIAGRAM FOR IP COUNTER**
SYNCHRONOUS-UP-COUNTER:
![alt text](<Screenshot 2025-12-15 143602.png>)
SYNCHRONOUS-DOWN-COUNTER:
![alt text](<Screenshot 2025-12-15 212512.png>)

**TRUTH TABLE**
SYNCHRONOUS-UP-COUNTER:
| Clock Pulse | Q2 | Q1 | Q0 | Decimal Count |
| ----------- | -- | -- | -- | ------------- |
| Initial     | 0  | 0  | 0  | 0             |
| 1           | 0  | 0  | 1  | 1             |
| 2           | 0  | 1  | 0  | 2             |
| 3           | 0  | 1  | 1  | 3             |
| 4           | 1  | 0  | 0  | 4             |
| 5           | 1  | 0  | 1  | 5             |
| 6           | 1  | 1  | 0  | 6             |
| 7           | 1  | 1  | 1  | 7             |
| 8 (reset)   | 0  | 0  | 0  | 0             |

SYNCHRONOUS-DOWN-COUNTER:
| Clock Pulse | Q2 | Q1 | Q0 | Decimal Count |
| ----------- | -- | -- | -- | ------------- |
| Initial     | 1  | 1  | 1  | 7             |
| 1           | 1  | 1  | 0  | 6             |
| 2           | 1  | 0  | 1  | 5             |
| 3           | 1  | 0  | 0  | 4             |
| 4           | 0  | 1  | 1  | 3             |
| 5           | 0  | 1  | 0  | 2             |
| 6           | 0  | 0  | 1  | 1             |
| 7           | 0  | 0  | 0  | 0             |
| 8 (reset)   | 1  | 1  | 1  | 7             |


**RESULTS:**                                                                                                                            
Thus the SYNCHRONOUS-UP-COUNTER and SYNCHRONOUS-DOWN-COUNTER circuits are designed and the truth tables is verified using Quartus software.
