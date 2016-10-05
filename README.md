# RStudio-journey

> Jornada pelo R com RStudio e RMarkdown

## Requisitos

* R instalado
* RStudio instalado

```
git clone git@github.com:joao-parana/RStudio-journey.git
cd RStudio-journey/first
open /Applications/RStudio.app # Abra o projeto no RStudio
```


Você deve criar um arquivo `token_and_secret.R` após a execução do comando `git clone`. Veja um exemplo abaixo

```bash
cat token_and_secret.R 
# token_and_secret.R
token <- 'DA4DBF75A1E3DE080F6031E78987E4E9'
secret <- '5w9NnBffoc1OJTkEA9NnBfGmR8Vg13SXL080F603'
```
Você deve substituir o `token` e o `secret` com os dados obtidos no seu **dashboard** `Admin` do 
[https://www.shinyapps.io](https://www.shinyapps.io) pois estes valores acima são inválidos.

Veja [first/first-R-doc.md](first/first-R-doc.md) para detalhes sobre a linguagem **R**



