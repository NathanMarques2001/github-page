# Deploy de página feita em React

Após ter criado a aplicação e o repositório no Github, crie um repositório .github, dentro dele crie mais um repositório chamado workflows e dentro deste crie um arquivo com a extensão .yml com o seguinte código:
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
´´´
