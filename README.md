# quarto-hugomd-test
testing equations in quarto's hugo-md export


I started this project with the steps described [in the quickstart guide](https://gohugo.io/getting-started/quick-start).

```
hugo new site quarto-hugomd-test
git init
```

When cloning this repo, you will have to include a theme:

```
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml
```

(the `baseof.html` is taken from that theme)


The `./content/hugomd_testing.qmd` file should be rendered with 

```
quarto render hugomd_testing.qmd --to hugo-md
```


# versions


```{sh}
# pacman -Qv hugo quarto pandoc
hugo 0.145.0-1
quarto-cli-bin 1.7.6-1
pandoc-cli 3.1.12.1-5
```
