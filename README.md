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

![image](https://people.cs.pitt.edu/~don/coe1502/current/Unit4a/fig548.jpg)

<br>จากรูปประกอบด้วย

    *  1 ALU 
    
    *  1 Memory 
    
    *  คำสั่งไม่จบใน1cycle
    
    *  เวลาแต่ละคำสั่งไม่เท่ากัน
    
    * มีการพักData ที่ A B ก่อน
    
    *หลังากคำนวณนำค่าไปเก็บในALUOUT




