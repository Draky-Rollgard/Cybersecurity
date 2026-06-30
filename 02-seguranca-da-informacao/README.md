# Information Security

A segurança da informação não se resume apenas aos equipamentos e tecnologias como firewalls, IP’s e proxies; mas sim, em como a proteção da informação contra ameaças é direcionada. Ademais, com o objetivo de garantir a continuidade de um negócio, ou ainda ser entendida como a preservação da confidencialidade, integridade e disponibilidade da informação. Essa tríade retrata, por sua vez, os pilares básicos da segurança da informação, referenciadas como CID.



- **Certificado Digital**: identidade digital da pessoa física ou jurídica no meio eletrônico, garantindo a autenticidade, confidencialidade, integridade e não repúdio das operações, assegurando a validade jurídica e permitindo que serviços sejam realizados sem a necessidade de presença física.

---

## ROSI (Return on Security Investment)

Como uma resposta às questões financeiras essenciais sobre os tópicos abaixo, o Retorno Sobre Investimento em Segurança da Informação se mostra essencial para a minimização de riscos aos quais os ativos da organização possam vir a ser expostos, calculando-se quanto de perda poderá ser evitada para o negócio.

- Os impactos financeiros com a falta de segurança sobre a produtividade;
- Pagamento ou gasto ideal por segurança;
- Benefícios que as práticas ou dispositivos de segurança trazem;
- Momento em que os investimentos são ou deixam de ser suficientes.

---

## Princípios da Segurança da Informação

O sistema de Administração dos recursos de Tecnologia da Informação - SISP, do poder executivo Federal, dentre outras reconhecidas instituições, coloca como estratégias:



### Privilégios Mínimos

Usuários devem ter privilégios para uso de recursos informáticos limitados ao mínimo necessário para o pleno desempenho de suas funções.



### Defesa em Profundidade

Implementação de um sistema defensivo na forma de camadas, onde ambos mecanismos de proteção se complementam.
Um exemplo, da camada mais externa para a mais interna, seria:

1. Programa de segurança
2. Segurança física e ambiental
3. Segurança das redes, FW, IDS, NIDS e VPN
4. Hardering OS, autenticação, antivírus, criptografia
5. Segurança das aplicações

### Elo Mais Fraco

Encadeamento de estratégias de forma a dificultar o acesso e a sobreposição aos pontos mais vulneráveis dos sistemas de proteção com soluções simples, como: implementação de VPN, credenciais fortes e bloqueio com limite de tentativa, de modo que o atacante recorra às técnicas de engenharia social ao invés de ataques diretos.

### Ponto de Verificação

Quando toda e qualquer topologia apresenta um conjunto de equipamentos passantes por um único ponto de troca de tráfego entre rede "confiável" e "não confiável" e todo esse tráfego pode ser inspecionado e submetido às políticas de segurança configuradas, de forma a minimizar o comprometimento aos pilares da segurança da informação.

### Segurança por Obscuridade

É um sistema ou prática de segurança muito frágil, porque consiste simplesmente na dependência do segredo do projeto ou implementação como garantias.

Um exemplo para esse princípio é: a segurança de um aplicativo recair sobre o segredo do seu código-fonte. Porém, como é muito fraca essa prática, manter apenas o código em segredo não é suficiente, agregá-la às demais permitirá que a segurança não recaia sobre o mesmo.

### Princípio da Simplicidade

Referenciado como o princípio do beijo (KISS), ele aborda práticas de engenharia de software que privilegiam abordagens simples e inteligentes.

Quanto maior a complexidade de um código, maior tende a ser a dificuldade de auditoria, manutenção e identificação de falhas, aumentando a probabilidade de vulnerabilidades. Administradores são movidos por resultados, muitas vezes em tempo ágil, acarretando em inserções e testes frenéticos de novas regras sem o devido critério.

### Segregação de Funções

Controle clássico para a resolução de conflitos de interesse e prevenção de fraudes mediante a restrição dos poderes de cada indivíduo e à criação de barreiras, fazendo com que mais de um indivíduo seja necessário para concluir uma tarefa.

---

# Resumo e Complementos

### Resumo

A Segurança da Informação tem como principal objetivo proteger os ativos de informação de uma organização, garantindo os três pilares fundamentais da segurança (CID):

