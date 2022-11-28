# Deploy de página feita em React

- Criar aplicação e repositório no Github
- Commitar aplicação
- Criar diretório ".github"
- Dentro do repositório ".github", criar o repositório "workflows"
- Dentro de workflows criar um arquivo com a extensão ".yml" com o código a seguir:
```
name: deploy

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v1
        with:
          node-version: '14.x'
      - name: Build web-app
        run: |
          npm ci
          npm run build
      - name: Deploy to gh-pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
```
> ATENÇÃO! Se atentar a branch que está fazendo o deploy.
- Commitar mudanças
- Entrar no arquivo "package.json"
- Criar o parametro a seguir: "homepage": "github-page/"
- Fazer o deploy da aplicação para o Github pages
