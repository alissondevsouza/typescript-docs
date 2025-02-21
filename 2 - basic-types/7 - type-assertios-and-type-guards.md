# Type Assertions e Type Guards no TypeScript

### Type Assertions (Asserções de Tipo)

Type Assertions são usadas para informar ao TypeScript que um valor deve ser tratado como um tipo específico. Isso equivale a uma conversão de tipo, porém sem modificar o valor original.

### Sintaxe:

- `variavel as Tipo` (explicit cast )
- `<Tipo>variavel` (diamond operator - **não é mais usado, não pode ser utilizado em JSX**)

### Exemplo Básico:

```ts
const tipo: any = "oi";
const tipo2 = tipo;  // TypeScript infere `tipo2` como `any`
const tipo2 = tipo as string; // Converte `tipo` de `any` para `string`
```

### Exemplos com Tipos Literais:

```ts
const literal = "literal" as "literal";
const literal = "literal" as const; // Os dois são equivalentes
```

### Conversão para outro tipo:

```ts
let tamanho: number = (tipo as string).length; // Converte `any` para `string` e obtém o tamanho
```

### Trabalhando com `unknown`

```ts
const naoSei: unknown = { a: 1, b: "outro valor" };
naoSei.a; // Erro: TypeScript não sabe o que há dentro de `naoSei`

;(naoSei as { a: number; b: string }).a; // Funciona, pois foi feito cast de `unknown` para um objeto
```

### Interface e Type Assertions

```ts
interface AlgumaCoisa {
    a: number;
    b: string;
}
;(naoSei as AlgumaCoisa).b; // Agora funciona corretamente
```

### Casos Inválidos de Type Assertion

```ts
const a: string = 123 as string; // Erro: Tipos não têm interseção
```

Para contornar isso, primeiro converta para `unknown`, depois para o tipo desejado:

```ts
const a: string = 123 as unknown as string; // Correto
```

### Type Assertions com Objetos

```ts
interface Pessoa {
    nome: string;
}
let pessoa: Pessoa = {}; // Erro: `nome` é obrigatório
let pessoa: Pessoa = {} as Pessoa; // Funciona, mas pode ocultar erros
```


## Type Guards (Proteção de Tipos)

Type Guards são uma maneira de informar ao TypeScript que, após uma determinada verificação, um valor pode ser tratado como um tipo específico.

### Exemplo de Type Guard:

```ts
function isString(value: unknown): value is string {
    return typeof value === "string";
}

const valor: unknown = 123;

if (isString(valor)) {
    valor.length; // Aqui `valor` já é uma string
}
```

### Assertion Functions

As **Assertion Functions** garantem que um valor é de um determinado tipo ou lançam um erro se a condição não for atendida.

### Exemplo de Assertion Function:

```ts
function assertString(value: unknown): asserts value is string {
    if (typeof value !== "string") {
        throw new Error("Precisa ser uma string");
    }
}

const valor: unknown = 123;

assertString(valor);
// A partir daqui, `valor` é garantidamente uma string
```
