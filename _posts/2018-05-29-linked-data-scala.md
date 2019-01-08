---
title: "Linked data + Scala: primeiro contato"
tagline: 
tags : [scala,rdf,functional programming] 
published: true
---


Antes de mais nada, essa possível série de posts tem como principal objetivo registrar meus primeiros contatos com a linguagem Scala.

A linguagem Scala é multiparadigma, integrando principalmente os paradigmas: funcional e orientado a objetos. Alguns poderiam dizer que ela é uma "evolução" do Java. Eu não gosto de treta, então digo que ela é uma linguagem funcional que soube usar bem a integração com o universo Java. É uma linguagem fácil, principalmente para quem conhece Java e alguma linguagem funcional.

Então estes posts serão informais, incompletos e não muito bem escritos. Porém, espero que seja bem útil.

Para começar, vamos assumir que já tenham instalado o SBT (Simple Build Tool). O SBT tem algumas similaridades com o Maven, porem mais simples. Ainda estou aprendendo a usar esta ferramenta. Existem alguns projetos bases, que podemos usar para iniciar um novo projeto. Porém, aqui vamos criar um a partir do zero. Então, primeiro criamos uma pasta projeto1, uma subpasta project é um arquivo build.properties:

```
$ mkdir -p projeto1/project
$ cd projeto1
$ >project/build.properties
```

Entre com a seguinte linha no arquivo build.properties usando seu editor preferido.

```
sbt.version=1.1.4
```
No diretório base, crie o arquivo build.sbt:

```
$ >build.sbt
```

Então, com seu editor de texto entre com a seguinte configuração mínima:

```scala
name := "projeto1"
version := "0.1"
scalaVersion in ThisBuild := "2.11.5"
libraryDependencies ++= Seq(
    "org.w3" %% "banana-rdf" % "0.8.1",
    "org.w3" %% "banana-jena" % "0.8.1"
)
```
As linhas são auto explicativas. Em library dependencies estamos incluindo as bibliotecas banana-rdf e banana-jena. Essas bibliotecas serão usadas para criar e ler dados RDFs. A organização das pastas é muito similar a usada pelo Maven. Iremos então criar as pastas aonde serão armazenados nossos arquivos fontes.

```
$ mkdir -p src/main/scala
$ >src/main/scala/Main.scala
```

Então iremos fazer agora um programa simples, para testar o uso da biblioteca. Nesse programa criamos uma tripla simples.

```scala
import org.w3.banana._
import org.w3.banana.jena.Jena
import Jena._
import Jena.ops._
object Main extends App {
  val foaf = FOAFPrefix[Rdf]
  val timbl = URI(
       "https://www.w3.org/People/Berners-Lee/card#i") 
       -- foaf.name ->- "Tim Berners Lee"
  println (timbl.graph)
}
```

Então, agora se tudo der certo, a partir do diretório padrão, basta executar o seguinte comando:

```
$ sbt run
```
A saída esperada é:

```
{https://www.w3.org/People/Berners-Lee/card#i @http://xmlns.com/foaf/0.1/name "Tim Berners Lee"}
```

Então, agora já temos um ambiente inicial para aprendermos melhor sobre Scala e a biblioteca de dados conectados, banana-rdf.
