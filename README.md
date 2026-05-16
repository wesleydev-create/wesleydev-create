name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"

  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Generate github contribution grid snake
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: wesleydev-create
          outputs: dist/github-contribution-grid-snake.svg

      - name: Push snake animation
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
