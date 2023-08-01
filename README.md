# Redes - dos conceitos iniciais à criação de uma intranet  

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

### Conectando computadores

Essa é uma rede criada utilizando o software *Cisco Packet Tracer*. Ela consiste em 3 computadores ligados a um HUB.
![Captura de tela 2023-07-31 151415](https://github.com/trcosta97/redes-estudos/assets/101136329/aa9fb525-a24d-4c5b-98fc-604f8881a144)
Eles foram configurados com o IP 192.168.3.1, 192.168.3.2 e 192.168.3.3 respectivamente. As setas verdes indicam que a conexão foi bem sucedida.  
Utilizando o comando *ping*, foi comprovado que a conexão entre o computador Manufatura e o computador Embalagem estão realmente conectados.
O aplicativo tem um painel que monitora todos os protocolos utilizados durante o teste:
![image](https://github.com/trcosta97/redes-estudos/assets/101136329/ef85bd04-db39-46c2-bd76-a659d25044be)
O protocolo *ICMP* é o que faz o comando *ping* funcionar. Ele é usado para trocar informações de controle e mensagens de erro entre dispositivos em uma rede IP (Internet Protocol). 
O protocolo *ARP* permite que identificar o endereço físico de uma máquina a partir de seu protocolo de IP.  

Mesmo com o *ping* sendo direcionado para o computador da Embalagem, o computado do Acabamento também recebeu os pacotes, tanto na ida quando na volta. Isso ocorreu por que o HUB funciona assim. Ele manda os pacotes pra todos os dispositivos conectados. Ele funciona como um *broadcast*, o que causa congestionamento da rede, além de poder divulgar mensagens de caráter privado. Por isso o HUB só é utilziado em redes menores e menos exigentes em questão de requisitos.

#### DNS e Nslookup

O protocolo DNS funciona como uma agenda de telefone num celular. Ele associa o nome do domínio com o endereço de IP do site na rede. A partir do Nslookup, é possível pesquisar pelo prompt de comando nessa "agenda de contatos".

```console
$ nslookup www.google.com
Servidor:  UnKnown
Address:  192.168.1.1

Não é resposta autoritativa:
Nome:    www.google.com
Addresses:  2800:3f0:4001:823::2004
          142.250.219.132
```

#### Cabos de conexão







