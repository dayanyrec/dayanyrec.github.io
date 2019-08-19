---
layout: post
title:  "Kubernetes e a feature de cuidar da vida do Pod: pode ser uma armadilha"
date:   2019-08-19 12:00:37 -0200
categories: Kubernetes liveness delay
---

Uma das features de Kubernetes que aparece nos artigos como uma coisa muito boa é que ela cuida de manter a aplicação viva.  

A ideia é que as pessoas que antes cuidavam de reinstalar a aplicação numa outra máquina quando ela quebrava, agora podem ficar tranquilas porque Kubernetes vai levantar um novo nó ao ver que a aplicação não tá bem.

E como Kubernetes sabe que a aplicação não tá bem? Usando `liveness probe`.

Existem algumas maneiras mas vou falar da verificação por HTTP.

Exemplo real:
Uma aplicação Spring com Actuator ativado tem no endpoint `/actuator/health` o seu status.
Daí, no objeto Kubernetes `Deployment` é possível dizer que pra saber quando a app tá bem/viva, uma chamada HTTP pra esse endpoint deve retornar 200.

Em código:
```
        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 8080
```

Nesse momento, eu já tinha sofrido com 15 restarts da app e o deploy tava corria aleatoriamente mal.  
O problema é que a inicialização da app demora e uma das últimas coisas que acontece é a disponibilização dos endpoints. 
Kubernetes perguntava pra aplicação se ela tava bem, ganhava um 404 como resposta e restartava o Pod. Um belo loop de falhas!

Para resolver, é preciso pedir pra que Kubernetes espere um pouco antes de checar o endpoint.

Em código:
```
        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 8080
          initialDelaySeconds: 90
          periodSeconds: 30
```

Enfim, *zero* restarts aleatórios. Deploy feliz! :)
