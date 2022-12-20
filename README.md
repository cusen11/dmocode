# Files

```
- Variable.scss:             Chứa nội dung biến
- Func.scss, Mix.scss:       Chứa tất cả function, Mixin 
- Styles.scss :              Chứa nội dung style
- Reset.scss  :              Chứa nội dung reset css *nếu khách hàng có rồi thì xóa hết bên trong đi*
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
    @include listE(10, 3)
```

