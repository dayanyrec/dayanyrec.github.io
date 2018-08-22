---
layout: post
title:  "Jasmine + Karma: Ferramentas que vc usa e não se dá conta do motivo"
date:   2018-08-22 19:19:37 -0200
categories: ferramentas
---

No dia a dia tem umas coisas que entram no automático e a gente nem se dá conta do motivo de estar usando.

Hoje lendo sobre [testes e Angular](https://codecraft.tv/courses/angular/unit-testing/jasmine-and-karma/), na sessão sobre Unit Testing, caiu a ficha sobre o motivo de usar *Karma + Jasmine*.

Em resumo:  

*[Jasmine](https://jasmine.github.io/)* é um framework de testes.

Para [rodar sozinho](https://github.com/jasmine/jasmine#installation) (*standalone mode*), Jasmine precisa que seja criada uma página HTML incluindo os arquivos css e js obrigatórios para o funcionamento.  

Então o fluxo de trabalho comum era:  
1- fazer esse setup  
2- ir incluindo cada arquivo a ser testado e seu respectivo teste na página HTML criada  
3- abrir o browser para ver o resultado dos testes.  
4- *[Devia dar mt trabalho fazer isso!]*  

Aí é que entra *Karma*!

*[Karma](https://karma-runner.github.io/2.0/index.html)* é um rodador de testes.

Usando *Jasmine + Karma* o fluxo de trabalho é otimizado.  
Não é preciso fazer setup nem se preocupar em abrir uma página no browser. A interação é feita através do terminal e o trabalho de abrir browser, rodar os testes e exibir o resultado fica por conta do *Karma*.  

O foco nesse caso se volta ao mais importante: escrever testes que tragam rápido feedback.
