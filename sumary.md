# Guia de Comandos PostgreSQL

## WHERE
Filtra registros com base em uma condição específica.

**Exemplo:** Mostrar todos os carros da marca 'Ford'

```sql
SELECT * FROM car WHERE make = 'Ford';
```

---

## LIKE
Busca padrões em texto usando curingas (`%` para qualquer sequência, `_` para um caractere).

**Exemplo:** Mostrar carros cujo nome termina com a letra 'o'

```sql
SELECT * FROM car WHERE make LIKE '%o';
```

---

## ILIKE
Funciona como o `LIKE`, mas ignora diferenças entre maiúsculas e minúsculas.

**Exemplo:** Mostrar pessoas cujo primeiro nome começa com 'l', ignorando case

```sql
SELECT * FROM person WHERE first_name ILIKE 'l%';
```

---

## COUNT
Conta o número de registros em uma consulta.

**Exemplo:** Contar todos os registros da tabela pessoa

```sql
SELECT COUNT(*) FROM person;
```

**Exemplo:** Contar registros agrupados por primeiro nome

```sql
SELECT first_name, COUNT(*) FROM person GROUP BY first_name;
```

---

## SELECT
Seleciona quais colunas exibir nos resultados.

**Exemplo:** Selecionar apenas o primeiro nome

```sql
SELECT first_name FROM person;
```

**Exemplo:** Selecionar todas as colunas

```sql
SELECT * FROM person;
```

---

## FROM
Especifica de qual tabela os dados serão consultados.

**Exemplo:** Consultar dados da tabela pessoa

```sql
SELECT * FROM person;
```

---

## GROUP BY
Agrupa registros com base em uma ou mais colunas.

**Exemplo:** Contar quantas pessoas nasceram em cada país

```sql
SELECT country_birth, COUNT(*) FROM person GROUP BY country_birth;
```

---

## GROUP BY HAVING
Adiciona uma condição de filtro aos grupos criados pelo `GROUP BY`.

**Exemplo:** Mostrar nomes que aparecem mais de 7 vezes

```sql
SELECT first_name, COUNT(*) 
FROM person 
GROUP BY first_name 
HAVING COUNT(*) > 7 
ORDER BY first_name;
```

---

## LIMIT
Limita o número de registros retornados.

**Exemplo:** Mostrar apenas as primeiras 20 pessoas

```sql
SELECT * FROM person LIMIT 20;
```

---

## OFFSET
Pula um número específico de registros antes de começar a retornar resultados.

**Exemplo:** Mostrar pessoas do ID 60 ao 80

```sql
SELECT * FROM person OFFSET 60 LIMIT 20;
```

---

## FETCH
Alternativa ao `LIMIT` para buscar um número específico de linhas (sintaxe SQL padrão).

**Exemplo:** Buscar apenas a primeira linha

```sql
SELECT * FROM person OFFSET 168 FETCH FIRST 1 ROW ONLY;
```
## MAX
Busca em uma lista que desejo procurar o maior item nele.

**Exemplo:** Mostrar o maior preço da linha price.
```sql
SELECT MAX(price) FROM car;
``` 

## MIN
Busca em uma lista que desejo procurar o menor item nele.

**Exemplo:** Mostrar a pessoa da lista que é mais nova
```sql
SELECT MIN(age) FROM person;
```

## AVERAGE
Busca em uma lista que desejo procurar a media dos itens nele.
**Exemplo:** Mostrar a media das datas de aniversarios da lista.
```sql
SELECT AVG(date_of_birth) FROM person;
```

## ROUND
Abaixa o numero de casas decimais da lista.
**Exemplo:** Mostrar a media dos preços dos carros com somente duas casas decimais.
```sql
SELECT ROUND(AVG(price,2)) FROM car;
```

## ORDER BY ASC OR ORDER BY DESC
ORDER BY ASC: ele arruma a ordem do menor pro maior

ORDER BY DESC: ele arruma a ordem do maior para o menor
**Exemplo:** quero pegar mostrar as pessoas mais novas primeiros e depois os mais velhos
```sql
SELECT * FROM person ORDER BY ASC;
```

**Exemplo:** quero pegar mostrar as pessoas mais velhas primeiros e depois os mais novos
```sql
SELECT * FROM person ORDER BY DESC;
```
## ARITMÉTICAS BÁSICAS DE OPERAÇÕES
Conta de mais
```sql
SELECT 190 + 280;
```

Conta de menos
```sql
SELECT 175 - 80;
```

