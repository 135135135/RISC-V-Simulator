# 标题

## 选定指令集（RISC-V）

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/44ec3295f97d9ae49a1b2b0e4ffb16b3.png)

| R                 | func7   | rs2      | rs1      | func3 | rd      | op      |
| ----------------- | ------- | -------- | -------- | ----- | ------- | ------- |
| ADD rd, rs1, rs2  | 0000000 | rs2[4:0] | rs1[4:0] | 000   | rd[4:0] | 0110011 |
| SUB rd, rs1, rs2  | 0100000 | rs2[4:0] | rs1[4:0] | 000   | rd[4:0] | 0110011 |
| XOR rd, rs1, rs2  | 0000000 | rs2[4:0] | rs1[4:0] | 100   | rd[4:0] | 0110011 |
| OR rd, rs1, rs2   | 0000000 | rs2[4:0] | rs1[4:0] | 110   | rd[4:0] | 0110011 |
| AND rd, rs1, rs2  | 0000000 | rs2[4:0] | rs1[4:0] | 111   | rd[4:0] | 0110011 |
| SLL rd, rs1, rs2  | 0000000 | rs2[4:0] | rs1[4:0] | 001   | rd[4:0] | 0110011 |
| SRL rd, rs1, rs2  | 0000000 | rs2[4:0] | rs1[4:0] | 101   | rd[4:0] | 0110011 |
| SRA rd, rs1, rs2  | 0100000 | rs2[4:0] | rs1[4:0] | 101   | rd[4:0] | 0110011 |
| SLT rd, rs1, rs2  | 0000000 | rs2[4:0] | rs1[4:0] | 010   | rd[4:0] | 0110011 |
| SLTU rd, rs1, rs2 | 0000000 | rs2[4:0] | rs1[4:0] | 011   | rd[4:0] | 0110011 |

Reg写入：ALU；100000101001

ALU1：regA；

ALU2：regB

| I                    | imm               | rs1      | func3 | rd      | op      |
| -------------------- | ----------------- | -------- | ----- | ------- | ------- |
| ADDI rd, rs1, imm    | imm[11:0]         | rs1[4:0] | 000   | rd[4:0] | 0010011 |
| XORI rd, rs1, imm    | imm[11:0]         | rs1[4:0] | 100   | rd[4:0] | 0010011 |
| ORI rd, rs1, imm     | imm[11:0]         | rs1[4:0] | 110   | rd[4:0] | 0010011 |
| ANDI rd, rs1, imm    | imm[11:0]         | rs1[4:0] | 111   | rd[4:0] | 0010011 |
| SLLI rd, rs1, imm    | 0000000\|imm[4:0] | rs1[4:0] | 001   | rd[4:0] | 0010011 |
| SRLI rd, rs1, imm    | 0000000\|imm[4:0] | rs1[4:0] | 101   | rd[4:0] | 0010011 |
| SRAI rd, rs1, imm    | 0100000\|imm[4:0] | rs1[4:0] | 101   | rd[4:0] | 0010011 |
| SLTI rd, rs1, imm    | imm[11:0]         | rs1[4:0] | 010   | rd[4:0] | 0010011 |
| SLTIU rd, rs1, imm   | imm[11:0]         | rs1[4:0] | 011   | rd[4:0] | 0010011 |
| LB rd, offset(rs1)   | offset[11:0]      | rs1[4:0] | 000   | rd[4:0] | 0000011 |
| LH rd, offset(rs1)   | offset[11:0]      | rs1[4:0] | 001   | rd[4:0] | 0000011 |
| LW rd, offset(rs1)   | offset[11:0]      | rs1[4:0] | 010   | rd[4:0] | 0000011 |
| LBU rd, offset(rs1)  | offset[11:0]      | rs1[4:0] | 100   | rd[4:0] | 0000011 |
| LHU rd, offset(rs1)  | offset[11:0]      | rs1[4:0] | 101   | rd[4:0] | 0000011 |
| JALR rd, offset(rs1) | offset[11:0]      | rs1[4:0] | 000   | rd[4:0] | 1100111 |
| ECALL                | 000000000000      | 00000    | 000   | 00000   | 1110011 |
| EBREAK               | 000000000001      | 00000    | 000   | 00000   | 1110011 |

