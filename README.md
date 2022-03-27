decoder_3_8
module decoder_2_4(E , In , Out);
input E;                                            //宣告致能輸入E
input  [1:0]   In;                                  //宣告輸入In[0]~In[1]
output [3:0]   Out;                                 //宣告輸出Out[0]~Out[3]
wire  [3:0]   Out;
assign   Out = E ? 1'b1 << In : 4'h0;               //E為1時輸出1位元的二進制左移In個位元，為0輸出0
endmodule


module decoder_3_8(E , In , Out);
input  E;                                           //宣告致能輸入E
input  [2:0] In;                                    //宣告輸入In[0]~In[2]
output  [7:0] Out;                                  //宣告輸出Out[0]~Out[7]
wire E1 , G1 , G2;                                  //宣告三對8解碼器致能線
                                                    //宣告2對4解碼器1之致能線G1
                                                    //宣告2對4解碼器2之致能線G2



  not u1(E1 , In[2]);                               //E1=致能線E1與輸入In[2]透過NOT閘連接
  and a1(G1 , E   In[2]);                           //G1=致能線E與輸入In[2]透過AND閘連接
  and a2(G2 , E , E1);                              //G2=致能線E與輸入E1透過AND閘連接
  decoder_2_4 block1(G1  , In[1 : 0] , Out[7 : 4]);
  decoder_2_4 block2(G2  , In[1 : 0] , Out[3 : 0]);
  endmodule
