# Biblioteca CEPK — HTML, CSS, JavaScript e Firebase

Este projeto não usa Node.js nem servidor próprio. O frontend é estático e pode ser publicado no GitHub Pages. Os dados ficam no Cloud Firestore.

## Arquivos
- `index.html`: telas do site.
- `css/styles.css`: estilos responsivos.
- `js/app.js`: integração com Firebase, catálogo, painel, livros e empréstimos.
- `firestore.rules`: regras iniciais para proteger o banco.

## Contas
- 'Área do Responsável': Tela com login pre definido que pode adicionar livros ao catalogo realizar empréstimos de livros para as pessoas.
- 'Catálogo': Tela que qual quer um pode abrir e visualizar todos os livros do catalogo, quantas copias tem.