00100：

Reg写入：ALU；1001001

ALU1：regA；

ALU2：IMM

00000：

Reg写入：MEM；11001010

ALU1：regA；

ALU2：IMM

11001：

Reg写入：PC+4；10011001100

ALU1：regA；

ALU2：IMM

| S                   | imm[11:5]    | rs2      | rs1      | func3 | imm[4:0]    | op      |
| ------------------- | ------------ | -------- | -------- | ----- | ----------- | ------- |
| SB rs2, offset(rs1) | offset[11:5] | rs2[4:0] | rs1[4:0] | 000   | offset[4:0] | 0100011 |
| SH rs2, offset(rs1) | offset[11:5] | rs2[4:0] | rs1[4:0] | 001   | offset[4:0] | 0100011 |
| SW rs2, offset(rs1) | offset[11:5] | rs2[4:0] | rs1[4:0] | 010   | offset[4:0] | 0100011 |

Save；111001000

ALU1：regA；

ALU2：IMM

| B                     | imm[12\|10:5]    | rs2      | rs1      | func3 | imm[4:0\|11]    | op      |
| --------------------- | ---------------- | -------- | -------- | ----- | --------------- | ------- |
| BEQ rs1, rs2, offset  | offset[12\|10:5] | rs2[4:0] | rs1[4:0] | 000   | offset[4:1\|11] | 1100011 |
| BNE rs1, rs2, offset  | offset[12\|10:5] | rs2[4:0] | rs1[4:0] | 001   | offset[4:1\|11] | 1100011 |
| BLT rs1, rs2, offset  | offset[12\|10:5] | rs2[4:0] | rs1[4:0] | 100   | offset[4:1\|11] | 1100011 |
| BGE rs1, rs2, offset  | offset[12\|10:5] | rs2[4:0] | rs1[4:0] | 101   | offset[4:1\|11] | 1100011 |
| BLTU rs1, rs2, offset | offset[12\|10:5] | rs2[4:0] | rs1[4:0] | 110   | offset[4:1\|11] | 1100011 |
| BGEU rs1, rs2, offset | offset[12\|10:5] | rs2[4:0] | rs1[4:0] | 111   | offset[4:1\|11] | 1100011 |

Branch；1000101000

ALU1：RegA；ALU2：RegB

ALU1：PC_old；ALU2：IMM

| U             | imm[31:12] | rd      | op      |
| ------------- | ---------- | ------- | ------- |
| LUI rd, imm   | imm[31:12] | rd[4:0] | 0110111 |
| AUIPC rd, imm | imm[31:12] | rd[4:0] | 0010111 |

LUI

Reg写入：ALU；1000001001001

ALU1：regA；

ALU2：IMM



AUIPC

Reg写入：ALU；11010001

ALU1：PC_old；

ALU2：IMM；

| J              | imm                         | rd      | op      |
| -------------- | --------------------------- | ------- | ------- |
| JAL rd, offset | offset[20\|10:1\|11\|19:12] | rd[4:0] | 1101111 |

Reg写入：PC；10011010100

ALU1：PC_old；

ALU2：IMM；

将func3和func7[5]拼接得到ALUop

| 助记词 | ALUop |
| ------ | ----- |
| ADD    | 0000  |
| SUB    | 0001  |
| XOR    | 1000  |
| OR     | 1100  |
| AND    | 1110  |
| SLL    | 0010  |
| SRL    | 1010  |
| SRA    | 1011  |
| SLT    | 0100  |
| SLTU   | 0110  |
| B      | 1101  |
