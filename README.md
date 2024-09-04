Name: BHARGAV GORIVALE

Company: CODETECH IT SOLUTIONS

ID : CT08DS7688

Domain : Embedded Systems

Duration : Aug to Sept 2024

Mentor : NEELA SANTOSH KUMAR

# **Overview of the Project**

## **Project : LED BLINKING WITH ARDUINO USING EMBEDDED C PROGRAMMING**

### **Objective**
The primary objective of translating the TASK1 (Arduino-based program) into Embedded C is to provide a more direct, efficient, and low-level control over the microcontroller's hardware resources. 

This approach allows for:

1.Optimized Performance: Direct register manipulation can reduce overhead and improve execution speed.

2.Better Resource Management: Embedded C enables fine-grained control over memory and processing power, which is crucial for resource-constrained environments.

3.Portability Across Different Platforms: Embedded C programs can be adapted to various microcontroller families (e.g., AVR, PIC, ARM) with minimal changes, whereas Arduino code is specific to the Arduino environment.

### **Key Featues**

1.Direct Hardware Access:

Embedded C allows direct manipulation of hardware registers (DDRB, PORTB), giving full control over the microcontroller's pins, timers, and peripherals.

2.Efficiency:

The code is often more efficient and faster since it eliminates the overhead associated with the Arduino abstraction layer.
Memory usage is optimized, which is crucial for microcontrollers with limited RAM and flash memory.

3.Fine-Grained Control:

Developers can control every aspect of the microcontroller's operation, including setting pin modes, adjusting clock speeds, and handling interrupts directly.
It allows for precise timing control, which is essential in real-time applications.

4.Portability and Flexibility:

Embedded C code can be ported to other microcontroller platforms with minimal modifications.
The code can be customized for different microcontroller architectures, providing greater flexibility.

5.Scalability:

As projects grow in complexity, Embedded C provides better scalability, allowing for more advanced features like interrupt handling, power management, and peripheral control.

6.Custom Libraries:

Embedded C allows developers to write their own libraries, optimizing them for specific hardware, which is not as straightforward in the Arduino environment.

**Detailed Explanation**
Let's break down the C program step by step, understanding each component and its role in controlling the LED.

1. Including Necessary Headers
   
  #include <avr/io.h>
  
  #include <util/delay.h>

- <avr/io.h>:

    + Purpose: Provides definitions for the Input/Output registers specific to AVR microcontrollers.
      
    + Usage: Allows direct manipulation of hardware registers like DDRB (Data Direction Register for Port B) and PORTB (Data Register for Port B).
      
- <util/delay.h>:

    + Purpose: Contains functions for creating delays, such as _delay_ms().
      
    + Usage: Facilitates pausing the program execution for a specified amount of time, essential for creating visible LED blinking intervals.
      
2. Defining the LED Pin

    #define LED_PIN PB5

#define LED_PIN PB5:
 
   + Purpose: Creates a macro named LED_PIN representing PB5 (Pin 5 of Port B).

   + Explanation: On an Arduino Uno (which uses an ATmega328P microcontroller), the built-in LED is connected to PB5, which corresponds to digital pin 13. Using a macro enhances code readability and maintainability.
     
3. The main Function

   int main(void) {
      // Initialization and main loop
      return 0;
   }

 int main(void):
Purpose: The entry point of the C program.
Usage: In embedded systems, main typically contains initialization code and an infinite loop to keep the program running indefinitely.
3. Initializing the LED Pin as Output
c
Copy code
DDRB |= (1 << LED_PIN);  // Set PB5 as output by setting the 5th bit of DDRB
DDRB:

Definition: Data Direction Register for Port B.
Purpose: Determines whether each pin of Port B is configured as an input (0) or output (1).
(1 << LED_PIN):

Explanation: Shifts the binary 1 left by LED_PIN positions. Since LED_PIN is PB5 (which is 5), this results in 0b00100000.
DDRB |= (1 << LED_PIN);:

Operation: Sets the 5th bit of DDRB to 1 without altering other bits.
Effect: Configures PB5 as an output pin, enabling it to send voltage signals to drive the LED.
5. Infinite Loop to Blink the LED
c
Copy code
while (1) { // Infinite loop
    // LED control and delays
}
while (1) { ... }:
Purpose: Creates an infinite loop that keeps the microcontroller executing the enclosed instructions repeatedly.
Usage: Ensures that the LED continues to blink as long as the microcontroller is powered.
6. Turning the LED On
c
Copy code
PORTB |= (1 << LED_PIN);   // Set PB5 high
PORTB:

Definition: Data Register for Port B.
Purpose: Controls the output voltage of each pin in Port B.
(1 << LED_PIN):

Explanation: Similar to before, creates a bitmask for the specific pin.
PORTB |= (1 << LED_PIN);:

Operation: Sets the 5th bit of PORTB to 1 without altering other bits.
Effect: Applies a high voltage (typically 5V) to PB5, turning the LED on.
7. Introducing a Delay

_delay_ms(1000);            // Delay for 1000 milliseconds
_delay_ms(1000):

Purpose: Pauses program execution for 1000 milliseconds (1 second).
Usage: Keeps the LED in its current state (on or off) for a visible duration.
Note: The _delay_ms() function is a blocking delay, meaning the CPU does nothing else during this time. For simple applications like blinking an LED, this is acceptable. However, for more complex systems, non-blocking delays or timers are preferred.

8. Turning the LED Off

PORTB &= ~(1 << LED_PIN);  // Set PB5 low

~(1 << LED_PIN):

Explanation: Creates a bitmask where all bits are 1 except the bit corresponding to LED_PIN, which is 0 (0b11011111 for PB5).

PORTB &= ~(1 << LED_PIN);:

Operation: Clears the 5th bit of PORTB to 0 without altering other bits.

Effect: Applies a low voltage (0V) to PB5, turning the LED off.


9. Repeating the Cycle
After turning the LED off and introducing another delay, the loop reiterates, turning the LED back on, and so forth. This creates a continuous blinking effect with 1-second intervals.
