---
layout: post 
category: 
title: "Tutorial sobre banco de dados geográficos"
tagline: 
permalink: /posts/2018/11/tutorial-bd/
tags : [gis, qgis, postgres, postgis, banco de dados] 
published: true
---

**(Esse tutorial foi baseado nas aulas do professor Eduilson Livio Neves da Costa Carneiro - IFPI)**
**Sumário** 
1. Programa e instalação
2. Criando e manipulando dados com o pgAdmin III
3. Integração de banco de dados com sistemas de informação geográfica

### 1. Programas e instalação
Os programas usados neste tutorial são: QGIS, PostgreSQL, PgAdmin III, PostGIS e PostGIS Shapefile importer. Eles são relativamente simples para instalar, apenas do PostgresSQL será destacado alguns passos. O processo de instalação do QGIS é bem simples, podendo fazer a instalação padrão apenas pressionando o botão “Próximo”. Para este tutorial é possível utilizar o QGIS a partir da versão 2.11. Porém, aqui foi utilizado a versão 2.18.15. Você poderá baixar diretamente do site do QGIS, ou temporariamente no seguinte link: [QGIS 2.18.15](https://www.dropbox.com/s/orzsr7svplmptsj/QGIS-OSGeo4W-2.18.15-1-Setup-x86_64.exe?dl=0).  

![](https://lh4.googleusercontent.com/Cen1ctydfHDVCQM8WbLZ5iw1JrF63UfxCGRThaMWl4TdXoJXub72CYUlVHji6ZqgiFXyPYIw-JuA6P1r5QpcZpgy3J1CII6rcdYxT4yRKbcuFA7efFFqMaJBVwm3Xp3hKWjh0E_x)


O PostgresSQL é de fato uma coleção de programas, incluindo o servidor e alguns programas. Destacando o PG Admin III que é usado para administrar o servidor e como cliente, para acessar e gerenciar os dados. A versão utilizada nesse tutorial é a 9.5, e pode ser baixada  diretamente pelo site: [https://www.postgresql.org/download/](https://www.postgresql.org/download/)
Na tela inicial da instalação, basta clicar em “Next”.

![](https://lh5.googleusercontent.com/01uP23QXIs72wRPvha9F6Sk28r8DrLfLnD5P1NTAb5EtiC0s09SEQNktEHt2BFfBZEjHIBUSA6w2G8PuW2lMmT_Edp9XPMxgu7omWAcd-ZY91xl23YxPIKKvdp29dm3FTLHNqOjO)


Selecione o diretório destino, pode utilizar o diretório indicado por padrão:

![](https://lh4.googleusercontent.com/aGfzB5bO3X7HQ8cE2UFM4bvR4r3_ljsu8CKpc-IpofUQ45ustPTvWq-Xe4ck2KBNXnMyrvRzY36zO86A8vwG9Kbej5V99V2WQpGjY6mKBfE9Cf6EsoR0-zio2JZxTjRzxv8cAgct)


 O mesmo se aplica ao diretório aonde serão armazenados os dados:

![](https://lh3.googleusercontent.com/yf5ZpSNRosD2AnV67vCF65NuxNu3XMv-afTIHcHGfIZ6bN45hH-vVYad3vMkcldFLawTSkqf9QViXOGiJ8W-EFpJBeDI0k0Nzw2xmefJbw_fNHLVNMm0lJ9497ZoJsi5W1eW3Ij8)


Na tela a seguir entre com a senha que será usado pelo usuário postgres para acessar o servidor. Para uso pessoal, pode-se usar a senha postgres.

![](https://lh4.googleusercontent.com/38sQ3w0REHox-r5UCfNo2njLjL5mNa0eSV-Bwbyji88nUZH3-pPYhLi0Ms6se0pYjPGO5zxiQUsi7eEHk4c0TmFNQ-0modrvOhGdGCWm0DwbUo37fU1xWLSBAg8e8TEH5QhGa16D)


A porta para acessar o servidor pode ser a padrão:

![](https://lh4.googleusercontent.com/99dau4ydYOGQKGPEb3bey1bW1hHXvzaxQmuLwOP4hJVEvk9YBme3Jj3EIQQGvX8Wb6rYHIj4lD6UyeB57HeP1XWzHi2Hh-X9aCFPg_WIyd_kERglosm6RACPehh9VjDqLTK_TR2o)


Para as próximas telas, basta clicar em “Next”. Após a instalação, aparecerá a seguinte tela:

![](https://lh3.googleusercontent.com/UOCNKW1ke47_qQ7oIfln7vSGxe6FB7M9YkZlR5TDttLjFmWdb965kl964v_IUzr5zJG06QMnBtEP53Tu5eimfGPpsOV-UrtBulSl6TGa7A5xCGxrSBCFVgWm-xtG2Knw6kXgEX2w)


Mantenha selecionado a opção “Stack Builder”. Essa opção iniciará a instalação dos adicionais, incluindo o PostGIS. Na primeira tela, deve aparecer selecionado o servidor instalado, no caso PosgreSQL 9.5
 

![](https://lh3.googleusercontent.com/jPTvB5ft0n8yc-LXkGa-LhnePqQ_k2G3S2y90sH4RIYtAcCfDILo1GPsntU-22RQIcu-ql89YYo2QHhVxI4ElRi-EHJKeCE2nnZ9Ai-ZtW0mytb4ZpDU9x4gQ4xrRx_r7KXwynlR)


A seguir irá aparecer uma lista para selecionar os componentes. Para este tutorial será preciso selecionar apenas o PostGIS como abaixo:

![](https://lh5.googleusercontent.com/MnhrKx1Tz5tzjd00LrU05DYlMpzBqa6ji9Pzg8laLCTz9svBpQGd9pR86qxCoUK0dPU7JG6mRPMJeScayJYqxAh8kbmIBtg_oJ2EeFJ8-ZdvPs3XrkiBV-90gFVsUQr_ZTcB6z-H)


Para concluir a instalação basta selecionar “Next” nas próximas telas, então terá os programas PostgreSQL, PgAdmin III, PostGIS e PostGIS Shapefile importer instalados e prontos para iniciar o tutorial.

----------

### 2. Criando e manipulando dados com o pgAdmin III

#### 2.1 Criando o banco de dados
No pgAdmin III selecione o servidor através de um click duplo. O sistema pode te pedir a senha, nesse caso entre com a senha criada durante a instalação.

![](https://lh6.googleusercontent.com/NoV3ll5nlnDQsnNCQLmoozvf4sKvBY4VukCqKwam5Z_LEeGOuESU4apVlSzmNQCgxjDkzefxAbXOKoZ0r7xWa5EM_V6jJszWHVrLAWrGibYLL9tL57BbM7SpJrrh4N5K7WdxMq3j)


Selecione DATABASES em *object browser*, e em seguida selecione:
Menu Edit – New Object – New Databases

![](https://lh5.googleusercontent.com/e7zRtBtNNk36UPWTCZm0p7F9bwptH_OySQWFVdj9HaMpDYJa8Qungkj5St1dcLdu-BccoWNREvnnRC_3UB14lOC2y8LFS9O3ck-31QXbb_6lYSifcuK3VpruYp4DoJSnIR9etIoQ)


Na janela seguinte, nomeie o banco de dados como: banco01:

![](https://lh3.googleusercontent.com/V3VbGcPPgiefndMCLFRHhgZggPPwZ1sSb1maxdlc8z_ILWA5H09kTDbF1o58tF81wfVId-noohxeULNxUwhXANIP3k40zMYYjdG3WzSMSzOdjqvQT14i-7JXG7Ts75gR4l9FPvKr)


Com o banco de dados banco01 selecionado:
Menu Tools – Query Tool ou (Ctrl + E)
Após abrir o ambiente digite 

```sql
 create extension postgis;
```
e pressione (F5):

![](https://lh5.googleusercontent.com/sz7CIz_uY5ZcKi0XKi3JaqfSyA6E6JXXcYj0tXR4FRgKLFkc1BHiAJe3eX8YrY7C6MgwFhrhLWpN5ytNCQ_VGkwESGPXvCpTU8shVHUzVwYqrNjBzdhU-opuEsNlrLtZW8pIao7v)



#### 2.2 Criando uma tabela de pontos

Na Ferramenta de Consulta (Ctrl+E), digite o seguinte comando SQL e depois pressione F5:

```sql
CREATE TABLE pontos (
geom_pt      geometry(POINT,0),
nome           varchar
);
```

![](https://lh4.googleusercontent.com/5Jjr_bZEwAtAv8lItrQuIGHTbKsx6Th-IpnDGun23wZb2fZtzubOHsZrFzDDAz8uw25LHbN2EqB8zyukc8HTMdRTZp58vqD6BsT1Ieo4YFumDQ7dsbsnjZm-FrL3MtnaGGJiXlsZ)


Caso tenha algumas dúvidas sobre os comandos SQLs, um bom site é o mantido pela W3cSchools: [https://www.w3schools.com/sql/](https://www.w3schools.com/sql/)

#### 2.3 Inserindo alguns pontos hipotéticos
Considere três pontos no plano cartesiano, como os da figura abaixo:

![](https://lh4.googleusercontent.com/iVWucoX0_7w7lTCIE2ocM_dS6GEpNMhRamG3Iphpm-aY2l3HWdNu9oDHLSMX1LUcXEHe--Msz9AYs99rhxwVmAI8YeMXN9ACjqgrq3Oto46FycfWLjZ9CssAOJjxyVPZMPhkhiS3)


Na Ferramenta de Consulta (Ctrl+E), digite então os seguintes comandos SQL e depois pressione F5:
```sql
INSERT INTO pontos  VALUES ('POINT(0 0)', 'Origem');
INSERT INTO pontos  VALUES ('POINT(5 0)',  'Eixo X');
INSERT INTO pontos  VALUES ('POINT(0 5)',  'Eixo Y');
```

#### 2.4 Consultando os dados inseridos
Na Ferramenta de Consulta (Ctrl+E), digite então os seguintes comandos SQL e depois pressione F5:

```sql
SELECT nome, geom_pt
FROM pontos;
```

![](https://lh5.googleusercontent.com/8U0hheGqJkwLRxWptjoL41-ziy9WHbZzXAwVBIOTlHc7rx1GukXJ6GEnheGe5H00SvkBgrYZMtWRzkD3yKnwTw1kGsmynYl39kDYeDMwKnZHRMNOEJAg1Euxj0RXldiVe-3nSVmT)


O resultado da consulta anterior está no formato WKB (Well Known Binary). Para visualizar os dados em um formato textual, digite o seguinte comando:

```sql
SELECT nome, ST_AsText(geom_pt)
FROM pontos;
```

No comando anterior já foi utilizado uma função espacial, dado que ela tem como entrada um dado espacial. A função espacial ST_AsText() transforma uma geometria em uma expressão textual, chamada “Well-KnowText” – WKT. Nesse formato as seguintes geometrias simples são representados como se segue:


| Geometria | Well-KnowText                        |
| --------- | ------------------------------------ |
| Ponto     | POINT (1 1);                         |
| Linha     | LINESTRING (11, 2 2, 3 4);           |
| Poligono  | POLYGON ((0 0, 0 1, 1 1, 1 0, 0 0)); |


O resultado da consulta é mostrado na imagem a seguir:

![](https://lh4.googleusercontent.com/eWr7PEKgvqyUo_riuOdGT_LYjW2pTBZvYX2H76IGy4pB8bF3v7QTpwoauUFbGJYQmO33b-FDbc5phs85_dr0ZZVUnyX-dhtJFVa8_ZMzzq9ZdiQlKELZQw_wRMS9XxqVEzrR1eFd)


Em uma consulta, podemos usar as diversas operações espaciais suportadas pelo PostGIS, por exemplo a função para calcular a distância entre duas geometrias. A função ST_Distance() é usada para calcular a menor distância cartesiana  entre dois objetos espaciais. Considere então um quarto ponto (em vermelho) no plano cartesiano.

![](https://lh4.googleusercontent.com/MjtfpRsllKf1KUtNzSGqCTWrPJsMEZ1Q_FqqU7GRfc6xaR6LbL_2pdzh1sc_aucZXzaQTkgYRflPpYLai2y4JD1wKj2SQ7sROv8G4Fo5dmW-5IoT5zAophsLdmrsUPRmLo4KjpBo)


Podemos então calcular a distância de cada ponto da tabela para este quarto ponto usando o seguinte comando SQL:

```sql
SELECT nome, ST_AsText(geom_pt),
             ST_Distance(geom_pt, 'POINT(5 5)')
FROM pontos;
```

![](https://lh3.googleusercontent.com/eSv_oDOcqOlt4WDcIPZJ7Jda1td3yWbA6VePx6RADnViYLlc4pwJ-u30nwmAyC_u-3FhkU9VBfsRaMUnxxlkSPjr4n-tN4oE-VExrgLfCsVmml6jyS3SoY6uXAVKAEngJnSzbnp6)



#### 2.5 Exercícios

1. Criar duas tabelas, a primeira para armazenar lotes e a segunda para armazenar quadras. Ambas terão apenas 3 campos:
- codigo do tipo inteiro, 
- nome do tipo varchar(10) e  
- geom do tipo geometry(POLYGON, 0).
2.  Na tabela lotes insira quatro polígonos como na figura a seguir:

![](https://lh6.googleusercontent.com/0LUyzc-YSiGbY6sl4b2t0txb06RSv4nSryTHeExczrR98B3Aqn6TAYVjxbUjkhxxzJCGCXME5R96XUyNEP1onqO3ndzZCho9XIPVcLf-tAhV-d_Rg8MynNrijWKi-U5gmtkUSeWn)

3. Na tabela quadras, insiram dois polígonos como na figura abaixo:

![](https://lh6.googleusercontent.com/ijEFbuJsvtddgIa2EiYGf4g_4pP8kwAeCfM3YyiAgIhbQcVq5V6JlC6OK_8nQaHzg_vDarOpLmBxQTXRjV-F4r01yoAiAkY3SvxA8rjc76zcs9khfddZQrui5nzm1PNCxD_Q0Vae)

4. Escrever as consultas espaciais para responder individualmente cada questão:
* Selecione os registros da tabela lotes.
* Mostre os registros da tabela quadras.
* Visualize os nomes dos registros da tabela lotes.
* Quantos registros constam na tabela quadras;
* Selecione os registros da tabela lotes com nome igual a L1.
* Selecione os registros da tabela quadras com codigo igual a 1.
* Selecione a geometria de quadras com codigo = 2.
 
5. Usando as funções espaciais, escrevam códigos SQL para as seguintes questões:
* Qual a área dos lotes ?
* Qual o perímetro da quadra Q2?
* Qual a distância entre o lote L1 e a quadra Q2?
* Quais os lotes vizinhos ao lote L2 ?
* Quantos lotes estão dentro da quadra Q1?
* Quais os lotes estão dentro da quadra Q2?
* Quantos lotes estão dentro da quadra Q2?
* Quais os lotes vizinhos ao lote L3 ?


----------

### 3. Integração de banco de dados com sistemas de informação geográfica

#### 3.1 Acessando um banco de dados existente
Caso queira verificar as respostas da consulta SQL, podemos visualizar as tabelas como camadas vetoriais no sistema de informação geográfica aberto, QGIS. No menu camadas, selecione Adicionar Camada - PostGIS. Uma opção mais rápida é usando o atalho Ctrl+Shift+D.
.

![](https://lh6.googleusercontent.com/45qWdZYvkkKH8iiS4A2v6reoIELVIddYu0OJLOEXc-PF0wYBXkSIbyArphN8-_vG7P8CGEoNIcfoJqX3wnXKLf-7-r6pytezE6w3apB8NIe_R2ThguXnRp-LcYNPfKQxj995FfU-)


Na próxima janela, selecione novo, para criar uma nova conexão:

![](https://lh6.googleusercontent.com/Q7sgh9w_nW3m4JLbqtTGdWHrIiWoUmOe77w2AEs1rrxqAS8ntdQA-Uz8VRLUJ_txXsgjN3e3SEFrmVmTDW-Zulm6NK9EiooWYaa8lI0sDureEggsxq6LnPPwgda8NGzckYbHrmgM)


Ao clicar em Novo, deverá entrar com um nome para conexão, o nome da máquina (servidor), o nome do banco de dados que deseja conectar, nome do usuário e senha. Como o servidor de banco de dados está instalado na nossa máquina local, então o nome da máquina é localhost.

![](https://lh4.googleusercontent.com/h_phYE9rTN_gxuiExF6ymmBzRHnO139IlX6biPZO6wt5XPwLw4CD0qJZlAzlmNHLouI428Mp7OPCsFMdvPhVbNS9-D_FBaK-WX0k7XzdkL0-pGADhTU991LJM_pNEJTkE9kYm_u-)



Depois, basta clicar em conectar e selecionar e adicionar as tabelas lotes e quadras. Apois isso, será necessário selecionar “Sistema de coordenadas definida pelo usuário” dado que nosso dado não possui um sistema de coordenada. Então, poderemos visualizar nosso dado hipotético através do QGIS:

![](https://lh6.googleusercontent.com/xxsege9NxvO3n-5PLapZwGC3HQM4h58Dc-8Yw-jNiQ2mQktEZ_32xmamOc6P8gjoo2b2QyywuREgZh3aNmeyDLfSLLWXiDBVxxip6U0eaFBe9kYB6ddyPoLv3sfxThdpTSlaumAY)


#### 3.2 Criando novo banco de dados a partir de um arquivo SQL

Nessa sequência, veremos como carregar dados de um script SQL para um novo banco de dados. No aplicativo PGAdmin III, crie um banco de dados com nome banco02. Na Ferramenta de Consulta (Ctrl+E):

- Menu File – Open (Ctrl+O)
- Abrir arquivo [banco02.sql](https://profsergiocosta.github.io/pages/bdg/dados/banco02.sql)
- Executar o script que irá criar algumas tabelas e inserir os dados

Abra o QGIS, crie um novo projeto e selecione adicionar uma camada PostGIS, de modo similar ao passo anterior. Crie uma conexão para o banco02 recém criado:

![](https://lh5.googleusercontent.com/L3qHDe_s3YtGbbBkm6y41_GpUVQvTSbgKaVzmiJfG0UJM-Pjjr5RLKja6VwUCIK2OHihWiViisjHw_0huPc-MV5cyNE_GS0EIfPgfCrf6iPUSLIpakIeXZbWjFIiGffUeaqefB4Z)



Conecte e selecione todas as tabelas (camadas ou layers):

![](https://lh6.googleusercontent.com/6Kp6Dy9PsaV6-PZuTMaunBmDaIeZKMBUlbJ8BIC44Np7w-aG1Ch3IpJ2FNseS62Z0_YqJhWTfbtMIyag_JLEIr8tzQnuRxG2TdviFiIVS6cXxWR6jbUHgFyqeCGzAD6UxoascPLb)


Modifique a posição das camadas para que todas fiquem visíveis:

1. Viveiros
2. Pontes
3. Rios
4. Estradas_duplicadas
5. Estradas
6. Edificacoes (pontos)
7. Edificacoes
8. Localidades
9. Lagos
10. Florestas
11. Bordas_mapa

Como na figura abaixo:

![](https://lh6.googleusercontent.com/Mosr9Q5DfKZnC18vWiiILLrphavQpsCIbVmbVlSp_xTyEGQhbyNw8IoZsmJVyRaeV-e851iLOhCKsKimahD2qrh-urBhnw8fUB7KSSQK2F-hWVC_ooQoIq5SMUbG6FafM1OE3LZy)


#### 3.3 Exercícios

6) Usando o banco de dados banco02, escreva as seguintes consultas em SQL:

1. Qual a dimensão da geometria da tabela lagos?
2. Qual o tipo da geometria da BR 700?
3. Verificar se uma geometria esta vazia
4. Verificar se uma geometria é simples
5. Qual as bordas de uma geometria
6. Qual o Retângulo Envolvente (Envelopamento) de uma geometria
7. Qual a coordenada X de uma geometria ponto
8. Qual a coordenada Y de uma geometria ponto

#### 3.4 Importando dados geográficos

Nesta atividade iremos usar alguns dados geográficos usando o sistema de informação geográfica QGIS. 
Inicialmente, baixe os seguintes [dadosshp.zip](https://profsergiocosta.github.io/pages/bdg/dados/dadosshp.zip), e descompacte os arquivos em alguma pasta.

Então crie um novo banco de dados denominado Brasil no PG Admin III.
Após, como realizado anteriormente, crie uma conexão no QGIS

![](https://lh3.googleusercontent.com/Opr_Gvq6J-nXRD24gx6jxCiCl0r8y-0Ucv0SQOSIq2M_dL3FRR9D3Xb2AHblwzDsEE0XlmS8s2RpwClppO99MvsGEiYuffKwS3pic8HzyrRaAbHPIPw3WpmH6ABuDgNj0AczbXHG)


Verifique se está instalado o plugin DBManager no menu Complementos:

![](https://lh5.googleusercontent.com/JcFVCvM58h5We5lRJPatvTdIzaTwYMu-oZOdu_3oAiRJ015pQ6H5NSDrfb8E-0BG68Ko7UtVV4NUkqnHNz7s9R9jtOz7LRWLmLwePLpPzV7wYAzp7CHpRjsY2H-hT4kVxxTANADL)


Caso ele não esteja instalado, basta pesquisar e adicionar. Com o plugin instalado, acesse o menu Banco de Dados - Gerenciar banco de dados.

![](https://lh5.googleusercontent.com/ckAlGCBBTwBUS8DpMH93JQj6WMYpPi_OA7WheMgrNEKl6uwnkIUU7LQeWRyEh6cYIUYPN-cxZarTWI9HBHcU1Ojl899MuXTniwoKOPkqws6sbEkleuKTrtdYcqc2xfdch2SiI5LV)


Clique na conexão criada anteriormente.  Selecione o esquema public. Então no menu Base de Dados acesse SQL Window. Na janele entre com o código SQL:

```sql
create extension postgis;
```


![](https://lh5.googleusercontent.com/HZLZQzUDT3O8xcWlT_0vaqvZoib3mOZfWK4YXNjgSNwIylXXqjeX0hOVu8dnhenge4nAaHaIEBwKF_vWmAwb_nmoMf7kxJXUD7xYRP4N0QRaOS-r58yjYYRjExepm_qw2npXX8yj)


Então, basta clicar no icone Importar layer. Na janela que irá surgir, selecione o layer municipios_br e preenche os demais campos como abaixo.


![](https://lh6.googleusercontent.com/oXIqenIhkv5EHxjAyYTfix_TpbRcD4vlcTVvI6EdbydhTYfaWgJl_R6cal0qMPeQcCndgDIoaU0EQH9HncdGyU0KoUevrlriy33pTuPxPfJzGL85yeGjNy8Xc0bXuysju0vtlVpk)


Na janela que segue, escolha o sistema de referência 4326. 

![](https://lh6.googleusercontent.com/sT2qxj3nA3j6AMwk5Kv_j7FWldHF7XPBUwaEFS8pNHW9GsJkXN18yv4JeDZAEnqmAy-1ECv5hGlvfuIUc7PvKF1t9jFnpILK6GPzL-uMLhgfZZ3fMBBCi_5V2zSDAe8azqyp1ZLx)



 Após a importação, adicione o layer importado a tela como na figura abaixo:

![](https://lh3.googleusercontent.com/FPvyKpnwt0KMePMnsq1ChAfZAyCQBSM_HM0KVW7fyN0vZdQzkhJN6TOw8qQruQikhaT2wt01UpnVpa0Yg-W3_GZRPl8neC-FTlTQYd4tFxVEvlWdMBNi2rhSn51L-n0X6CKQDQNu)



Então, no QGIS será visto o layer de municipios como abaixo:

![](https://lh3.googleusercontent.com/PmQ8B7X6yxt0V8KoKS_VJ54S_DGIDzxdPLdpJ-p6MFA1_gEr-InKRfEaewEvENRXEWayuyiZtBtgEeuDzmCOif6G6RHQkvT0cItvxYB49Qqi_YkOJhAM-B4pLE050nW0hg7nJCq6)


Realize o mesmo processo com os seguintes dados: 
Observação: Caso prefira, pode utilizar o **Shp2pgSQL ou GUI Shape file loader:**

#### 3.5 Exercícios

**7. Utilizando o banco de dados brasil, faça as seguintes consultas espaciais:**

1. Quantas sedes de municípios estão dentro de um raio de 100km do aeroporto de São Luiz?
2. O nome dos municípios em que suas sedes estão a pelo menos 100KM de distância de algum aeroporto.
3. Criar uma nova tabela com todas as áreas indígenas que estão dentro dos limites do município de São Felix do Xingu.
4. Qual o tamanho em quilômetros da rede ferroviária do Estado do Maranhão?


#### 3.6 

Por fim, é sempre imporante criar indices para as colunas de geometria, para que o gerenciador de banco de dados seja mais eficiente durante as operações espaciais.

```sql
CREATE INDEX sedes_gix ON sedes USING GIST (geom);
CREATE INDEX estados_gix ON estados USING GIST (geom);
```




