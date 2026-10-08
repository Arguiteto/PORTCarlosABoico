# Portfólio — sistema organizado para edição

Esta pasta foi organizada para facilitar novas atualizações.

## Estrutura

- `index.html`  
  Arquivo principal do site. Nele ficam o layout, o conteúdo e o funcionamento.

- `assets/`  
  Pasta das imagens: logo, capas dos projetos, fotos internas e desenhos.

## Onde editar

### 1. Alterar projetos do hall

Abra `index.html` e procure:

```js
const projects = [
```

Cada bloco dentro dessa lista é um projeto.

### 2. Trocar capa de um projeto

Dentro do projeto, altere:

```js
src: 'assets/nome-da-capa.jpg'
```

### 3. Trocar fotos internas do projeto

Dentro do projeto, altere:

```js
images: [
  { title: 'Fachada', type: 'Foto', src: 'assets/fachada.jpg' }
]
```

### 4. Trocar desenhos / plantas

Dentro do projeto, altere:

```js
drawings: [
  { title: 'Planta baixa', src: 'assets/planta-baixa.jpg' }
]
```

### 5. Alterar abas superiores

Procure:

```js
const systemPages = {
```

Ali ficam os textos de:

- Sobre mim
- Projeto
- Contato

## Como adicionar um novo projeto

Copie um bloco inteiro dentro de `const projects`, cole abaixo do último projeto e altere:

- `title`
- `apelido`
- `meta`
- `category`
- `src`
- `description`
- `info`
- `images`
- `drawings`

Exemplo:

```js
{
  id: 'projeto-07',
  title: 'Nome do projeto',
  meta: 'Residencial',
  category: 'Casa',
  src: 'assets/projeto-07-capa.jpg',
  description: 'Descrição curta do projeto.',
  info: {
    'Terreno': '12 x 30 m',
    'Área construída': '180 m²'
  },
  images: [
    { title: 'Fachada', type: 'Foto', src: 'assets/projeto-07-fachada.jpg' }
  ],
  drawings: [
    { title: 'Planta baixa', src: 'assets/projeto-07-planta.jpg' }
  ]
}
```

## Endereço curto de cada projeto (apelido)

- Cada projeto pode ter a linha `apelido`, logo abaixo do `title`. Ela define o que aparece depois do `#` no link:

```js
title: 'Salão Vitalina de Beleza',
apelido: 'vitalina',
```

- Com isso o link do projeto fica `.../#vitalina`. Os apelidos de hoje: `vitalina`, `quarto`, `reforma`, `dopamine`, `paisagismo` e `moveis`.
- O endereço comprido, gerado a partir do título (`#salao-vitalina-de-beleza`), continua abrindo o projeto. Links já enviados não quebram.
- Use só letras minúsculas, sem acento e sem espaço. Não repita apelido entre projetos e não use `inicio`, `sobre`, `projetos`, `contato` nem `processo`. Se repetir, o projeto fica com o endereço comprido e o Console (F12) mostra um aviso.
- Projeto sem a linha `apelido` usa o endereço comprido.

## Importante

Não altere os nomes de classes, ids e funções se você só quiser trocar textos e imagens.  
Eles controlam o funcionamento do carrossel, das páginas internas, dos botões Infos/Desenhos e das visualizações ampliadas.

## Projetos em andamento

- `andamento: true` dentro do projeto coloca as fitas vermelhas "EM ANDAMENTO" na capa (hall, aba Projetos e página do projeto) e mostra, ao lado da capa, o cartão com a descrição.
- Quando o projeto terminar: apague a linha `andamento: true`, troque o `src` pela capa nova e preencha `images` e `drawings`.
- Os quatro projetos em andamento já têm a **revista preparada e bloqueada** (veja "Revista do projeto → Projetos em andamento"). Ela aparece sozinha quando a linha `andamento: true` sair e as fotos entrarem.
- `capa: true` numa imagem faz a capa ilustrada aparecer inteira, na proporção dela, dentro da página do projeto.
- As capas ilustradas ficam em `assets/`:
  - `capa-reforma-unifamiliar.svg`
  - `capa-interiores.svg`
  - `capa-paisagismo.svg`
  - `capa-moveis-planejados.svg`

## Revista do projeto

Seção que aparece abaixo das fotos, com as imagens do projeto diagramadas como páginas de revista de arquitetura.

