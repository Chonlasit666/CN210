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

Format ของ R - Format
|**R-Format**|     |     |     |     |     |
|------------|-----|-----|-----|-----|-----|
|     op     | $rs | $rt | $rd |shamt|func |
|     6bit   | 5bit| 5bit| 5bit|5bit |6bit |

op = Operation code(6 bits)
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

