## `null` e `undefined`

### Diferença entre `null` e `undefined`

- **`null`**: Representa a ausência de um valor. A variável existe, mas não possui um valor atribuído.
- **`undefined`**: Representa a ausência da existência de um valor. Qualquer variável declarada sem um valor inicial é automaticamente `undefined`.

**Observação**: `undefined` não é uma palavra reservada no JavaScript/TypeScript.

No TypeScript, `null` e `undefined` são tipos distintos, mas possuem o mesmo comportamento padrão: podem ser atribuídos a qualquer variável, a menos que haja restrições na configuração do compilador.

## Configuração no `tsconfig.json`
O TypeScript permite configurar como `null` e `undefined` devem ser tratados por meio da opção `strictNullChecks`.

### Exemplo:

`Com strictNullChecks: true`

```ts
let nome: string | null;
console.log(nome.toUpperCase()); // Erro! Pois 'nome' pode ser null.
```
Com strictNullChecks ativado, o TypeScript reclama porque a variável nome pode ser null, evitando possíveis erros em tempo de execução.

`Com strictNullChecks: false`
```ts
let nome: string | null;
console.log(nome.toUpperCase()); // Funciona, mas pode causar um erro em tempo de execução.
```
Sem essa verificação, o TypeScript permite chamar toUpperCase() mesmo que nome seja null, o que pode resultar em erro.

### Operador Non-null Assertion (!)
O operador `!` informa ao TypeScript que temos certeza de que uma variável não será null ou undefined. Isso pode ser considerado uma "gambiarra", pois ignora a checagem de tipos.

`strictNullChecks: true;`
```ts
let nome: string | null;
console.log(nome!.toUpperCase()); // Funciona, mas pode causar erro se 'nome' for realmente null.
```
***O uso desse operador deve ser feito com cuidado, pois pode mascarar problemas reais no código.***

### Uso do Optional Chaining (?.)
O optional chaining `?.` permite acessar propriedades ou chamar métodos de um valor que pode ser null ou undefined sem causar um erro.

```ts
function foo(x?: string | null) {
    return x?.toUpperCase(); // Retorna string | undefined
}
```

`Aqui, se x for null ou undefined, o retorno será undefined, em vez de lançar um erro.`

**Por outro lado:**

```ts
function foo(x?: string | null) {
    return x.toUpperCase(); // Erro! x pode ser undefined.
}
```
Isso gera um erro porque x pode ser undefined, e não se pode chamar toUpperCase() de algo indefinido.

```ts
function foo(x?: string | null) {
    return x!.toUpperCase(); // Funciona, mas pode quebrar em tempo de execução.
}
```
Aqui, o `!` força a execução, assumindo que x sempre terá um valor válido.

### Tipo unknown
O tipo unknown representa um valor desconhecido e é considerado mais seguro que any, pois impede atribuições diretas sem uma verificação de tipo.

```ts
let a: string = "Alisson";
const b = 23;
let c: unknown = a; // Pode receber qualquer valor
c = b;
c = null;
c = undefined;
c = {};
c = [];
c = c;
c = void 0;
```

`Por inferência:`

```ts
const x = c;  // TypeScript infere que x é do tipo unknown
```

```ts
const z: string = c; // Erro! unknown não pode ser atribuído a um tipo específico sem verificação.
```
***O unknown precisa ser convertido antes de ser utilizado.***

```ts
if (typeof c === "string") {
    const z: string = c; // Agora funciona!
}
```

### Tipo never
O tipo never representa valores que nunca podem ocorrer. Nenhum outro tipo pode ser atribuído a ele.

```ts
let a: string = "Alisson";
const b = 23;
let c: never = a;  // Erro!
c = b;  // Erro!
c = null;  // Erro!
c = undefined;  // Erro!
c = {};  // Erro!
c = [];  // Erro!
c = c;  // Erro!
c = void 0;  // Erro!
```

`O never geralmente aparece em funções que nunca retornam, como loops infinitos ou lançamentos de erro:`

```ts
function error(message: string): never {
    throw new Error(message);
}

function infiniteLoop(): never {
    while (true) {}
}
```

**Observação:** Diferente de unknown, never pode ser atribuído a qualquer tipo, mas nenhum tipo pode ser atribuído a never.
