Any
O tipo mais famoso de todos e que nao deve nunca ser usado

Ele pode ser associado ou se associar a qualquer coisa, ele é como se estivesse desligando o typescript

O objetivo da sua criação, foi conseguir migrar codigos legados que nao utilizam tipo

tsconfig:
noImplicityAny -> Da um erro de compilação sempre que o typescript infere qualquer tipo para any

noImplicityAny: true
function (x) {
    console.log(x)
}  // Ira dar erro por que trypescript inferira any para x, ja que nao te nenhum tipo explicito


noImplicityAny: false
function (x) {
    console.log(x)
}  // nao dara erro por que o parametro no tsconfig esta false

EVANGELIZE SUA GALERA PARA NAO USAR ANY NUNCA
