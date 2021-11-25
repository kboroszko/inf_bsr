# Jak działa procesor

[LMC](https://www.101computing.net/lmc-simulator/)

Program sprawdzający nierówność trójkąta:
```
        INP
        STA num1
        INP
        STA num2
        INP
        STA num3
check1	LDA num1
        ADD num2
        SUB num3
        BRP check2
fail    LDA zero
        OUT
        HLT
check2  LDA num2
        ADD num3
        SUB num1
        BRP check3
	BRA fail
check3  LDA num1
        ADD num3
        SUB num2
        BRP succ
        BRA fail
succ    LDA one
        OUT
        HLT
		
num1    DAT
num2    DAT
num3    DAT
zero    DAT 0
one     DAT 1
```