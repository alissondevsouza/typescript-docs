type assertions e type guards

type-assertions -> É quando fazemos uma asserção, quando dizemos para o typescript que um tipo é na verdade outro tipo. É uma conversao de um tipo para outro

sintaxe:
- variavel as tipo   (explicit cast)
- <string>variavel   (diamond operator)    // não é usada mais, nao pode ser usado em jsx

Exemplo:
const tipo: any = 'oi'
const tipo2 = tipo  // typescript vai inferir que o tipo 2 é any
const tipo2 = tipo as string   // força o typescript tratar tipo 2 como string, a uma conversao de tipo, de any para string

exemplos com tipos literais
const literal = 'literal' as 'literal'
const literal = 'literal' as const 
Os dois sao a mesma coisa

let tamanho: number = (tipo as string).length    // Esta fazendo o cast para string e ja usando a variavel string para outra coisa

const naoSei: unknow = { a: 1, b: 'outro valor' }
naoSei.a   // Da erro de typescript pois o typescrit nao sabe o que tem no tipo naoSei
;(naoSei as { a: number, b: string}).a   // agora funciona, por que foi feito o cas de unknow para o objeto. Lembra que é necessarios usar o ; quando se inicia uma linha com cast

interface AlgumaCoisa {
    a: number,
    b: string
}
;(naoSei as AlgumaCoisa).b   

const a: string = 123 as string   // Erro de typescript, por nao é possivel fazer cast de dois tipos que nao se intercectam no conjunto de tipos, nao fazer overlap

Precisa primeiro converter para unknown para depois converter para string
const a: string = 123 as unknown as string


interface Pessoa {
    nome: string
}
let pessoa: Pessoa = { }   // Erro de typescript ao iniciar pessoa do tipo Pessoa com array vazio, por Pessoa tem um atributo nome
let pessoa: Pessoa = { } as Pessoa    // Assim funciona



Type Guards -> Forma de dizer para o typescript que depois de determinado ponto aquele tipo vai ser um tipo que estamos dizendo

Exemplo:

function isString (value: unknown): value is string {
    return typpeof value === 'string'
}

const valor: unknown = 123

if(isString(valor)) {
    valor.lenght   // aqui valor ja se torna uma string
}


Assertion function
function assertString (value: unknown): asserts values is string {
    if( typeof value !== 'string') {
        throw new Error ('Precisa ser uma string')
    }
}

const valor: unknown = 123

assertString(valor)
// apartir daqui tudo sera string