Conta de multiplicação 
```sql
SELECT 10 * 8;

```
Conta de divisão
```sql
SELECT 75 / 5;
```
Conta de potência
```sql
SELECT 5^3;
```

Conta de fatorial
```sql
SELECT 5!;
```

Conta de resto de divisão
```sql
SELECT 65 % 5:
```

## CONTAS ARITMÉTICAS UTILIZANDO O ROUND
## + 
Utilizamos o round com mais pra algum tipo desse problema aqui:
**Exemplo:** Quero dos preços dos carros ter 10% de desconto do preço original
```sql
SELECT id,make,model,price,ROUND(price *.10) FROM car;
```

## ALIAS
O alias que é o "as" serve que quando se usa round no titulo da lista nao fique "round" fique o nome de sua preferencia entao vamos usar o mesmo exemplo de cima:
***Exemplo:**Quero dos preços dos carros ter 10% de desconto do preço original,mudando o nome da tabela de round para price_descount.
```sql
SELECT id,make,model,price AS original_price, ROUND(price *.10,2)
AS price_descount, ROUND(price - (price * 10),2) AS discount_after_10_porcent FROM car;
```

## COALESCE
O coalesce serve para mostrar o nome da lista com o que eu quiser dentro da lista o que eu quiser.
**Exemplo:** Quero uma lista chamada Nomes que contem um nome chamado "James"
```sql
SELECT COALESCE(James) AS nomes;
```

**Exemplo:** Na lista person as datas de aniversarios que estiverem vazias colocar "Data de nascimento não encontrada"
```sql
SELECT COALESCE(date_of_birth, 'Data de nascimento não encontrada') FROM person;
```

## NULLIF
E pra checar se numero e igual o numero.


**Exemplo:** Quero verificar se o numero 200 e igual o numero 100
```sql
SELECT NULLIF(200,100);
nullif
-----
    200
```
**Exemplo:** Quero verificar se o numero 300 e igual o numero 300
```sql
SELECT NULLIF(300,300);
nullif
-----
```

## NOW()
Serve para mostrar a data e o horario atual
```sql
SELECT NOW()
            now
---------------------------
  2025-10-26 18:54:56.160701+00
```

## TIME()
Serve para mostrar o horario atual
```sql
SELECT NOW()::TIME;
        now
------------------
18:59:40.948543
```

## DATE()
Serve para mostrar a data atual
```sql
SELECT NOW()::DATE;
        now
------------------
2025-10-26
```

## INTERVAL
Serve para adicionar ou abaixar o ano atual que estamos.
**Exemplo:** Quero mostrar do ano atual - 10 anos
```sql
SELECT NOW() - INTERVAL ('10 YEARS');
        column
----------------------------
    2015-10-26 19:09:12.601774+00
```
**Exemplo:** Quero mostrar o ano atual + 27 anos
```sql
SELECT NOW() + INTERVAL '27 YEARS';
        column
-----------------------------
2052-10-26 19:11:46.775456+00
```
**Exemplo:** Quero mostrar somente a data - 7 meses com inves escrito "column" escrito "date"
```sql
SELECT (NOW()::DATE - INTERVAL '7 MONTHS')::DATE;
    date
------------------
2025-03-26
```

## EXTRACT
É para extrair alguma informação de alguma lista

**Exemplo:** Quero mostrar a idade das pessoas da tabela "person"
```sql
SELECT first_name,last_name,gender,country_birth,date_of_birth, AGE(NOW() ,date_of_birth ) AS age FROM person;
``` 
## ADDING PRIMARY KEY
Para adicionar uma "primary key" usaremos o "ALTER TABLE" e lembrando que a ID nao pode estar duplicada

**Exemplo:** Quero adicionar uma PRIMARY KEY de um id
```sql
ALTER TABLE person ADD PRIMARY KEY (id);
```

## ADDING CONSTRAINTS
Para adicionar uma "constraints" usaremos o "ALTER TABLE" como uma UNICA constraints então ficaria assim,lembrando que o id nao pode estar duplicado ou seja se tentar add uma pessoa com mesmo email de outra pessoa vai dar ERRO
```sql
ALTER TABLE person ADD CONSTRAINT unique_email_adress UNIQUE (email);
```

## DELETE PRIMARY KEY
Para apagar uma "primary key" usaremos o "DELETE".
**Exemplo:** Quero Deletar o id 58
```sql
DELETE from person WHERE id = 58;
```

## DELETE CONSTRAINTS
Para deletar constancias usaremos o "DROP CONSTRAINT" entao ficaria assim:
```sql
ALTER TABLE person DROP CONSTRAINT unique_email_adress;
```

