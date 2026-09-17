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

Investigar a indisponibilidade de Internet utilizando uma abordagem de troubleshooting por etapas, identificar os pontos de falha, realizar as correções necessárias e validar a conectividade ponta a ponta.

## Topologia

![Topologia da rede](topologia.png)

## Equipamentos

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

Resultado: 100% de sucesso.

Conclusão: a comunicação entre o PC1 e o gateway local estava funcionando.

### Teste 2 — Router Cliente → Router ISP

Comando:

`ping 203.0.113.1`

Resultado: 100% de sucesso.

Conclusão: o enlace WAN entre o Router Cliente e o Router ISP estava funcionando.

### Teste 3 — Router ISP → Router Internet

Comando:

`ping 198.51.100.2`

Resultado: 100% de sucesso.

Conclusão: o enlace entre o Router ISP e o Router Internet estava funcionando.

## Falhas identificadas

### 1. Ausência de rota padrão no Router Cliente

Foi identificado:

`Gateway of last resort is not set`

Correção:

`ip route 0.0.0.0 0.0.0.0 203.0.113.1`

### 2. Gateway incorreto no Server

O gateway do Server estava incorreto.

Foi corrigido para:

`8.8.8.1`

### 3. Ausência de rota para a rede do cliente no Router ISP

Correção:

`ip route 192.168.10.0 255.255.255.0 203.0.113.2`

### 4. Ausência de rota de retorno no Router Internet

Correção:

`ip route 192.168.10.0 255.255.255.0 198.51.100.1`

## Evidências

As capturas utilizadas durante a investigação estão disponíveis em:

[evidencias/](evidencias/)

### Principais evidências

[01 — PC1 → Gateway](evidencias/01-pc-gateway.png)

[02 — Router Cliente → Router ISP](evidencias/02-cliente-isp.png)

[03 — Router ISP → Router Internet](evidencias/03-isp-internet.png)

[04 — Tabela de roteamento](evidencias/04-show-ip-route.png)

[05 — Falha de conectividade](evidencias/05-falha.png)

[06 — Validação final](evidencias/06-validacao-final.png)

## Validação final

No PC1:

`ping 8.8.8.8`

Resultado: Reply.

A conectividade ponta a ponta foi restabelecida.

## Diagnóstico final

O problema envolvia múltiplas falhas de configuração de roteamento e gateway.

Foram identificados:

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

## Arquivo do laboratório

[Baixar laboratório Cisco Packet Tracer](laboratorio.pkt)
