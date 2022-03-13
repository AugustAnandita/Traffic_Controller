
# Traffic_Controller
A traffic controller is designed using verilog code in esim.





## Contents

* [Abstract]
* [Introduction]
* [Tools used]
* [Reference circuit]
* [Traffic Controller Design]
* [Verilog code]
* [Model created]
* [Waveforms]
* [Author]
* [Ackwedgement]
* [Reference]





## Abstract

This report presents a traffic controller for a T-intersection using Verilog and corresponding waveform is achieved as per the state diagram of problem statement.



## Introduction
Due to the increasing number of commuters on roads, monitoring and control of traffic flow are one of the problems that countries are facing nowadays. This is due to the increasing number of commuters on roads. To address the issue this report presents a traffic controller design for a T intersection.






## Tools Used
eSim

It is an Open Source EDA developed by FOSSEE, IIT Bombay. It is used for electronic circuit simulation. It is made by the combination of two software namely NgSpice and KiCAD. For more details refer:

https://esim.fossee.in/home

NgSpice

It is an Open Source Software for Spice Simulations. For more details refer:

http://ngspice.sourceforge.net/docs.html

Makerchip

It is an Online Web Browser IDE for Verilog/System-verilog/TL-Verilog Simulation. For more details refer:

https://www.makerchip.com/

Verilator

It is a tool which converts Verilog code to C++ objects. For more details refer:

https://www.veripool.org/verilator/









##  Traffic controller Design
Problem Statement- 
Traffic controller design for a T-Intersection where we have 6 different states conditions and corresponding lights ( Red, Green, Yellow) status explained below





![Untitled](https://user-images.githubusercontent.com/100422485/158073735-e8395224-9052-4ecf-bf1d-e720f730acc0.png)




* **State Diagram**



![statetable](https://user-images.githubusercontent.com/100422485/158073459-3cfb5c87-a068-4b89-8ae3-9d9a052296ee.jpg)





## Verilog Code
\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/  /* verilator lint_off LATCH*/  /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/  /* verilator lint_off NULLPORT*/  /* verilator lint_off EOFNEWLINE*/  /* verilator lint_off WIDTHCONCAT*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/  /* verilator lint_off TIMESCALEMOD*/  

//Your Verilog/System Verilog Code Starts Here:
module Anandita_Traffic_Light(
        

           input clk,rst,
           output reg [2:0]light_S1,
           output reg [2:0]light_S2,
           output reg [2:0]light_S3,
           output reg [2:0]light_S4
           );

           parameter T1=0, T2=1, T3=2, T4=3, T5=4, T6=5;
           reg [3:0] count;
           reg [2:0] ps;
           parameter sec7=7, sec5=5, sec2=2, sec3=3;


           always@(posedge clk or posedge rst)
               begin
               if (rst==1)
               begin
               ps<T1;
               count<=0;
               end
               else



                         case(ps)
                                 T1: if(count<sec7)
                                            begin
                                            ps<=T1;
                                            count<=count+1;
                                            end

                                       else
                                            begin
                                            ps<=T2;
                                            count<=0;
                                            end
                                  T2: if(count<sec2)
                                            begin
                                            ps<=T2;
                                            count<=count+1;
                                            end

                                       else
                                            begin
                                            ps<=T3;
                                            count<=0;
                                            end
                                  T3: if(count<sec5)
                                            begin
                                            ps<=T3;
                                            count<=count+1;
                                            end

                                       else
                                            begin
                                            ps<=T4;
                                            count<=0;
                                            end
                                  T4: if(count<sec2)
                                            begin
                                            ps<=T4;
                                            count<=count+1;
                                            end

                                       else
                                            begin
                                            ps<=T5;
                                            count<=0;
                                            end
                                  T5: if(count<sec3)
                                            begin
                                            ps<=T5;
                                            count<=count+1;
                                            end

                                       else
                                            begin
                                            ps<=T6;
                                            count<=0;
                                            end
                                  T6: if(count<sec2)
                                            begin
                                            ps<=T6;
                                            count<=count+1;
                                            end

                                       else
                                            begin
                                            ps<=T1;
                                            count<=0;
                                            end
                                 default: ps<=T1;
                                 endcase
                           end
  

                         always@(ps)
                         begin


                               case(ps)


                                       T1:
                                         begin
                                             light_S1<=3'b001;
                                             light_S2<=3'b001;
                                             light_S3<=3'b100;
                                             light_S4<=3'b100;
                                          end
                                       T2:
                                         begin
                                             light_S1<=3'b001;
                                             light_S2<=3'b010;
                                             light_S3<=3'b100;
                                             light_S4<=3'b100;
                                          end
                                       T3:
                                         begin
                                             light_S1<=3'b001;
                                             light_S2<=3'b100;
                                             light_S3<=3'b001;
                                             light_S4<=3'b100;
                                          end
                                       T4:
                                         begin
                                             light_S1<=3'b010;
                                             light_S2<=3'b100;
                                             light_S3<=3'b010;
                                             light_S4<=3'b100;
                                          end
v                                       T5:
                                         begin
                                             light_S1<=3'b100;
                                             light_S2<=3'b100;
                                             light_S3<=3'b100;
                                             light_S4<=3'b001;
                                          end
                                       T6:
                                         begin
                                             light_S1<=3'b100;
                                             light_S2<=3'b100;
                                             light_S3<=3'b100;
                                             light_S4<=3'b001;
                                          end
                                       default:
                                         begin
                                             light_S1<=3'b000;
                                             light_S2<=3'b000;
                                             light_S3<=3'b000;
                                             light_S4<=3'b000;
                                          end
                                          endcase
                                  end


endmodule


 



//Top Module Code Starts here:
	module top(input logic clk, input logic reset, input logic [31:0] cyc_cnt, output logic passed, output logic failed);
		logic  rst;//input
		logic  [2:0] light_S1;//output
		logic  [2:0] light_S2;//output
		logic  [2:0] light_S3;//output
		logic  light_S4;//output
//The $random() can be replaced if user wants to assign values
		assign rst =0;
		Anandita_Traffic_Light Anandita_Traffic_Light(.clk(clk), .rst(rst), .light_S1(light_S1), .light_S2(light_S2), .light_S3(light_S3), .light_S4(light_S4));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule

## Model created

![symbol created](https://user-images.githubusercontent.com/100422485/157703539-b9b6dde5-d7bc-4d14-a64b-728ac6547218.png)



![symbol](https://user-images.githubusercontent.com/100422485/157703543-594acfcc-fb52-46fa-86d4-6ef903e1e95a.png)





## Waveforms







![Screenshot (8459)](https://user-images.githubusercontent.com/100422485/157703524-b22e6c91-2405-49d4-b53e-2c0bd0409254.png)







## Author


```bash
Anandita, National Institute of Technology, Patna
```


## Acknowledgements


 - Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
 
 -FOSSEE, IIT Bombay

 -Steve Hoover (Founder, Redwood EDA)

 -Sumanto Kar (eSim Team, FOSSEE, IIT Bombay)

 
## References

-[1]	NPTEL Lecture on Digital Design by Professor Srinivasan.

