TYPE ALIASES

Forma de dar nome aos nossos tupos

usa se o type aliases para poder criar tipos de outros tipos

type MeuTipo = string      // não use camelCase, use PascalCase

function foo (x: MeuTipo) {
    return x
}  Typescript inferiria o x como string e o retorno como string, por que sempre que tiver type aliases de tipos primitivos, o typescript derivara seu tipo e usara o primitivo que foi dado a ele

type NullableStrin = string | null

function foo(name: NullableStrin) {
    if (name) console.log(name)
    return name
} //Typescript inferiria o name como NullableStrin e o retorno como NullableStrin, por que NullableStrin é um tipo complexo

foo('Alisson')  // nao da erro por que é string
foo(null)  // nao da erro por que é null
foo(1234)  // da erro por que nao é string nem null

type Nullable<T> = T | null
function foo(name: Nullable<string>) {
    if (name) console.log(name)
    return name
}  // O retorno sera Nullable<string>)  segue tudo como quando string ou null

JEITO ERRADO
const objeto: { name: string } = { name: 'Alisson' }
const user: { name: string } = { name: 'Lais' }

JEITO CERTO
type User = { name: string}
const objeto: User = { name: 'Alisson' }
const user: User = { name: 'Lais' }


