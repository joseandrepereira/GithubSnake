# 🐍 GitHub Snake 

Este tutorial ensina como adicionar a animação da cobrinha ao seu perfil do GitHub, mostrando sua atividade de contribuições de forma interativa!  

> 📌 **Créditos**: Este workflow foi criado por [Platane](https://github.com/Platane). O repositório original está disponível em:  
> 🔗 [https://github.com/Platane/snk](https://github.com/Platane/snk)

---
<br/>

# 📌 Estilos de Cobrinhas
### aqua.svg
![Snake animation - Aqua](https://github.com/joseandrepereira/joseandrepereira/blob/output/aqua.svg)

---

### burnt-yellow.svg
![Snake animation - burnt-yellow](https://github.com/joseandrepereira/joseandrepereira/blob/output/burnt-yellow.svg)

---

### candy.svg
![Snake animation - candy](https://github.com/joseandrepereira/joseandrepereira/blob/output/candy.svg)


---

### cool.svg
![Snake animation - cool](https://github.com/joseandrepereira/joseandrepereira/blob/output/cool.svg)

---

### cyberpunk.svg
![Snake animation - cyberpunk](https://github.com/joseandrepereira/joseandrepereira/blob/output/cyberpunk.svg)

---

### dusky-bloom.svg
![Snake animation - dusky-bloom](https://github.com/joseandrepereira/joseandrepereira/blob/output/dusky-bloom.svg)

---

### fire.svg
![Snake animation - fire](https://github.com/joseandrepereira/joseandrepereira/blob/output/fire.svg)

---

### forest.svg
![Snake animation - forest](https://github.com/joseandrepereira/joseandrepereira/blob/output/forest.svg)

---

### galaxy.svg
![Snake animation - galaxy](https://github.com/joseandrepereira/joseandrepereira/blob/output/galaxy.svg)

---

### github-snake-dark.svg
![Snake animation - github-snake-dark](https://github.com/joseandrepereira/joseandrepereira/blob/output/github-snake-dark.svg)

---

### github-snake.svg
![Snake animation - github-snake](https://github.com/joseandrepereira/joseandrepereira/blob/output/github-snake.svg)

---

### neon.svg
![Snake animation - neon](https://github.com/joseandrepereira/joseandrepereira/blob/output/neon.svg)

---

### ocean-dark.svg
![Snake animation - ocean-dark](https://github.com/joseandrepereira/joseandrepereira/blob/output/ocean-dark.svg)

---

### ocean.svg
![Snake animation - ocean](https://github.com/joseandrepereira/joseandrepereira/blob/output/ocean.svg)

---

### rainbow-dark.svg
![Snake animation - rainbow-dark](https://github.com/joseandrepereira/joseandrepereira/blob/output/rainbow-dark.svg)

---

### rainbow.svg
![Snake animation - rainbow](https://github.com/joseandrepereira/joseandrepereira/blob/output/rainbow.svg)

---

### space.svg
![Snake animation - space](https://github.com/joseandrepereira/joseandrepereira/blob/output/space.svg)

---

### sunset.svg
![Snake animation - sunset](https://github.com/joseandrepereira/joseandrepereira/blob/output/sunset.svg)


# ⚙️ Como configurar o workflow da cobrinha

Para adicionar a animação da cobrinha ao seu perfil do GitHub, siga os passos abaixo:

## 1️⃣ Criar um repositório no GitHub  
1. Acesse o [GitHub](https://github.com/) e faça login.  
2. Crie um novo repositório **público** com o nome **exatamente igual ao seu usuário do GitHub**.  
   - Exemplo: Se seu usuário for `joseandrepereira`, o repositório deve ser chamado `joseandrepereira`.  

## 2️⃣ Adicionar o workflow ao repositório  
1. No seu repositório, vá até a aba **Actions**.  
2. Clique no botão **New workflow** → **Set up a workflow yourself**.  
3. Substitua o conteúdo pelo código abaixo e salve como `.github/workflows/snake.yml`:  

   ```yaml
   name: Generator Snake

    on:
      schedule:
        - cron: "0 */12 * * *"
      workflow_dispatch:
      push:
        branches:
          - master
          - main
    
    jobs:
      generate:
        permissions: 
          contents: write
        runs-on: ubuntu-latest
        timeout-minutes: 10
        
        steps:
          - name: Checkout repository
            uses: actions/checkout@v4
    
          - name: Ensure dist directory exists
            run: mkdir -p dist
    
          - name: Generate GitHub Contribution Snake
            uses: Platane/snk/svg-only@v3
            with:
              github_user_name: ${{ github.repository_owner }}
              outputs: |
                dist/github-snake.svg
                dist/github-snake-dark.svg?palette=github-dark
                dist/ocean.svg?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
                dist/ocean-dark.svg?palette=github-light&color_snake=purple&color_dots=#8bd6cf,#1da2c2,#146589,#123b55,#12172b
                dist/burnt-yellow.svg?palette=github-light&color_snake=#3f170b&color_dots=#fff8cd,#d59037,#985a27,#673316,#3f170b
                dist/dusky-bloom.svg?palette=github-light&color_snake=#323021&color_dots=#fff8cd,#ffb2ed,#bfa0ff,#4b643f,#323021
                dist/sunset.svg?color_snake=red&color_dots=#ffdab9,#ffb347,#ff8c00,#ff4500,#dc143c
                dist/forest.svg?color_snake=green&color_dots=#d4edda,#a3d9a5,#76c68f,#45b06f,#2e8b57
                dist/galaxy.svg?color_snake=purple&color_dots=#e0bbff,#c77dff,#9d4edd,#6a0dad,#4b0082
                dist/fire.svg?color_snake=#141406&color_dots=#f2ffc4,#ffff7d,#ffc62b,#ff7219,##ff0054
                dist/neon.svg?color_snake=#412904&color_dots=#e6ffcc,#ccff99,#99ff66,#66ff33,#33cc00
                dist/candy.svg?color_snake=purple&color_dots=#ffb6c1,#ff85a2,#ff4f79,#ff1a52,#c71585
                dist/aqua.svg?color_snake=cyan&color_dots=#e0ffff,#b3ffff,#80ffff,#4dffff,#00ced1
                dist/space.svg?color_snake=red&color_dots=#16213e,#0f3460,#533483,#e94560,#ff6f61
                dist/cyberpunk.svg?color_snake=#004366&color_dots=#142107,#0f5a45,#ff948d,#ffcb9c,#fffab7
                dist/rainbow.svg?palette=github-light&color_snake=#1a1a1a&color_dots=#ffb3b3,#ffbb66,#ffec80,#66cc99,#6699ff,#4b1f5c
                dist/rainbow-dark.svg?palette=github-light&color_snake=#1a1a1a&color_dots=#e68a00,#e0d100,#4d8b66,#3366cc,#3d145e
                dist/cool.svg?palette=github-light&color_snake=#2b372f&color_dots=#f3eae8,#fffbc0,#ffe262,#ff921f,#327285
    
          - name: Debug - List generated files
            run: ls -R dist || echo "Directory dist does not exist"
    
          - name: Push generated files to output branch
            uses: crazy-max/ghaction-github-pages@v3.1.0
            with:
              target_branch: output
              build_dir: dist
            env:
              GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

## 3️⃣ Habilitar GitHub Actions
- Acesse a aba Actions no seu repositório.
- Verifique se o workflow foi criado corretamente.
- Se necessário, clique em Enable Workflow para ativá-lo.

## 4️⃣ Executar o workflow
O workflow roda automaticamente a cada 12 horas, mas você pode rodá-lo manualmente:

- Acesse Actions → Generator Snake.
- Clique em Run workflow para executar imediatamente.

## 5️⃣ Adicionar a cobrinha ao seu README do perfil
Edite seu README.md no repositório do seu perfil.

Adicione a imagem da cobrinha com este código:

```md
![GitHub Snake](https://github.com/SEU-USUARIO/SEU-USUARIO/blob/output/ESTILO-COBRINHA.svg)
```
- Substitua **SEU-USUARIO** pelo seu nome de usuário no GitHub.
- Substitua **ESTILO-COBRINHA** pelo estilo que você deseja adicionar.
   - [Ir para Estilos de Cobrinhas](#-estilos-de-cobrinhas)
- Salve o arquivo e veja a animação no seu perfil! 🎉
##
