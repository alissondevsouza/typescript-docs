## Type Aliases no TypeScript

Os **Type Aliases** permitem criar nomes personalizados para tipos existentes, tornando o código mais legível e reutilizável. Eles são especialmente úteis para definir tipos complexos e evitar repetições.

### Criando um Alias de Tipo

```ts
type MeuTipo = string; // Utilize PascalCase para nomear tipos

function foo(x: MeuTipo) {
    return x;
}
```

Aqui, `MeuTipo` é um alias para `string`. O TypeScript infere que `x` e o retorno da função são do tipo `string`.

### Type Alias com União de Tipos

Podemos definir aliases para tipos mais complexos, como uma união:

```ts
type NullableString = string | null;

function foo(name: NullableString) {
    if (name) console.log(name);
    return name;
}

foo("Alisson"); // Ok, pois é string
foo(null);      // Ok, pois é null
foo(1234);      // Erro, pois não é string nem null
```

Aqui, `NullableString` pode ser `string` ou `null`, e o TypeScript mantém a inferência correta.

### Criando Type Aliases Genéricos

```ts
type Nullable<T> = T | null;

function foo(name: Nullable<string>) {
    if (name) console.log(name);
    return name;
}
```

Esse alias genérico `Nullable<T>` permite definir qualquer tipo como nullable, garantindo flexibilidade sem perder segurança.

### Jeito Errado vs Jeito Certo

#### Código Repetitivo (Errado)

```ts
const objeto: { name: string } = { name: "Alisson" };
const user: { name: string } = { name: "Lais" };
```

#### Usando Type Alias (Certo)

```ts
type User = { name: string };

const objeto: User = { name: "Alisson" };
const user: User = { name: "Lais" };
```

Definir um alias `User` torna o código mais limpo, reutilizável e fácil de manter.

