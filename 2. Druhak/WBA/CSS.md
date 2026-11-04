
## Display
### Flex
```
display:flex
```
umozni manipulaci
#### flex-direction:
```
flex-direction: column;
```
nastavi aby to bylo pod sebou
## Selektory
### element selektor
```
p:hover{
color: blue
}
```
kdyz mas mys nad `p` ktere ma v sobe tuhle `class` tak se zbarvy na modrou

#### Class selektor:
```
.menu > li {
color: deeppink
}
```
vsechni primi "potomci" `class` *.menu*, ktere jsou `li` budou "deeppink"

#### kombinace
```
div p{
color: pink
}
```
vsechny `p` v `div` jsou ruzove

#### ID
```
#header {
color: red
}
```
vsechny elementy s `id` `header` 