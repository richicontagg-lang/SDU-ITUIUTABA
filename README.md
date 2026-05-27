Pré-requisitos Necessário
Verifique se você tem Node.js 20 e Docker Desktop instalados. Se não tiver, instale primeiro.

Zip do projeto extraído (ex: C:\projetos\sdu-ituiutaba)

1 Abra o projeto no VS Code
No VS Code: File → Open Folder e selecione a pasta sdu-ituiutaba extraída do zip.
Você verá as pastas client/, server/ e o arquivo docker-compose.yml na raiz.

2
Abra o terminal do VS Code
Pressione Ctrl + (acento grave) ou vá em Terminal → New Terminal. O terminal abre na raiz do projeto.

3
Suba o banco de dados
No terminal (ainda na raiz do projeto), rode:
Terminal 1 — raiz do projeto
docker-compose up postgres -d
Aguarde aparecer Started ou healthy. O PostgreSQL estará rodando na porta 5432.
O Docker Desktop precisa estar aberto (ícone na barra de tarefas) para isso funcionar.

4
Instale as dependências do backend
Ainda no mesmo terminal, entre na pasta server:
Terminal 1
cd server
npm install
Aguarde o npm terminar de baixar os pacotes (pode levar 1–2 minutos na primeira vez).

5
Crie as tabelas no banco
Ainda dentro da pasta server/, rode o comando de migration:
Terminal 1 — dentro de server/
npm run migrate
Esse comando cria todas as tabelas (users, denuncias, etc.) e insere o usuário admin padrão.
Se aparecer erro de "psql not found", instale o PostgreSQL client ou rode: docker-compose exec postgres psql -U postgres sdu_ituiutaba -f /docker-entrypoint-initdb.d/001_init.sql

6
Inicie o backend
No mesmo terminal (dentro de server/):
Terminal 1 — dentro de server/
npm run dev
Deve aparecer a mensagem:
✅ API SDU rodando na porta 3001
Deixe esse terminal aberto. A API precisa continuar rodando.

7
Abra um segundo terminal
Clique no ícone + no painel de terminais (canto superior direito do terminal) ou pressione Ctrl + Shift + `. Um novo terminal abre na raiz do projeto.

8
Instale e inicie o frontend
No segundo terminal:
Terminal 2 — raiz do projeto
cd client
npm install
npm run dev
Deve aparecer:
Local: http://localhost:5173/

9
Acesse no navegador
Pronto!
Abra o navegador e acesse:
http://localhost:5173
