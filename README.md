# CN210
## สรุปเนื้อหาโดยรวมของMIPS Instruction(ชุดคำสั่งของMIPS)
<br>**MIPS  Instruction** เข้ารหัสในรูปแบบ Binary
<br>**ชุดคำสั่งทุกคำสั่งมีความยาว 32 Bits**
<br>**คำสั่งมี 3 ประเภทใหญ่ๆได้แก่**


|**R-Format**|     |     |     |     |     |
|------------|-----|-----|-----|-----|-----|
|     op     | $rs | $rt | $rd |shamt|func |
|     6bits   | 5bits| 5bits| 5bits|5bits |6bits |

|**คำสั่งอื่นๆ**    |     |     |     |     |     |
|------------|-----|-----|-----|-----|-----|
|ALU         | alu | $rd | $rs | $rt |     |
|JR          | jr  | $rs |     |     |     |

คำสั่งส่วนใหญ่จะไว้ใช้ทำงานในส่วนของการคำณวณทางตรรกศาสตร์

<br>**I-Format**(เป็นคำสั่งที่ใช้ย้ายข้อมูล)
<br> op	      $rs	     $rt	     offset
<br>6bits	   5bits	  5bits	     16bits

<br>**I-Format**(อื่นๆ)
<br>ALUi	alui	$rt	$rs	value
<br>Data Transfer	lw	$rt	offset($rs)	
<br>              sw	$rt	offset($rs)
<br>Branch	      beq	$rs	$rt	offset	
<br>**J-Format**(jump จาก Address ปัจจุบัน ไปยังอีกตำแหน่งนึง)
<br>op	Address
<br>6bits	26bits
<br>**J-Format**(อื่นๆ)
<br>jump	j address
<br>jump&link	jal address
