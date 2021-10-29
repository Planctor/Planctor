<h1 align="center">Hi dear <img src="https://raw.githubusercontent.com/kaueMarques/kaueMarques/master/hi.gif" width="30px">, I'm Lucas</h1>

[![card](https://github-readme-stats.vercel.app/api?username=Planctor&theme=default&show_icons=true)](https://github.com/Planctor/)

[![Planctor](https://github-readme-stats.vercel.app/api/top-langs/?username=Planctor&hide=html&layout=compact&theme=default)](https://github.com/Planctor/)

name: generate animation

on:
  # run automatically every 6 hours
  schedule:
    - cron: "0 */6 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10

    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk@master
        with:
          github_user_name: ${{ github.repository_owner }}
          svg_out_path: dist/github-contribution-grid-snake.svg

      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v2.5.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
