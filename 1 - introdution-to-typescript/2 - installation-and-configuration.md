## 1. Instalação do Node.js
Para utilizar TypeScript, primeiro é preciso instalar o Node.js. 

### Instalação via nodejs.org (Instalador)

Instalação a partir do [site oficial](https://nodejs.org/).

Verificar se a instalação foi bem-sucedida:
```sh
node -v  # Verifica a versão do Node.js
npm -v   # Verifica a versão do NPM
```

### Instalação via NVM (Node Version Manager)

O NVM permite instalar e gerenciar várias versões do Node.js no mesmo sistema.

Instalação do NVM no repositório oficial: [nvm-sh](https://github.com/nvm-sh/nvm)

Após a instalação, fechar e reabrir o terminal:

```sh
nvm install --lts  # Instala a versão mais recente LTS do Node.js
nvm use --lts  # Define a versão instalada como padrão
nvm ls  # Lista as versões instaladas e a que esta em uso
```


## 2. Criação de um Projeto Node.js com TypeScript
### Inicializando o Projeto Node.js
```sh
npm init -y  # Cria o arquivo package.json com configurações padrão
```

### Instalando o TypeScript e Tipagens do Node.js
```sh
npm install typescript @types/node --save-dev
```

### Instalando lib para execução do typescript em tempo de Desenvolvimento
```sh
npm install ts-node --save-dev
```

### Criando o Arquivo de Configuração do TypeScript
```sh
npx tsc --init  # Gera o arquivo tsconfig.json
```

## 3. Configuração do `tsconfig.json`
O `tsconfig.json` define as configurações do compilador TypeScript para o projeto. Aqui estão algumas das principais opções:

### **Opções Principais**
- **`incremental`**: Ativa a compilação incremental. Cria um cache (`tsconfig.tsbuildinfo`) para compilar apenas arquivos modificados. Ideal para projetos grandes.
- **`target`**: Define a versão do JavaScript a ser gerada (exemplo: `ES6`, `ES2020`).
- **`lib`**: Permite incluir bibliotecas extras para compatibilidade com versões mais antigas do JavaScript.
- **`rootDir`**: Diretório onde está o código fonte TypeScript.
- **`outDir`**: Diretório onde serão gerados os arquivos compilados.
- **`resolveJsonModule`**: Permite importar arquivos `.json` no projeto.
- **`allowJs`**: Permite que arquivos `.js` coexistam no projeto TypeScript.
- **`checkJs`**: Faz verificação de tipo em arquivos JavaScript.
- **`sourceMap`**: Gera arquivos `.map` para depuração.
- **`removeComments`**: Remove comentários nos arquivos compilados.
- **`strict`**: Ativa todas as verificações estritas de tipos do TypeScript (recomendado).
- **`noImplicitAny`**: Impede que o TypeScript infira `any` implicitamente.

Exemplo de `tsconfig.json` minimalista:
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "CommonJS",
    "rootDir": "src",
    "outDir": "dist",
    "strict": true,
    "esModuleInterop": true
  }
}
```

## 4. Extensão do `tsconfig.json`
Para evitar configurar tudo manualmente, podemos usar configurações predefinidas:

### **Utilizando Configurações Base**
O TypeScript oferece pacotes prontos para o tsconfig.json no GitHub ([tsconfig/bases](https://github.com/tsconfig/bases)) para facilitar a configuração:

#### Exemplo:
```sh
npm install @tsconfig/node20 --save-dev
```
Depois, no `tsconfig.json`, basta adicionar:
```json
{
  "extends": "@tsconfig/node20/tsconfig.json"
}
```
Para adicionar configurações personalizadas, basta sobrescrevê-las dentro de `compilerOptions`.

Exemplo :
```json
{
  "extends": "@tsconfig/node20/tsconfig.json",
  "compilerOptions": {
    "target": "ES2020",
    "strict": true,
    "esModuleInterop": true
  }
}
```

## 5. Configuração de Scripts no `package.json`
Para facilitar a compilação e execução do TypeScript, pode se adicionar scripts no `package.json`:

```json
"scripts": {
  "build": "tsc",
  "start": "node dist/index.js",
  "dev": "ts-node-dev --respawn --transpile-only src/index.ts"
}
```

`ts-node-dev` para um ambiente de desenvolvimento com recarregamento automático:
```sh
npm install ts-node-dev --save-dev
```

Agora para rodar o projeto:
```sh
npm run dev  # Inicia o projeto em modo desenvolvimento
npm run build  # Compila o TypeScript para JavaScript
npm start  # Executa o código compilado
```

## Conclusão

Mais informações sobre `tsconfig.json`: [documentação oficial](https://www.typescriptlang.org/tsconfig).

