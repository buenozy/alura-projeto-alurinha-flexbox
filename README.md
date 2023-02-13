## **<u>Conceitos abordados durante o módulo sobre FlexBox</u>**


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
.container {
  display: flex; /* or inline-flex */
}
```

O `display: flex` veio com o intuito de facilitar nossa vida nesses aspectos de posicionamento. Ele permite os elementos ficarem um do lado do outro, permite espaçar os elementos de forma mais intuitiva e sem ter que fazer cálculos. Além disso ele também permite alinhar os elementos verticalmente de forma fácil.

Propriedades  aplicadas ao `container` e as aplicadas`flex items`

Seguindo a documentação temos:

## **container:**

- `display: flex`
- `justify-content`
- `flex-direction`
- `flex-wrap`
- `flex-flow`
- `align-items`
- `align-content`
- `gap`

```
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```

- `flex-start`(padrão): os itens são compactados no início da direção flexível.
- `flex-end`: os itens são embalados no final da direção flexível.
- `start`: os itens são embalados no início da `writing-mode`direção.
- `end`: os itens são embalados no final da `writing-mode`direção.
- `left`: os itens são empacotados na borda esquerda do contêiner, a menos que isso não faça sentido com o `flex-direction`, então ele se comporta como `start`.
- `right`: os itens são embalados na borda direita do contêiner, a menos que isso não faça sentido com o `flex-direction`, então ele se comporta como `end`.
- `center`: itens são centralizados ao longo da linha
- `space-between`: os itens são distribuídos uniformemente na linha; primeiro item está na linha de partida, último item na linha final
- `space-around`: os itens são distribuídos uniformemente na linha com espaço igual ao redor deles. Observe que visualmente os espaços não são iguais, pois todos os itens possuem espaço igual em ambos os lados. O primeiro item terá uma unidade de espaço contra a borda do contêiner, mas duas unidades de espaço entre o próximo item porque esse próximo item tem seu próprio espaçamento aplicável.
- `space-evenly`: os itens são distribuídos de forma que o espaçamento entre quaisquer dois itens (e o espaço até as bordas) seja igual.



Há também duas palavras-chave adicionais que você pode associar a esses valores: `safe`e `unsafe`. O uso `safe`garante que, independentemente de como você faça esse tipo de posicionamento, você não pode empurrar um elemento para que ele seja renderizado fora da tela (por exemplo, fora da parte superior) de forma que o conteúdo também não possa ser rolado (chamado “perda de dados”) .



```
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

- `row`(padrão): da esquerda para a direita em `ltr`; direita para esquerda em`rtl`

- `row-reverse`: direita para esquerda em `ltr`; da esquerda para a direita em`rtl`

- `column`: o mesmo que, `row`mas de cima para baixo

- `column-reverse`: o mesmo que, `row-reverse`mas de baixo para cima

  