- **No computador** é um caderno aberto que vira a folha, com o mesmo efeito do leitor da BibliChaos: clique na página, arraste a folha (ela acompanha o cursor e a sombra segue a dobra), use as setas ← → do teclado, as setas da seção ou o canto dobrado. Clicar na capa abre a revista.
- **No celular e no tablet** as páginas ficam lado a lado e passam com o dedo.
- Clicar (ou tocar) em uma foto abre a ampliação, igual às fotos do carrossel.
- Com a revista, o botão "Revista" aparece no topo do projeto e leva até ela.

### Onde fica

- Dentro do projeto, em `const projects`, no bloco `revista`. Hoje aparece em "Salão Vitalina de Beleza" e em "Quarto Maria".
- A do Salão Vitalina tem 8 páginas: capa (projeto final), texto com ficha, render conceito em página inteira, render em ângulo aberto na página dupla, 1º render com o texto do processo, planta baixa e contracapa.
- Página com fundo colorido (a planta terracota do salão, por exemplo): as letras miúdas trocam sozinhas para uma cor legível, escura em fundo médio e clara em fundo escuro. A cor do fundo vem de `fundo` na página ou do `bg` da imagem, escrita como `#RRGGBB`.
- Para tirar a revista de um projeto, apague o bloco `revista` inteiro. Para pôr em outro, copie o bloco do Quarto Maria e troque as páginas.
- Os números em `foto` e `fotos` são a **posição da imagem na lista `images`** do projeto: `0` é a primeira, `1` a segunda. Se mudar a ordem de `images`, confira os números da revista.
- O nome que aparece junto de cada foto é o `title` dela na lista `images`.

```js
revista: {
  titulo: 'Quarto Maria, página a página',   // título da seção
  edicao: 'Nº 02 · 2026',                    // aparece no alto da capa
  paginas: [
    { tipo: 'capa', foto: 0, chamada: 'Reforma, interiores e paisagismo externo' },
    { tipo: 'colagem', fotos: [1, 5, 4, 2] },
    { tipo: 'texto', kicker: 'O projeto', titulo: 'Título', olho: 'Frase de abertura.',
      texto: ['Primeiro parágrafo.', 'Segundo parágrafo.'], ficha: ['Área', 'Tipologia'] },
    { tipo: 'dupla', foto: 6, kicker: 'Paisagismo externo', texto: 'Texto curto.' },
    { tipo: 'foto-texto', foto: 3, kicker: 'À noite', titulo: 'Título', texto: ['Parágrafo.'] },
    { tipo: 'pranchas', fotos: [8, 7], kicker: 'Vistas ortogonais', fundo: '#F4F7FE' },
    { tipo: 'contracapa' }
  ]
}
```

### Tipos de página

- `capa`: foto, nome da revista ("Caderno de Projetos") e título do projeto. `titulo` e `kicker` são opcionais; sem eles, entram o nome e a categoria do projeto. Com `imagem: 'assets/arquivo.jpg'`, a capa mostra esse arquivo no lugar da foto (a `foto` continua sendo a que amplia no celular), e `foco` escolhe o ponto que fica à mostra.
- `colagem`: uma foto larga em cima e três embaixo (duas empilhadas à esquerda, uma em pé à direita). A ordem em `fotos` é: larga, esquerda de cima, esquerda de baixo, em pé. Aceita de 1 a 4 fotos. A legenda com os nomes é montada sozinha.
- `texto`: `kicker` (linha pequena), `titulo`, `olho` (frase de abertura em itálico), `texto` (parágrafos) e `ficha`. Sem a linha `texto`, entra a descrição do projeto. Em `ficha`, liste as linhas de `info` que entram (`['Área', 'Tipologia']`) ou use `true` para todas.
- `dupla`: uma foto atravessando as duas páginas, com um quadro de texto (`kicker` e `texto`). Precisa cair em **página par** (a da esquerda); fora disso vira página de foto inteira. No celular aparece como uma página só.
- `foto-texto`: foto em cima, de ponta a ponta, e texto embaixo.
- `pranchas`: até 3 imagens inteiras, sem corte, com o nome embaixo de cada uma. Em `fundo`, ponha a cor de fundo das imagens, para a página ficar da mesma cor (sem `fundo`, vale o `bg` da primeira imagem).
- `foto`: uma foto ocupando a página inteira.
- `contracapa`: logo, nome, cidade, uma frase e o Instagram (vêm de `const identidade`). O @ é um botão que abre o Instagram, com o mesmo link do botão da aba Contato. Para trocar a frase: `texto: 'Sua frase.'`.

