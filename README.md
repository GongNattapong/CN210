# รายงานวิชา CN210

## สรุปเนื้อหาวิชา

### สรุปเนื้อหา
วิชาสถาปัตยกรรมคอมพิวเตอร์ จะเรียนรู้เรื่องการทำงานของ Cpu MIPS แบบละเอียด โดย MIPS เป็นหน่วยประมวลผลที่มีความจำ 32 bits ออกแบบโดยบริษัท MIPS มี 3 รูปแบบ 
คือ R-Format จะใช้คำนวณค่า ,I-Format จะใช้อ่านค่าและนำค่าที่เก็บมาใช้ และ J-Format จะใช้ข้ามไปใช้คำสั่งที่ตำแหน่งอื่นๆ ซึ่ง cpu จะทำงานคำสั่งเป็นขั้นเป็นตอน คำสั่งที่เจอส่วนใหญ่จะเป็น add sub and or slt beq jump lw sw โดยจะมีรูปแบบการทำงานแบบ Single Cycle, Multicycle และ Pipelining โดย Pipelining จะทำงานเร็วสุดแต่ต้องเขียนคำสั่งให้การทำงานของคำสั่งทุกคำสั่งตามกันจนจบ ส่วน Multicycle จะเร็วรองลงมา และ Single Cycle จะช้าสุด ถ้าต้องทำคำสั่งเยอะมากๆ จะเห็นผลได้ชัด

