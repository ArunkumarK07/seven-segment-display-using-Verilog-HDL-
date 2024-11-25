Aim
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.
module seven_segment_display ( input wire
[3:0] binary_input, output reg [6:0]
seg_output ); always @(*) begin
 case (binary_input) 4'b0000:
seg_output = 7'b0111111; // 0
 4'b0001: seg_output = 7'b0000110; // 1
 4'b0010: seg_output = 7'b1011011; // 2
 4'b0011: seg_output = 7'b1001111; // 3
 4'b0100: seg_output = 7'b1100110; // 4
 4'b0101: seg_output = 7'b1101101; // 5
 4'b0110: seg_output = 7'b1111101; // 6
 4'b0111: seg_output = 7'b0000111; // 7
 4'b1000: seg_output = 7'b1111111; // 8 4'b1001:
seg_output = 7'b1101111; // 9 default: seg_output =
7'b0000000; // blank or error endcase end endmodule
Testbench for Seven-Segment Display:
module ledseg_tb;
 reg [3:0]
seg_in; wire
[6:0] s;
 ledseg dut(
.seg_in(seg_in),
 .s(s)
 );
 initial begin
seg_in = 4'b0000; #100;
seg_in = 4'b0001; #100;
seg_in = 4'b0010; #100;
seg_in = 4'b0011; #100;
seg_in = 4'b0100; #100;
seg_in = 4'b0101; #100;
seg_in = 4'b0110; #100;
seg_in = 4'b0111; #100;
seg_in = 4'b1000; #100;
seg_in = 4'b1001; #100;
seg_in = 4'b1010; #100;
seg_in = 4'b1111; #100;
$finish; end endmodule

conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs. This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
