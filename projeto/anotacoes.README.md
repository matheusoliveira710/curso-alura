# Aula sobre criar elementos e passar as cores para tags do HTML

Criei o elemento `.cor-branca` do seguinte modo, para as tags `h1` (título), `p` (parágrafo), e `a` (links):

```css
.cor-branca {
  color: #FFFFFF;
}
```

## Resetar o estilo do CSS que vem por padrão do navegador

Um reset básico pode ser feito com algumas poucas linhas:

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

### Exemplo de Reset CSS mais completo

Também existem resets mais extensos, que padronizam muito mais propriedades. Um exemplo clássico é o de Eric Meyer:

```css
/* Reset CSS de Eric Meyer - versão reduzida */

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
```

Esse reset limpa praticamente todas as diferenças entre navegadores, criando uma base totalmente "neutra".

## Comparativo entre abordagens, vantagens e desvantagens

| Abordagem | O que faz? | Vantagens | Desvantagens |
| :--- | :--- | :--- | :--- |
| **Reset tradicional** | Remove todos os estilos padrões do navegador (margens, paddings, fontes etc...) | Base totalmente limpa, sem interferências externas | Pode ser agressivo demais, removendo estilos necessários e úteis |
| **Normalize.css** | Harmoniza estilos entre navegadores antes de limpar tudo. | Mantém estilos considerados boas práticas (ex: botões, inputs) | Arquivo maior que um reset simples |
| **Reset Customizado** | Criação Manual de um conjunto mínimo de resets. | Flexibilidade, apenas o que é necessário é ajustado | Exige análise e manutenção constante |

O importante é entender que o Reset CSS garante consistência visual e previsibilidade, facilitando a vida na hora de construir interfaces responsivas e compatíveis em diferentes navegadores.

## Tipos de Fontes

```css
font-family: serif;
font-family: sans-serif;
font-family: monospace;
font-family: cursive;
font-family: fantasy;
```

## Configurar as classes do HTML no CSS (Cascading Style Sheet - Folhas de estilo em cascata)

* `.hero {}` - classe
* `#btn-demo {}` - id 
* `section {}` - tag 

## Explorando tipos de fontes de sistema

As fontes de sistema possuem alguns tipos principais. Vamos aumentar o tamanho da nossa tag `h1` para 70 pixels, facilitando a compreensão. 

```css
h1 {
    font-size: 70px;
}
```

A primeira família de fonte é a **Serif**, caracterizada por acabamentos mais finos e curvas nas letras, como as pontas na letra U. Essa é uma fonte do tipo Serifada.

```css
h1 {
  font-size: 70px;
  font-family: serif;
}
```

Se não definirmos nada no CSS, o navegador aplicará automaticamente uma fonte do sistema que considera adequada. Podemos verificar isso inspecionando o elemento `h1` e acessando a aba *Computed*, onde é possível filtrar as propriedades aplicadas ao elemento. O navegador pode aplicar, por exemplo, a fonte Times, que faz parte da família Serif.

### Comparando fontes Sans Serif e Monospace

O próximo tipo de fonte de sistema é a **Sans Serif**, que é mais reta e não possui tantos detalhes de acabamento quanto a Serif. É uma fonte mais sóbria e neutra, facilitando a leitura, sendo frequentemente utilizada em sistemas e sites.

```css
h1 {
  font-size: 70px;
  font-family: sans-serif;
}
```

Outra família de fontes é a **Monospace**, ou monoespaçada, geralmente usada para escrita de código e em terminais.

```css
h1 {
  font-size: 70px;
  font-family: monospace;
}
```

### Explorando fontes cursivas e decorativas

A fonte **cursiva**, ou Family Cursive, imita a escrita manuscrita, com mais curvas e acabamentos, sendo utilizada para imitar caligrafia em algumas situações.

```css
h1 {
  font-size: 70px;
  font-family: cursive;
}
```

```css
p {
    font-family: "Poppins", sans-serif;
}
```

O próximo passo é aprender a usar os arquivos de fonte diretamente. Para isso, vamos comentar o trecho de código referente ao Google Fonts. Como vamos utilizar os arquivos, manteremos apenas eles. O fallback está funcionando ao lado, pois solicitamos o uso das fontes personalizadas e, caso elas não existam, utilizamos o fallback e o sans-serif. Removemos o import das fontes, e agora está funcionando o sans-serif.

<!-- <link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900&family=Unbounded:wght@200..900&display=swap" rel="stylesheet"> -->


### Baixando e organizando arquivos de fontes 

