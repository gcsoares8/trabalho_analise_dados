# Análise de dados
## Integrantes/Ra:
###### Guilherme Cardoso/318135325; Medllyn Thayna/318136828 ; Filipe Drumond/318127731; Victor Dutra/31811206; Breno Guimarães/31811209; Rafael Castro/318115768

## Estratégia utilizada: 
A estratégia utilizada para realizar a coleta de dados foi o método  Web Crawler com o framework Scrapy sendo programado com linguagem Python. Este método consiste em criar um coletor que é direcionado para um site web de nosso interesse aonde podemos realizar a coleta de dados por meio de um filtro. Este filtro é definido por arquivos css aonde nestes selecionamos quais os campos(ou tags) pelo código fonte da página aonde iremos realizar a coleta irá determinar o que será coletado. Neste arquivo, optamos por selecionar os nomes dos filmes mais populares e o seu ranking no ano de 2020. No código fonte, selecionamos as tags "td class = titleColumn" que está inserida na classe lister-list para realizar a filtragem pelo nome dos filmes e a tag "a". Para filtrar o ranking dos filmes, selecionamos a tag "div" em conjunto com a classe Velocity. Com a união de todos estes parâmetros, foi possível realizar a coleta necessária e com o resultado esperado.
O código utilizado em python para criar o webcrawler foi: 

import scrapy

class FilmesSpider(scrapy.Spider):
    name = 'filmes'
    allowed_domains = ['imdb.com']
    start_urls = ['https://www.imdb.com/chart/moviemeter']

    def parse(self,response):
    for filme in response.css('td.titleColumn'):
    yield {
        'titulo' : filme.css('td a::text').get(),
        'ranking' : filme.css('td div::text').get()
    }