#### ส่งการบ้านครั้งที่ 1
  ![](Clip1.png)

  * [CLIP1(Youtube)](https://youtu.be/qxfaD4DFBt8)
    
  ** คำอธิบาย : คลิปนี้จะอธิบายเกี่ยวกับ MIPs โดย MIPS เป็นหน่วยประมวลผลที่มีความจำ 32 bits ออกแบบโดยบริษัท MIPS มี 3 รูปแบบ คือ R-Format,I-Format และ
  J-Format ซึ่งจะสาธิตการใช้ MIPS ในการคำนวณซึ่งจะใช้ R-Format ในการเก็บค่า ซึ่งฟังก์ชั่นในการคำนวณที่สาธิตคือ ฟังก์ชัน add ซึ่ง R-Format จะประกอบ
  ด้วย op rs rt rd shamt func โดย op มีไว้บอกว่าเป็น R-type หรือ I-type rs rt rd ใช้บอกว่าเก็บค่าไว้ Register ตัวไหน shamt ใช้บอกว่าจะ 
  shift ไปทางไหน func ใช้บอกว่าจะทำคำสั่งอะไร โดยโครงสร้าง R-Format เป็นดังนี้
               
   | โครงสร้าง | op | rs | rt | rd | shamt | func |      
   |----------|----|----|----|----|-------|------| 
   | จำนวนบิต  | 6  |  5 |  5 |  5 |   5   |   6  | 
   
   โดยคำสั่ง add คือคำสั่งบวก มีโครงสร้างดังนี้
   
                    Add  $rd, $rs, $rt
                โดย $rs, $rt คือ register ที่จะรับค่ามาจาก pc แล้วมาทำฟังก์ชั่นตรรกะศาสตร์
                    $rd คือ register ที่จะเก็บค่าจากการทำฟังก์ชั่นตรรกะศาสตร์ของ $rs กับ $rt
               
               
#### ส่งการบ้านครั้งที่ 2

  ![](Clip2.png)
  
  * [CLIP2(Youtube)](https://youtu.be/QzaD13TMT6o)
  
  ** คำอธิบาย : คลิปนี้จะอธิบายเกี่ยวับการทำงานของ cpu โดยการทำงานจะเริ่มต้นเมื่อเปิดสวิซท์ จากนั้นมันจะอ่านคำสั่งที่ตำแหน่ง 0 แล้วทำงาน ไม่ว่าจะเป็นการ jump คำสั่ง 
               add คำสั่ง load คำสั่ง store ทุกอย่างจะรันเป็นขั้นเป็นตอนตามรูป I-Format หรือ R-Format หรือ J-Format ขึ้นอยู่กับ opcode ของคำสั่ง
  
#### ส่งการบ้านครั้งที่ 3

  ![](Clip3.png)
  
  * [CLIP3(Youtube)](https://youtu.be/hyol9zuLm_Q)
  
  ** คำอธิบาย : คลิปนี้จะอธิบายเกี่ยวกับความแตกต่างระหว่าง Single Cycle กับ Multicycle โดยที่เห็นได้ชัดคือ รอบการทำงานของ Multicycle จะมากกว่า Single 
               Cycle จะมีรูปแบบสถาปัตยกรรมที่ต่างกัน Multicycle จะมี ALU น้อยกว่า Single Cycle แต่จะมี Mux มากกว่า Single Cycle และที่เห็นได้ชัดเจนที่สุดคือ 
               Multicycle จะใช้เวลาในการทำคำสั่งน้อยกว่า Single Cycle โดยสรุปเป็นตารางได้ดังนี้
               
   |ลักษณะ|Single Cycle| Multi Cycle|
   |------|------------|------------|
   |รอบการทำงาน| 1 รอบต่อ 1 คำสั่ง|มากกว่า 1 รอบต่อ 1 คำสั่ง|
   |รูปแบบสถาปัตย์|Harvard architecture|Von Neuman architecture|
   |จำนวน ALU| 1 ตัว + 2 Adder| 1 ตัว|
   |จำนวน Mux| 4 ตัว| 5 ตัว|
   |เวลาในการทำงาน| 8 ns|6.3 ns|
   
  
#### ส่งการบ้านครั้งที่ 4

  ![](Clip4.png)
  
  * [CLIP4(Youtube)](https://youtu.be/hsoW6MwFPeI)
  
  ** คำอธิบาย : คลิปนี้จะอธิบายเกี่ยวกับการทำงานของคำสั่ง Load Word ในรูปแบบ Multicycle โดยเริ่มต้นจากการ Fetch จะเป็นการส่งค่าให้ register และส่งค่าให้ ALU 
               เพื่อ +4 และพร้อมทำขั้นตอนต่อไป เสร็จแล้วก็ทำการ Fetch+1 เพื่อเก็บค่าเข้า register 2 ตัว และส่งเข้าไปที่ ALUOut หลังจากนั้นทำการ Mem1 เป็นการส่ง
               ค่าจาก Register เข้า ALU เพื่อทำคำสั่งแล้วส่งให้ ALUOut หลังจากนั้นก็ส่งเข้า Memory data register ซึ่งมีคำสั่งเป็น Step ดังนี้
        
    T1 Fetch               IR <- MEMORY[PC] & PC <- PC + 4
    T2 Fetch + 1           A <- Reg[IR[25-21]] & B <- Reg[IR[20-16]] & ALUOut <- PC + signext(IR[15-0]) << 2
    T3 Dispatch1: Mem1     ALUOut <- A + sign_extend(IR[15-0])
    T4 Dispatch 2: Lw2     Memory data register <- ALUOut
    
#### ส่งการบ้านครั้งที่ 5
  
  ![](Clip5.png)
  
  * [CLIP5(Youtube)](https://youtu.be/LtYXk1vCkGU)
  
  ** คำอธิบาย : คลิปนี้จะอธิบายเกี่ยวกับการทำงานของคำสั่ง Branch On Equal ในรูปแบบ Multicycle โดยจะเริ่มต้นจากการ Fetch จะเป็นการส่งค่าให้ register และส่งค่า
               ให้ ALU เพื่อ +4 และพร้อมทำขั้นตอนต่อไป เสร็จแล้วก็ทำการถอดรหัสเพื่อเก็บค่าเข้า register 2 ตัว และอ่านค่า offset+pc จากนั้นส่งเข้าไปที่ ALUOut 
               หลังจากนั้นทำการเช็ค register 2 ตัวนี้ว่าเท่ากันมั้ย ถ้าเท่ากันจะส่งให้ ALUOut แต่ถ้าไม่เท่ากันจะส่งให้ PC
               
    T1 Fetch               IR <- MEMORY[PC] & PC <- PC + 4
    T2 Fetch + 1           A <- Reg[IR[25-21]] & B <- Reg[IR[20-16]] & ALUOut <- PC + signext(IR[15-0]) << 2
    T3 Dispatch 1     If (A == B) : PC = ALUOut : PC <- 0 
             
#### ส่งการบ้านครั้งที่ 6

  ![](Clip6.png)
  
  * [CLIP6(Youtube)](https://youtu.be/pyeTy94TIKw)
  
  ** คำอธิบาย : คลิปนี้จะอธิบายเกี่ยวกับการทำงาน State Machine ของ r-format ใน cpu รูปแบบ Multicycle โดยจะส่วนประกอบของการทำงานจะมีั้ง Fetch, 
               Reg/Dec, Exec, Wr โดยการทำงานจะใช้ MemRead, MemWrite, lorD, IRWrite, ALUSrcA, ALUSrcB, ALUOP, PCWrite, PCSource, RegWrite, 
               MemtoReg และ RegDst ในการทำงาน โดยมี State Machine คร่าวๆ ดังนี้
               
    T1 : Fetch  MemRead                        T2 : Decode  ALUSrcA = 0 (=PC)
                MemWrite = 0                                ALUSrcB = 3 (=signext(IR<<2))
                lorD = X                                    ALUOP = 0 (=add)
                IRWrite = 0
                
    T3 : ExecALU  ALUSrcA = 1 (=A=Reg[$rs])    T4 : WriteReg  RegWrite = 1 (Reg[$rd] <- ALUout)
                  ALUSrcB = 0 (=B=Reg[$rt])                   MemtoReg = 0 (=ALUout)
                  ALUOP = 0 (=IR[28-26])                      RegDst = 1 (=$rd)
                     
  #### ส่งการบ้านครั้งที่ 7
 
  ![](Clip7.jpg)
  
   * [CLIP7(Youtube)](https://youtu.be/YiI7OqvRDE0)
  
  ** คำอธิบาย : คลิปนี้จะอธิบายเกี่ยวกับ Pipelining ว่ามันคืออะไร มีองค์ประกอบอะไร ข้อดี ปัญหาของ Pipelining การทำงาน ความแตกต่างของการทำงาน
               โดย Pipelining เป็นหน่วยความจำที่อ่านคำสั่งต่างๆ ผ่านกระบวนการต่างๆ จนจบคำสั่งคล้าย Register แต่ต่างที่ Pipelining เก็บค่าได้มากกว่า Register 
               แต่ทำงานช้ากว่า Register โดย Pipelining จะสามารถทำคำสั่งได้มากกว่า 1 คำสั่งเพราะใช้หลักการแบบเมื่อกระบวนการทำงานทำงานคำสั่งก่อนหน้า จะ
               สามารถทำงานคำสั่งต่อไปได้ แต่มันมีปัญหาคือคำสั่งมีโอกาสทำกระบวนการเดียวกันเกิน 1 คำสั่ง หรือมีโอกาสที่จะผิดพลาดเมื่อคำสั่งหลังต้องการรับค่าจากคำสั่งก่อน
               หน้า แต่คำสั่งก่อนหน้ายังไม่เสร็จ ซึ่งวิธีแก้ปัญหามี 4 อย่างคือ Waiting Forwarding Load-Forwarding และ Reordering
