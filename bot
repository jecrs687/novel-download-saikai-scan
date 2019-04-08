import requests
from bs4 import BeautifulSoup
from ebooklib import epub

link = '/novels/the-beginning-after-the-end-tbate/post/capitulo-01-a-luz-no-fim-do-tunel/1304'
for y in range(0,10):
    conteudo = ''
    for z in range(0,15):
        site = requests.get('https://saikaiscan.com.br' + link)
        soup = BeautifulSoup(site.content, 'html.parser')
        link = soup.find_all('a', href = True)[2]['href']
        texto = soup.find_all('p')
        title = soup.find_all('h2')[0].text
        nome = soup.find_all('h1')[0].text
        conteudo = conteudo + '<h1>{}</h1>'.format(title)
        print(link)
        for x in range(0, len(soup.find_all('p'))):
            conteudo = conteudo+'<p>{}</p>'.format(texto[x].text)




    book = epub.EpubBook()
    book.set_identifier('id123456')
    book.set_title('tbate {}'.format(y))
    book.set_language('en')
    book.add_author('Desconhecido')
    c1 = epub.EpubHtml(title='Intro', file_name='chap_{}.xhtml'.format(y), lang='hr')
    c1.content='{}'.format(conteudo)
    book.add_item(c1)
    book.spine = ['nav', c1]
    book.add_item(epub.EpubNcx())
    book.add_item(epub.EpubNav())
    style = 'BODY {color: white;}'
    nav_css = epub.EpubItem(uid="style_nav", file_name="style/nav.css", media_type="text/css", content=style)
    book.add_item(nav_css)
    epub.write_epub('tbate {}.epub'.format(y), book, {})
    print(nome)
