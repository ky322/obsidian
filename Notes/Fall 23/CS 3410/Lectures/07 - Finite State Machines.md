### Stateful Circuits
- Combinational logic
	- Output computed directly from inputs
	- System has no internal state
	- Nothing depends on past
- Need
	- To record data
	- To build stateful circuits
	- A state holding device

### Finite State Machines
- An electronic machine which has external inputs, externally visible outputs, internal state
- Output and next state depends on inputs and current state
### Automata Model
- Inputs from external world
- Outputs to external world
- Internal state
- Combinational logic

### Mealy Machine
- Outputs and next state depends on both current state and input

### Moore Machine
- Output depend only on current state
### FSM in a Processor
- Multicycle (non pipelined) processor
- Handling cache misses, branch mispredictions, interrupts
- Branch predictor
- Tracking the state of data in your cache (cache coherency)

### Build a Circuit for a Serial adder
- Add two infinite input bit streams
- Streams sent with LSB first
1. Draw a state diagram
2. Write output and next-state tables
3. Encode states, inputs, and outputs as bits
4. Determine logic equations for next state and outputs
5. Draw the circuit