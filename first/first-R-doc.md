first-R-doc
================
João Antonio Ferreira
1 de outubro de 2016

-   [R Markdown](#r-markdown)
-   [Incluindo gráficos](#incluindo-graficos)
-   [Uma seção de exemplo no R](#uma-secao-de-exemplo-no-r)

R Markdown
----------

Este é um documento R Markdown. Markdown é um formato simples para gerar documentos HTML, DOCX e PDF. Mais detalhes em <http://rmarkdown.rstudio.com>.

Clicando no botão **Knit** será gerado um docuemnto contendo o texto formatado além dos resultados dos comandos R presentes no documento.

Uma documentação completa pode ser encontrada na WEB. Por exemplo, no endereço abaixo podemos ver a documentação sobre o atributo `output` do R-Markdown com valor `github_document`.

<http://rmarkdown.rstudio.com/github_document_format.html>

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

Incluindo gráficos
------------------

Você pode incluir gráficos como no exemplo abaixo:

![](first-R-doc_files/figure-markdown_github/pressure-1.png)

Observe o parâmetro `echo = FALSE` que previne da impressão (na saida) da linha de comando R que gerou o gráfico.

Uma seção de exemplo no R
-------------------------

Antes de começar vamos listar algumas URL úteis:

-   Stack Exchange para métodos numéricos em Estatística <http://stats.stackexchange.com/questions/tagged/r>

Operador atribuição

``` r
x <- 3.1416
print(x)
```

    ## [1] 3.1416

``` r
x
```

    ## [1] 3.1416

O `[1]` indica que `x` é um vetor e que `3.1416` é seu valor.

Outro exemplo:

``` r
msg <- "alô mundo !"
```

Podemos comentar o código R

``` r
# aqui entra comentário.
```

Podemos solicitar Help de um comando. Nesta caso uma pagina HTML será renderizada no painel Help (Normalmente embaixo à direita).

Suponha que desejemos usar o pacote `arules` e nem saibamos por onde começar. Podemos começar assim:

``` r
help("install.packages")
```

Então podemos instalar o pacote assim:

``` r
# Execute install.packages("arules")
```

Após a instalação podemos usá-lo

``` r
library("arules")
```

    ## Loading required package: Matrix

    ## 
    ## Attaching package: 'arules'

    ## The following objects are masked from 'package:base':
    ## 
    ##     abbreviate, write

Que tal verificar como funciona a funcão que lida com DataSetes

``` r
help("data")
```

Podemos listar todos os datasets instalados

``` r
data()
```

Ou podemos listar os datasets instalados apenas com o `arules`

``` r
try(data(package = "arules") )
```

OK, então podemos usar um dos datasets listados

``` r
ds <- c("Adult")
data(list = ds)
```

Agora podemos inspecionar o dataset Adult verificando sua dimensão (linhas e colunas)

``` r
dim(Adult)
```

    ## [1] 48842   115

Ou podemos inspecionar o dataset Adult vendo todo o resumo

``` r
summary(Adult)
```

    ## transactions as itemMatrix in sparse format with
    ##  48842 rows (elements/itemsets/transactions) and
    ##  115 columns (items) and a density of 0.1089939 
    ## 
    ## most frequent items:
    ##            capital-loss=None            capital-gain=None 
    ##                        46560                        44807 
    ## native-country=United-States                   race=White 
    ##                        43832                        41762 
    ##            workclass=Private                      (Other) 
    ##                        33906                       401333 
    ## 
    ## element (itemset/transaction) length distribution:
    ## sizes
    ##     9    10    11    12    13 
    ##    19   971  2067 15623 30162 
    ## 
    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    9.00   12.00   13.00   12.53   13.00   13.00 
    ## 
    ## includes extended item information - examples:
    ##            labels variables      levels
    ## 1       age=Young       age       Young
    ## 2 age=Middle-aged       age Middle-aged
    ## 3      age=Senior       age      Senior
    ## 
    ## includes extended transaction information - examples:
    ##   transactionID
    ## 1             1
    ## 2             2
    ## 3             3

Observe acima as métricas e resumos estatísticos sobre este dataset

    48842 linhas
      115 colunas
    ...
    ítens mais frequentes (valores discretos e seu quantitativo de ocorrências), etc.

Podemos executar uma função `eclat` sobre o dataset

``` r
e <- eclat(Adult)
```

    ## Eclat
    ## 
    ## parameter specification:
    ##  tidLists support minlen maxlen            target   ext
    ##     FALSE     0.1      1     10 frequent itemsets FALSE
    ## 
    ## algorithmic control:
    ##  sparse sort verbose
    ##       7   -2    TRUE
    ## 
    ## Absolute minimum support count: 4884 
    ## 
    ## create itemset ... 
    ## set transactions ...[115 item(s), 48842 transaction(s)] done [0.04s].
    ## sorting and recoding items ... [31 item(s)] done [0.01s].
    ## creating bit matrix ... [31 row(s), 48842 column(s)] done [0.01s].
    ## writing  ... [2616 set(s)] done [0.01s].
    ## Creating S4 object  ... done [0.00s].

E ver o resumo

``` r
summary(e)
```

    ## set of 2616 itemsets
    ## 
    ## most frequent items:
    ##            capital-loss=None            capital-gain=None 
    ##                         1255                         1220 
    ## native-country=United-States                   race=White 
    ##                         1213                         1169 
    ##                     sex=Male                      (Other) 
    ##                          932                         5459 
    ## 
    ## element (itemset/transaction) length distribution:sizes
    ##   1   2   3   4   5   6   7   8   9 
    ##  31 185 504 757 666 352 104  16   1 
    ## 
    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##     1.0     3.0     4.0     4.3     5.0     9.0 
    ## 
    ## summary of quality measures:
    ##     support      
    ##  Min.   :0.1000  
    ##  1st Qu.:0.1168  
    ##  Median :0.1390  
    ##  Mean   :0.1762  
    ##  3rd Qu.:0.1956  
    ##  Max.   :0.9533  
    ## 
    ## includes transaction ID lists: FALSE 
    ## 
    ## mining info:
    ##   data ntransactions support
    ##  Adult         48842     0.1

Ou inspecionar os detalhes

``` r
inspect(e)
```

Nesta inspeção vemos que a saida é muito grande e praticamente inutil para uma sessão interativa. Então vamos pegar apenas os *top five* considerando o atributo `support`

``` r
s <- sort(e)
```

``` r
p <- s[1:5]
inspect(p)
```

    ##      items                                 support  
    ## 2586 {capital-loss=None}                   0.9532779
    ## 2587 {capital-gain=None}                   0.9173867
    ## 2588 {native-country=United-States}        0.8974243
    ## 2585 {capital-gain=None,capital-loss=None} 0.8706646
    ## 2589 {race=White}                          0.8550428

Que tal integrar com o <https://www.shinyapps.io> ?

Fácil ! Instale o pacote `rsconnect`

``` r
# Execute install.packages("rsconnect")
```

Crie uma conta tipo **Free** usando seu e-mail preferido e entre no Dashboard <https://www.shinyapps.io/admin/#/dashboard>

``` r
# Read R file with token and secret 
source("../token_and_secret.R")
rsconnect::setAccountInfo(
        name='joao-parana',
              token=token,
              secret=secret)
```

**OBS:** *Crie sua propria conta e atualize a sua **secret***

Veja o texto abaixo retirado da página e Ajuda do RStudio.

**Using your R packages in the cloud**

In order to run your applications on shinyapps.io, the service needs to replicate the environment from your local machine. shinyapps.io is built using **Ubuntu Linux** as the base operating system, and is likely to be different from most users’ systems.

``` r
library(shiny)
server = function(input, output) {
  output$distPlot <- renderPlot({
    # generate bins based on input$bins from ui.R
    x    <- faithful[, 2]
    bins <- seq(min(x), max(x), length.out = input$bins + 1)
    # draw the histogram with the specified number of bins
    hist(x, breaks = bins, col = 'darkgray', border = 'white')
  })
}

ui <- shinyUI(fluidPage(

  # Application title
  titlePanel("Old Faithful Geyser Data"),
  # Sidebar with a slider input for number of bins
  sidebarLayout(
    sidebarPanel(
      sliderInput("bins",
                  "Number of bins:",
                  min = 1,
                  max = 50,
                  value = 30)
    ),
    # Show a plot of the generated distribution
    mainPanel(
      plotOutput("distPlot")
    )
  )
))

# shinyApp(ui = ui, server = server)
```

``` r
# getwd()
# library(rsconnect)
# rsconnect::deployApp('/Users/admin/Desktop/Development/yarn-cefet/R-studio-sessions/shinyApp')
```
