# Lab 01 — Cliente sem Internet

## Cenário

Uma empresa cliente de um provedor de Internet entrou em contato informando que estava sem acesso à Internet.

### Cliente

- Empresa: Empresa Alfa
- Serviço: Internet
- Velocidade contratada: 500 Mbps
- Prioridade: Alta
- Status inicial: Em aberto

## Objetivo

Investigar a indisponibilidade de Internet utilizando uma abordagem de troubleshooting por etapas, identificando os pontos de falha, realizando as correções necessárias e validando a conectividade ponta a ponta.

## Topologia

A topologia deste laboratório utiliza:

- 1 PC
- 1 Switch Cisco 2960
- 3 Routers Cisco ISR 4331
- 1 Server

## Endereçamento IP

| Equipamento | Interface | Endereço IP | Máscara | Função |
|---|---|---|---|---|
| PC1 | NIC | 192.168.10.10 | 255.255.255.0 | Cliente |
| Router Cliente | G0/0/0 | 192.168.10.1 | 255.255.255.0 | Gateway LAN |
| Router Cliente | G0/0/1 | 203.0.113.2 | 255.255.255.252 | WAN |
| Router ISP | G0/0/0 | 203.0.113.1 | 255.255.255.252 | WAN |
| Router ISP | G0/0/1 | 198.51.100.1 | 255.255.255.252 | Upstream |
| Router Internet | G0/0/0 | 198.51.100.2 | 255.255.255.252 | Upstream |
| Router Internet | G0/0/1 | 8.8.8.1 | 255.255.255.0 | Rede externa |
| Server | NIC | 8.8.8.8 | 255.255.255.0 | Destino |

## Investigação

### Teste 1 — PC1 → Gateway

Comando:

`ping 192.168.10.1`

Resultado:

100% de sucesso.

Conclusão:

A comunicação entre o PC1 e o gateway local estava funcionando.

### Teste 2 — Router Cliente → Router ISP

Comando:

`ping 203.0.113.1`

Resultado:

100% de sucesso.

Conclusão:

O enlace WAN entre o Router Cliente e o Router ISP estava funcionando.

### Teste 3 — Router ISP → Router Internet

Comando:

`ping 198.51.100.2`

Resultado:

100% de sucesso.

Conclusão:

O enlace entre o Router ISP e o Router Internet estava funcionando.

## Falhas identificadas

### Falha 1 — Ausência de rota padrão no Router Cliente

Foi identificado:

`Gateway of last resort is not set`

Foi configurada a rota padrão:

`ip route 0.0.0.0 0.0.0.0 203.0.113.1`

### Falha 2 — Gateway incorreto no Server

O gateway do Server estava incorreto.

Foi corrigido para:

`8.8.8.1`

### Falha 3 — Ausência de rota para a rede do cliente no Router ISP

Foi configurada:

`ip route 192.168.10.0 255.255.255.0 203.0.113.2`

### Falha 4 — Ausência de rota de retorno no Router Internet

Foi configurada:

`ip route 192.168.10.0 255.255.255.0 198.51.100.1`

## Validação final

No PC1:

`ping 8.8.8.8`

Resultado:

Reply.

A conectividade ponta a ponta foi restabelecida.

## Diagnóstico final

O problema envolvia falhas de configuração de roteamento e gateway.

Durante a investigação foram identificados:

- ausência de rota padrão no Router Cliente;
- gateway incorreto no Server;
- ausência de rota para a LAN do cliente no Router ISP;
- ausência de rota de retorno no Router Internet.

## Competências praticadas

- IPv4
- Endereçamento IP
- Gateway
- ICMP
- Ping
- Cisco IOS
- Tabela de roteamento
- Rota estática
- Rota padrão
- Rota de retorno
- Troubleshooting
- Validação ponta a ponta
