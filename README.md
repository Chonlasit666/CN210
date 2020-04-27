# CN210
## สรุปเนื้อหาโดยรวมของMIPS Instruction(ชุดคำสั่งของMIPS)
<br>**MIPS  Instruction** เข้ารหัสในรูปแบบ Binary
<br>**ชุดคำสั่งทุกคำสั่งมีความยาว 32 Bits**
<br>**คำสั่งมี 3 ประเภทใหญ่ๆได้แก่**

<br>**R-Format**(คำสั่งส่วนใหญ่ในตรรกศาสตร์)
<br> op	$rs	$rt	$rd	shamt	func
<br> 6bits	5bits	5bits	5bits	5bits	6bits
<br>**R-Format**(อื่นๆ)
<br> ALU	alu	$rd	$rs	$rt	
<br> JR	jr $rs	

<br>**I-Format**(เป็นคำสั่งที่ใช้ย้ายข้อมูล)
<br>op	$rs	$rt	offset
<br>6bits	5bits	5bits	16bits

<br>**I-Format**(อื่นๆ)
<br>ALUi	alui	$rt	$rs	value
<br>Data Transfer	lw	$rt	offset($rs)	
<br>              sw	$rt	offset($rs)
<br>Branch	      beq	$rs	$rt	offset	
<br>**J-Format**(jump จาก Address ปัจจุบัน ไปยังอีกตำแหน่งนึง)
<br>
