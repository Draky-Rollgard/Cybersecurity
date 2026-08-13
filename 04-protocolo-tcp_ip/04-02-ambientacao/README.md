# 27. Hands-on — Construção do ambiente

A parte prática utiliza **máquinas virtuais (VMs)**.

Uma VM é um computador virtualizado que utiliza recursos da máquina física hospedeira.

```text
Computador físico
       │
       └── VirtualBox
              │
              └── Debian VM
```

A máquina física é chamada de:

```text
Host
```

A máquina virtual é chamada de:

```text
Guest
```

---

# 28. Por que utilizar máquinas virtuais?

As VMs oferecem vantagens importantes para estudos de redes e CyberSecurity.

### 1. Snapshots

É possível salvar um estado da VM e retornar a ele posteriormente.

```text
Configuração inicial
       ↓
Teste
       ↓
Erro
       ↓
Restaurar snapshot
```

### 2. Isolamento para testes

Permite realizar experimentos que poderiam ser perigosos para o sistema operacional principal.

Exemplo:

- análise de malware;
- testes de rede;
- alterações de configuração;
- experimentos de segurança.

### 3. Backup completo

Como a VM é composta essencialmente por arquivos, o backup pode preservar:

- sistema operacional;
- aplicativos;
- configurações;
- dados;
- ambiente de testes.

---

# 29. VirtualBox

O **VirtualBox** é um **hypervisor do tipo 2**.

Isso significa que ele é executado sobre um sistema operacional hospedeiro.

```text
Hardware
   ↓
Windows/Linux/macOS
   ↓
VirtualBox
   ↓
VM
   ↓
Debian
```

Como as VMs compartilham recursos do computador físico, é necessário considerar:

- CPU;
- RAM;
- armazenamento;
- virtualização de hardware.

A virtualização precisa estar habilitada no firmware/BIOS/UEFI, normalmente através de tecnologias como:

```text
Intel VT-x
AMD-V
```

---

# 30. Requisitos mínimos indicados pelo material

O material recomenda aproximadamente:

```text
CPU: Intel i3
RAM: 4 GB
Armazenamento: 40 GB
```

Esses valores são referências do material original e podem ser insuficientes para múltiplas VMs ou versões atuais de sistemas operacionais.

---

# 31. Instalação do VirtualBox

## Passo 1 — Download

Baixar o instalador a partir do site oficial do VirtualBox.

## Passo 2 — Verificação de integridade

Antes de instalar, calcular o hash SHA-256 do arquivo.

No Windows, o material utiliza:

```text
CRC SHA → SHA-256
```

O valor obtido deve ser comparado ao hash publicado pelo fabricante.

### Regra

```text
Hash calculado = Hash oficial
        ↓
Arquivo íntegro
```

Se:

```text
Hash calculado ≠ Hash oficial
```

não instalar o arquivo e realizar novo download.

---

# 32. Por que verificar SHA-256?

Um **hash criptográfico** funciona como uma espécie de impressão digital do arquivo.

Se um único bit for alterado, o resultado do hash deverá ser diferente.

A finalidade aqui é verificar principalmente:

- integridade;
- autenticidade do arquivo em relação ao valor publicado.

É importante não confundir isso com criptografia.

---

# 33. Instalação do VirtualBox

Depois de confirmar a integridade:

1. executar o instalador;
2. utilizar permissões administrativas quando solicitado;
3. aceitar as opções padrão;
4. finalizar a instalação.

Depois, instalar o **Extension Pack**, que adiciona funcionalidades adicionais, como suporte relacionado a USB e outras capacidades do VirtualBox.

Procedimento indicado:

```text
VirtualBox
→ Arquivo
→ Preferências
→ Extensões
→ Adicionar pacote
```

Depois:

1. selecionar o Extension Pack;
2. aceitar a licença;
3. finalizar.

Após isso, o VirtualBox pode ser utilizado normalmente sem execução permanente como administrador.

---

# 34. Download do Debian

O Debian será utilizado como sistema operacional da VM.

O material utiliza uma imagem **ISO netinstall**.

Netinstall significa que a imagem inicial é relativamente pequena e contém os componentes necessários para iniciar a instalação, obtendo outros pacotes posteriormente pela Internet.

## Procedimento

