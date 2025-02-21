## O que são tipos primitivos?

Os tipos primitivos são aqueles que não derivam de nenhum outro tipo. Eles não são objetos e não possuem métodos ou propriedades próprias. São os tipos fundamentais que representam os valores básicos em TypeScript.

### Principais tipos primitivos:

`*string:*` Qualquer valor em texto  
`*number:*` Qualquer valor numérico (inteiros e decimais)  
`*boolean:*` Representa valores true ou false  
`*null:*` Representa a ausência intencional de um valor  
`*undefined:*` Indica que uma variável foi declarada, mas não possui valor atribuído.

### Exemplos de uso com Type Annotations:

```ts
const nome: string = 'Alisson';
const age: number = 30;
const programer: boolean = true;

function ola(nome: string): void {
    console.log(`Olá ${nome}`);
}
```

### Tipos primitivos vs. Construtores

- ***Em JavaScript e TypeScript, existem versões construtoras dos tipos primitivos***

`String:` Construtor para valores de string  
`Number:` Construtor para valores numéricos  
`Boolean:` Construtor para valores booleanos  

### Exemplo de Construtores:

```ts
const nome = new String('Alisson');
const age = new Number(30);
const programer = new Boolean(true);
```

### Por que evitar construtores?

***O uso dessas versões construtoras não é recomendado porque elas criam objetos em vez de valores primitivos, o que pode levar a problemas de desempenho e comportamento inesperado.***

### Inferência de Tipos `(Type Inference)`

A inferência de tipos no TypeScript permite que o compilador deduza automaticamente o tipo de uma variável com base no valor atribuído a ela. Isso reduz a necessidade de anotações explícitas de tipo, tornando o código mais conciso.

### Exemplos de inferência de tipos:

```ts
let nome = 'Alisson';   // TypeScript infere que 'nome' é do tipo string
let age = 30;           // TypeScript infere que 'age' é do tipo number
let programer = true;   // TypeScript infere que 'programer' é do tipo boolean
```

#### Tipagem de Parâmetros em Funções

Os parâmetros de entrada de funções devem sempre ser tipados explicitamente. Já o tipo de retorno pode ser inferido automaticamente pelo TypeScript, a menos que seja necessário especificá-lo.

**Exemplo:**

```ts
function ola(nome: string) {
    return nome;
}  // O retorno será inferido como string
```

`Caso o retorno deva ser forçado para um tipo específico, podemos anotá-lo explicitamente`

```ts
function soma(a: number, b: number): number {
    return a + b;
}
```

### Inferência de Tipo em Arrays

Se um array contém diferentes tipos de valores, o TypeScript inferirá automaticamente o tipo mais adequado para o conjunto de dados.

**Exemplo:**

```ts
let arr = [1, 'Alisson', true, null];
// TypeScript infere que 'arr' é do tipo (number | string | boolean | null)[]
```

`Se quisermos garantir um tipo específico para um array, podemos declarar de forma explícita`

```ts
let numeros: number[] = [1, 2, 3, 4, 5];
let textos: string[] = ['Alisson', 'TypeScript', 'JavaScript'];
```

- Tipos primitivos são os valores básicos: string, number, boolean, null, undefined.

- Construtores (String, Number, Boolean) existem, mas não são recomendados.

- Inferência de tipos permite que o TypeScript deduza automaticamente o tipo de uma variável.

- Parâmetros de funções devem ser tipados explicitamente, enquanto o retorno pode ser inferido.

- Arrays podem conter múltiplos tipos, e o TypeScript infere o tipo do conjunto.

