---
title: "Tutorial sobre banco de dados geográficos"
tagline: 
date: 2018-11-06
permalink: /posts/2018/11/tutorial-bd/
tags : [gis, qgis, postgres, postgis, banco de dados] 
published: true
---

Esse tutorial foi baseado nas aulas do professor Eduilson Livio Neves da Costa Carneiro - IFPI

Nele iremos falar brevemente sobre o processo de instalação,criação e manipulação de dados com o pgAdmin III e Integração de banco de dados com sistemas de informação geográfica

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

