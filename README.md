# Cenário de Segurança de Rede — Cisco Packet Tracer

Projeto de laboratório de segurança de redes, implementado em **Cisco Packet Tracer**, numa topologia *hub-and-spoke* com firewall ASA, SSL Clientless VPN e VPN IPsec site-to-site.

![Topologia da rede](topologia.png)

## Visão geral

A rede liga duas LANs (Lisboa e Porto) a um Datacenter central e à Internet, implementando:

- **Firewall Cisco ASA 5506-X** a separar a rede interna do exterior (interfaces inside/outside, níveis de segurança, ACLs e inspeção de tráfego)
- **SSL Clientless VPN** na ASA, com **3 grupos de utilizadores** — cada grupo acede apenas ao seu servidor web (Site), através de um portal HTTPS autenticado
- **2 túneis IPsec site-to-site** (Lisboa ↔ Datacenter e Porto ↔ Datacenter), com o **Router5 como hub**
- **Encaminhamento estático** e acesso das LANs à Internet
- **Hardening de gestão** (SSH com chave RSA, palavras-passe, banner) em todos os equipamentos

## Tecnologias

- Cisco IOS (routers 2811 e 1941)
- Cisco ASA 9.6 (5506-X)
- IPsec / IKE (ISAKMP) — AES-256, SHA, Diffie-Hellman grupo 2, chave pré-partilhada
- SSL Clientless VPN (WebVPN)
- SSH, ACLs, inspeção stateful

## Endereçamento (resumo)

| Sub-rede | Endereço |
|---|---|
| Datacenter | 192.168.73.0/27 |
| LAN Lisboa | 192.168.73.32/27 |
| LAN Porto | 192.168.73.64/27 |
| Trânsito VPN Lisboa | 192.168.73.200/30 |
| Trânsito VPN Porto | 192.168.73.204/30 |
| Rede de Acesso (ASA–ISP) | 200.200.200.200/30 |
| Rede Externa | 204.204.204.0/24 |

## Conteúdo do repositório

- `rede.pkt` — ficheiro do Cisco Packet Tracer
- `Relatorio_PacketTracer.docx` — relatório com a configuração **passo a passo** (todos os comandos)
- `topologia.png` — diagrama da topologia

## Como abrir

Abrir `rede.pkt` no **Cisco Packet Tracer 8.x** (ou superior). O relatório descreve, fase a fase, todos os comandos necessários para reproduzir o cenário de raiz.

## Nota

As palavras-passe presentes são de **laboratório/simulação** e não devem ser reutilizadas em ambientes reais.

---

*Trabalho académico — Curso de Cibersegurança.*
