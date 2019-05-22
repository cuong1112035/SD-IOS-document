**Guideline SDUI, SDDS**

- Prefix components: 				SDDSCxxx (**SDDSNavTabNorm**)
- Prefix components delegate: 	SDDSCxxxDelegate (**SDDSNavTabNormDelegate**)
- Prefix protocol data:				SDDSxxxData (**SDDSTabMenuData**)
- Prefix varible protocol data:	varibleName\_SDDSxxx (**title\_SDDSTabMenuData**)
- Prefix SDUI:						SDUIxxx (**SDUIConfig**)


**xxx**: Class name, protocol name

**Guideline Cache**

KeyCache: Prefix\_Center + "Cache" + Page\_Name + Feature\_Name

**Func Bind() input tối đa 3 params, nếu nhìu hơn thì sử dụng Protocol**

- 

	```
	Func Cong2So(numer1: Int, number2: Int) { }
	```
	```
	Protocol Number {
		var number1
		var number2
		var number3
		var number4
	}
	Func Cong4So(numbers: Number) { }
	```