# Verilog-FPGA
Verilog FPGA tutorial

重點觀念:
1. 學Verilog 要用「數位邏輯 Logic gate」的觀念，不可用C語言的思維。
2. 時序圖  (時序對於Verilog 很重要)
3. 狀態機(Finite State Machines Modeling)
4. 序向邏輯電路 (Sequential Logic Circuit)
5. 數位電路的「導線」wire
6. Verilog 可以設定 波形、單位、精度、強度(strength)
7. 示波器，Verilog 是否在上升波型、或下降波型觸發程式碼
8. 邏輯訊號產生器
9. FPGA 處理影像時速度很快，且IC 發熱量低，可以做影像即時處理。
10. FPGA 是用數位邏輯閘(Logic gate)面積達成硬體加速
11. FPGA 是用同一個上升時序，同時間處理很多指令(並行處理)，來達成硬體加速。
12. C HLS verilog。C-to-Verilog.com: High-Level Synthesis Using LLVM，但是還是要用 Verilog 的觀念下去寫程式。
13. 
  
Verilog 最重要的部分，負責描述模組的電路架構與功能  
主要有四種層次的描述：（高階→低階 )  
行為層次（Behavior Level）  
資料流層次（Dataflow Level）  
邏輯閘層次（Gate Level）  
電晶體層次（Switch Level）  
------------
重點觀念:
FPGA 是並行處理指令的，Example 指令1跟指令2是同時執行。  
1. Procedural Assignments(cont' d)  
  Race condition  
    -When the final result of simulating two (or more)  
    concurrent processes depends on their order of execution  
 Example:  
   always @(posedge clock)  
       b = a;  
   always @(posedge clock)  
       a = b;  
 Solution:  
    always @(posedge clock)  
       b <= a;  
    always @(posedge clock)  
       a <= b;  
   重點在於 <= (要使用 < 符號，才不會 Race condition)  
  
出自 9.2.2 The nonblocking procedural assignment - verilog-std-1364-2005.pdf
  
  範例：  
  
module 模組名稱( In1, In2, Out1, Out2, InOut1 );  
    input in1, in2;  
    output Out1, Out2;  
    inout InOut1;  
  
    wire In1, In2, Out1;  
    wire InOut1;  
    reg Out2;  
  
    // 以下為三種層級分別描述 In1 與 In2 and 做 and 運算的方法  
    // 邏輯閘層次( Gate Level )  
    and and1( Out1, In1, In2 );  
  
    // 資料流層次( Dataflow Level )  
    assign Out1 = In1 & In2;  
  
    // 行為層次( Behavior Level )  
    allways @(*) begin  
        Out2 = In1 & In2;  
    end  
endmodule  
  
  Open Code  
  https://opencores.org/  
  
  petalinux  
  PetaLinux tools enable developers to synchronize the software platform with the hardware design as it gains new features and devices. PetaLinux tools will automatically generate a custom, Linux Board Support Package including device drivers for Xilinx embedded processing IP cores, kernel and boot loader configurations.
Parent organization: Advanced Micro Devices  
    
  [petalinux 教學](https://ys-hayashi.me/2021/08/xilinx-petalinux-01/)  
    
--補充教學  
  1.數位邏輯  
  https://ocw.nthu.edu.tw/ocw/index.php?page=course_news_content&cid=230&id=1023  
  2. [溤天懋 lesson2 筆記](https://numerous-earl-9fa.notion.site/Xilinx-Lesson-2-64dd21013e2e4b968c354b9eea8f7229)
