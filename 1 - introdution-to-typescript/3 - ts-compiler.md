## **Exemplo de Código TypeScript Traspilado para JavaScript**

### Código ts:
```ts
function main(name: string, idade: number) {
    console.log(`Olá, ${name} e ${idade}`);
}

main('teste');
```

```js
function main(name, idade) {
    console.log(`Olá, ${name} e ${idade}`);
}

main('john', 25);
```


## **Compilar um Arquivo TypeScript**

### Para compilar o arquivo `.ts` e gerar um `.js`:
Isso criará um arquivo `.js` equivalente na mesma pasta do código-fonte.
```sh
npx tsc  # Transpila o código para JavaScript
```

### **Compilar Apenas para Verificação de Tipos**
Para verificar erros de tipo sem gerar um arquivo `.js` de saída:
```sh
npx tsc --noEmit  # Apenas faz a verificação de tipos
```

### **Compilar para uma Versão Específica do JavaScript**
Podemos definir a versão desejada do JavaScript no qual o código será compilado:
```sh
npx tsc --target es6  # Gera um arquivo compatível com ES6
```

### **Ajuda do TypeScript Compiler**
Para visualizar todas as opções disponíveis do compilador:
```sh
npx tsc --all  # Mostra todas as opções disponíveis
```


## 2. Modo Estrito do TypeScript (`strict`)

O modo estrito (`strict`) melhora a segurança do código ao ativar várias regras rígidas de tipagem. Ativa se o mesmo no arquivo `tsconfig.json`:
```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

### **Exemplo sem `strict`**
```ts
async function main(name) {
    console.log(`Olá ${name}`);
}
```
Se `strict` estiver ativado, o TypeScript acusará erro, pois `name` não tem um tipo definido. Se `strict` estiver desativado e `noImplicitAny` estiver `false`, o código funcionará sem erros, mas sem tipagem segura.


## 3. Sobrescrevendo Opções do `tsconfig.json`
Todas as opções do `tsconfig.json` podem ser sobrescritas ao rodar o comando `npx tsc --opção`. Isso é útil para testes rápidos sem modificar a configuração do projeto.

## 4. Organização do Código Compilado

Uma boa prática é gerar o código compilado em uma pasta separada (`dist`, `build`, etc.).

### **Emitir Código em uma Pasta Separada**
```sh
npx tsc --outDir dist  # Salva os arquivos compilados na pasta "dist"
```
Ou configure diretamente no `tsconfig.json`:
```json
{
  "compilerOptions": {
    "outDir": "dist"
  }
}
```

### **Compilação Automática ao Salvar Arquivos (`watch mode`)**
Para que o TypeScript gere automaticamente a build ao salvar um arquivo:
```sh
npx tsc --outDir dist --watch  # Compila automaticamente ao salvar
```
Isso permite um fluxo de desenvolvimento mais eficiente sem precisar rodar `npx tsc` manualmente a cada alteração.

## Observação
Por padrão, todas as opções do TypeScript vêm desativadas, e ativamos apenas o que queremos configurar.

## Conclusão

Para mais detalhes sobre configurações avançadas: [documentação oficial](https://www.typescriptlang.org/docs/handbook/compiler-options.html).
