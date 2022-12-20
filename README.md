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
    $vw-viewport: 375;  <!-- kích thước màng hình design mobie dùng cho vw -->
    $baseSize: 16; <!-- Font size chuẩn dùng cho em và rem -->
```

# Use  

## PX to VW

```
    tovw(value)
    Ex: tovw(10) -->  2.3364485981vw
```
## PX to PT

```
    topt(value)
    Ex: topt(10) -->  7.5pt
```
## PX to em

```
    toem(value)
    Ex: toem(10) -->  0.625em
```
## PX to rem

```
    torem(value)
    Ex: torem(10) -->  0.625rem
```

## Gird list

```
    @include listE(margin,items);
    Ex: Give list 12 item 3 rows and 4 colums, margin right 10px
    .ex{
        @include listE(10, 3)
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
        .ex:nth-of-type(3n + 0) {
            margin-right: 0;
        }

```


## Befoce & After

```
    Variable :
    TR = Top Right
    TL = TOP Left
    BR = Bottom Right
    BL = Bottom Left
    

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

