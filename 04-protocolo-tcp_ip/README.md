# Redes de Computadores — TCP/IP, Protocolos e Ambiente Prático

> Material técnico estruturado para estudo, revisão e prática de Redes de Computadores, TCP/IP, análise de tráfego e construção de laboratório com máquinas virtuais.
>
> **Observação:** este material preserva o conteúdo fornecido e inclui as correções técnicas indicadas na seção final.

---

## 1. Origem da Internet e da ARPANET

Em **1969**, a **ARPA (Advanced Research Projects Agency)** financiou a criação da **ARPANET**, uma rede experimental baseada em **comutação de pacotes**.

O objetivo era estudar técnicas capazes de proporcionar comunicação de dados:

- confiável;
- robusta;
- independente de fabricante;
- distribuída entre diferentes sistemas.

O projeto teve grande sucesso e passou a ser utilizado para comunicações reais por organizações conectadas à rede.

Em **1975**, a ARPANET deixou de ser experimental e passou a operar como uma rede administrada pela **DCA (Defense Communications Agency)**.

### Adoção do TCP/IP

Em **1983**, o **TCP/IP** foi adotado como padrão militar. Os hosts conectados à rede passaram a ser obrigados a utilizar essa suíte de protocolos.

Para facilitar a migração, a **DARPA** contratou a **BBN Technologies (Bolt, Beranek and Newman)** para implementar TCP/IP no **Berkeley Unix (BSD)**.

Essa implementação foi extremamente importante porque estabeleceu uma forte associação entre:

> **Unix + TCP/IP**

Nesse período, o termo **Internet** começou a ser utilizado para designar a rede baseada nessa arquitetura.

---

# 2. Modelo TCP/IP

A suíte TCP/IP utiliza uma arquitetura de **quatro camadas**, derivada do modelo do **Departamento de Defesa dos Estados Unidos (DoD)**.

Ela não deve ser confundida com o modelo **OSI**, que possui sete camadas.

## Comparação

| Modelo OSI | TCP/IP | Função principal |
|---|---|---|
| 7 — Aplicação | Aplicação | Serviços de rede para aplicações |
| 6 — Apresentação | Aplicação | Representação dos dados |
| 5 — Sessão | Aplicação | Gerenciamento de sessões |
| 4 — Transporte | Transporte | Comunicação processo-a-processo |
| 3 — Rede | Internet | Endereçamento e roteamento |
| 2 — Enlace | Acesso à rede | Comunicação na rede local |
| 1 — Física | Acesso à rede | Transmissão física |

Portanto:

- **OSI 7 + 6 + 5 → TCP/IP Aplicação**
- **OSI 4 → TCP/IP Transporte**
- **OSI 3 → TCP/IP Internet**
- **OSI 2 + 1 → TCP/IP Acesso à Rede**

---