- **Confidencialidade:** somente pessoas autorizadas podem acessar as informações.
- **Integridade:** as informações devem permanecer corretas e sem alterações indevidas.
- **Disponibilidade:** os dados e serviços devem estar acessíveis quando necessários.

Além desses pilares, conceitos como **Certificado Digital**, **ROSI (Return on Security Investment)** e os princípios de **Privilégios Mínimos**, **Defesa em Profundidade**, **Segregação de Funções** e **Segurança por Obscuridade** auxiliam na construção de ambientes mais seguros e resilientes.



### Diferença entre Segurança da Informação e Cibersegurança

Embora os termos sejam frequentemente utilizados como sinônimos, eles possuem escopos diferentes.

| Segurança da Informação | Cibersegurança |
|--------------------------|----------------|
| Protege qualquer tipo de informação, seja física ou digital. | Protege sistemas, redes, dispositivos e serviços conectados. |
| Abrange documentos, contratos, arquivos físicos e digitais. | Foca na prevenção, detecção e resposta a ataques cibernéticos. |
| Baseia-se principalmente nos pilares CID. | Engloba tecnologias, processos e pessoas para combater ameaças digitais. |

Em resumo, **a Cibersegurança faz parte da Segurança da Informação**, sendo especializada na proteção do ambiente digital.

---

### Tecnologias modernas de Segurança

O material apresenta mecanismos tradicionais, como **Firewall**, **IDS**, **NIDS** e **VPN**, que continuam sendo amplamente utilizados. Entretanto, atualmente outras soluções ganharam destaque:

| Tecnologia | Finalidade |
|------------|------------|
| **EDR (Endpoint Detection and Response)** | Detecta, investiga e responde a ameaças em computadores e servidores. |
| **XDR (Extended Detection and Response)** | Correlaciona eventos de diversos sistemas (endpoints, rede, e-mail e nuvem) para detectar ataques mais complexos. |
| **SIEM (Security Information and Event Management)** | Centraliza logs de segurança e realiza monitoramento e correlação de eventos em tempo real. |
| **SOAR (Security Orchestration, Automation and Response)** | Automatiza respostas a incidentes e integra diversas ferramentas de segurança. |
| **Zero Trust** | Modelo de segurança baseado no princípio "Nunca confie, sempre verifique", exigindo autenticação contínua. |
| **MFA (Multi-Factor Authentication)** | Exige dois ou mais fatores de autenticação para validar a identidade do usuário. |
| **CASB (Cloud Access Security Broker)** | Controla e protege o acesso de usuários aos serviços em nuvem. |
| **SASE (Secure Access Service Edge)** | Integra funções de rede e segurança em uma arquitetura baseada em nuvem. |

Essas tecnologias representam a evolução das soluções tradicionais e são amplamente utilizadas em ambientes corporativos.

---

### Exemplos práticos

#### Privilégios Mínimos

Um funcionário do setor de Recursos Humanos deve possuir acesso apenas aos sistemas relacionados ao seu trabalho, não sendo autorizado, por exemplo, a acessar o banco de dados financeiro da organização.



#### Defesa em Profundidade

Em vez de depender apenas de um firewall, uma organização pode utilizar diversas camadas de proteção:

- Firewall
- VPN
- MFA
- Antivírus
- EDR
- Backup
- Criptografia
- Monitoramento por SIEM

Caso uma camada seja comprometida, as demais continuam protegendo o ambiente.

---

### Principais normas e frameworks

A Segurança da Informação é fortemente baseada em normas e boas práticas internacionais.

| Norma / Framework | Objetivo |
|-------------------|----------|
| **ISO/IEC 27001** | Sistema de Gestão da Segurança da Informação (SGSI). |
| **ISO/IEC 27002** | Boas práticas e controles de segurança. |
| **ISO/IEC 27005** | Gestão e tratamento de riscos de segurança da informação. |
| **NIST Cybersecurity Framework (CSF)** | Framework para gerenciamento de riscos cibernéticos baseado nas funções Identificar, Proteger, Detectar, Responder e Recuperar. |
| **LGPD (Lei Geral de Proteção de Dados)** | Legislação brasileira que regulamenta o tratamento de dados pessoais e impõe requisitos de segurança e privacidade. |

Essas normas servem como referência para empresas e órgãos públicos implementarem políticas, controles e processos de segurança da informação.

---
