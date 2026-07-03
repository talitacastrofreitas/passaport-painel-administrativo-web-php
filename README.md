# 🛂 Passaporte-ADM - Painel Administrativo Bahiana Covid-19
O **Passaporte-ADM** é um painel administrativo desenvolvido em **PHP** e **Bootstrap 5** com o propósito de gerenciar acessos, sintomas e registros de usuários no contexto do sistema *Passaporte Bahiana Covid-19*.
O projeto utiliza conceitos de **Programação Orientada a Objetos (POO)** e a extensão **PDO (PHP Data Objects)** para se comunicar de forma segura e estruturada com o banco de dados MySQL.

---
## 🚀 Funcionalidades
- **Autenticação de Usuários:** Sistema completo de login baseado em sessões (`session_start()`).
- **Verificação de Acesso:** Proteção de rotas através do script `verifica.php`, impedindo que usuários não autenticados acessem o painel administrativo.
- **Roteamento Dinâmico:** Estrutura simples de roteamento via parâmetro `GET` (`index.php?pg=...`) que carrega dinamicamente as páginas de gerenciamento de forma limpa.
- **Classe PHP Estruturada:** Utilização da classe `Usuario.class.php` para concentrar as operações de autenticação e carregamento de perfil.
- **Visual Responsivo:** Interface construída com componentes do Bootstrap 5 e folha de estilo customizada para a tela de login.
---
## 📂 Estrutura do Projeto
Abaixo está a organização dos diretórios e arquivos do painel administrativo:
```bash
Passaporte-ADM/
├── conexao/
│   └── connection.php     # Configuração e inicialização da conexão PDO com o MySQL
├── css/
│   └── style.css          # Estilização personalizada para a interface de Login (gradientes, cartões e sombras)
├── img/
│   └── logo.png           # Logotipo institucional
├── index.php              # Ponto de entrada do painel (gerencia o menu e inclui subpáginas)
├── home.php               # Tela de boas-vindas do painel administrativo
├── login.php              # Formulário visual de login para acesso administrativo
├── logar.php              # Lógica que processa o envio do formulário e valida credenciais
├── logout.php             # Rotina que encerra a sessão ativa e redireciona ao login
├── registros.php          # Página/Painel para gerenciamento de registros (Placeholder)
├── sintomas.php           # Página/Painel para gerenciamento de sintomas (Placeholder)
├── usuarios.php           # Página/Painel para gerenciamento de usuários (Placeholder)
├── verifica.php           # Middleware de validação que verifica se o usuário está logado
├── Usuario.class.php      # Classe PHP com métodos de autenticação de dados de usuário
└── README.md              # Documentação do projeto
```
---
## 🛠️ Tecnologias Utilizadas
- [PHP](https://www.php.net/) (Estrutura Orientada a Objetos, controle de sessões e templates)
- [PDO (PHP Data Objects)](https://www.php.net/manual/pt_br/book.pdo.php) (Driver de abstração e consultas seguras)
- [Bootstrap 5](https://getbootstrap.com/) (Estilização responsiva e Navbar)
- [CSS3](https://developer.mozilla.org/pt-BR/docs/Web/CSS) (Estilos adicionais e gradientes)
- [MySQL](https://www.mysql.com/) (Banco de dados relacional)
---
## 🗄️ Estrutura do Banco de Dados
O projeto requer um banco de dados MySQL chamado **`system_db`** contendo uma tabela chamada **`usuarios`**.
### Script SQL para criação da tabela:
```sql
CREATE DATABASE system_db;
USE system_db;
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    senha VARCHAR(32) NOT NULL -- Senha armazenada como hash MD5 (32 caracteres)
);
```
> [!NOTE]
> As senhas na tabela são comparadas utilizando criptografia simples via hash `md5()`. Para inserir um usuário administrador inicial no banco, utilize um gerador de MD5 para sua senha:
> ```sql
> INSERT INTO usuarios (nome, email, senha) VALUES ('Administrador', 'admin@bahiana.edu.br', MD5('sua_senha_secreta'));
> ```
---
## 💻 Como Rodar o Projeto Localmente
1. **Configure o Servidor Apache & MySQL:**
   Você pode usar um ambiente integrado como [XAMPP](https://www.apachefriends.org/), [Laragon](https://laragon.org/) ou [WampServer](https://www.wampserver.com/).
2. **Importe o Banco de Dados:**
   - Acesse o `phpMyAdmin` ou seu cliente MySQL preferido.
   - Crie o banco de dados `system_db` e execute a tabela `usuarios` utilizando o script acima.
3. **Mova o Projeto:**
   - Transfira a pasta `Passaporte-ADM` para o diretório raiz do servidor (ex: `htdocs` no XAMPP ou `www` no Laragon).
4. **Configure a Conexão (se necessário):**
   - Caso seu banco de dados MySQL utilize uma senha ou credenciais diferentes das padrão (`root` com senha vazia), edite o arquivo [conexao/connection.php](file:///C:/Users/TALITA%20CASTRO/.gemini/antigravity/scratch/Passaporte-ADM/conexao/connection.php).
5. **Acesse o Sistema:**
   - Acesse pelo navegador: `http://localhost/Passaporte-ADM`
