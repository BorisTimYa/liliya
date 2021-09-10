Description: https://github.com/BorisTimYa/liliya/raw/c1643fa39fe535ff27807f2329584df7ed1423a7/tz.docx

1. `git clone https://github.com/BorisTimYa/liliya.git` 
2. `docker-compose up --no-start`
3. `docker-compose start`
4. `docker-compose exec app php composer.phar install`   
5. `docker-compose exec app bin/console doctrine:migration:migrate --no-interaction`
6. `docker-compose exec app bin/phpunit --verbose`
-------------------
USAGE:
   
    Author create: `curl -X POST -d "{\"name\":\"test1\"}" localhost:8888/author/create`
        {"id":10001}
    Book and author create: `curl -X POST -d "{\"name\":\"English title|Русское название\",\"author\":[\"Main author \",\"Second author\"]}" localhost:8888/book/create`
        {"id":10001}
    Search russian book: `curl -X SEARCH -d "название" localhost:8888/ru/book/search`
        [{"id":10001,"Name":"English title|Русское название","Author":[{"id":10002,"Name":"Main author "},{"id":10003,"Name":"Second author"}]}]
    Search english book in russian locale: `curl -X SEARCH -d "English" localhost:8888/ru/book/search`
        []
    Get english book info: `curl localhost:8888/en/book/10001`
        {"Name":"English title","Author":[{"Name":"Main author "},{"Name":"Second author"}]}    
    Get russian book info: `curl localhost:8888/ru/book/10001`
        {"Name":"Русское название","Author":[{"Name":"Main author "},{"Name":"Second author"}]}    
    
