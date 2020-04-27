# CN210
## สรุปเนื้อหาโดยรวมของMIPS Instruction(ชุดคำสั่งของMIPS)
<br>**MIPS  Instruction** เข้ารหัสในรูปแบบ Binary
<br>**ชุดคำสั่งทุกคำสั่งมีความยาว 32 Bits**
<br>**คำสั่งมี 3 ประเภทใหญ่ๆได้แก่**
**R-Format** -เป็นคำสั่งที่ใช้ทางคณิตศาสตร์และตรรกศาสตร์ มีรูปแบบดังนี้
|**R-Format**|     |     |     |     |     |
|------------|-----|-----|-----|-----|-----|
|     op     | $rs | $rt | $rd |shamt|func |
|     6bits   | 5bits| 5bits| 5bits|5bits |6bits |

 |**คำสั่งอื่นๆ**|     |     |     |     |     
 |------------|-----|-----|-----|-----|
 |ALU         | alu | $rd | $rs | $rt |     
 |JR          | jr  | $rs |     |     |     

<br>**I-Format**(เป็นคำสั่งที่ใช้ย้ายข้อมูล)
|I-Format|     |     |      |   
----- | ----- | ----- | ----- | 
|op  | rs  |  rt | offset |
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
|op  | rs  |  rt | rd  | shamt  | func  |
----- | ----- | ----- | ----- | ----- | ----- |
| 6bits | 5bits | 5bits | 5bits | 5bits | 6 bits |

op = Operation code(6 bits)
<br>**หากเป็นR-format default คือ 000000**
<br>rs = 1st register operand(5 bits)
<br>rt = 2nd register operand(5 bits)
<br>rd = register destination(5 bits)
<br>shamt = shift amount(00000 หากไม่มีการใช้ส่วนนี้)(5bits)
<br>funct = function code(6 bits)

<br>**function code**

<br>![image](https://i.stack.imgur.com/QwYfS.gif)