Vamos retornar ao site do Google Fonts para baixar os arquivos de fonte. No Google Fonts, em vez de usar o botão "Get Embed Code", que não vamos utilizar, clicamos em "Download All". Ao clicar, o download será feito para nossa máquina. Vamos até a pasta de downloads, abrir o Finder, acessar "Downloads" e encontrar o arquivo zip das fontes. Extraímos o conteúdo do zip, entramos na pasta das fontes e começamos pela "Unbounded". Dentro da pasta "Unbounded", há uma fonte que pode variar em todos os pesos e, dentro de "estático", as fontes específicas de cada peso desejado. Estamos usando a bold, então copiamos essa fonte, voltamos à pasta do projeto "Curso Alura Tech Board" e, de forma organizada, criamos uma nova pasta chamada "Fonts". Dentro dessa pasta, colamos a "Unbounded Bold". Arrastamos para dentro da pasta "Fonts". Voltamos à pasta de downloads e repetimos o processo com a Poppins. Para a Poppins, estamos usando a regular, então copiamos apenas a fonte regular, voltamos à pasta do projeto "Tech Board", dentro da pasta "Fonts", e colamos a fonte.

Agora, já temos os arquivos no nosso projeto. O próximo passo é vincular esses arquivos no nosso CSS. Como vamos criar uma família de fonte a partir de arquivo, não fazemos isso no HTML, mas sim no CSS. No documento CSS, damos um espaçamento acima do nosso Reset e, para importar e criar uma nova família de fonte, usamos um seletor chamado @font-face.

### Configurando a fonte Unbounded no CSS

Escrevemos @font-face. O VS Code já oferece um autocomplete. Dentro desse autocomplete, ele traz duas propriedades principais. A primeira é o nome que daremos para essa font-family. Escrevemos, entre aspas, "Unbounded". A próxima propriedade é a origem do nosso arquivo. Não estamos na raiz, como no documento HTML. O que queremos dizer com raiz é que o documento está no mesmo nível do projeto, no primeiro nível. O index está na raiz, o favicon está na raiz, as pastas estão na raiz, mas o nosso arquivo CSS não está na raiz. Então, passamos o caminho saindo da pasta CSS para, em seguida, acessar a pasta "Fonts". Na URL, passamos entre aspas duplas. Para sair da pasta em que estamos, toda vez que quisermos voltar um nível, usamos ../. Escrevemos ../, e o VS Code reconhece que agora estamos na raiz. Podemos selecionar a pasta "Fonts" e a nossa fonte "Unbounded Bold". Passamos a URL e adicionamos uma propriedade que não veio descrita no VS Code, mas que precisamos adicionar: o formato dessa fonte, format. Passamos entre aspas duplas. Existem vários formatos de fonte. Um dos mais comuns é o WOFF2, mas, no nosso caso, é um .ttf. TTF é a abreviação de True Type. Escrevemos "True Type".

@font-face {
  font-family: "Unbounded";
  src: url("../fonts/Unbounded-Bold.ttf");
  format("truetype");
}

o que significa cada comando desse?:

🔤 @font-face

É a regra que permite importar uma fonte externa pro seu projeto.

Sem isso, o navegador só usa fontes padrão tipo Arial, Times, etc.

🏷️ font-family: "Poppins";

Define o nome que você vai usar no CSS pra chamar essa fonte.

📁 src: url(../fonts/Poppins-Regular.ttf)

Aqui você diz onde está o arquivo da fonte.

url(...) → caminho do arquivo

../ → volta uma pasta

fonts/ → entra na pasta de fontes

👉 Ou seja: ele tá buscando o arquivo na pasta fonts fora da pasta atual.

🧩 format("truetype");

Define o formato da fonte.

"truetype" → arquivo .ttf

Outros comuns:

"woff" (melhor pra web)

"woff2" (mais leve ainda 🔥)

👉 Isso ajuda o navegador a entender e otimizar o carregamento.

⚖️ font-weight: 400;

Define o peso da fonte.

400 → normal

700 → negrito (bold)

300 → mais fina

👉 Se você tiver vários arquivos (Regular, Bold, Light), cada um precisa de um @font-face.

🎭 font-style: normal;

Define o estilo da fonte.

normal → padrão

italic → itálico

👉 Igual ao weight, se tiver versão itálica, você declara separado.

⚡ font-display: swap;

Esse você já viu, mas resumindo:

Mostra uma fonte padrão primeiro

Depois troca pela fonte carregada

👉 Evita texto invisível.