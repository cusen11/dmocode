# Files

```
- Variable.scss:             Chứa nội dung biến
- Func.scss, Mix.scss:       Chứa tất cả function, Mixin 
- Styles.scss :              Chứa nội dung style
- Reset.scss  :              Chứa nội dung reset css *nếu khách hàng có rồi thì xóa hết bên trong đi*
```
# Config
Variable.scss file:
```
    $vw-viewport: 375;  // kích thước màng hình design mobie dùng cho vw 
    $baseSize: 16; // Font size chuẩn dùng cho em và rem 
```

# Use  

## PX to VW

```
    Syntax

        tovw(value)
        Ex: tovw(10) -->  2.3364485981vw
```
## PX to PT

``` 
    Syntax
        topt(value)
        Ex: topt(10) -->  7.5pt
```
## PX to em

```
    Syntax
        toem(value)
        Ex: toem(10) -->  0.625em
```
## PX to rem

```
    Syntax
        torem(value)
        Ex: torem(10) -->  0.625rem
```

## Grid 

```
    
    - List
        Syntax

            @include listE(margin,items,classChild);

        Ex: Give list 12 item 3 rows and 4 colums, margin right 10px
            .ex{
                @include listE(10, 3,class)
            }

        Result: 

            .ex {
                display: -webkit-box;
                display: -ms-flexbox;
                display: flex;
                -webkit-box-pack: start;
                    -ms-flex-pack: start;
                        justify-content: flex-start;
                -ms-flex-wrap: wrap;
                    flex-wrap: wrap;
                margin-right: 10;
            }
            .ex .class:nth-of-type(3n + 0) {
                margin-right: 0;
            }
    - Grid
        Variable : 
			wr: wrap;  
			nwr: nowrap;  
			jstart: flex-start;  
			jc: center;  
			jend: flex-end;  
			jbw: space-between;  
			jar: space-around;  
			als: flex-start;  
			alc: center;  
			ale: flex-end;  
			cl: column;  
			clr: column-reverse;  
			r: row;  
			rr: row-reverse; 
        Syntax
            @include(@value...)
        Normal css
            .ex {
                display: -webkit-box;
                display: -ms-flexbox;
                display: flex;
                -ms-flex-wrap: wrap;
                    flex-wrap: wrap;
                -webkit-box-orient: vertical;
                -webkit-box-direction: normal;
                    -ms-flex-direction: column;
                        flex-direction: column;
                -ms-flex-pack: distribute;
                    justify-content: space-around;
                -webkit-box-align: center;
                    -ms-flex-align: center;
                        align-items: center;
            }
        In new Syntax
            @include grid('wr','cl','jar','alc')

```


## Befoce & After

```
    Variable :
        TR = Top Right
        TL = TOP Left
        BR = Bottom Right
        BL = Bottom Left

    Syntax

        before{variable}(value, value){
            @content
        }

    Ex:  
        .ex{
            @include beforeTL(50%, 10px){
                content: '##';
            }
        }

    Result
        .ex {
            position: relative;
        }
        .ex::before {
            content: "##";
            position: absolute;
            top: 50%;
            left: 10px;
        }

```
## Responsive

``` 
    Syntax
        Max width: 
            @include toMin(value){
                @content
            }
        Min width:
            @include toMax(value){
                @content
            }

    Ex:
        .ex{
            display: block;
            @include toMax(758){
                dispay:none
            }
        }

    Result:

        .ex{
            display: block
        }
        @media screen and (max-width: 758px) {
            .ex {
                display: none;
            }
        }
    

```
## Position

```
    Syntax

        @include center
        @include centerX
        @include centerY

    Ex: 
        .center{ 
            @mixin center
        }
        .centerX{ 
            @mixin centerX
        }
        .centerY{ 
            @mixin centerY 
        }
    
    Result
        .center{ 
            position: relative;
            position: absolute;
            top: 50%;
            left: 50%;
            -webkit-transform: translate(-50%, -50%);
                    transform: translate(-50%, -50%);
            position: absolute; 
        }
        .centerX{ 
            position: absolute;
            top: 50%;
            -webkit-transform: translateY(-50%);
                    transform: translateY(-50%);
        }
        .centerY{ 
            position: absolute;
            left: 50%;
            -webkit-transform: translateX(-50%);
                    transform: translateX(-50%);
        }

```


## Text

```
    Syntax
        @include indent(value)

    Ex: 
        .ex{
            @include indent(10px)
        }
        .ex2{
            @include indent(tovw(10))
        }
    Result
    
        .ex{
            text-indent: -10px;
	        margin-left: 10px;
        }
        .ex2{
            text-indent: -2.3364485981vw;
	        margin-left: 2.3364485981vw;
        }

```
## Font
### font face
```
    Lưu ý: font cần thực hiện đổi đuôi ttf sang tất cả các định dạng khác để không bị lỗi font ở các trình duyệt or file svg tại website:
    https://transfonter.org/.
    TTF,WOFF,WOFF2,SVG,EOT
    Syntax
        @include font($name,$url',$fontWeight) 
    
    Ex: 
        @include font('Maryo','../abc/Maryo',300) 

    Result:

        @font-face {
            font-family: "Maryo";
            src: url("../abc/Maryo.eot");
            src: url("../abc/Maryo.eot?#iefix") format("embedded-opentype"), url("../abc/Maryo.woff2") format("woff2"), url("../abc/Maryo.woff") format("woff"), url("../abc/Maryo.ttf") format("truetype"), url("../abc/Maryo.svg#../abc/Maryo") format("svg");
            font-weight: 300;
            font-style: normal;
            font-display: swap;
        }

```
### font family
```
    Syntax:
        fontFamily($name,$fontWeight,$tag...)
    
    Ex:
        .ex{
            @include fontFamily('Family', 300,"h1","p")
        }
 
    Ex2:
        @include fontFamily('FamilyHihi', 500,".class","#id")
         
        
    
    Result: 
            .ex h1 {
                font-family: "Family";
                font-weight: 300;
            }
            .ex p {
                font-family: "Family";
                font-weight: 300;
            } 
            
            .class {
                font-family: "FamilyHihi";
                font-weight: 500;
            }
            #id {
                font-family: "FamilyHihi";
                font-weight: 500;
            }

```