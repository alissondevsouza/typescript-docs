Arrays

É uma serie de valores em uma lista

Pode ser de um unico tipo ou de varios tipos

const strings: string[] = ['a', 'b', 'c']
const numbers: Array<number> = [1, 2, 3, 4]  // generics
const booleans: boolean[] = [true, false, true]

const anys: any[] = [1, 'string', undefined, null]

const objects: object[] = [{a: 1}, {b: 2}]

const objectsLiterais: { name: string }[] = [{ name: 'alisson' }, { name: 'Lais' }]

cons arrays: string[][] = [['a', 'b'], ['c', 'd']]
cons arrays: Array<Array<string>> = [['a', 'b'], ['c', 'd']]

numbers.push(2)
strings.push('teste')
arrays.push(['e'])

numbers.pop()
numbers[0]
numbers.map()


const nomes = ['Maria', 'Joao', 'Pedro']    // Typescrit ia inferir que é um array de string


const multArray: (string | number)[] = ['alisson', 30]

reandolny arrays: São arrays somente de leituras

const readOnly: readonly string[] = ['a', 'b', 'c']
reasOnly.push() // Erro nao existe por que ele é readonly, nao existe metodos que modificam o array
readOnly[0]  // Isso funciona, pois nao modifica o array


type StringOrNumber = (string|number)[]
const arr: StringOrNumber = ['a', 2]

const arr: StringOrNumber[] = [['a'], ['2']]



