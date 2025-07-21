### 👨‍💻 Hi, I'm Mohsen!

Front-End Developer | HTML, CSS, JS, React, Next.js
Building responsive, accessible web apps with clean code and great UX..






![GitHub stats](https://github-readme-stats.vercel.app/api?username=mh3n&show_icons=true)  


### Contact me
[<img src='https://img.icons8.com/color/48/000000/linkedin-circled--v1.png' alt='linkedin' height='40'>](https://www.linkedin.com/in/mh3n/)    [<img src='https://img.icons8.com/color/48/000000/telegram-app--v1.png' alt='telegram' height='40'>](https://t.me/Seyedmh3n) 

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
