# DIÁRIO DE BORDO — MEMÓRIA

**Tema:** Processo de inicialização e acesso à memória, destacando hardware, BIOS/UEFI, sistema operacional, drivers e gerenciadores de recursos.

---

## 1. Ligamento do computador

Ao pressionar o botão de ligar, a fonte de alimentação fornece energia para a placa-mãe e para os componentes necessários à inicialização.

### Componentes de hardware acionados

- Fonte de alimentação;
- Placa-mãe;
- CPU;
- Memória Flash/ROM que armazena o BIOS/UEFI;
- Controladores da placa-mãe;
- Barramentos internos.

### O que acontece com a memória?

O BIOS/UEFI está armazenado em uma **memória não volátil**, normalmente Flash. Seu conteúdo permanece gravado mesmo quando o computador está desligado.

---

## 2. CPU inicia a execução do BIOS/UEFI

Após receber energia, a CPU começa a executar as primeiras instruções armazenadas na memória Flash/ROM.

### Componentes acionados

- CPU;
- Memória Flash/ROM;
- Controladores da placa-mãe;
- Barramentos internos.

### Funções do BIOS/UEFI

O BIOS/UEFI é responsável por:

- Iniciar o processo de inicialização do computador;
- Identificar os componentes de hardware;
- Inicializar dispositivos básicos;
- Verificar se os componentes necessários estão funcionando;
- Preparar o hardware para o carregamento do sistema operacional.

### Fluxo

```text
┌──────────────────────────────────┐
│        Memória Flash/ROM         │
│                ↓                 │
│             BIOS/UEFI            │
│                ↓                 │
│                CPU               │
│                ↓                 │
│      Execução das instruções     │
└──────────────────────────────────┘
```

---

## 3. BIOS/UEFI realiza o POST

O BIOS/UEFI executa o **POST (Power-On Self-Test)**, realizando uma verificação inicial dos componentes do computador.

### Componentes acionados

- CPU;
- Controladores da placa-mãe;
- Controladores relacionados à memória;
- Dispositivos de armazenamento;
- Dispositivos básicos de entrada e saída.

### Função do BIOS/UEFI

O firmware verifica se os componentes essenciais estão disponíveis e em condições de continuar o processo de inicialização.

### Fluxo

```text
┌──────────────────────────────────┐
│            BIOS / UEFI           │
│                 ↓                │
│                POST              │
│                 ↓                │
│       Verificação do hardware    │
│                 ↓                │
│       Hardware disponível?       │
│                 ↓                │
│                SIM               │
│                 ↓                │
│       Continua a inicialização   │
└──────────────────────────────────┘
```

---

## 4. BIOS/UEFI identifica o dispositivo de armazenamento

Após a verificação inicial, o BIOS/UEFI procura o dispositivo que contém os arquivos necessários para iniciar o sistema operacional.

### Exemplos de dispositivos

- SSD;
- HD;
- USB;
- Outros dispositivos de armazenamento.

### Componentes acionados

- CPU;
- BIOS/UEFI;
- Controlador SATA, NVMe ou USB;
- SSD/HD/USB;
- Barramento correspondente.

### Fluxo

```text
┌──────────────────────────────────┐
│            BIOS / UEFI           │
│                 ↓                │
│     Controlador de armazenament  │
│                 ↓                │
│             Barramento           │
│                 ↓                │
│           SSD / HD / USB         │
└──────────────────────────────────┘
```

O firmware localiza o **bootloader**, que será responsável por iniciar o sistema operacional.

---

## 5. Leitura do bootloader

O BIOS/UEFI solicita ao dispositivo de armazenamento os dados necessários para iniciar o sistema.

### Componentes acionados

- CPU;
- Controlador de armazenamento;
- Barramento;
- SSD/HD/USB;
- Memória de armazenamento.

### O que acontece?

Os dados são lidos do dispositivo de armazenamento e utilizados para iniciar o bootloader.

### Papel da memória

A memória de armazenamento mantém os arquivos de forma **não volátil**, ou seja, os dados permanecem armazenados mesmo depois que o computador é desligado.

### Fluxo

```text
┌──────────────────────────────────┐
│             SSD / HD             │
│                ↓                 │
│           Controlador            │
│                ↓                 │
│            Barramento            │
│                ↓                 │
│                CPU               │
│                ↓                 │
│           Bootloader             │
└──────────────────────────────────┘
```

---

## 6. Bootloader inicia o sistema operacional

O bootloader localiza o **kernel do sistema operacional** no dispositivo de armazenamento e inicia sua execução.

### Componentes acionados

- CPU;
- Dispositivo de armazenamento;
- Controlador de armazenamento;
- Barramentos.

### Fluxo

