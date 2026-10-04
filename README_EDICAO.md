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

- `id`
- `title`
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

## Importante

Não altere os nomes de classes, ids e funções se você só quiser trocar textos e imagens.  
Eles controlam o funcionamento do carrossel, das páginas internas, dos botões Infos/Desenhos e das visualizações ampliadas.

## Projetos em andamento

- `andamento: true` dentro do projeto coloca as fitas vermelhas "EM ANDAMENTO" na capa (hall, aba Projetos e página do projeto) e mostra, ao lado da capa, o cartão com a descrição.
- Quando o projeto terminar: apague a linha `andamento: true`, troque o `src` pela capa nova e preencha `images` e `drawings`.
- `capa: true` numa imagem faz a capa ilustrada aparecer inteira, na proporção dela, dentro da página do projeto.
- As capas ilustradas ficam em `assets/`:
  - `capa-reforma-unifamiliar.svg`
  - `capa-interiores.svg`
  - `capa-paisagismo.svg`
  - `capa-moveis-planejados.svg`

## Foto da página Sobre mim

- Arquivo: `assets/foto-sobre.jpg`, recortado na mesma proporção do quadro do site (1 : 1,08).
- Para trocar, salve a nova foto com esse mesmo nome dentro de `assets/`.

## Modelo 3D

- `viewer3d.html` (na raiz, ao lado do `index.html`) é o visualizador 3D. Ele aparece num quadro dentro da página do projeto, assim que o visitante entra. O botão no canto do quadro amplia o modelo para a tela inteira; o X volta ao tamanho normal.
- O quadro só aparece nos projetos que têm estas linhas dentro do bloco, em `const projects`:

```js
modelo3d: 'viewer3d.html',
modelo3dPosicao: 'lado',
```

- `modelo3dPosicao` escolhe onde o quadro fica:
  - `'lado'`: quadro fixo no canto esquerdo, do tamanho de uma foto do carrossel; o carrossel passa ao lado, com a mesma folga que existe entre as fotos. Em tela estreita (menos de 1100 px de largura) e no celular, o quadro vai para baixo do carrossel. Em monitores com mais de 1920 px de largura, o conjunto fica centralizado.
  - `'abaixo'`: quadro abaixo do carrossel de fotos.
  - `'acima'`: quadro acima do carrossel de fotos.
- Hoje as linhas estão no projeto "Salão Vitalina de Beleza". Para tirar o quadro, apague as duas linhas. Para usar em outro projeto, mova as duas linhas para o bloco dele.
- O tamanho do quadro fica no CSS do `index.html`, no bloco "07B. MODELO 3D". Na posição `'lado'`, ele repete as medidas das fotos do carrossel; se mudar o tamanho das fotos, repita as medidas ali. Nas posições `'abaixo'` e `'acima'`, o tamanho está em `.modelo3d-box` (`width` e `height`).
- O modelo fica em `assets/modelo.glb` (hoje, o do Salão Vitalina, já aliviado para a web). Se esse arquivo faltar, o visualizador mostra uma casa de teste e o aviso "Modelo de teste".

### O que editar no viewer3d.html

Tudo fica no bloco `CONFIG`, no começo do script:

- `modelo`: caminho do arquivo `.glb`.
- `cenas`: cada cena vira um botão. Tem a câmera e as peças que mudam (`mover`, `escala`, `opacidade`). Clicar de novo no botão da cena atual recentra a vista.
- `comodos`: nome e posição dos botões que aparecem na cena "Planta" (`area`, em m², é opcional).
- `desenho`: qual desenho da lista `drawings` do projeto abre ao tocar em um cômodo (`indice: 0` é o primeiro).
- `implantacao`: opcional. O Salão Vitalina é de interiores e não usa (`implantacao: null`, cenas "Salão" e "Planta"). Para um projeto com terreno, crie uma cena com `implantacao: true` e preencha os retângulos do terreno, da área construída e das áreas impermeáveis; a área permeável, as porcentagens e a legenda são calculadas a partir deles.

### Para colocar o modelo do SketchUp

1. No SketchUp, dê nome aos grupos e componentes que vão se mexer (por exemplo `Telhado`, `Paredes`, `Pisos`).
2. Exporte em `.glb` (glTF binário), sem compressão Draco, e salve como `assets/modelo.glb`.
3. Abra `viewer3d.html?ajuste=1` pelo link do site. Esse modo lista os nomes das peças que vieram no arquivo e mostra as coordenadas de qualquer ponto em que você clicar.
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
- Para um segundo projeto com outro modelo, copie o `viewer3d.html` com outro nome (por exemplo `viewer3d-reforma.html`), ajuste o `CONFIG` e aponte a linha `modelo3d` desse projeto para o novo arquivo.
- No `index.html`, o que é do Modelo 3D está marcado nos blocos "07B. MODELO 3D" (CSS) e "12B. MODELO 3D" (JavaScript).
