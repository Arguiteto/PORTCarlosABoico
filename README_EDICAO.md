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