```text
┌──────────────────────────────────┐
│      Memória de armazenamento    │
│                ↓                 │
│           Controlador            │
│                ↓                 │
│            Barramento            │
│                ↓                 │
│                CPU               │
│                ↓                 │
│            Bootloader            │
│                ↓                 │
│           Kernel do SO           │
└──────────────────────────────────┘
```

Nesse momento começa a transição do controle do BIOS/UEFI para o sistema operacional.

---

## 7. Sistema operacional assume o controle

O kernel do sistema operacional passa a controlar o computador.

O BIOS/UEFI deixa de ser o responsável principal pelo gerenciamento dos recursos do sistema.

### Componentes envolvidos

- CPU;
- Controladores;
- Barramentos;
- Dispositivos de armazenamento;
- Dispositivos de entrada e saída.

### Funções assumidas pelo sistema operacional

O sistema operacional passa a:

- Inicializar os dispositivos;
- Controlar o armazenamento;
- Gerenciar os recursos do computador;
- Controlar operações de entrada e saída;
- Carregar os drivers;
- Gerenciar o acesso aos dispositivos.

### Transição de controle

```text
┌──────────────────────────────────┐
│            BIOS / UEFI           │
│                 ↓                │
│            Bootloader            │
│                 ↓                │
│              Kernel              │
│                 ↓                │
│        Sistema Operacional       │
│                 ↓                │
│     Controle dos recursos do     │
│            computador            │
└──────────────────────────────────┘
```

---

## 8. Entrada dos drivers

Depois que o kernel assume o controle, o sistema operacional identifica os dispositivos instalados e carrega os drivers necessários.

### O que é um driver?

O driver é o software que permite ao sistema operacional se comunicar com determinado componente de hardware.

### Componentes envolvidos

- CPU;
- Controladores de armazenamento;
- Controladores de E/S;
- Barramentos;
- Dispositivos de armazenamento.

### Exemplo de acesso ao armazenamento

```text
┌──────────────────────────────────┐
│        Sistema Operacional       │
│                ↓                 │
│              Driver              │
│                ↓                 │
│     Controlador de armazenamento │
│                ↓                 │
│            Barramento            │
│                ↓                 │
│             SSD / HD             │
└──────────────────────────────────┘
```

O driver transforma as solicitações do sistema operacional em comandos que o controlador do dispositivo consegue executar.

---

## 9. Entrada dos gerenciadores de recursos

Com os drivers funcionando, o sistema operacional começa a administrar os recursos disponíveis.

### Componentes envolvidos

- CPU;
- Controladores;
- Barramentos;
- Dispositivos de armazenamento;
- Dispositivos de E/S.

### Funções dos gerenciadores de recursos

Os gerenciadores ajudam o sistema operacional a:

- Controlar o acesso aos dispositivos;
- Organizar operações de leitura e gravação;
- Gerenciar arquivos;
- Coordenar processos;
- Controlar dispositivos de entrada e saída;
- Administrar os recursos disponíveis.

### No contexto da memória

O sistema operacional controla **quando, como e qual dispositivo de armazenamento será acessado**.

---

## 10. Sistema operacional acessa a memória de armazenamento

Quando um programa solicita um arquivo armazenado em um SSD ou HD, ocorre uma sequência de comunicação entre software e hardware.

### Fluxo de leitura

```text
┌──────────────────────────────────┐
│            Aplicação             │
│                ↓                 │
│        Sistema Operacional       │
│                ↓                 │
│      Gerenciador de Recursos     │
│                ↓                 │
│              Driver              │
│                ↓                 │
│     Controlador de Armazenamento │
│                ↓                 │
│            Barramento            │
│                ↓                 │
│             SSD / HD             │
│                ↓                 │
│         Dados armazenados        │
└──────────────────────────────────┘
```

### Fluxo de gravação

Na gravação, os dados percorrem o caminho até o dispositivo de armazenamento:

```text
┌──────────────────────────────────┐
│            Aplicação             │
│                ↓                 │
│        Sistema Operacional       │
│                ↓                 │
│              Driver              │
│                ↓                 │
│            Controlador           │
│                ↓                 │
│            Barramento            │
│                ↓                 │
│             SSD / HD             │
│                ↓                 │
│         Gravação dos dados       │
└──────────────────────────────────┘
```

---

## 11. Papel dos barramentos

Os barramentos são responsáveis pela comunicação entre os diferentes componentes do computador.

### Exemplos

- PCIe;
- SATA;
- USB;
- Outros barramentos internos e externos.

### Função

Os barramentos transportam:

- Dados;
- Comandos;
- Sinais de controle.

### Exemplo com SSD NVMe

