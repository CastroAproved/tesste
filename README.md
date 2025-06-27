
# Projeto - Arraia Digital

## Arquivo iniciar.bat
### O iniciar.bat so funciona quando você ja editou as informações corretamente no seu .env do banco de daddos e ja rodou as migrations

- Script para inicializar o projeto localmente.
- Remove arquivos de cache antigos para evitar problemas.
- Executa comandos Artisan para recachear configurações, rotas e limpar views e eventos.
- Por fim, inicia o servidor de desenvolvimento do Laravel (`php artisan serve`).

---

## Explicação dos Controllers

### UsuarioController

- Valida dados do login (nome e senha).
- Verifica usuário e senha no banco.
- Cria sessão para usuário autenticado.
- Redireciona para área administrativa (`admin.home`) se login válido.
- Destrói sessão ao fazer logout e redireciona para página de login.

### VoluntariadoController

- Verifica se usuário está logado para acessar o painel.
- Lista todos voluntários na view `admin.index`.
- Exclui voluntário pelo `id`.
- Valida dados ao criar voluntário (nome, email, animação, etc).
- Salva voluntário novo no banco.
- Retorna mensagem JSON de sucesso após cadastro.

---

## Explicação das Rotas

- `/` — mostra a página inicial (`arraia.index`).
- `/barraquinhas` — exibe as barraquinhas do arraiá (`arraia.barraquinhas`).
- `/voluntariado` — formulário para se tornar voluntário (`arraia.voluntariado`).
- `/argola` — jogo da argola digital (`arraia.argola`).

Rotas administrativas (acesso restrito):

- `/admin/login` (GET) — página de login do painel admin.
- `/admin/login` (POST) — realiza login, valida usuário e senha.
- `/admin/logout` (POST) — faz logout, destrói sessão.
- `/admin/home` — painel admin com lista de voluntários.
- `/admin/voluntariado/{id}` (DELETE) — exclui voluntário pelo ID.

Cadastro voluntário:

- `/voluntariado` (POST) — recebe e salva cadastro do voluntário via formulário.

---

## Explicação das Views Principais

### Frontend

- `arraia.index` — página inicial com contador regressivo para o arraiá.
- `arraia.barraquinhas` — mostra as barraquinhas do evento com cards e imagens.
- `arraia.voluntariado` — formulário para inscrição de voluntários com validação.
- `arraia.argola` — página do jogo da argola com interação via JavaScript.

### Administrativo

- `admin.login.login` — formulário para o usuário entrar no painel.
- `admin.index` — lista os voluntários cadastrados, com opção de exclusão.

---

## Passo a passo

Passo a passo para configurar e rodar o projeto, além de informações úteis para entender a estrutura.

---

## 1. Configuração do Banco de Dados

Antes de mais nada, configure o banco de dados para que o projeto funcione corretamente.

1. Abra o arquivo `.env` que está na raiz do projeto (mesma pasta onde fica o arquivo `artisan`).
2. Verifique se a porta 3306 corresponde a correta do seu banco de dados.
4. Se quiser deixar database padrao tambem que é arraiaucb e já esta no .env pode deixar tambêm que com os comandos criara ele automaticamente.
3. Encontre as variáveis abaixo e altere para as informações do seu banco MySQL:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nomedobanco
DB_USERNAME=usuariodobanco
DB_PASSWORD=senhadobanco
```

Salve o arquivo após as alterações.

---

## 2. Inicialização do Projeto

Após configurar o banco de dados, abra um terminal (Prompt de Comando, Terminal do Linux/Mac, ou PowerShell) e **navegue até a raiz do projeto** (onde está o arquivo `artisan`).

Execute os comandos abaixo, um por vez, para preparar o banco e rodar o servidor local:

1. **Executar as migrations**
   Esse comando cria as tabelas no banco de dados com base nas definições do projeto.

   php artisan migrate

2. **Popular o banco com dados iniciais (seeders)**
   Insere dados de exemplo, como um usuário administrador, para facilitar o uso e testes.

   php artisan db:seed

3. **Rodar o servidor local**
   Inicia o servidor web embutido do Laravel para que você possa acessar o projeto no navegador.

   php artisan serve

Após rodar esse comando, geralmente o projeto estará disponível em `http://localhost:8000` verifique no terminal para saber a URL do servidor.

---

## 3. Acesso ao Painel Administrativo

Com o banco populado, você pode acessar o painel administrativo com as seguintes credenciais:

- **Usuário:** gabriel
- **Senha:** admin

Use esses dados para fazer login e começar a usar o sistema.

---

## 4. Comandos Importantes

Estes comandos foram usados para criar as Models e as Migrations do projeto. Normalmente, você não precisará executá-los novamente, a menos que queira adicionar novas entidades.

php artisan make:model Voluntariado -m
php artisan make:model Usuario -m

---

## 5. Glossário de Termos

- **Seeder:** Classe que insere dados automáticos no banco para facilitar testes.
- **Model:** Representa uma tabela no banco e manipula seus dados.
- **Migration:** Define a estrutura das tabelas no banco de dados.
- **Controller:** Controla a lógica da aplicação, processa requisições, manipula dados via Models e retorna respostas.
- **View:** Arquivo que exibe a interface visual para o usuário.
- **Route:** Define URLs e endpoints que direcionam para os Controllers.

---

## 6. Estrutura de Pastas Úteis

- `app/Http/Controllers` – Controladores que gerenciam as regras de negócio.
- `app/Models` – Models que representam as tabelas do banco.
- `database/migrations` – Definições da estrutura do banco de dados.
- `database/seeds` – Scripts para popular o banco com dados iniciais.
- `public` – Arquivos públicos como CSS, JS e imagens.
- `resources/views` – Arquivos de interface (HTML/Blade).
- `routes` – Arquivos que definem as rotas do sistema.

---

## 7. Links úteis

## Painel admin
- [Login](http://127.0.0.1:8000/admin/login)
- [Home](http://127.0.0.1:8000/admin/home)

## Arraia
- [Página principal](http://127.0.0.1:8000/)
- [Barraquinhas](http://127.0.0.1:8000/barraquinhas)
- [Voluntariado](http://127.0.0.1:8000/voluntariado)
- [Argola](http://127.0.0.1:8000/argola)

---
