# Biblioteca CEPK — HTML, CSS, JavaScript e Firebase

Este projeto não usa Node.js nem servidor próprio. O frontend é estático e pode ser publicado no GitHub Pages. Os dados ficam no Cloud Firestore.

## Arquivos
- `index.html`: telas do site.
- `css/styles.css`: estilos responsivos.
- `js/app.js`: integração com Firebase, catálogo, painel, livros e empréstimos.
- `firestore.rules`: regras iniciais para proteger o banco.

## 1. Ativar o Firestore
No console Firebase, abra o projeto `biblioteca-cepk` e confirme que o Cloud Firestore foi criado.

## 2. Configurar o Firebase Authentication
1. Abra **Authentication → Começar**.
2. Em **Sign-in method**, habilite **E-mail/senha**.
3. Em **Users**, crie a conta do responsável com e-mail e senha.
4. Copie o UID dessa conta na lista de usuários.

A tela do site mostra somente o campo de senha. Para isso, abra `js/app.js` e substitua `COLOQUE_O_EMAIL_DO_RESPONSAVEL_AQUI` na constante `ADMIN_EMAIL` pelo e-mail da conta administrativa criada no Firebase. O e-mail ficará configurado no código, mas a senha nunca fica no código; a validação é feita pelo Firebase Authentication.

## 3. Configurar regras do Firestore
1. Abra **Firestore Database → Regras**.
2. Copie o conteúdo de `firestore.rules`.
3. Substitua as duas ocorrências de `COLOQUE_AQUI_O_UID_DO_RESPONSAVEL` pelo UID real do responsável.
4. Publique as regras.

**Não publique regras permissivas para escrita pública.** As regras do Firestore são verificadas no servidor, mesmo quando o site é estático. O UID é um identificador, não uma senha.

## 4. Indexar e testar
A aplicação consulta livros com `archived == false` e empréstimos ordenados por `loanDate`. Se o Firebase solicitar um índice composto, siga o link de criação indicado no erro do console.

Para cadastrar o primeiro livro, entre no painel autenticado e use **Cadastrar livro**. Livros são salvos na coleção `books`; empréstimos na coleção `loans`. Cada livro tem uma capa frontal opcional (URL), sem contracapa ou lombada.

## 5. Executar localmente
Por usar módulos JavaScript e os SDKs do Firebase, abra a pasta com uma extensão de servidor local, como **Live Server** no VS Code. Não abra `index.html` com `file://`.

## 6. Publicar no GitHub Pages
Envie `index.html`, `css/`, `js/` e `firestore.rules` para um repositório GitHub. Em **Settings → Pages**, selecione a branch e a pasta raiz. Depois abra a URL publicada.

## Limitações importantes desta versão
- O painel usa Firebase Authentication com e-mail/senha por trás, mas a interface exibe apenas o campo de senha porque o e-mail administrativo fica configurado em `js/app.js`. Não compartilhe a conta administrativa.
- A capa é uma URL de imagem. Não há upload de arquivo nesta versão.
- O catálogo público lê livros; as alterações e empréstimos dependem do UID configurado nas regras.
- Antes de uso real em escola, teste regras e fluxos com o responsável pela biblioteca e com a equipe escolar. Evite cadastrar dados pessoais desnecessários dos estudantes.
- A configuração web do Firebase é visível no navegador por design; a proteção depende de Authentication e Security Rules. Nunca publique uma chave privada de conta de serviço.