```text
┌──────────────────────────────────┐
│               CPU                │
│                ↓                 │
│         Controlador PCIe         │
│                ↓                 │
│          Barramento PCIe         │
│                ↓                 │
│        Controlador do SSD        │
│                ↓                 │
│      Memória Flash do SSD        │
└──────────────────────────────────┘
```

Assim, o barramento permite que o sistema operacional envie comandos e receba dados da memória de armazenamento.

---

## 12. Dispositivos de E/S

Os dispositivos de **Entrada e Saída (E/S)** permitem que o computador receba, envie ou armazene informações.

### Exemplos

- Teclado;
- Mouse;
- USB;
- Rede;
- SSD;
- HD;
- Outros periféricos.

### Relação com a memória

Um dispositivo de E/S pode solicitar que informações sejam lidas ou gravadas no armazenamento.

### Exemplo

```text
┌──────────────────────────────────┐
│              Usuário             │
│                 ↓                │
│             Aplicação            │
│                 ↓                │
│        Sistema Operacional       │
│                 ↓                │
│               Driver             │
│                 ↓                │
│            Controlador           │
│                 ↓                │
│             Barramento           │
│                 ↓                │
│              SSD / HD            │
│                 ↓                │
│               Dados              │
└──────────────────────────────────┘
```

---

# 13. Sistema em funcionamento normal

Depois de toda a inicialização, o sistema operacional passa a controlar o acesso aos dispositivos e à memória de armazenamento.

### Fluxo geral

```text
┌──────────────────────────────────┐
│            APLICAÇÃO             │
│                ↓                 │
│       SISTEMA OPERACIONAL        │
│                ↓                 │
│     GERENCIADOR DE RECURSOS      │
│                ↓                 │
│              DRIVER              │
│                ↓                 │
│           CONTROLADOR            │
│                ↓                 │
│            BARRAMENTO            │
│                ↓                 │
│      MEMÓRIA DE ARMAZENAMENTO    │
│                ↓                 │
│              DADOS               │
└──────────────────────────────────┘
```

---

# 14. Fluxograma completo

```text
┌──────────────────────────────┐
│    1. COMPUTADOR É LIGADO    │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│     2. CPU É INICIALIZADA    │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│  3. BIOS/UEFI É EXECUTADO    │
│     A PARTIR DA FLASH/ROM    │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│   4. POST E VERIFICAÇÃO DO   │
│          HARDWARE            │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ 5. LOCALIZA DISPOSITIVO DE   │
│        ARMAZENAMENTO         │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│  6. LÊ O BOOTLOADER DO       │
│        ARMAZENAMENTO         │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│  7. BOOTLOADER INICIA O      │
│           KERNEL             │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│   8. SO ASSUME O CONTROLE    │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│   9. DRIVERS SÃO CARREGADOS  │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ 10. GERENCIADORES DE RECURSOS│
│           ATUAM              │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ 11. SO ACESSA A MEMÓRIA DE   │
│         ARMAZENAMENTO        │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│   12. SISTEMA EM OPERAÇÃO    │
└──────────────────────────────┘
```

---

# 15. Resumo dos componentes e funções

| **COMPONENTE** | **FUNÇÃO NO PROCESSO** |
|---|---|
| **Flash/ROM** | Armazena o BIOS/UEFI de forma não volátil. |
| **BIOS/UEFI** | Inicializa e verifica o hardware e localiza o dispositivo de inicialização. |
| **CPU** | Executa o firmware, o bootloader e o sistema operacional. |
| **SSD/HD** | Armazena permanentemente o sistema operacional e os arquivos. |
| **Controlador** | Controla a comunicação com o dispositivo de armazenamento. |
| **Barramento** | Transporta dados e comandos entre os componentes. |
| **Driver** | Permite ao sistema operacional controlar o hardware. |
| **Gerenciador de recursos** | Organiza e controla o uso dos recursos do sistema. |
| **Sistema operacional** | Assume o controle do hardware e gerencia os acessos ao armazenamento. |
| **Dispositivos de E/S** | Permitem entrada, saída e transferência de informações. |

---

# Conclusão

Durante o processo de inicialização, a **memória Flash/ROM** fornece as instruções do BIOS/UEFI. O firmware inicializa e verifica o hardware e, posteriormente, localiza o dispositivo de armazenamento que contém o sistema operacional.

Em seguida, o **bootloader** inicia o kernel, que assume o controle do computador. A partir desse momento, o **sistema operacional** passa a administrar os recursos do sistema, utilizando **drivers, controladores e barramentos** para se comunicar com os dispositivos.

Por fim, o sistema operacional realiza operações de **leitura e gravação** na memória de armazenamento, permitindo que aplicações acessem e salvem dados no **SSD, HD ou outro dispositivo de armazenamento não volátil**.
