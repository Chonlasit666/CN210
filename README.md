# CN210
## สรุปเนื้อหาโดยรวมของMIPS Instruction(ชุดคำสั่งของMIPS)
<br>**MIPS  Instruction** เข้ารหัสในรูปแบบ Binary
<br>**ชุดคำสั่งทุกคำสั่งมีความยาว 32 Bits**
<br>**คำสั่งมี 3 ประเภทใหญ่ๆได้แก่**
<br>**R-Format** -เป็นคำสั่งที่ใช้ทางคณิตศาสตร์และตรรกศาสตร์ มีรูปแบบดังนี้

|**R-Format**|     |     |     |     |     |
|------------|-----|-----|-----|-----|-----|
|     op     | $rs | $rt | $rd |shamt|func |
|     6bit   | 5bit| 5bit| 5bit|5bit |6bit |

 |**คำสั่งอื่นๆ**|     |     |     |     |     
 |------------|-----|-----|-----|-----|
 |ALU         | alu | $rd | $rs | $rt |     
 |JR          | jr  | $rs |     |     |     

**I-Format**(เป็นคำสั่งที่ใช้ย้ายข้อมูล)

|**I-Format**|     |     |     |
|------------|-----|-----|-----|
|     op     | $rs | $rt | offset |
|     6bit   | 5bit| 5bit| 16bit  |

|**คำสั่งอื่นๆ**    |     |     |        |         | 
|------------|-----|-----|---------|--------|
|ALUi        |alui | $rt | $rs     | value   |
|Data Transfer | lw | $rt | offset($rs)  |   |
|             |  sw | $rt | offset($rs)  |   |
|Branch      |  beq | $rs | $rt | offset |   | 

**J-Format** -เป็นคำสั่งjump จาก Address ปัจจุบัน ไปยังอีกตำแหน่งนึง

|**J-Format**|     |
|------------|-----|
|     op     | Address |
|     6bit   | 26bit|

|**คำสั่งอื่นๆ**    |           |
|------------|------------|
| jump       |  j address|
| jump&link  |jal address|

## การบ้านครั้งที่ 1

### คำสั่ง ADD ในคอมพิวเตอร์ MIPS

ชุดคำสั่งอยู่ในประเภท R-format
<br>Format ของ R - Format

|**R-Format**|     |     |     |     |     |
|------------|-----|-----|-----|-----|-----|
|     op     | $rs | $rt | $rd |shamt|func |
|     6bit   | 5bit| 5bit| 5bit|5bit |6bit |

<br>op = Operation code(6 bits)
<br>**หากเป็นR-format default คือ 000000**
<br>rs = 1st register operand(5 bits)
<br>rt = 2nd register operand(5 bits)
<br>rd = register destination(5 bits)
<br>shamt = shift amount(00000 หากไม่มีการใช้ส่วนนี้)(5bits)
<br>funct = function code(6 bits)

<br>**function code**

