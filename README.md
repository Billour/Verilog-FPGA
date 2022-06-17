# Verilog-FPGA
Verilog FPGA tutorial

重點觀念:
1. 學Verilog 要用「數位邏輯」的觀念，不可用C語言的思維。
2. 時序圖  (時序對於Verilog 很重要)
3. 狀態機
4. 序向邏輯電路 (Sequential Logic Circuit)
5. 數位電路的「導線」
6. Verilog 可以設定 波形、單位、精度、強度(strength)
7. 示波器
8. 邏輯訊號產生器
9. 數位邏輯達成硬體加速
10. GPU 是用面積達成硬體加速
11. FPGA 是用同一個上升時序，同時間處理很多指令(並行處理)，來達成硬體加速。
12. C HLS verilog。C-to-Verilog.com: High-Level Synthesis Using LLVM
13. 


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
