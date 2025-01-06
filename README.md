# Uncommon Integer Overflow in VHDL Counter

This repository demonstrates a subtle integer overflow bug in a simple VHDL counter.  The bug arises from the use of an integer type without explicit bounds checking. While standard VHDL simulation might not immediately reveal the problem, it can lead to unexpected behavior in hardware implementations. The solution shows how to address this by using a more robust approach, preventing the counter from wrapping around.

## Bug Description:

The `buggy_counter.vhdl` file contains a counter that increments on each rising clock edge. However, it uses an integer type with a predefined range (0 to 15). When the counter reaches 15, the next increment would normally lead to an overflow.  Although the code has an `if` condition to reset the counter to 0, the implicit overflow may cause unexpected values, especially in synthesizable code. 

## Solution:

The `buggy_counter_solution.vhdl` file provides a corrected version using an unsigned type, which prevents unexpected wraparound behavior.  The use of unsigned provides the intended modulo-16 behavior.