# Hardening de Switch Intelbras SG 2404D PoE Max

Esse repositório é o registro do nosso laboratório com um switch Intelbras SG 2404D PoE Max.

A ideia é acompanhar o projeto do jeito que ele está acontecendo: entender como o switch está hoje, testar alguns cenários com Kali Linux, aplicar as configurações de segurança que fizerem sentido e comparar o antes e o depois.

Não é um ambiente corporativo. É uma rede doméstica usada como laboratório de estudo, prática e portfólio.

## Cenário do lab

```text
Internet
   |
Roteador residencial
   |
Switch Intelbras SG 2404D PoE Max
   |--- PC Windows
   |--- Kali Linux
```

Equipamentos que estamos usando:

- switch Intelbras SG 2404D PoE Max;
- roteador residencial;
- computador Windows;
- Kali Linux, em uma máquina separada;
- cabos de rede.

O lab não tem firewall dedicado, Active Directory, Radius, TACACS, SIEM ou servidor de logs. Então a ideia é não forçar cenário corporativo onde ele não existe.

## O que já levantamos até agora

| Item | Valor |
|---|---|
| Modelo | SG 2404D PoE Max |
| Hardware | V1.0 |
| Firmware atual | 65.10.23.2 |
| Firmware mais recente encontrado | 65.10.23.7 |
| IP atual do switch | 192.168.100.3 |
| Backup inicial | feito |
| Data e hora | ajustadas manualmente |

## Como pretendemos conduzir

Nosso plano é seguir mais ou menos esta ordem:

1. Registrar o estado inicial do switch.
2. Conectar a Kali na mesma rede.
3. Fazer reconhecimento básico antes de qualquer hardening.
4. Rodar alguns testes controlados de camada 2.
5. Anotar o que realmente aconteceu no lab.
6. Atualizar firmware, se tudo estiver seguro para isso.
7. Aplicar hardening somente com recursos confirmados no equipamento.
8. Repetir os testes depois.
9. Comparar o antes e o depois.
10. Transformar o material em relatório e artigo.

## Testes que queremos documentar

Antes de mexer nas configurações, queremos observar o que a Kali consegue enxergar na rede:

- hosts ativos;
- IP do switch;
- portas abertas no switch;
- interface Web;
- tráfego básico no Wireshark.

Depois disso, pretendemos testar alguns cenários de Layer 2, sempre dentro do nosso próprio laboratório:

- ARP spoofing;
- MAC flooding, se conseguirmos fazer de forma controlada;
- DHCP starvation, provavelmente mais como estudo do que como teste pesado;
- STP manipulation, se fizer sentido no equipamento e na topologia;
- VLAN hopping somente se realmente montarmos VLAN/trunk no lab.

Não vamos usar brute force, malware, phishing, exploração de CVE ou teste em rede de terceiros. Esse projeto é para aprender e documentar defesa, não para derrubar ambiente.

## Regras que estamos seguindo

A regra principal é não assumir que o switch suporta alguma coisa só porque existe em material de Cisco ou em guia genérico de Layer 2.

Para cada recurso, vamos separar:

- o que confirmamos no SG 2404D PoE Max;
- o que ainda precisamos validar;
- o que não se aplica ao nosso laboratório.

Também não pretendemos subir arquivos sensíveis aqui. Backup real do switch, senha, configuração com credencial e captura com tráfego privado ficam fora do GitHub.

## Estrutura que vamos usar

Ainda vamos ajustar a estrutura conforme o projeto andar, mas a ideia inicial é esta:

```text
docs/
checklists/
evidencias/
relatorios/
assets/
```

## Status

- [x] Switch acessível pela interface Web
- [x] Firmware identificado
- [x] Versão de hardware identificada
- [x] Backup inicial feito
- [x] Data e hora ajustadas
- [ ] Firmware atualizado
- [ ] Kali conectada no lab
- [ ] Reconhecimento antes do hardening
- [ ] Hardening aplicado
- [ ] Testes depois do hardening
- [ ] Relatório final

## Observação

Esse repositório vai mudar bastante conforme formos testando. A intenção não é deixar tudo perfeito desde o primeiro commit, e sim registrar o processo real: dúvidas, decisões, testes, erros e ajustes.
