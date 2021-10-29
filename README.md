<h1 align="center">Hi dear <img src="https://raw.githubusercontent.com/kaueMarques/kaueMarques/master/hi.gif" width="30px">, I'm Lucas</h1>

[![card](https://github-readme-stats.vercel.app/api?username=Planctor&theme=default&show_icons=true)](https://github.com/Planctor/)

[![Planctor](https://github-readme-stats.vercel.app/api/top-langs/?username=Planctor&hide=html&layout=compact&theme=default)](https://github.com/Planctor/)

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10

    steps:
      # generates a snake game from a github user (https://github.com/Planctor) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk@master
        with:
          github_user_name: ${{ github.repository_owner }}
          svg_out_path: dist/github-contribution-grid-snake.svg
