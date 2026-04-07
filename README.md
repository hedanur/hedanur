<p align="center">
  <img src="https://raw.githubusercontent.com/Platane/snk/output/github-contribution-grid-snake-dark.svg" width="100%" alt="snake animation" />
</p>








name: Yilan Oyunu

on:
  schedule: # Her 12 saatte bir çalışır
    - cron: "0 */12 * * *"
  workflow_dispatch: # Manuel çalıştırma butonu ekler

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Yilani Olustur
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Dosyalari Kaydet
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
