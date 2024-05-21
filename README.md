Universidade Lusófona
**Programação Web**

# Ficha 12: Projeto 📜

### Enquadramento
* Esta é a última ficha constituinte do projeto de Programação Web.
* O projeto congrega todas as tarefas descritas nas fichas 4 a 12.
* A avaliação do projeto é feita avaliando a satisfação dos requisitos, que são as várias tarefas especificadas nas fichas 4 a 12.
* O prazo de submissão do projeto é 9 junho (o prazo e submissão das fichas das últimas semanas é apenas sugestivo, não representando *hard-deadlines* de submissão. No entanto, têm sido criadas fichas semanais para dosear o trabalho e pequenos módulos, realizando entregas regulares para se disciplinar e assim não acumular trabalho).
* A defesa do projeto será no dia 11 de junho de manhã. Terá duas partes: 
   * Implementação de um conjunto de alterações ao projeto.
   * Apresentação do website para os colegas.


### Objetivo desta ficha
**Desenvolver duas aplicações, meteorologia e portfólio**:
* Criar a aplicação Meteorologia, para se familiarizar com a utilização e criação de APIs
* Criar a aplicação Portfolio, onde definirá a *landing-page* do seu website axxxxxx.pythonanywhere.com, e que interligará através do menu todas as aplicações desenvolvidas.
* Aplicar em todas as páginas técnicas de CSS para aprimorar o layout e design, que deverá ser responsivo e dinâmico, garantindo que todas as paginas ficam bem no telemóvel e desktop. 
* Criar um repositório GitHub.

# Aplicação de Meteorologia 🌦️