1. acessar o site oficial do Debian;
2. baixar a ISO;
3. verificar a integridade;
4. comparar o hash publicado pelo projeto com o hash calculado localmente.

O material original utiliza **MD5**, mas, para uma prática atual, é preferível utilizar um mecanismo criptográfico mais forte, como **SHA-256**, quando fornecido oficialmente.

---

# 35. Criação da VM Debian1

Abrir o VirtualBox.

Selecionar:

```text
Novo
```

Configurar:

```text
Nome: Debian1
Tipo: Linux
Versão: Debian
```

O VirtualBox normalmente detecta automaticamente o sistema a partir do nome escolhido.

---

# 36. Memória da VM

O material originalmente sugere:

```text
1024 MB
```

ou:

```text
768 MB
```

caso necessário.

Essa configuração é bastante limitada para sistemas atuais, portanto deve ser tratada como configuração histórica do material.

O princípio importante é:

> A RAM alocada à VM é retirada da memória disponível no host enquanto a VM está em execução.

---

# 37. Disco virtual

Selecionar:

```text
Criar um novo disco virtual agora
```

Formato:

```text
VDI — VirtualBox Disk Image
```

Armazenamento:

```text
Dinamicamente alocado
```

Nome:

```text
Debian1
```

Depois:

```text
Criar
```

---

# 38. Configuração da VM

Ajustar:

### Geral

Sem alterações.

### Sistema

Garantir:

```text
VT-x/AMD-V
```

habilitado.

### Monitor

Sem alterações.

### Armazenamento

Sem alterações.

### Áudio

Desabilitar:

```text
Habilitar áudio
```

### Rede

Utilizar:

```text
NAT
```

### Portas seriais

Sem alterações.

### USB

Habilitar:

```text
Controladora USB
```

e selecionar:

```text
USB 2.0 / EHCI
```

quando disponível e apropriado.

### Pastas compartilhadas

Sem alterações.

### Interface do usuário

Sem alterações.

---

# 39. Instalação do Debian

## Passo 1

Iniciar a VM.

Selecionar a ISO Debian como disco de boot.

## Passo 2

No instalador:

```text
INSTALL
```

## Passo 3

Idioma:

```text
Português do Brasil
```

## Passo 4

Localização:

```text
Brasil
```

## Passo 5

Teclado:

```text
Português brasileiro
```

## Passo 6

Aguardar o carregamento dos componentes.

## Passo 7

Hostname:

```text
debian01
```

## Passo 8

Domínio:

```text
localdomain
```

## Passo 9

Definir a senha do:

```text
root
```

e confirmá-la.

## Passo 10

Criar um usuário comum, sem privilégios administrativos permanentes.

## Passo 11

Definir e confirmar a senha desse usuário.

## Passo 12

Configurar o fuso horário.

## Passo 13

Escolher particionamento assistido.

## Passo 14

Aceitar o esquema sugerido.

## Passo 15

Selecionar o disco:

```text
/dev/sda
```

## Passo 16

Selecionar:

```text
Finalizar particionamento
```

e confirmar:

```text
SIM
```

para gravar as alterações.

## Passo 17

Aguardar a instalação do sistema básico.

## Passo 18

Quando questionado sobre outra mídia:

```text
NÃO
```

## Passo 19

Configurar o repositório:

```text
País: Brasil
Espelho: padrão
Proxy HTTP: deixar vazio
```

## Passo 20

Aguardar a configuração do `apt` e instalação dos pacotes.

## Passo 21

No `popularity-contest`:

```text
NÃO
```

Depois selecionar os componentes de software necessários.

## Passo 22

Permitir instalação do:

```text
GRUB
```

## Passo 23

Selecionar:

```text
/dev/sda
```

como dispositivo de instalação do bootloader.

## Passo 24

Reiniciar a VM.

---

# 40. Ajustes iniciais

Após iniciar o Debian:

1. fazer login;
2. abrir o terminal;
3. obter privilégios administrativos;
4. instalar:
   - Guest Additions;
   - `net-tools`;
   - Wireshark;
5. desabilitar IPv6 conforme o laboratório.

---

# 41. VirtualBox Guest Additions

As **Guest Additions** melhoram a integração entre host e guest.

## Procedimento

No VirtualBox:

```text
Dispositivos
→ Inserir imagem de CD dos adicionais de convidados
```

Se aparecer uma mensagem sobre execução automática:

```text
Cancelar
```

Depois, no terminal como root:

```bash
apt-get update
apt-get install -y build-essential
apt-get install -y linux-headers-$(uname -r)
mount /dev/sr0 /mnt
cp /mnt/VBoxLinuxAdditions.run .
umount /mnt
./VBoxLinuxAdditions.run
```

### O que cada comando faz?

```bash
apt-get update
```

Atualiza os índices dos repositórios.

```bash
apt-get install -y build-essential
```

Instala ferramentas necessárias para compilação.

```bash
apt-get install -y linux-headers-$(uname -r)
```

Instala os headers correspondentes ao kernel atualmente executado.

```bash
mount /dev/sr0 /mnt
```

Monta a mídia virtual do CD em `/mnt`.

```bash
cp /mnt/VBoxLinuxAdditions.run .
```

Copia o instalador para o diretório atual.

```bash
umount /mnt
```

Desmonta a mídia.

```bash
./VBoxLinuxAdditions.run
```

Executa o instalador.

> **Nota:** esses comandos refletem o procedimento do material original. Em versões atuais do VirtualBox/Debian, o método de instalação pode variar.

---

# 42. Instalação das ferramentas de rede

O pacote `net-tools` disponibiliza ferramentas tradicionais de administração de redes, como:

```text
arp
ifconfig
netstat
rarp
nameif
route
```

Instalar:

```bash
apt-get install -y net-tools wireshark
```

Depois verificar:

```bash
which ifconfig
which wireshark
```

O comando `which` retorna o caminho do executável encontrado.

Exemplo:

```text
/usr/sbin/ifconfig
```

Isso permite confirmar que o programa está instalado e acessível.

---

# 43. Wireshark

O **Wireshark** é um analisador de protocolos de rede.

Ele permite:

- capturar tráfego;
- visualizar frames;
- analisar cabeçalhos;
- estudar protocolos;
- investigar problemas de rede;
- observar encapsulamento;
- auxiliar em análises de segurança.

Durante a instalação, o material recomenda manter:

```text
Permitir captura por usuários não privilegiados?
→ NÃO
```

Essa escolha reduz o acesso de usuários comuns à captura de tráfego.

---

# 44. Desabilitação do IPv6

O laboratório original não necessita de IPv6.

Primeiro identificar a interface:

```bash
ifconfig
```

Exemplo apresentado:

```text
Interface: enp0s3
IPv4: 10.0.2.15
IPv6: fe80::a00:27ff:fe98:ee12
MAC: 08:00:27:98:ee:12
```

A interface:

```text
enp0s3
```

é a interface de rede da VM.

---

# 45. Configuração do sysctl

Editar:

```bash
nano /etc/sysctl.conf
```

Adicionar as configurações necessárias ao final do arquivo para desabilitar IPv6.

Depois aplicar:

```bash
sysctl -p
```

Reiniciar:

```bash
init 6
```

Após a reinicialização:

```bash
/sbin/ifconfig
```

Verificar se a interface apresenta somente o endereço IPv4 esperado.

> **Nota:** desabilitar IPv6 é uma decisão específica do laboratório. Em sistemas reais, IPv6 não deve ser desabilitado sem uma justificativa de arquitetura, compatibilidade ou segurança.

---

# 46. Fluxo completo de uma comunicação TCP/IP

Uma forma importante de consolidar todo o conteúdo é visualizar o caminho completo.

Imagine:

```text
Navegador
   ↓
HTTP
   ↓
TCP
   ↓
IP
   ↓
Ethernet
   ↓
Rede
```

O processo de encapsulamento pode ser representado como:

```text
DADOS DA APLICAÇÃO
        ↓
SEGMENTO TCP/UDP
        ↓
DATAGRAMA IP
        ↓
FRAME ETHERNET
        ↓
BITS
```

No destino ocorre o processo inverso:

```text
BITS
 ↓
FRAME
 ↓
DATAGRAMA IP
 ↓
SEGMENTO TCP/UDP
 ↓
DADOS DA APLICAÇÃO
```

Esse conceito é fundamental para entender **Wireshark, análise de tráfego e segurança de redes**.

---