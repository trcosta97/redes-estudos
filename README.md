# Redes
## dos conceitos iniciais à criação de uma intranet


### Camadas, protocolos, ping e traceroute   
Uma rede é um emaranhado de dispositivos que se comunica entre si. A internet é uma rede global.Uma rede precisa de um padrão de comunicação para que os dispositivos de uma rede se entendam e esse padrão são os protocolos.  

#### Camadas
Uma rede é dividida em 4 camadas. Essas camadas são:  

##### Aplicação
É o dispositivo inicial, como um celular onde uma mensagem é digitada.

##### Transporte
É a camada onde a mensagem é empacotada assim que o botão de enviar é pressionado no celular para que possa ser enviada pela rede.A principal função da camada de transporte é prover comunicação segura e eficiente entre processos de aplicação em dispositivos computacionais

#####  Rede
Aqui já é fora do nosso dispositivo (celular no nosso exemplo). Essa camada fica no roteador e é responsável por conectar dispositivos diferentes.  
O principal protocolo utilizado aqui é o de endereçamento IP. Ele acrescenta um cabeçalho com o endereço de destino e origem do pacote e calcula a rota de tráfego, ou seja, os dispositivos que o pacote passará para chegar no seu destino.

##### Física
Consiste na transmissão dos bits dessa mensagem pelos dispositivos no caminho. Ao final, a mensagem passa pelo processo inverso das camadas, sendo desempacotada e chegando no dispositivo destino pronta para o usuário.

#### Ping e Traceroute
Ping é um comando que testa com um pacote de 32 bytes se ele alcança seu destino e com qual velocidade. Ele também prove a latência, ou seja, o tempo que demorou para que o pacote atingisse o destino.
```console
    $ ping www.google.com

    Disparando www.google.com [142.250.219.132] com 32 bytes de dados:
    Resposta de 142.250.219.132: bytes=32 tempo=3ms TTL=119
    Resposta de 142.250.219.132: bytes=32 tempo=3ms TTL=119
    Resposta de 142.250.219.132: bytes=32 tempo=3ms TTL=119
    Resposta de 142.250.219.132: bytes=32 tempo=3ms TTL=119

    Estatísticas do Ping para 142.250.219.132:
        Pacotes: Enviados = 4, Recebidos = 4, Perdidos = 0 (0% de
                perda),
    Aproximar um número redondo de vezes em milissegundos:
        Mínimo = 3ms, Máximo = 3ms, Média = 3ms

```  
Traceroute é a rota de tráfego de um pacote. Com o comando *tracert*, podemos checar o número de saltos (roteadores pelos quais o pacote passou) e os dispositivos percorridos. 

```console
    $ tracert www.google.com

    Rastreando a rota para www.google.com [142.250.219.132]
    com no máximo 30 saltos:

    1    <1 ms    <1 ms    <1 ms  192.168.1.1
    2    12 ms     3 ms     3 ms  100.64.0.1
    3     2 ms     2 ms     1 ms  10.1.90.1
    4     6 ms     3 ms     3 ms  10.1.74.1
    5     3 ms     3 ms     3 ms  179.96.88.241
    6     3 ms     3 ms     8 ms  209.85.168.138
    7     3 ms     2 ms     3 ms  74.125.243.1
    8     3 ms     2 ms     3 ms  209.85.254.181
    9     3 ms     3 ms     3 ms  gru14s29-in-f4.1e100.net [142.250.219.132]

    Rastreamento concluído.

```