### 0. Antes de iniciar esta aplicação:
* reveja os [slides](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-django-apis.pptx) sobre APIs
* explore a API do IPMA, em https://api.ipma.pt/. Em particular. familiarize-se com:
   * Previsões de vários tipos, disponiveis em URLs específicos e retornando dados em formato JSON. Exemplo de [endpoint](https://api.ipma.pt/open-data/forecast/meteorology/cities/daily/1110600.json)
   * [Lista](https://api.ipma.pt/open-data/distrits-islands.json) que mapeia identificadores (globalIdLocal) em nome da capital (local) 
   * [Lista](https://api.ipma.pt/open-data/weather-type-classe.json) de classes de tempo e descrição 
   * [Icons](https://api.ipma.pt/open-data/forecast/meteorology/icons_ipma_weather.zip) animados do estados do tempo 
* veja a aplicação https://pwback.pythonanywhere.com/meteo/
* Para consultar com o método GET o endpoint de uma API que disponibiliza um JSON, eis um exemplo:

```Python
import requests
url = 'url.do.endpoint.com'
response = requests.get(url)

if response.status_code == 200:
  dic_dados = response.json()
```

### 1. Aplicação Meteo
1. No seu projeto, crie uma nova aplicação chamada `meteo`
1. Guarde na pasta `static/meteo` os icones SVG animados disponibilizados na API. PAra tal, carregue o zip e crie um script em Python que descomprima os ficheiros. Execute a instrução `python manage-py collectstatic` para que fiquem disponíveis.

### 2. O tempo hoje em Lisboa 
Crie uma página com a previsão para meteorológica para hoje em Lisboa:
* Crie um caminho/view/template que apresenta previsão para meteorológica para hoje em Lisboa. 
* Consulte a API do IPMA e renderiza num HTML, de forma semelhante à apresentada na aplicação da [aula](https://pwback.pythonanywhere.com/meteo#api), a seguinte informação para a cidade de Lisboa:
   * nome da cidade
   * temperatura minima
   * temperatura maxima
   * data
   * descrição do tempo
   * link para o icone animado do tempo
* Para tal, deverá:
   * consultar o endpoint que retorna previsão para Lisboa.
   * consultar o endpoint que retorna as classes de tempo, e extrair a descrição do tipo de tempo correspondente ao `idWeatherType`.
   * construir o nome do ficheiro com o icon animado correspondente ao `idWeatherType`.
 
### 3. O tempo nos próximos 5 dias
Crie uma página que apresente o tempo hoje numa cidade à sua escolha.
* crie um caminho/view/template que apresenta num seletor a lista de cidades para as quais existem previsões meteorologicas.
* Mediante a escolha do utilizador, apresente na mesma página, a previsão meteorológica para os próximos 5 dias.

### 4. API meteo
Crie uma página que descreve uma API construida por si. deverá descrever em detalhe, e no formato dos últimos [slides](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-django-apis.pptx)  sobre APIs. 
Deverá ter pelo menos 3 enpoints diferentes:
* um que retorne a lista de cidades
* um que retorne previsao meteorologica de hoje para uma cidade
* um que retorne previsao meteorologica para os próximos 5 dias para uma cidade

Em termos de parâmetros, deverá devolver:
 * nome da cidade
 * temperatura minima
 * temperatura maxima
 * data
 * descrição do tempo
 * precipitação
 * link para o icone do tempo (que permita ser usado numa página como um URL)

# Aplicação Portfolio 

### 0. Antes de iniciar esta aplicação
* Explore os slides sobre [web design](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-web-design.pptx)
* Explore os slides sobre [efeitos e animações com CSS](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-efeitos-e-animacoes.pptx)
* Explore os slides sobre [layouts](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-layouts.pptx)
* Recomendação: esta aplicação fará a ponte para todas as aplicações desenvolvidas nas fichas anteriores, com links no seu menu. Uma aplicação do principio KISS é reutilizar a palavra index para a pagina de chegada de todas as aplicações. Como temos várias aplicações dentro do mesmo projeto e todas teem um caminho/route com `name='index'`, e vamos integrar tudo, para evitar ambiguidades em links usa-se o `app_name`. Garanta que define em `urls.py` a variável `app_name=‘meteo’`, e o usa em todos os links, por exemplo `{% url ‘meteo:index’ %}`.

### 1. Aplicação
1. No seu projeto, crie uma nova aplicação portfolio.
2. Aprimore a estética das páginas desta aplicação usando algumas das técnicas apresentadas nos slides.
3. Aplique as tecnicas CSS aplicadas nas últimas fichas, tais como flex, grid.
4. Escolha e use uma fonte Google a seu gosto.
   
### 2. *Landing-page*
1. Crie uma belissima página *landing-page* do seu projeto. Será a página do URL axxxxxx.pythonanywhere.com, página de chegada ao seu website, aplicando um bom design, e com um menu com apontadores para todas as aplicações que constituem o projeto.
2. Conceba a *landing-page* como uma *hero page*, constituída por três componentes: uma imagem grande, uma frase média, e um menu pequeno. Veja o exemplo nos slides de [web design (pg. 42 e seguintes)](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-web-design.pptx) e o vídeo:
https://github.com/ULHT-PW/pw-24-13-final/assets/42048382/885ce5fe-ec79-4aff-9b19-f033ac7dc65e
4. Aprimore a estética da página usando algumas das técnicas disponiveis nos slides sobre [efeitos e animações com CSS](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-efeitos-e-animacoes.pptx), tais como o uso de uma imagem de fundo ou vídeo, respeitando as boas práticas de web design!
3. Crie um menu global que encaminhe para as páginas desta aplicação assim como para as restantes aplicações que construiu. Inclua o botão de login (use um icon de [Font Awesome](https://fontawesome.com/)).
   * Garanta que, em todas as aplicações, em urls define `app_name`, de modo a que não haja incongruencias com links de aplicações.
   * Garanta que o menu está sempre disponível, permitindo a navegação entre todas as páginas.
5. Integre na landing-page o icon do tempo que fará hoje, utilizando a API meteo que desenvolveu.
6. Integre pelo menos 2 efeitos com JavaScript (que aprenderá na próxima semana) tais como botão de darkmode e apresentação da data e hora (com segundos a avançar).
   
### 3. MeByMe
* Crie uma página sobre si, a falar dos seus interesses, aptidões, competências, experiência, ao estilo de um CV. 
* Divida em partes, aplicando CSS flex para separar as várias componentes.
* Seja criativo.
  
### 4. Sobre o seu Website
1. Imagine que vai ter uma entrevista de emprego e quer partilhar um link que apresente tudo o que sabe de programação Web. Será esta página, onde falará sobre todos os aspectos tecnológicos aplicados neste Website. Torne esta página numa boa carta de apresentação tecnológica.
1. Liste as tecnologias que utilizou neste projeto Django.
1. Crie e inclua um vídeo de 1 minuto "Django hands-on" para leigos, a explicar como é que funciona o Django, baseado no MVC. Explique como se estrutura um projeto Django: projeto, aplicação, models, views, urls, templates.
1. Crie um vídeo de 1 minuto que faça uma "visita guiada" ao seu projeto Django e suas aplicações e páginas.
1. Em termos de design, experimente aplicar o efeito parallax nesta página, descrito nos slides sobre [efeitos, slide 12](https://moodle.ensinolusofona.pt/pluginfile.php/615262/course/section/443721/pw-24-12-efeitos-e-animacoes.pptx) e [CodePen](https://codepen.io/LucioStuder/pen/XWVKzpK?editors=1100).
1. Escolha uma palavra para colocar no menu link para esta página. Sobre, ou invente um nome ao seu gosto (WebWizardry, WebAlchemy, TechTools, WebTools, ...).

### 5. Automação
1. Crie uma página onde apresente o vídeo resultante da automação que fez com Selenium (TPC teórico da próxima semana).

# Criação de repositório GitHub
1. crie um repositório GitHub para o seu projeto com o nome axxxxxx-projeto-pw
2. carregue o projeto do PythonAnyWhere para esse repositório. Para tal, abra a consola, e na pasta onde está o `manage.py` execute os seguintes comandos:
   * `git init`
   * `git add *`
   * `git commit -m "projeto final"`
   * `git branch -M main`
   * `git remote add origin https://github.com/axxxxxx-projeto-pw`
   * git push -u origin main
  
   
# Submissão
* submeta o link para o seu projeto aqui (entrega a ser criada no Moodle)
* garanta que adicionou em `PythonAnyWhere\Account\Education\Yout Teacher` o user `pwprofs`
