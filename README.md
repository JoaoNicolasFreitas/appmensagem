# appmensagem — Trabalho POO

Descrição
--------
Aplicação Java didática que demonstra conceitos de Programação Orientada a Objetos (POO) através de um pequeno sistema de mensagens entre usuários. Provê modelos para usuários, contatos e mensagens, além de um serviço simples para criar/enviar mensagens.

Stack
-----
- Linguagem: Java (JDK 11+ recomendado)
- Build: Gradle (inclui Gradle Wrapper)
- Estrutura: projeto Gradle com módulo `app`

Organização do repositório
-------------------------
Top-level:
- `.gitattributes`, `.gitignore` — configurações Git
- `gradle/`, `gradlew`, `gradlew.bat`, `gradle.properties`, `settings.gradle` — configurações do Gradle
- `app/` — módulo principal da aplicação

Estrutura de código (em `app/src/main/java`)
- `poo.mensagens/`
  - `App.java` — classe principal (ponto de entrada) que demonstra uso das classes do sistema.
- `poo.mensagens.usuarios/`
  - `Usuario.java` — modelo de usuário (propriedades e comportamentos básicos).
  - `Admin.java` — usuário com privilégios estendidos (herda de `Usuario`).
  - `UsuariosUtility.java` — utilitários para manipulação/coleção de usuários.
- `chat/`
  - `Contato.java` — representa informações de contato (nome, telefone/email, etc).
  - `Mensagem.java` — entidade de mensagem (remetente, destinatário, conteúdo, data/hora).
  - `MensagemServico.java` — serviço responsável por criar/enviar/gerenciar mensagens.

Como rodar
----------
Pré-requisitos:
- JDK 11+ instalado
- Git

Passos rápidos:
1. Clone o repositório:
   git clone https://github.com/JoaoNicolasFreitas/appmensagem.git
2. Entre no diretório do projeto:
   cd appmensagem
3. Compile com o Gradle Wrapper:
   ./gradlew build

Executando:
- Pela IDE: importe o projeto Gradle e execute a classe `poo.mensagens.App` como aplicação Java.
- Pela linha de comando (após build): se o projeto estiver configurado com o plugin `application`, você pode executar:
   ./gradlew :app:run
  Caso não tenha o `application` configurado, execute a classe principal diretamente (exemplo):
   java -cp app/build/classes/java/main poo.mensagens.App

Observação: ajuste o comando `java -cp` caso o layout do build seja diferente; executar pela IDE é mais simples para visualização.

Resumo das classes (rápido)
--------------------------
- poo.mensagens.App
  - Demonstra a execução: cria usuários/contatos, instancia o serviço de mensagens e envia/exibe mensagens.
- poo.mensagens.usuarios.Usuario
  - Representa um usuário comum com propriedades (ex.: id, nome, contato) e métodos para interação.
- poo.mensagens.usuarios.Admin
  - Extende `Usuario`; pode ter métodos adicionais (ex.: gerenciar usuários ou enviar mensagens em massa).
- poo.mensagens.usuarios.UsuariosUtility
  - Funções utilitárias: carregar listas de usuários, buscar por id/nome, etc.
- chat.Contato
  - Modelo com dados de contato (nome, telefone, email).
- chat.Mensagem
  - Modelo que encapsula conteúdo, remetente (Usuario/Contato), destinatário e timestamp.
- chat.MensagemServico
  - Serviço que cria e "envia" mensagens (possivelmente armazena em memória e exibe no console).

Exemplo de uso (trecho Java)
----------------------------
```java
// Exemplo ilustrativo de uso das classes
Contato c1 = new Contato("Ana", "ana@example.com", "99999-0000");
Usuario u1 = new Usuario(1, "Ana", c1);

Contato c2 = new Contato("Bruno", "bruno@example.com", "98888-1111");
Admin admin = new Admin(2, "Bruno", c2);

MensagemServico servico = new MensagemServico();
Mensagem m = new Mensagem(u1, admin, "Olá, Bruno! Tudo bem?");
servico.enviar(m);
