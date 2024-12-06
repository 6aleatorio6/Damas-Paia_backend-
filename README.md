<p align="center" >
  <a href="#" target="blank"><img src="https://raw.githubusercontent.com/6aleatorio6/Damas-Paia_mobile/main/src/assets/icon.png" width="200" alt="DAMASPAIA Logo" /></a>
</p>

<p>
    <p align="center">Jogo de Damas Online</p>
</p>

## Descrição

Este repositório contém o backend de um jogo de Damas Online, desenvolvido com **NestJS**, **TypeORM**, **Socket.io** e **PostgreSQL**. O projeto oferece uma arquitetura sólida, integrações modernas e funcionalidades em tempo real.  

Conta com uma cobertura abrangente de testes, incluindo testes **unitários** e **end-to-end**, garantindo alta confiabilidade e desempenho.  

| Plataforma                                                   | Tecnologia   | Status       |
| ------------------------------------------------------------ | ------------ | ------------ |
| [Backend](https://github.com/6aleatorio6/damas-online_backend) | NestJS       | Finalizado   |
| [Mobile](https://github.com/6aleatorio6/damas-online_app)   | React Native | Finalizado   |


### **Segurança**

- **Autenticação Segura:** Autenticação via nome e senha com geração de tokens JWT e revalidação de tokens expirados.  
- **Login com OAuth2:** Integração com Google, Discord e GitHub para login rápido e seguro.  
- **WebSocket Protegido:** A conexão WebSocket é aberta apenas após validação do token JWT, garantindo segurança e identificação do usuário com UUID.  

### **Usuário**

- **Cadastro e Gerenciamento:** Permite criar, editar e excluir usuários com rotas protegidas por token.  
- **Validação de Dados:** Verifica disponibilidade de nome de usuário e e-mail antes do cadastro.  

### **Jogo**

- **Pareamento Automático:** Sistema de fila que organiza jogadores para início rápido de partidas.  
- **Movimentação de Peças:** Backend valida movimentos das peças, aplicando regras como capturas e promoções automáticas.  
- **Consulta de Jogadas Permitidas:** O backend informa, sob demanda, os movimentos válidos de uma peça com base na posição atual e no estado do tabuleiro.  
- **Controle de Turnos:** Alternância precisa entre jogadores, garantindo a integridade do fluxo de jogo.  
- **Ranking por Vitórias:** Classificação dos jogadores com base no número de vitórias acumuladas em partidas.  
- **Histórico de Partidas:** Registro detalhado de partidas com resultados, datas e adversários.  
- **Finalização Inteligente:** Partidas encerram automaticamente por desistência, desconexão ou ausência de peças, com controle de tempo de reconexão (`TIMEOUT_TO_RECONNECT`).  
- **Suporte ao Frontend:** Backend fornece dados completos sobre movimentos, status de turnos e resultados em tempo real.  

### **Diferenciais**

- **Segurança Avançada:** Validação de token antes de conexões WebSocket e autenticação integrada com provedores OAuth2.  
- **Automação no Jogo:** Gerenciamento de regras, turnos e encerramento de partidas de forma automática.  
- **Engajamento:** Ranking e histórico detalhado promovem a competição saudável entre jogadores.  


#### Regras do Jogo

<details>
  <summary>Clique aqui para ver as regras completas</summary>

  - **Peças**: Cada jogador inicia com 12 peças distribuídas nas primeiras três linhas do tabuleiro.

  - **Movimentação**: As peças comuns se movem uma casa por vez na diagonal, para frente. As damas podem se mover quantas casas desejar ao longo das diagonais.

  - **Promoção para Damas**: Quando uma peça comum alcança a extremidade oposta do tabuleiro, ela se torna uma dama. As damas possuem a habilidade de se mover e capturar em qualquer direção ao longo das diagonais.

  - **Captura de Peças**: As peças comuns e damas podem capturar peças adversárias. A captura é realizada quando um movimento salta por cima de uma peça inimiga, removendo-a do tabuleiro.

  - **Captura para Trás**: Capturas para trás são permitidas para ambas as peças, comuns e damas.

  - **Opcionalidade da Captura**: A captura não é obrigatória; o jogador é livre para executar qualquer movimento disponível, mesmo que não envolva capturas.

  - **Capturas em Cadeia**: Capturas em cadeia são permitidas, possibilitando que uma única peça capture múltiplas peças adversárias em sequência, incluindo mudanças de direção.

  - **Movimentação da Dama Após Captura**: Após realizar uma captura, seja ela normal ou em cadeia, a dama deve se mover para a casa vazia que fica imediatamente após a última peça capturada.

  - **Condição de Vitória**: Um jogador vence a partida quando captura todas as peças adversárias ou quando o oponente desiste.

</details>




## Instalação

1. Clone o repositório:

   ```bash
   git clone https://github.com/6aleatorio6/Damas-Paia_backend.git
   ```

2. Acesse o diretório do projeto:

   ```bash
   cd Damas-Paia_backend
   ```

3. Crie um arquivo `.env` usando o `.env.example` como base:

   ```bash
   cp .env.example .env
   ```

## Executando a Aplicação

Para iniciar a aplicação com Docker Compose, utilize o seguinte comando:

```bash
 npm run compose:dev
```

## Testes

### Testes Unitários

Atualmente, a aplicação possui **44 testes unitários**. Para executá-los, utilize o seguinte comando:

```bash
npm run compose test
```

### Testes E2E

A aplicação conta com **54 testes end-to-end**. Para executá-los, utilize o seguinte comando:

```bash
npm run compose test:e2e
```

### Modo Watch

Para executar os testes automaticamente sempre que houver mudanças nos arquivos, utilize o modo watch. O comando a seguir permite que você especifique um padrão para os arquivos que deseja observar:

```bash
npm run compose test:e2e -- --watch <pattern>
npm run compose test -- --watch <pattern>
```

Substitua <pattern> pelo caminho ou padrão de arquivos que deseja monitorar.

## Teste o Jogo de Damas com `demo.html`

O `demo.html` serve como um frontend simples para testar o jogo de damas. Conseguindo testar as seguintes partes:

- **Criação de Usuário**: Permite criar um novo usuário e conectar ao servidor.
- **Pareamento**: Coloca o usuario criado na fila de pareamento.
- **Simulação de Partida**: Abra duas abas para simular uma partida completa.

![demonstração do html](demo.gif)

### Para simular uma partida:

O backend deve estar em execução em `localhost:3000`.

1. **Abra o Arquivo**:
   Use duas abas ou janelas diferentes do navegador para abrir `demo.html`.

2. **Crie e Conecte Usuários**:
   O formulário é preenchido automaticamente com valores aleatórios. Clique em **Criar Usuario** em ambas as abas para conectar dois jogadores.

3. **Inicie a Partida**:
   A partida começará automaticamente após ambos os jogadores se conectarem.