### Projetos em andamento: revista preparada e bloqueada

- Reforma Unifamiliar, Interiores Dopamine, Paisagismo Residencial e Móveis Planejados já têm o bloco `revista` montado, com um modelo de 8 páginas: capa, colagem, texto, página dupla, foto inteira, desenhos e contracapa.
- Enquanto o projeto tiver a linha `andamento: true`, a revista e o botão "Revista" **não aparecem**. A página continua só com a capa, a fita e o cartão "Em andamento".
- Para liberar, quando o projeto terminar:
  1. Apague a linha `andamento: true` e preencha `images` com as fotos finais (plantas e cortes também entram em `images`, como no Salão Vitalina).
  2. Confira os números de `foto` e `fotos` do bloco `revista`. Página que aponta para uma foto que não existe é pulada. Com menos de 3 fotos nas páginas, a revista não aparece.
  3. Na página de texto, sem a linha `texto` entra a descrição do projeto. Para escrever outro: `texto: ['Primeiro parágrafo.', 'Segundo parágrafo.']`.
- O modelo usa as posições 0 a 8 da lista `images`. Com menos fotos, as páginas que sobram são puladas e a numeração se ajeita.

### Outros ajustes

- **Capitular** (a letra grande que abre o texto): tem duas linhas de altura e é calculada sozinha a partir do tamanho da letra do texto. Texto que começa com número ou aspas fica sem capitular.
- **Texto que não cabe**: no computador a página tem tamanho fixo. Se o texto passar do pé da página, o site diminui um pouco a letra só daquela página. Se nem assim couber, o Console (F12) mostra o aviso "o texto da página N passou do pé da página": encurte o texto ou tire linhas da ficha.
- A contagem de páginas é feita sozinha. Se o total der ímpar, entra uma página em branco no fim.
- Corte da foto: quando a foto é cortada para caber no quadro, a linha `foco` na imagem (na lista `images`) escolhe o ponto que fica à mostra. `foco: '74% 50%'` quer dizer 74% da largura e 50% da altura.
- Nome da revista: `nome: 'Outro nome'` dentro de `revista` troca o "Caderno de Projetos".
- Duração da virada da folha: `REVISTA_VIRADA_MS`, no JavaScript "12D. REVISTA DO PROJETO" (600 = 0,6 segundo, igual ao leitor da BibliChaos).
- O visual fica no CSS "07C. REVISTA DO PROJETO" e a montagem no JavaScript "12D. REVISTA DO PROJETO".
- Em navegador muito antigo (sem as medidas `cqw`), a seção e o botão não aparecem; o resto do site funciona igual.

## Foto da página Sobre mim

- Arquivo: `assets/foto-sobre.jpg`, recortado na mesma proporção do quadro do site (1 : 1,08).
- Para trocar, salve a nova foto com esse mesmo nome dentro de `assets/`.

## Google e pré-visualização do link

O que o Google, o WhatsApp e os outros leitores automáticos enxergam está escrito no próprio `index.html`. Nada disso muda o que aparece na tela.

### Título e descrição

Ficam no começo do `index.html`. São o que aparece no resultado do Google e na aba do navegador:

```html
<title>Carlos A. Boico — Portfólio de Arquitetura e Urbanismo</title>
<meta name="description" content="Portfólio de Carlos A. Boico, estudante de..." />
```

- Título com até uns 60 caracteres; descrição com até uns 160.
- Se mudar, repita o texto nas linhas `og:title` e `og:description` (logo abaixo) e em `const identidade` (`titulo` e `resumo`).

### Pré-visualização do link (WhatsApp, LinkedIn, Instagram...)

- As linhas `og:`, no começo do `index.html`, dão o título, a frase e a imagem que aparecem quando o link é colado numa conversa.
- A imagem é `assets/compartilhar.jpg`, com 1200 × 630 px. Para trocar, salve outra imagem com esse mesmo nome e esse mesmo tamanho.
- **Quando o endereço do site mudar** (domínio próprio ou outro nome no GitHub), troque o começo da linha `og:image`. É a única linha do arquivo que depende do endereço:

