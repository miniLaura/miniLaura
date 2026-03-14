<h1 align="center">Hi 🥰! I'm Laura Eduarda</h1>
<h3 align="center">💻 Systems Developer | 📊 Data Analysis Enthusiast</h3>

<p align="center">
🎓 Software Engineering Student <br>
📍 Brazil
</p>

---

## 👩‍💻 About Me

- 🔎 Passionate about technology and problem solving  
- 📊 Interested in Data Analysis and Backend Development  
- ⚙️ Experience with systems analysis and process improvement  
- 🚀 Always learning and building new projects  

---

## 🚀 Tech Stack

C • C++ • Java • Python • Flask • SQL • HTML • CSS • Git

---

## 📊 GitHub Stats

![GitHub stats](https://github-readme-stats.vercel.app/api?username=miniLaura&show_icons=true&theme=tokyonight)

---
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/miniLaura/miniLaura/output/pacman-contribution-graph-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/miniLaura/miniLaura/output/pacman-contribution-graph.svg">
  <img alt="pacman contribution graph" src="https://raw.githubusercontent.com/miniLaura/miniLaura/output/pacman-contribution-graph.svg">
</picture>

###
name: Generate pacman animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate pacman-contribution-graph.svg
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}


      - name: push pacman-contribution-graph.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}


