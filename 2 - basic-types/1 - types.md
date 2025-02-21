## O que são tipos?
`Tipos definem quais valores determinados dados podem assumir em um software. Eles garantem maior previsibilidade e segurança no código.`

## Checagem de Tipos

`Linguagem Dinamicamente Tipada`  
A verificação de tipos ocorre **em tempo de execução**, ou seja, quando o código está sendo executado. Linguagens desse tipo são interpretadas.

- **Prós**:
  - Maior flexibilidade na escrita do código.
  - Menos código boilerplate para definir tipos.
  - Melhor para prototipação rápida.

- **Contras**:
  - Maior chance de erros inesperados em produção.
  - Dificuldade de manutenção em grandes projetos.
  - Depuração mais difícil.

`Linguagem Estaticamente Tipada`  
A checagem de tipos ocorre **durante a compilação**, antes do código ser executado.

- **Prós**:
  - Erros de tipo são detectados antes da execução.
  - Melhor manutenção e escalabilidade do código.
  - Melhor suporte a IDEs, como autocomplete e refatoração segura.

- **Contras**:
  - Código pode ser mais verboso.
  - Maior curva de aprendizado.
  - Pode exigir mais tempo na configuração inicial.

## TypeScript
O **TypeScript** é uma linguagem estaticamente tipada construída sobre o **JavaScript**, que é dinamicamente tipado. No TypeScript, os tipos são opcionais, permitindo maior segurança sem perder flexibilidade.

### Exemplo:

#### JavaScript (Sem Tipagem)
```javascript
const message = "Olá";

message(); // Isso dará erro em produção! Mas não durante o desenvolvimento.
```
No JavaScript, não há verificação de tipos em tempo de desenvolvimento, o que pode levar a erros inesperados em produção.

#### TypeScript (Com Tipagem)
```ts
const message: string = "Olá";

message(); // Erro em tempo de desenvolvimento: 'message' é uma string e não uma função!
```
No TypeScript, o compilador infere que message é uma string, impedindo chamadas inválidas.

### Compatibilidade de Tipos
O TypeScript usa o modelo de tipagem estrutural `*(Structural Typing)*`. Isso significa que a compatibilidade de tipos não é baseada no nome do tipo, mas na estrutura dos membros desse tipo.

```ts
interface Person {
    name: string;
}

class Employee {
    name: string;
}

let person: Person;
let newEmployee = new Employee();

person = newEmployee; // Funciona, pois Employee tem os mesmos atributos de Person.
```

O TypeScript considera Person e Employee como compatíveis porque ambos possuem o mesmo membro `*(name: string).*`

### Tipo Literal

```ts
let person: Person;
let alisson = { name: 'Alisson', age: 30 }; // TypeScript infere: { name: string, age: number }

person = alisson; // Erro: 'age' não faz parte de 'Person'
person = { name: 'Alisson' }; // Funciona, pois os atributos são compatíveis.
```

Aqui, se atribuirmos diretamente um objeto literal a person, o TypeScript exige que ele corresponda estritamente ao tipo Person. No entanto, se atribuirmos uma variável contendo um objeto com atributos extras, o TypeScript permite, pois verifica apenas os atributos necessários.

### Soundness (Som de Tipos)
O conceito de soundness refere-se à certeza de que um programa não entrará em estados inválidos. O TypeScript não é totalmente sound, pois permite algumas exceções para manter a compatibilidade com JavaScript.

`Exemplo onde o TypeScript pode falhar em garantir soundness:`

```ts
let num: number;
num = JSON.parse("5"); // Nenhuma verificação se a string pode ser convertida corretamente.
```
**Isso pode causar erros inesperados se o JSON não for válido.**

### Recursos Adicionais sobre Tipos no TypeScript
- Inferência de Tipos: O TypeScript infere tipos automaticamente, reduzindo a necessidade de anotações explícitas.
- Tipos Opcionais e Union Types: Permite mais flexibilidade na definição de tipos.
- Tipos Avançados: Includes, Interseções, Genéricos, Tipos Condicionais, entre outros.

`Esses recursos tornam o TypeScript uma ferramenta poderosa para desenvolvimento seguro e escalável!`
