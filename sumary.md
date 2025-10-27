### Postgres
WHERE  = Exemplo: Quero mostrar nos make quais sao os nomes de carro que são 'Ford' o where fica nesse tipo de problema entao pra resolvermos usaremos assim o comando WHERE
```SQL
SELECT * FROM car WHERE = 'Ford'
```
LIKE = Exemplo: Quero mostrar os primeiro nome que contem no final a letra 'o' o LIKE fica nesse tipo de problema então pra resolvermos usaremos assim o comando LIKE:
```SQL
SELECT * FROM car WHERE make LIKE '%o';
```
ILIKE = O ILIKE e a mesma coisa do LIKE mas oque muda que ele ignora se a letra for minuscula ou maiuscula por exemplo: Quero mostrar os primeiro nome de pessoas mas ignorando letras maiusculas ou minusculas,esse tipo de problema então pra resolvermos usaremos o comando ILIKE:
```SQL
SELECT * FROM person WHERE first_name 'l%';
```
COUNT = O COUNT e pra contar quantos elementos tem em alguma parte da lista especifica que eu escolher ou tudo COUNT(first_name) vai conta so o primeiro nome ,COUNT(*) vai conta tudo da lista entao usaremos um tipo assim se encaixaria numa situação que contem o COUNT:
```SQL
SELECT first_name ,COUNT(*) FROM person;
```
SELECT = SELECT E pra selecionar o que eu quero mostrar da lista por exemplo: SELECT * FROM person -> ele vai mostrar tudo da lista 'person'
```SQL
SELECT first_name FROM person;
```
 FROM = FROM e pra selecionar a lista que voce escolher por exemplo:
 ```SQL
 SELECT * FROM person;
 ```
 GROUP BY = GROUP BY ele serve para agrupar quantos elementos repetem em cada item por exemplo: Quero contar quantas pessoas que vivem em cada pais entao nesse caso usaremos o GROUP BY e o COUNT:
 ```SQL
 SELECT country_birth,COUNT(*) FROM person GROUP BY country_birth;
```
GROUP BY HAVING = GROUP BY HAVING é a mesma coisa do GROUP BY,so que eu boto um limite nele por exemplo:Quero contar quantos nomes repetem mais de 7 vezes na lista de primeiro nome(first_name) então nesse tipo situação usaremos o GROUP BY HAVING:
```SQL
ame,COUNT(*) FROM person GROUP BY first_name HAVING COUNT(*) > 7 ORDER BY first_name;
```
LIMIT = LIMIT e pra marcar uma da 0 ate a parte da lista que eu quero por exemplo:Quero mostrar as informações das 20 primeiras pessoas da lista entao usaremos este comando LIMIT então ficaria assim:
```SQL
SELECT * FROM person LIMIT 20;
```
OFFSET = OFFSET e pra marcar um inicio da onde que eu quero mostrar na lista e Limit do 0 ate o final entao vai aqui um exemplo: quero mostras as informações entres as pessoas que estao no id de 60-80 entao nesse caso usaremos o OFFSET e o LIMIT então ficaria assim:
```SQL
SELECT * FROM person OFFSET 60  LIMIT 80;
```
FETCH = FETCH e pra marcar literalmente um elemento da lista então usaremos um exemplo:Quero marcar todas as informações do id 168 então pra mostrarmos as informações do id 168 usaremos este comando:
```SQL
SELECT * FROM person 168 FETCH FIRST ROW ONLY; 
```