```
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

- `nowrap`(padrão): todos os itens flexíveis estarão em uma linha

- `wrap`: os itens flexíveis serão agrupados em várias linhas, de cima para baixo.

- `wrap-reverse`: os itens flexíveis serão agrupados em várias linhas de baixo para cima.

  

```
.container {
  flex-flow: column wrap;
}
```

Este é um atalho para as propriedades `flex-direction`e `flex-wrap`, que juntas definem os eixos principal e transversal do contêiner flexível. O valor padrão é `row nowrap`.



```
.container {
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
}
```

- `stretch`(padrão): esticar para encher o recipiente (ainda respeitando min-width/max-width)
- `flex-start`/ `start`/ `self-start`: os itens são colocados no início do eixo transversal. A diferença entre estes é sutil, e trata-se de respeitar as `flex-direction`regras ou as `writing-mode`regras.
- `flex-end`/ `end`/ `self-end`: os itens são colocados no final do eixo transversal. A diferença novamente é sutil e é sobre respeitar `flex-direction`regras versus `writing-mode`regras.
- `center`: os itens são centralizados no eixo cruzado
- `baseline`: itens são alinhados como suas linhas de base alinhadas

As palavras-chave modificadoras `safe`e podem ser usadas em conjunto com todas as outras palavras-chave (embora observe [o suporte do navegador](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items) ) e ajudam a evitar o alinhamento de elementos de modo que o conteúdo se torne inacessível.`unsafe`



```
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}
```

- `default `(padrão): os itens são compactados em sua posição padrão, como se nenhum valor fosse definido.
- `flex-start`/ `start`: itens embalados no início do contêiner. O (mais apoiado) `flex-start`honra o `flex-direction`enquanto `start`honra a `writing-mode`direção.
- `flex-end`/ `end`: itens embalados até o final do container. O (mais suporte) `flex-end`homenageia o `flex-direction`while end homenageia a `writing-mode`direção.
- `center`: itens centralizados no contêiner
- `space-between`: itens distribuídos uniformemente; a primeira linha está no início do contêiner enquanto a última está no final
- `space-around`: itens distribuídos uniformemente com espaço igual ao redor de cada linha
- `space-evenly`: os itens são distribuídos uniformemente com espaço igual ao seu redor
- `stretch`: as linhas se estendem para ocupar o espaço restante

As palavras-chave modificadoras `safe`e podem ser usadas em conjunto com todas as outras palavras-chave (embora observe [o suporte do navegador](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items) ) e ajudam a evitar o alinhamento de elementos de modo que o conteúdo se torne inacessível.`unsafe`



```
.container {
  display: flex;
  ...
  gap: 10px;
  gap: 10px 20px; /* row-gap column gap */
  row-gap: 10px;
  column-gap: 20px;
}
```

[A  propriedade](https://css-tricks.com/almanac/properties/g/gap/) `gap` controla explicitamente o espaço entre os itens flexíveis. Aplica esse espaçamento *apenas entre os itens* que não estão nas bordas externas.

O comportamento pode ser pensado como uma calha *mínima* , como se a calha fosse maior de alguma forma (por causa de algo como `justify-content: space-between;`), então a lacuna só teria efeito se esse espaço acabasse menor.

Não é exclusivo para flexbox, `gap`funciona em grade e layout de várias colunas também.

## flex item:

- `order`
- `flex-grow`
- `flex-shrink`
- `flex-basis`
- `flex`
- `align-self`



```
.item {
  order: 5; /* default is 0 */
}
```

Por padrão, os itens flexíveis são dispostos na ordem de origem. No entanto, a `order`propriedade controla a ordem em que aparecem no contêiner flexível.

Itens com o mesmo `order`revertem para a ordem de origem.



```
.item {
  flex-grow: 4; /* default 0 */
}
```

Isso define a capacidade de um item flexível crescer, se necessário. Aceita um valor sem unidade que serve de proporção. Ele determina a quantidade de espaço disponível dentro do contêiner flexível que o item deve ocupar.

Se todos os itens forem `flex-grow`definidos como `1`, o espaço restante no contêiner será distribuído igualmente para todos os filhos. Se um dos filhos tiver um valor de `2`, esse filho ocuparia o dobro do espaço de qualquer um dos outros (ou tentará, pelo menos).

Números negativos são inválidos.



```
.item {
  flex-shrink: 3; /* default 1 */
}
```

Isso define a capacidade de um item flexível encolher, se necessário.

Números negativos são inválidos.



```
.item {
  flex-basis:  | auto; /* default auto */
}
```

Isso define o tamanho padrão de um elemento antes que o espaço restante seja distribuído. Pode ser um comprimento (por exemplo, 20%, 5rem, etc.) ou uma palavra-chave. A palavra- `auto`chave significa “olhar para minha propriedade de largura ou altura” (o que foi temporariamente feito pela palavra- `main-size`chave até ser obsoleto). A palavra- `content`chave significa “dimensioná-lo com base no conteúdo do item” – esta palavra-chave ainda não é bem suportada, então é difícil testar e mais difícil saber o que seus irmãos `max-content`, `min-content`e `fit-content`fazem.

Se for definido como `0`, o espaço extra ao redor do conteúdo não será contabilizado. Se for definido como `auto`, o espaço extra será distribuído com base em seu `flex-grow`valor. 



```
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```

Esta é a abreviação de `flex-grow,` `flex-shrink`e `flex-basis`combinado. O segundo e terceiro parâmetros ( `flex-shrink`e `flex-basis`) são opcionais. O padrão é `0 1 auto`, mas se você defini-lo com um único valor numérico, como `flex: 5;`, isso muda `flex-basis`para 0%, então é como definir `flex-grow: 5; flex-shrink: 1; flex-basis: 0%;`.

**É recomendável usar essa propriedade abreviada em** vez de definir as propriedades individuais. A abreviação define os outros valores de forma inteligente.



```
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

Isso permite que o alinhamento padrão (ou aquele especificado por `align-items`) seja substituído por itens flexíveis individuais.

Consulte a `align-items`explicação para entender os valores disponíveis.

Observe que `float`, `clear`e `vertical-align`não têm efeito em um item flexível.



Fonte: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
