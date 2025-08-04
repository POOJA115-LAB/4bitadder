# 4bitadder
Designed a 4-bit adder in Xilinx Vivado using Verilog HDL. Inputs A, B (4-bit) and Cin generate Sum (4-bit) and Cout. Used a testbench to simulate all input cases and verify correctness. Synthesized the design and analyzed the RTL schematic, logic connections, and synthesis reports

//Main Code
module bit4_adder(
    input [3:0] a, b,
    input cin,
    output [3:0] sum,
    output cout
);
    assign{cout,sum}=a+b+cin;
endmodule


//Test Bench
module stimulii;
    reg [3:0] a, b;
    reg       cin;
    wire [3:0] sum;
    wire      cout;
bit4_adder uut ( .a(a), .b(b), .cin(cin),.sum(sum), .cout(cout));
    initial begin
        a = 4'b0000; b = 4'b0000; cin = 0;
        #10 a = 4'b0011; b = 4'b0101; cin = 0;
        #10 a = 4'b1111; b = 4'b0001; cin = 0;
        #10 a = 4'b1010; b = 4'b0000; cin = 1;
        #10 a = 4'b1111; b = 4'b0000; cin = 1;
        #10;
        $stop;
    end
endmodule

