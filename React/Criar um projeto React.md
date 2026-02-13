#React 
#            Ordem para baixar dependências e rodar

1 - ordem de para criar projeto sem usar o VITE:
- npx create-react-app *nome do projeto* --template typescript
- npm install sass
- npm install @types/sass
- npm start (RODAR O CODIGO)

2 - Criar projeto com VITE:
- npm create vite@latest (ele vai perguntar todo o resto e vc vai selecionando)
-  npm install sass
- npm install @types/sass
- npm run dev(roda o codigo obviamente)


# fazer imagen e module SCSS funcionar precisa criar um arquivo
Nome do arquivo: "declarations.d.ts"

```
declare module "*.png";
declare module "*.jpg";
declare module "*.jpeg";
declare module "*.gif";
declare module "*.svg";
declare module "*.module.scss";
```