# Tour / Sketch Tool

Ferramenta isolada em HTML puro para criar tours com fotos 360° e sketches/croquis, sem precisar editar configuração em JSON.

## Como usar

1. Abra `index.html` no navegador.
2. Preencha o nome do projeto.
3. Adicione ambientes ou estruturas.
4. Use foto 360° para panoramas e Sketch / foto comum para croquis, plantas, cortes e imagens de estudo.
5. Crie pontos de navegação entre os ambientes.
6. Clique em **Baixar pacote GitHub** para gerar um ZIP pronto para subir no repositório.

## Publicar no GitHub Pages

1. Extraia o ZIP gerado pela ferramenta.
2. Envie `index.html` e a pasta `assets/` para um repositório.
3. No GitHub, vá em **Settings → Pages**.
4. Publique a branch principal.
5. Abra o link gerado pelo GitHub Pages.

## Estrutura recomendada

```text
tour-sketch-tool/
├─ index.html
└─ assets/
   ├─ sala.jpg
   ├─ cozinha.jpg
   └─ sketch-planta.png
```

## Botões principais

- **Salvar local**: guarda o projeto no navegador.
- **Baixar HTML pronto**: baixa um `index.html` com o projeto embutido.
- **Baixar pacote GitHub**: baixa um ZIP com `index.html`, `assets/` e este README.
- **Carregar HTML**: reabre um `index.html` gerado por esta ferramenta para continuar editando.

## Fotos 360°

Use imagens equiretangulares em `.jpg`, `.png` ou `.webp`. Para criar um ponto de navegação, abra o ambiente, gire a vista até o ponto desejado e clique em **Marcar ponto**.

## Sketch / croqui

Use qualquer imagem comum. Clique em **Marcar ponto** e depois clique direto no local da imagem onde o botão deve aparecer.