## CHECK CONSTRAINTS
Para checar constancias usaremos o "CHECK" entao ficaria assim:
**Exemplo:** Quero que so tenha homens e mulheres de genero
```sql
ALTER TABLE person ADD CONSTRAINT gender_contraint CHECK (gender = 'Female' OR 'Male');
```

## DELETE RECORDS
 ```sql
 DELETE FROM person WHERE gender = 'Male';
 ```

 ## UPDATE RECORDS 
Usaremos para atualizar informações de algum usuario(id) da lista ou substituir informações do id

**Exemplo:** O id 172 não aparece o ano de nascimento dele,e o ano de nascimento dele é:2025-02-04
```sql
UPDATE person SET date_of_birth = '2025-02-04' WHERE id = 172; 
```

## INNER JOINS
E a combinação de duas listas(tables).
**Exemplo:** Tenho a TABLE A e a TABLE B e tipo fazer uma junção de TABLE A + TABLE B = TABLE C
```sql
SELECT * FROM person
JOIN car ON person.car_id = car.id;
```
**Exemplo:** Quero mostrar o primeiro nome,modelo do carro,preço do carro,onde ele é feito.
```sql
SELECT person.first_name,car.make,car.model,car.price
FROM person
JOIN car ON person.car_id = car.id;
```

## LEFT JOINS
O left joins e simplesmente a adição de uma table toda com pouca de uma outra table
**Exemplo:** Tenho uma TABLE A e a TABLE B incluo toda a TABLE A e somo com um pouco da TABLE B
```sql
SELECT * FROM person
LEFT JOIN car ON car.id = person.car_id;
```

## EXPORTING QUERY RESULTS TO CSV
Tem um comando "\copy" que server para pegar a table que voce fez e transforma-la em um arquivo para voce ver essa table dentro desse arquivo e para funcionar voce tem que digitar esse comando:
```sql
\copy (SELECT * FROM person LEFT JOIN car ON car.id = person_car_id) TO'/home/lucas/Desktop/results.csv' DELIMITER ','CSV HEADER;
```

## SERIAL & SEQUENCES
sequence = para mostrar o ultimo numero da sequencia sequence e simbolizado por: "seq",next value = next value e para mostrar o proximo valor do ultimo valor da sequencia e é simbolizado por: "nextval" e na proxima vez que voce colocar um insert person se voce usou o comando nextval e parou no 8 o proximo insert person que voce usar o ID vai ser 9
```sql
SELECT * FROM person_id_seq;
```
```sql
SELECT nextval('person_id_seq'::regclass);
```
e voce pode restartar o contador de valor usando o RESTART e o ALTER SEQUENCE juntos entao ficaria assim o comando
```sql
ALTER SEQUENCE person_id_seq RESTART WITH 8;
```
E ai a lista voltaria pro 8

## EXTENSIONS
voce pode ver as extensões que voce pode usar utilizando este comando:
```sql
SELECT * FROM pg_available_extensions;
```

## UNDERSTANDING UUID DATA TYPE
https://en.wikipedia.org/wiki/Universally_unique_identifier ler sobre isso pra enter as datas types sobre UUID
nas partes das extensões vemos que possamos utilizar o "uuid-ossp" e para usar ele ter que tem instalado uma versão

.Instalar extensão
```Sql
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
CREATE EXTENSION
```
Usaremos do comando "uuid-ossp" o sub-comando chamado "uuid_generate_v4()(random);
```Sql
SELECT uuid_generate_v4();
```
ele sempre vai gerar uma chave aleatória vai mudar a chave da data base que ajuda muito a evitar ataques,infiltrações etc

## UID AS PRIMARY KEYS
se utiliza pra mostrar o uid de algum usuario(ID) da TABLE entao vai ficar tipo;
```sql
-[RECORD 3]-----------------------
person_uid       | 03124a50-407e-4d8e-95c1-e534393503f4
first_name       | Adriana
last_name        | Matuschek
gender           | Female
email            | amatuschek2@feedburner.com
date_of_birth    | 1965-02-28
country_of_birth | Cameroon
car_uid          |

insert into person (person_uid, first_name, last_name, gender, email, date_of_birth, country_of_birth) values (uuid_generate_v4,'Adriana','Matuschek','Female','amatuschek2@feedburner.com','1965-02-28','Cameroon');
```

## Dicas
- Use `*` para selecionar todas as colunas, mas especifique colunas quando possível para melhor performance
- Combine `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`, `LIMIT` e `OFFSET` para consultas mais complexas
- `ILIKE` é específico do PostgreSQL; em outros bancos use `LOWER()` ou `UPPER()`