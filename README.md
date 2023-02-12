```
display: inline
```

Colocando `display: inline` nos elementos permite eles se posicionarem um do lado do outro, o problema do `display: inline` é que os elementos não aceitam mais que seja modificada tanto a `width` quanto a `height`. Isso limita MUITO nossas possibilidades.

```
display: inline-block
```

O `display: inline-block` permite os elementos se posicionarem um do lado do outro porém, diferentemente do `display: inline` ele permite que os elementos tenham sua `width` e `height` modificadas. Por esse motivo o `display: inline-block` é muito mais interessante na maioria dos casos do que o `display: inline`.

O problema de usar `display: inline-block` é espaçar os elementos entre si. Para fazer isso teríamos que colocar `margins` e fazer contas.

```
float: left | right
```

O `float` é mais complicado, ele empurra o elemento para um dos lados (left | right) e os elementos que estão embaixo sobem. Isso nem sempre é o que a gente quer. Além do mais o `float` não permite que usemos a propriedade `vertical-align: middle` para alinhar os elementos verticalmente. Ou seja, para contornar isso uma possibilidade seria ter que colocar `margin-top` ou `bottom` nos elementos e usar os temidos números mágicos!

```
display: flex
```

O `display: flex` veio com o intuito de facilitar nossa vida nesses aspectos de posicionamento. Ele permite os elementos ficarem um do lado do outro, permite espaçar os elementos de forma mais intuitiva e sem ter que fazer cálculos. Além disso ele também permite alinhar os elementos verticalmente de forma fácil.

```
justify-content:
```

Colocar todo espaço à esquerda, jogando o conteúdo para direita com `justify-content: flex-end`.

Colocar todo espaço à direita, jogando o conteúdo para esquerda com `justify-content: flex-start` (que é o padrão).

Colocar todo espaço à esquerda e à direita, jogando o conteúdo para o meio com `justify-content: center`.

Colocar todo espaço entre os elementos usando `justify-content: space-between`.

Colocar o espaço em volta dos elementos usando `justify-content: space-around`.

```
flex-direction:
```



```
flex-wrap:
```



```
flex-flow:
```

