## Laboratórios

| Laboratório | Cenário | Status |
|---|---|---|
| [Lab 01 — Cliente sem Internet](labs/lab-01-cliente-sem-internet/) | Diagnóstico de indisponibilidade de Internet | ✅ Concluído |
| [Lab 02 — Gateway incorreto](labs/lab-02-gateway-incorreto/) | Diagnóstico de configuração de gateway | ✅ Concluído |
| Lab 03 — Máscara incorreta | Diagnóstico de endereçamento IPv4 | ⬜ |
| Lab 04 — Falha de roteamento | Diagnóstico de rotas e encaminhamento | ⬜ |
| Lab 05 — Problema de DNS | Diagnóstico de resolução de nomes | ⬜ |

## Lab 01 — Cliente sem Internet

O primeiro laboratório simula uma empresa cliente de um provedor de Internet que informa ao suporte estar sem acesso à Internet.

Durante a investigação foram utilizados testes de conectividade, análise de interfaces, análise de tabelas de roteamento, configuração de rotas estáticas e validação ponta a ponta.

### Principais pontos investigados

- Comunicação entre o PC e o gateway.
- Comunicação entre o Router Cliente e o Router ISP.
- Comunicação entre o Router ISP e o Router Internet.
- Existência de rotas para redes externas.
- Configuração do gateway do servidor.
- Existência de rotas de retorno para a rede do cliente.
- Validação final da comunicação entre o cliente e o servidor.

### Resultado

Após a identificação e correção das falhas de configuração, o PC1 conseguiu alcançar o servidor `8.8.8.8`.

[Ver o Lab 01 completo →](labs/lab-01-cliente-sem-internet/)

## Estrutura do projeto

```text
telecom-support-lab/
│
├── README.md
│
├── labs/
│   ├── lab-01-cliente-sem-internet/
│   │   ├── README.md
│   │   ├── comandos.txt
│   │   ├── laboratorio.pkt
│   │   ├── topologia.PNG
│   │   └── evidencias/
│   │       ├── README.md
│   │       ├── 01-pc-gateway.png
│   │       ├── 02-cliente-isp.png
│   │       ├── 03-isp-internet.png
│   │       ├── 04-show-ip-route.png
│   │       ├── 05-falha.png
│   │       └── 06-validacao-final.png
│   │
│   └── lab-02-gateway-incorreto/
        ├── README.md
        ├── laboratorio.pkt
        ├── topologia.PNG
        └── evidencias/
            ├── README.md
            ├── 05-falha-gateway.png
            └── 06-validacao-final.png
│   │  
│   │ 
│   ├── lab-03/
│   └── ...
│
└── docs/
    ├── metodologia-troubleshooting.md
    └── enderecamento-ip.md ```text