```html
<meta property="og:image" content="https://arguiteto.github.io/PORTCarlosABoico/assets/compartilhar.jpg" />
```

- Os aplicativos guardam a pré-visualização por um tempo. Depois de trocar a imagem ou o texto, um link já enviado pode continuar mostrando a versão antiga.

### Identidade (`const identidade`)

Fica no começo do script, no bloco "03B. IDENTIDADE DO SITE": nome, resumo, cidade, áreas, perfis, WhatsApp e e-mail.

- `perfis`: links do Instagram, LinkedIn, Behance etc. Hoje tem o Instagram. O link do Instagram também vira o botão "Instagram @..." da aba Contato; sem ele na lista, o botão some. Para acrescentar outro perfil, coloque o link entre aspas, separado por vírgula:

```js
perfis: ['https://www.instagram.com/boicostar_/', 'https://www.linkedin.com/in/seu-perfil'],
```

- `whatsapp` e `email` são os mesmos dos botões da aba Contato: mudando aqui, muda lá.
- Com esses dados o site monta sozinho os "dados estruturados" que o Google lê (de quem é o portfólio, cidade, áreas e lista de projetos). Eles usam o endereço em que o site estiver aberto, então não precisam de ajuste na troca de domínio.

### Descrição das imagens (`alt`)

Cada imagem pode ter uma linha `alt`, com uma frase dizendo o que aparece nela. É o que o Google Imagens e os leitores de tela leem:

```js
{ title: 'Fachada', type: 'Foto', src: 'assets/fachada.jpg',
  alt: 'Fachada da casa com porta em arco e painel de ripas' }
```

Sem a linha `alt`, o site usa o título da imagem e o nome do projeto ("Fachada (foto) — Nome do projeto").

### Versão em texto do portfólio

- No começo do `<body>` existe o bloco "VERSÃO EM TEXTO DO PORTFÓLIO": o resumo, o "Sobre mim", os projetos (descrição, infos e imagens) e o contato, escritos direto no HTML.
- Com o site funcionando normalmente, o bloco fica escondido. Ele só aparece para quem abre a página com o JavaScript desligado.
- É uma **cópia** dos textos de `const identidade`, `const systemPages` e `const projects`. Ao abrir, o site refaz o bloco com os textos atuais; a cópia escrita no arquivo vale para quem lê o arquivo sem rodar o JavaScript.
- Depois de mudar um texto no script (descrição de projeto, "Sobre mim", infos, projeto novo), atualize a cópia:
  1. Abra o site, aperte F12 e entre na aba "Console".
  2. Digite `copy(montarVersaoTexto())` e aperte Enter. O bloco atualizado vai para a área de transferência.
  3. No `index.html`, apague o que está entre a linha `<section class="versao-texto" id="versaoTexto" ...>` e a linha `</section>` logo abaixo dela, e cole no lugar.
- Se a cópia ficar desatualizada, o site continua funcionando igual. O Console mostra o aviso "A versão em texto escrita no index.html está diferente dos textos atuais".
- O visual do bloco está no CSS "07A. VERSÃO EM TEXTO DO PORTFÓLIO". O que monta o bloco, os textos alternativos e os dados para o Google está no JavaScript "12C. TEXTO PARA O GOOGLE".

### Para quando o domínio próprio existir

Ficaram de fora de propósito, porque dependem do endereço definitivo: o arquivo `CNAME`, o `sitemap.xml`, o `robots.txt`, a linha `canonical` e o cadastro no Google Search Console.

## Modelo 3D

- `viewer3d-vitalina.html` (na raiz, ao lado do `index.html`) é o visualizador 3D do Salão Vitalina; `viewer3d-quarto-maria.html` é o do Quarto Maria. Cada projeto com modelo tem o seu: `viewer3d-nome.html` na raiz e `nome-modelo.glb` em `assets`. Ele aparece num quadro dentro da página do projeto, assim que o visitante entra. O botão no canto do quadro amplia o modelo para a tela inteira; o X volta ao tamanho normal.
- O quadro só aparece nos projetos que têm estas linhas dentro do bloco, em `const projects`:

```js
modelo3d: 'viewer3d-vitalina.html',
modelo3dPosicao: 'lado',
```