<br>![image](https://i.stack.imgur.com/QwYfS.gif)

<br>ตัวอย่าง ADD $16 $17 $18
<br> rd = rs + rt

<br>หากเข้าformatจะได้

|op  | rs  |  rt | rd  | shamt  | func  |
----- | ----- | ----- | ----- | ----- | ----- |
| 000000 | 10011 | 10010 | 10000 | 00000 | 100000 |

<br>คำสั่งนี้จะเป็นการนำregisterตัวที่ 17 รวมกับตัวที่ 18 แล้วนำไปเก็บไว้ที่registerตัวที่16

## ส่งการบ้านครั้งที่ 1

### [คลิปอธิบายคำสั่ง ADD in MIPS](https://drive.google.com/file/d/1e2wFgEWxxR-G7eHH0iZLWzz-NmiGx2iD/view?usp=sharing)

## การบ้านครั้งที่ 2

### อธิบายการทำงานของ CPU

<br>**ภาษามนุษย์ที่ใช้ในการเรียกคำสั่ง**


                    === JAVA Language ===

    class Test{

        public static void main(String[] args){
    
            int a = 10;
        
            int b = 20;
        
            int c = a+b;
        
        }
    
    }
 <br>**machine languageที่แปลงมาจากภาษามนุษย์**
 
 
                    === Machine Language ===
        Address          Instrution code
        00000000:           08400000        //j  01000000
        
เมื่อมีการทำงานCPUจะเริ่มทำงานที่Address 00000000 ซึ่งในแต่ละAddress จะมีชุดคำสั่งที่ให้CPUทำงาน
<br>เมื่อพบแล้วจะทการแปลงชุดคำสั่งจากเลขฐาน16 เป็นฐาน2 ในตัวอย่างคือ 08400000

<br>จะได้ในฐาน2คือ 0000 1000 0100 0000 0000 0000 0000 0000
หลังจากนั้นจะทำการเช็ค6bitsแรกว่าทำไงในชุดคำสั่งไหนในที่นี้คือคำสั่ง J-formatแล้วทำตามชุดคำสั่งจนจบ

## ส่งการบ้านครั้งที่ 2

### [คลิปอธิบายการทำงานของ CPU](https://youtu.be/Js-kAyI459E)

## การบ้านครั้งที่ 3

### เปรียบเทียบ Single Cycle และ Multi Cycle 

<br>**Single cycle**

![image](https://cseweb.ucsd.edu/~j2lau/cs141/single_cycle_cpu_datapath.png)

<br>จากรูปประกอบด้วย

    *  3 ALU

    *  2 Memory

    * คำสั่งจบใน Cycle เดียว

    * เวลาแต่ละคำสั่งเท่ากัน(เป็นเวลาของคำสั่งที่นานที่สุด)

<br>**Multi cycle**

![image](https://people.cs.pitt.edu/~don/coe1502/current/Unit4a/fig548.jpg)

<br>จากรูปประกอบด้วย

    *  1 ALU 
    
    *  1 Memory 
    
    *  คำสั่งไม่จบใน1cycle
    
    *  เวลาแต่ละคำสั่งไม่เท่ากัน
    
    * มีการพักData ที่ A B ก่อน
    
    *หลังากคำนวณนำค่าไปเก็บในALUOUT

### งานครั้งที่ 3
[คลิปงานครั้งที่ 3 อธิบายความแตกต่างระหว่าง Single Cycle และ Multi Cycle](https://youtu.be/6s3bkImpZWE)
## การบ้านครั้งที่ 4

### การทำงานแบบ Multi cycle ของคำสั่ง Load Word(lw) ใน MIPS

![image](https://i.imgur.com/mWXHWpT.png)

จากรูป Multi cycle 

lw $rt,offset($rs)

<br>**คำสั่งload wordมี5ขั้นตอน**

    1. IR = Memory[PC]

      PC = PC + 4
      
<br>**นำค่าจากmemoryมาเก็บในIR และบวกค่า pc ไป 4**

    2. A = Reg[IR[25-21]]

      B = Reg[IR[20-16]]
   
      ALUout = PC + (sign-extend(IR[15-0])<<2)
 
 
<br>**นำค่าrs rt ไปเก็บไว้ที่ A , B นำค่าoffset(แปลงเป็น 32 bitsแล้วshift bitsไป2)มาที่ALUแล้วรวมกับ PC+4 เก็บไว้ที่ ALUOUT**

    3. ALUOut = A + sign-extend(IR[15-0])

<br>**นำ A + Sign-Extend(IR15-0)**

    4. MDR = Memory[ALUout]

<br>**การชี้ Address นี้ที่ memory เพื่ออ่านค่าออกมา**

    5. Reg[IR[20-16]] = MDR
    
<br>**ค่าที่อ่านออกมาได้ไปเก็บในrt**

### งานครั้งที่ 4
  [คลิปงานครั้งที่ 4 การทำงานคำสั่ง lw ใน Multi Cycle](https://youtu.be/WP203l_PNBA)

## สรุปเนื้อหาการบ้านครั้งที่ 5
  **การทำงานของคำสั่ง beq ใน Multi Cycle**
  ![multicycle](https://people.cs.pitt.edu/~don/coe1502/current/Unit4a/fig548.jpg)
  จากรูป Multi cycle 

beq $rs,$rt,$offset

<br>**คำสั่ง Branch on equal มีการทำงาน 3 ขั้นตอน ดังนี้**

    1. IR = Memory[PC]

      PC = PC + 4
   
 *(อ่านคำสั่งจาก Memory มาเก็บใน Instruction register ขณะเดียวกัน PC = PC + 4 )*
   
    2. A = Reg[IR[25-21]]

      B = Reg[IR[20-16]]
   
      ALUout = PC + (sign-extend(IR[15-0])<<2)
   
 *(แปลงคำสั่ง นำค่า rs กับ rt เก็บที่ A,B นำค่า offset(แปลงเป็น 32 bits และ shiftซ้าย 2) มาที่ ALU และนำมาบวกกับ PC(PC+4) )*
    
    3. if(A==B) then PC = ALUout

 *(branch on equal จะเป็นคำสั่งที่ดูว่า A=B มั้ย ถ้าเท่ามันจะทำการ jump ไปที่ address ใหม่(ที่เกิดจาก offset + PC)*
 ### งานครั้งที่ 5
  [คลิปงานครั้งที่ 5 การทำงานของคำสั่ง beq ใน Multi Cycle](https://youtu.be/jKVPW9OTVnA)

## สรุปเนื้อหาการบ้านครั้งที่ 6
  **State Machine ของ คำสั่งชนิด R-Format**
  ![statemachine](https://image3.slideserve.com/5922537/the-four-stages-of-r-type-l.jpg)
  
  #### มีทั้งหมด 4 Cycle ด้วยกันดังนี้
  
  ### Cycle 1 Instruction Fetch
  
  ![stateno1](https://image1.slideserve.com/3211244/slide21-n.jpg)
  
  **จากรูปภาพ ตัวหนังสือสีแดง แสดงถึงส่วนที่ทำใน Cycle นี้ ตัวหนังสือสีดำ แสดงถึงส่วนที่ไม่ได้ทำใน Cycle นี้** 
  
  <br>MemRead = 1 คือ ทำการอ่านค่าจาก Memory
  <br>IorD    = 1 คือ เช็คว่า PC นั้นชี้ไปที่ Address ใดใน Memory
  <br>IRWrite = 1 คือ นำค่าจาก Address Memory ที่ถูกชี้ ไปเก็บไว้ใน IR
  <br>ALUSrcA = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ PC ค่าที่ถูกเขียนใน IR จะมี ALUSrcA ทำการควบคุม
  <br>ALUSrcB = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ 4 ค่าที่ถูกเขียนใน IR จะมี ALUSrcB ทำการควบคุม
  <br>ALUOP   = ADD คือ การนำค่า PC มาบวกกับ 4
  <br>PCWrite = 1, PCSource = 1   นำผลลัพธ์การคำนวณเขียนทับที่ PC = PC + 4
  
  ### Cycle 2 Decode & Register Fetch
  
  ![stateno2](https://image1.slideserve.com/3211244/slide23-n.jpg)
  
  **จากรูปภาพ ตัวหนังสือสีแดง แสดงถึงส่วนที่ทำใน Cycle นี้ ตัวหนังสือสีดำ แสดงถึงส่วนที่ไม่ได้ทำใน Cycle นี้** 
   
   <br>ALUSrcA = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ PC 
   <br>ALUSrcB = 3 คือ Mux เลือกค่าจาก 3 ซึ่งคือ Offset 
   <br>ALUop   = 0 คือ ALUop จะทำการควบคุมคำสั่ง ADD
   
   ### Cycle 3 R-Format Execution
  
  ![stateno3](https://image1.slideserve.com/3211244/slide25-n.jpg)
  
  **จากรูปภาพ ตัวหนังสือสีแดง แสดงถึงส่วนที่ทำใน Cycle นี้ ตัวหนังสือสีดำ แสดงถึงส่วนที่ไม่ได้ทำใน Cycle นี้** 
  
  <br>ALUSrcA = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ $rs 
  <br>ALUSrcB = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ $rt
  <br>ALUop   = 2 คือ ALUop จะทำการควบคุมคำสั่งให้เป็นไปตามคำสั่งใน IR
  
   ### Cycle 4 R-Format Write Register
  
  ![stateno4](https://image1.slideserve.com/3211244/slide27-n.jpg)
  
  **จากรูปภาพ ตัวหนังสือสีแดง แสดงถึงส่วนที่ทำใน Cycle นี้ ตัวหนังสือสีดำ แสดงถึงส่วนที่ไม่ได้ทำใน Cycle นี้** 
  
  <br>RegWrite = 1 คือ นำค่าจาก ALUout มาเขียนใน $rd
  <br>MemtoReg = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ ALUout
  <br>RegDst   = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ $rd
  
  ### งานครั้งที่ 6
  [คลิปงานครั้งที่ 6 อธิบาย State Machine ของ คำสั่งชนิด R-Format](https://youtu.be/nz5YiuctV4U)
  
## สรุปเนื้อหาการบ้านครั้งที่ 7
 
 **Pipelining**
Pipelining เป็นวิธีการทำคำสั่งที่ช่วยให้ทำไวขึ้น หลักๆคือ 1 คำสั่ง จบในหลายๆ Cycle ถึงแม้ว่าจะทำคำสั่งแรกยังไม่เสร็จแต่สามารถนำคำสั่งถัดไปมาทำงานต่อได้

<br>รูปต่อไปนี้คือการยกตัวอย่างว่าใช้กับไม่ใช้แตกต่างกันอย่างไร
![pipe1](https://cs.stanford.edu/people/eroberts/courses/soco/projects/risc/pipelining/laundry1.gif)

<br>จากภาพด้านบนจะสังเกตได้ว่าถ้าผ้ากองA (Process แรก)ยังทำงานไม่ครบทุกขั้นตอนแม้ว่ามีส่วนที่ใช้ทำงาน(เครื่องซักผ้า เครื่องอบผ้าที่ว่าง)เราไม่สามารถนำผ้ากองอื่นมาซักได้
คือการทำงานให้ครบcycleก่อนในsingle cycle

![pipe2](https://cs.stanford.edu/people/eroberts/courses/soco/projects/risc/pipelining/laundry2.gif)

<br>ภาพนี้แสดงให้เห็นว่าสมารถทำงานได้หลายprocessพร้อมกันรวมทั้งประหยัดเวลาด้วย


### งานครั้งที่ 7
  [คลิปงานครั้งที่ 7 Pipelining](https://youtu.be/CD11kbYG7tU)
  
  

 



    
 

 