```

# Competências Desenvolvidas

## Redes

- IPv4
- Endereçamento IP
- Máscaras de rede
- Gateway
- LAN e WAN
- Roteamento
- Rotas estáticas
- Rota padrão
- Rota de retorno
- ICMP

## Troubleshooting

- Isolamento de falhas
- Análise de evidências
- Testes de conectividade
- Formulação de hipóteses
- Diagnóstico técnico
- Correção controlada
- Validação pós-correção
- Análise do caminho de ida e retorno

## Cisco IOS

- `show ip interface brief`
- `show ip route`
- `ping`
- `configure terminal`
- `interface`
- `ip address`
- `ip route`
- `no shutdown`

# Metodologia de Troubleshooting

Os laboratórios deste projeto seguem uma abordagem sistemática de investigação de problemas de rede.

## Processo

1. Identificar o problema.
2. Coletar evidências.
3. Testar a conectividade.
4. Isolar o ponto de falha.
5. Formular uma hipótese.
6. Alterar uma variável por vez.
7. Validar a correção.
8. Documentar o resultado.

## Fluxo de troubleshooting

**Problema → Evidência → Hipótese → Teste → Diagnóstico → Correção → Validação**

## Princípios utilizados

### Trabalhar com evidências

As decisões são baseadas nos resultados dos testes realizados, evitando conclusões sem evidência técnica.

### Isolar o problema

O caminho da comunicação é dividido em segmentos para identificar em qual ponto ocorre a falha.

### Alterar uma variável por vez

Durante a correção, evita-se realizar várias mudanças simultaneamente. Isso facilita identificar qual alteração resolveu o problema ou provocou um novo comportamento.

### Validar após a correção

Uma configuração não é considerada concluída apenas porque foi aplicada. É necessário realizar novos testes e confirmar o funcionamento esperado.

### Registrar o diagnóstico

O problema, os testes realizados, a hipótese, a correção e o resultado final devem ser documentados.

# Documentação dos Laboratórios

Cada laboratório do projeto pode ser documentado seguindo uma estrutura padronizada.

## Estrutura

### 1. Cenário do incidente

Descrição do problema apresentado.

Exemplo:

> Cliente informa que está sem acesso à Internet.

### 2. Objetivo

Descrever o que precisa ser investigado e validado.

### 3. Topologia

Apresentar os equipamentos, conexões e estrutura da rede.

### 4. Endereçamento IP

Registrar os endereços IP, máscaras, gateways e interfaces utilizadas.

### 5. Testes realizados

Registrar os comandos utilizados e seus respectivos resultados.

Exemplo:

```text
ping 192.168.10.1

Resultado:

!!!!!
Success rate is 100 percent (5/5)
```

### 6. Evidências

Registrar capturas de tela relevantes da investigação.

### 7. Hipóteses investigadas

Documentar as possíveis causas consideradas durante o diagnóstico.

### 8. Diagnóstico

Identificar a causa ou conjunto de causas encontradas.

### 9. Correções aplicadas

Registrar as alterações realizadas para solucionar o problema.

### 10. Validação final

Realizar os testes finais para confirmar que o problema foi resolvido.

### 11. Resultado

Registrar o estado final do laboratório.

### 12. Lições aprendidas

Registrar os principais conceitos e conhecimentos obtidos durante o laboratório.

# Progresso do Projeto

## Fundamentos de Redes

| Área | Status |
|---|---|
| IPv4 | ✅ |
| Gateway e conectividade | ✅ |
| Ping / ICMP | ✅ |
| Tabela de roteamento | ✅ |
| Rota padrão | ✅ |
| Rotas estáticas | ✅ |
| Troubleshooting básico | ✅ |
| VLAN | ⬜ |
| DHCP | ⬜ |
| DNS | ⬜ |
| NAT | ⬜ |
| ACL | ⬜ |
| OSPF | ⬜ |

## Suporte e Infraestrutura

| Área | Status |
|---|---|
| Diagnóstico de conectividade | ✅ |
| Identificação de falhas | ✅ |
| Análise de evidências | ✅ |
| Documentação técnica | ✅ |
| Simulação de atendimento N1 | ⬜ |
| Cenários de NOC | ⬜ |
| Cenários de ISP | ⬜ |
| Monitoramento | ⬜ |

## Laboratórios

| Laboratório | Status |
|---|---|
| Lab 01 — Cliente sem Internet | ✅ |
| Lab 02 — Gateway incorreto | ✅ |
| Lab 03 — Máscara incorreta | ⬜ |
| Lab 04 — Falha de roteamento | ⬜ |
| Lab 05 — Problema de DNS | ⬜ |


# Autora

## Alinne Fernanda Costa

Estudante de Ciência da Computação e Técnica em Informática em formação.

Este projeto faz parte da minha formação prática e tem como objetivo desenvolver conhecimentos aplicados em:

- Suporte Técnico
- Redes de Computadores
- Telecomunicações
- Infraestrutura
- Troubleshooting
- NOC
- Provedores de Internet

## Objetivo profissional

Desenvolver experiência prática e construir uma base técnica para atuação nas áreas de Suporte Técnico, Redes, Telecomunicações, NOC e Infraestrutura.

## GitHub

[@Alinnefcc](https://github.com/Alinnefcc)
