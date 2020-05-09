# Análise de dados
## Integrantes/Ra:
###### Guilherme Cardoso/318135325; Medllyn Thayna/318136828 ; Filipe Drumond/318127731; Victor Dutra/31811206; Breno Guimarães/31811209; Rafael Castro/318115768

## Estratégia utilizada: 
A estratégia utilizada para realizar a coleta de dados foi o método  Web Crawler com o framework Scrapy sendo programado com linguagem Python. Este método consiste em criar um coletor que é direcionado para um site web de nosso interesse aonde podemos realizar a coleta de dados por meio de um filtro. Este filtro é definido por arquivos css aonde nestes selecionamos quais os campos(ou tags) pelo código fonte da página aonde iremos realizar a coleta irá determinar o que será coletado. Neste arquivo, optamos por selecionar os nomes dos filmes mais populares e o seu ranking no ano de 2020. No código fonte, selecionamos as tags "td class = titleColumn" que está inserida na classe lister-list para realizar a filtragem pelo nome dos filmes e a tag "a". Para filtrar o ranking dos filmes, selecionamos a tag "div" em conjunto com a classe Velocity. Com a união de todos estes parâmetros, foi possível realizar a criação de um outro arquivo para visualização dos dados com a extensão .json. 

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
    
    Segue resultado da coleta: 
    [
{"titulo": "Extraction", "ranking": "1\n(no change)\n"},
{"titulo": "Bad Education", "ranking": "2\n"},
{"titulo": "365 Days", "ranking": "3\n"},
{"titulo": "The Gentlemen", "ranking": "4\n"},
{"titulo": "The Lodge", "ranking": "5\n"},
{"titulo": "Once Upon a Time... in Hollywood", "ranking": "6\n"},
{"titulo": "The Willoughbys", "ranking": "7\n"},
{"titulo": "The Platform", "ranking": "8\n"},
{"titulo": "Parasite", "ranking": "9\n"},
{"titulo": "Star Wars: Episode IX - The Rise of Skywalker", "ranking": "10\n"},
{"titulo": "Dangerous Lies", "ranking": "11\n"},
{"titulo": "Knives Out", "ranking": "12\n"},
{"titulo": "Arkansas", "ranking": "13\n"},
{"titulo": "Avengers: Endgame", "ranking": "14\n"},
{"titulo": "Bad Boys for Life", "ranking": "15\n"},
{"titulo": "1917", "ranking": "16\n"},
{"titulo": "Dune", "ranking": "17\n"},
{"titulo": "Trolls World Tour", "ranking": "18\n"},
{"titulo": "Joker", "ranking": "19\n"},
{"titulo": "The Assistant", "ranking": "20\n"},
{"titulo": "Little Women", "ranking": "21\n"},
{"titulo": "The Goonies", "ranking": "22\n"},
{"titulo": "Code 8", "ranking": "23\n"},
{"titulo": "Hustlers", "ranking": "24\n"},
{"titulo": "Birds of Prey: And the Fantabulous Emancipation of One Harley Quinn", "ranking": "25\n"},
{"titulo": "The Shawshank Redemption", "ranking": "26\n(no change)\n"},
{"titulo": "Bloodshot", "ranking": "27\n"},
{"titulo": "The Godfather", "ranking": "28\n"},
{"titulo": "Django Unchained", "ranking": "29\n"},
{"titulo": "Jojo Rabbit", "ranking": "30\n"},
{"titulo": "Midsommar", "ranking": "31\n"},
{"titulo": "Onward", "ranking": "32\n"},
{"titulo": "The Invisible Man", "ranking": "33\n"},
{"titulo": "Snowpiercer", "ranking": "34\n"},
{"titulo": "Fantasy Island", "ranking": "35\n"},
{"titulo": "Jumanji: The Next Level", "ranking": "36\n"},
{"titulo": "Contagion", "ranking": "37\n"},
{"titulo": "Underwater", "ranking": "38\n"},
{"titulo": "Gretel & Hansel", "ranking": "39\n"},
{"titulo": "The Lighthouse", "ranking": "40\n"},
{"titulo": "Sonic the Hedgehog", "ranking": "41\n"},
{"titulo": "Uncut Gems", "ranking": "42\n"},
{"titulo": "After We Collided", "ranking": "43\n"},
{"titulo": "The Half of It", "ranking": "44\n"},
{"titulo": "Call Me by Your Name", "ranking": "45\n"},
{"titulo": "Inception", "ranking": "46\n"},
{"titulo": "Slumdog Millionaire", "ranking": "47\n"},
{"titulo": "The Irishman", "ranking": "48\n(no change)\n"},
{"titulo": "Interstellar", "ranking": "49\n"},
{"titulo": "Dolittle", "ranking": "50\n"},
{"titulo": "Ford v Ferrari", "ranking": "51\n"},
{"titulo": "It Chapter Two", "ranking": "52\n"},
{"titulo": "The Departed", "ranking": "53\n"},
{"titulo": "Men in Black: International", "ranking": "54\n"},
{"titulo": "Pulp Fiction", "ranking": "55\n"},
{"titulo": "Harry Potter and the Sorcerer's Stone", "ranking": "56\n"},
{"titulo": "No Time to Die", "ranking": "57\n"},
{"titulo": "Sergio", "ranking": "58\n"},
{"titulo": "The Hunt", "ranking": "59\n"},
{"titulo": "Life of Pi", "ranking": "60\n"},
{"titulo": "6 Underground", "ranking": "61\n"},
{"titulo": "Tenet", "ranking": "62\n"},
{"titulo": "Captain America: The First Avenger", "ranking": "63\n"},
{"titulo": "Mrs. Serial Killer", "ranking": "64\n"},
{"titulo": "The Dark Knight", "ranking": "65\n"},
{"titulo": "Avengers: Infinity War", "ranking": "66\n"},
{"titulo": "Love Wedding Repeat", "ranking": "67\n"},
{"titulo": "The Lord of the Rings: The Fellowship of the Ring", "ranking": "68\n"},
{"titulo": "Thor: Ragnarok", "ranking": "69\n"},
{"titulo": "The Outsiders", "ranking": "70\n"},
{"titulo": "The Lion King", "ranking": "71\n"},
{"titulo": "Bombshell", "ranking": "72\n"},
{"titulo": "Mulan", "ranking": "73\n"},
{"titulo": "Almost Famous", "ranking": "74\n"},
{"titulo": "Dune", "ranking": "75\n"},
{"titulo": "Suicide Squad", "ranking": "76\n"},
{"titulo": "Portrait of a Lady on Fire", "ranking": "77\n"},
{"titulo": "Spenser Confidential", "ranking": "78\n"},
{"titulo": "Blade Runner 2049", "ranking": "79\n"},
{"titulo": "Guardians of the Galaxy", "ranking": "80\n"},
{"titulo": "Inglourious Basterds", "ranking": "81\n"},
{"titulo": "Angel Has Fallen", "ranking": "82\n"},
{"titulo": "Gladiator", "ranking": "83\n"},
{"titulo": "The Matrix", "ranking": "84\n"},
{"titulo": "The Call of the Wild", "ranking": "85\n"},
{"titulo": "Frozen II", "ranking": "86\n"},
{"titulo": "Titanic", "ranking": "87\n"},
{"titulo": "The Wolf of Wall Street", "ranking": "88\n"},
{"titulo": "Black Widow", "ranking": "89\n"},
{"titulo": "The Breakfast Club", "ranking": "90\n"},
{"titulo": "Spider-Man: Far from Home", "ranking": "91\n"},
{"titulo": "It", "ranking": "92\n"},
{"titulo": "Wonder Woman 1984", "ranking": "93\n"},
{"titulo": "Jurassic World", "ranking": "94\n"},
{"titulo": "Jurassic Park", "ranking": "95\n"},
{"titulo": "Fight Club", "ranking": "96\n"},
{"titulo": "Se7en", "ranking": "97\n"},
{"titulo": "Yesterday", "ranking": "98\n"},
{"titulo": "The Killing of a Sacred Deer", "ranking": "99\n"},
{"titulo": "Doctor Sleep", "ranking": "100\n"}
]
