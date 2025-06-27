
# Projeto - Arraia Digital

Passo a passo para configurar e rodar o projeto, além de informações úteis para entender a estrutura.

---

## 1. Configuração do Banco de Dados (Necessário)

Antes de mais nada, configure o banco de dados para que o projeto funcione corretamente.

1. Abra o arquivo `.env` que está na raiz do projeto (mesma pasta onde fica o arquivo `artisan`).
2. Encontre as variáveis abaixo e altere para as informações do seu banco MySQL:

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
