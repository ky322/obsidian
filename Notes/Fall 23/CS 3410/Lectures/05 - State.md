### Stateful Components
- Combinational Logic
	- Output computed directly from inputs
	- System has no internal state
	- Nothing depends on the past
- Why State
	- Add two numbers (A+B)
	- Add three numbers
		- Use two adders
		- Reuse same adder multiple times
		- You can't drive a wire with two different values
		- Use Mux for flip control 1 -> for second addition

### Clocks
- Clocks help coordinate state changes
	- Fixed period
	- Frequency = 1/period
- State Change at clock edge
	- Positive edge triggered
	- Negative edge triggered 
	- Need to design edge triggered storage
- Positive Edge Triggered D Flip Flop
	- Data captured when clock low, before the positive edge
	- That becomes output for Q for the entire next clock cycle
	- Output Q only changes on rising edge

### Registers
- Store N bits
- D flip flips in parallel
- Shared clock
- Additional (optional) inputs, writeEnable, reset

### Clock Methodology
- Positive Edge Triggered D Flip Flop
- Output changes only on rising edge
- Data captured when clock low
- Signals must be stable prior to rising edge

### Register File
- N read/write registers
- Indexed by register number
- Registers
	- Numbered from 0-31
- How to write to one register in the register file
	- Need a decoder
	- Write enable signal prevents unintended writes
- Reading from register
	- Need a multiplexor
	- Read from two registers -> 2 multiplexors
	- Implementation
		- N$*$D flip flops to store bits
		- 1 mux for each read port
		- 1 decoder for each write port
- Register File Tradeoffs
	- Very fast
	- Adding extra ports straightforward
	- Does not scale
		- 32 MB register file with 32 it registers
			- Need 32x 1M to 1 multiplexor
			- Need 20 to 1M decoder
