# Arrays no TypeScript

### O que são Arrays?

Arrays são coleções ordenadas de valores em uma lista. Eles podem conter elementos de um único tipo ou de múltiplos tipos.

### Definição de Arrays

#### Arrays de um único tipo:

```ts
const strings: string[] = ["a", "b", "c"];
const numbers: Array<number> = [1, 2, 3, 4]; // Usando generics
const booleans: boolean[] = [true, false, true];
```

#### Arrays com `any` (evite usar `any` sempre que possível!):

```ts
const anys: any[] = [1, "string", undefined, null];
```

#### Arrays de objetos:

```ts
const objects: object[] = [{ a: 1 }, { b: 2 }];
```

```ts
const objectsLiterais: { name: string }[] = [{ name: "Alisson" }, { name: "Lais" }];
```

#### Arrays multidimensionais:

```ts
const arrays: string[][] = [["a", "b"], ["c", "d"]];
const arraysGenerics: Array<Array<string>> = [["a", "b"], ["c", "d"]];
```


### Métodos úteis de Arrays

#### Manipulação de valores:

```ts
numbers.push(2); // Adiciona um valor ao final
strings.push("teste");
arrays.push(["e"]);

numbers.pop(); // Remove o último elemento
numbers[0]; // Acessa o primeiro elemento
numbers.map(n => n * 2); // Aplica uma função a cada elemento
```

### Inferência de tipos:

```ts
const nomes = ["Maria", "João", "Pedro"]; // TypeScript infere automaticamente `string[]`
```

### Arrays com múltiplos tipos

```ts
const multArray: (string | number)[] = ["Alisson", 30];
```

```ts
type StringOrNumber = (string | number)[];
const arr: StringOrNumber = ["a", 2];
```

```ts
const arrMulti: StringOrNumber[] = [["a"], ["2"]];
```


### Readonly Arrays (Apenas Leitura)

Os **Readonly Arrays** são arrays que não podem ser modificados.

```ts
const readOnly: readonly string[] = ["a", "b", "c"];
```

#### Operações inválidas:

```ts
readOnly.push("d"); // Erro: push não existe em readonly array
readOnly[0]; // Isso funciona, pois não modifica o array
```

