EXP-1

Date:

                     SIMULATION OF LOGIC GATES ,ADDERS AND SUBTRACTORS
                                               
AIM: To simulate Logic Gates ,Adders and Subtractors using Vivado 2023.2.

APPARATUS REQUIRED: VIVADO 2023.2

PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

LOGIC GATES LOGIC DIAGRAM:

![301405876-ee17970c-3ac9-4603-881b-88e2825f41a4](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/35b01533-4316-40e9-9544-037d0a6540ad)

 VERILOG CODE
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
OUTPUT WAVEFORM

![328455264-a62e4538-0094-4126-b762-1a1fdc1e8931](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/26d53fcf-e177-40a0-8717-cf378ae8852d)


HALF ADDER LOGIC DIAGRAM

![328456195-8dbaa111-3916-4e39-bd03-852cd2d76982](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/79e1b294-5e5e-4570-9e3d-b55a0946e12d)


VERILOG CODE
```
module half_adder(a,b,sum,carry);

input a,b;

output sum,carry;

xor g1(sum,a,b);

and g2(carry,a,b);

endmodule
```
OUTPUT WAVEFORM

![328456731-d325278a-9829-4e71-b638-70f7285a1dcd](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/c5dd617b-ff97-4474-95b2-c05936b0024e)

FULL ADDER LOGIC DIAGRAM

![328457240-8713d8b5-e4b6-4c9d-a00b-41eae22c9a2c](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/e6e68dc7-b4b2-4c35-875c-ab20ba5c78aa)

VERILOG CODE
```
module fulladder(a,b,c,sum,carry);

input a,b,c;

output sum,carry;

wire w1,w2,w3;

xor(w1,a,b);

xor(sum,w1,c);

and(w2,w1,c);

and(w3,a,b);

or(carry,w2,w3);

endmodule
```
OUTPUT WAVEFORM

![328457694-5c2e8258-da0f-4afd-98eb-f56bd8c7ec30](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/c510528a-d700-4dce-883f-7012bd4ee77a)


HALF SUBTRACTOR LOGIC DIAGRAM

![328457975-a2ece9c5-3ea5-4656-ac14-51ae2f150460](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/d8174bdc-0cd8-4bbb-b72d-fa35d7ee117d)



VERILOG CODE
```
module halfsub(a,b,diff,borrow);

input a,b;

output diff,borrow;

xor(diff,a,b);

and(borrow,~a,b);

endmodule
```
OUTPUT WAVEFORM

![328458425-4bdf087c-428c-4822-bc46-c5e7dd254033](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/ee8a87d1-94e6-40bb-88f3-7c2ef608e895)

FULL SUBTRACTOR LOGIC DIAGRAM

![328458649-1b5c2122-0560-4d64-8eca-093cc6a727ec](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/26ff67e7-4270-4924-a914-866e89a2f29d)

VERILOG CODE
```
module fs(a,b,bin,d,bout);

input a,b,bin;

output d,bout;

wire w1,w2,w3;

xor(w1,a,b);

xor(d,w1,bin);

and(w2,~a,b);

and(w3,~w1,bin);

or(bout,w3,w2);

endmodule
```
OUTPUT WAVEFORM

![328458991-bc8d00b2-5048-427d-bf2c-c02c3045914c](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/d63f766b-77ba-4979-bba3-f8d511e98895)


RIPPLE CARRY ADDER LOGIC DIAGRAM

![328459224-a99aff44-dfa3-4e7b-9da8-69196df7a695](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/f50c0d73-626c-4392-b076-9f2191a6e0fe)

VERILOG CODE
```
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule

module rca_8bit(a,b,cin,s,cout);
input [7:0]a,b;
input cin;
output [7:0]s;
output cout;
wire [7:1]w;
fulladder f1(a[0], b[0], cin, s[0], w[1]);
fulladder f2(a[1], b[1], w[1], s[1], w[2]);
fulladder f3(a[2], b[2], w[2], s[2], w[3]);
fulladder f4(a[3], b[3], w[3], s[3], w[4]);
fulladder f5(a[4], b[4], w[4], s[4], w[5]);
fulladder f6(a[5], b[5], w[5], s[5], w[6]);
fulladder f7(a[6], b[6], w[6], s[6], w[7]);
fulladder f8(a[7], b[7], w[7], s[7], cout);
endmodule
```
OUTPUT WAVEFORM

![328459610-6bf9e606-80cb-4def-8503-210f60b0fbd4](https://github.com/Naradinakar/VLSI-LAB-EXP-1/assets/161109578/8068a70b-72d2-4385-af93-7a076cca5b7e)

RESULT:

       simulation of Logic Gates ,Adders and Subtractors using Vivado 2023.2 is verified.