- `modelo3dPosicao` escolhe onde o quadro fica:
  - `'lado'`: quadro fixo no canto esquerdo, do tamanho de uma foto do carrossel; o carrossel passa ao lado, com a mesma folga que existe entre as fotos. Em tela estreita (menos de 1100 px de largura) e no celular, o quadro vai para baixo do carrossel. Em monitores com mais de 1920 px de largura, o conjunto fica centralizado.
  - `'abaixo'`: quadro abaixo do carrossel de fotos.
  - `'acima'`: quadro acima do carrossel de fotos.
- Hoje as linhas estão nos projetos "Salão Vitalina de Beleza" e "Quarto Maria". Para tirar o quadro, apague as duas linhas. Para usar em outro projeto, mova as duas linhas para o bloco dele.
- O tamanho do quadro fica no CSS do `index.html`, no bloco "07B. MODELO 3D". Na posição `'lado'`, ele repete as medidas das fotos do carrossel; se mudar o tamanho das fotos, repita as medidas ali. Nas posições `'abaixo'` e `'acima'`, o tamanho está em `.modelo3d-box` (`width` e `height`).
- O modelo do Salão Vitalina fica em `assets/vitalina-modelo.glb` (já aliviado para a web). O caminho está na linha `modelo` do `CONFIG`. Se esse arquivo faltar, o visualizador mostra uma casa de teste e o aviso "Modelo de teste".

### Capa e desenhos do Quarto Maria

- A capa é `assets/quarto-maria-capa.jpg`: a casinha em perspectiva montada em pé (1200 × 1960 px) sobre o fundo claro da própria imagem (`#F4F7FE`), com respiro em volta. É a mesma no hall, na aba Projetos e na capa da revista. Para trocar, salve outra imagem em pé com esse nome.
- O painel "Desenhos" mostra a planta baixa (`assets/quarto-maria-planta-baixa.jpg`) e as três vistas ortogonais da lista `drawings` (inteiras, sem corte) e, em seguida, todas as outras fotos. Para trocar a planta, salve a nova imagem com o mesmo nome; se o fundo dela tiver outra cor, troque o `bg` na mesma linha.
- Na revista, no computador, o canto de cima da mesa mostra o aviso "Use as setas do teclado para folhear". Ele some no celular e no tablet. A frase fica no HTML do `index.html` (procure por `revista-teclado`).

### Modelo do Quarto Maria

- Visualizador: `viewer3d-quarto-maria.html`. Modelo: `assets/quarto-maria-modelo.glb`.
- Cenas: "Fachada" (casa fechada, vista do jardim) e "Planta" (telhado e forro sobem e somem; vista de cima).
- O arquivo saiu do SketchUp com 107 MB, acima do que o GitHub aceita, e foi aliviado para 12,8 MB: menos triângulos nos seixos, nas plantas, nas telhas e nos objetos miúdos, e texturas menores. Saíram as peças soltas longe da casa (um piso de tijolo a 18 m dela e os objetos de luz do Enscape).
- As peças foram reunidas em grupos com nome, que são os que as cenas usam: `Telhado` (telhas, toldo da janela e empenas), `Forro`, `Paredes`, `Pisos`, `Esquadrias`, `Mobiliario`, `Paisagismo` e `Muro`.
- O muro do jardim só aparece visto de dentro, para não tampar a fachada.
- A origem do modelo ficou no canto externo da casa, na fachada da janela: a casa vai de x 0 a 3,70 e de z −3,10 a 0; o jardim, de z 0 a 2,00.
- O projeto ainda não tem planta baixa em `drawings`, então a cena "Planta" não tem os botões dos cômodos. O comentário `comodos`, no `CONFIG`, mostra como ligar.

### O que editar no viewer3d-vitalina.html

Tudo fica no bloco `CONFIG`, no começo do script:

- `modelo`: caminho do arquivo `.glb`.
- `convite`: frase curta que aparece acima dos botões até o visitante clicar em um deles (por exemplo `'Toque em Planta para abrir o salão'`). Junto com ela, o botão da próxima cena pulsa, uma cor a cada pulso. Depois do clique os dois param; voltam sempre que o visitante retorna à primeira cena ("Fachada"). No computador, "Toque" vira "Clique" sozinho. Com `''`, não tem frase nem pulso.
- `area`: a área do projeto, que aparece no canto de baixo do modelo, à esquerda (por exemplo `'27,94 m²'`). Use o mesmo valor da linha `'Área'` do projeto no `index.html`. Com `''`, não aparece.
- `cenas`: cada cena vira um botão. Tem a câmera e as peças que mudam (`mover`, `escala`, `opacidade`). Clicar de novo no botão da cena atual recentra a vista.
- `comodos`: nome e posição dos botões que aparecem na cena "Planta" (`area`, em m², é opcional).
- `desenho`: qual desenho da lista `drawings` do projeto abre ao tocar em um cômodo (`indice: 0` é o primeiro).
- `implantacao`: opcional. O Salão Vitalina é de interiores e não usa (`implantacao: null`). As cenas dele são "Fachada" (salão fechado, com o forro) e "Planta" (ao clicar, o forro sobe e some, e a vista vai para cima, com os ambientes). Para um projeto com terreno, crie uma cena com `implantacao: true` e preencha os retângulos do terreno, da área construída e das áreas impermeáveis; a área permeável, as porcentagens e a legenda são calculadas a partir deles.

### Projetos em andamento, prontos para receber o modelo

- `viewer3d-reforma.html` (Reforma Unifamiliar) e `viewer3d-paisagismo.html` (Paisagismo Residencial) já estão na raiz, com as cenas "Fachada", "Planta" e "Implantação" (vista superior travada, hachuras e legenda com as áreas). Por enquanto mostram a casa de teste.
- No `index.html`, as duas linhas `modelo3d` desses projetos estão **comentadas** (com `//` na frente). Assim eles continuam só com a capa e o cartão "Em andamento", sem o quadro.
- Para ligar um deles quando o modelo chegar:
  1. Suba o modelo em `assets` com o nome que o viewer espera (`reforma-modelo.glb` ou `paisagismo-modelo.glb`).
  2. No viewer do projeto, troque no `CONFIG` as cenas, os cômodos e a implantação da casa de teste pelos do projeto.
  3. No `index.html`, apague as `//` das duas linhas `modelo3d` do projeto.
- Ligar o quadro não tira o "Em andamento": a fita e o cartão só saem quando a linha `andamento: true` for apagada.

### Para colocar o modelo do SketchUp

1. No SketchUp, dê nome aos grupos e componentes que vão se mexer (por exemplo `Telhado`, `Paredes`, `Pisos`).
2. Exporte em `.glb` (glTF binário), sem compressão Draco, e salve em `assets` com o nome do projeto (por exemplo `assets/vitalina-modelo.glb`).
3. Abra `viewer3d-vitalina.html?ajuste=1` pelo link do site. Esse modo lista os nomes das peças que vieram no arquivo e mostra as coordenadas de qualquer ponto em que você clicar.
4. Copie os nomes para `cenas` e as coordenadas para `comodos` e `implantacao`.

Na exportação, espaço no nome vira `_` (`Bloco A` fica `Bloco_A`). Nomes repetidos ganham `_1`, `_2`.

### Como o quadro se comporta

- No tamanho normal, o quadro não prende a rolagem da página. No computador, a rodinha só aproxima o modelo depois que o mouse se mexe em cima dele. No celular, o dedo na horizontal gira o modelo e o dedo na vertical rola a página.
- Ampliado, o controle é completo: arrastar gira, Shift + arrastar desloca, a rodinha aproxima; no celular, um dedo gira e dois dedos aproximam e deslocam.
- Tocar em um cômodo abre o desenho por cima, como na aba "Desenhos".

### Cuidados

- Teste sempre pelo link do site (`arguiteto.github.io/PORTCarlosABoico/`). Abrindo o arquivo direto do computador, o navegador bloqueia o carregamento do modelo.
- Pelo site do GitHub (Add file → Upload files), cada arquivo pode ter até 25 MB. Arquivos acima de 100 MB o GitHub recusa de qualquer jeito. Mantenha o `.glb` leve.
- O GitHub Pages diferencia maiúsculas de minúsculas: `Modelo.glb` e `modelo.glb` são arquivos diferentes.
- Para um segundo projeto com outro modelo, copie o `viewer3d-vitalina.html` com o nome do novo projeto (por exemplo `viewer3d-reforma.html`), troque no `CONFIG` a linha `modelo` (por exemplo `assets/reforma-modelo.glb`), as cenas e os ambientes, e aponte a linha `modelo3d` desse projeto para o novo arquivo.
- No `index.html`, o que é do Modelo 3D está marcado nos blocos "07B. MODELO 3D" (CSS) e "12B. MODELO 3D" (JavaScript).
