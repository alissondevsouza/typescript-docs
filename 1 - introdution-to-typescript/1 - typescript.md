# O que é TypeScript?

TypeScript é uma linguagem de programação desenvolvida pela Microsoft em 2012, que adiciona tipagem estática opcional ao JavaScript e melhora a qualidade do código. Ele é um superset de JavaScript, o que significa que todo código JavaScript válido também é válido em TypeScript.

- **Criador**: Anders Hejlsberg (também responsável pelo C# e Delphi).
- **Natureza**: TypeScript não é uma linguagem separada, mas sim uma extensão do JavaScript. Ele melhora a experiência do desenvolvedor sem alterar a execução no navegador ou em runtimes.


## Principais Benefícios do TypeScript
✅ **Tipagem Estática**: Permite detectar erros em tempo de desenvolvimento, reduzindo bugs em produção.  
✅ **Melhor Autocompletar (IntelliSense)**: Oferece sugestões inteligentes no editor, aumentando a produtividade.  
✅ **Suporte a Orientação a Objetos**: Permite o uso de interfaces, classes, herança e modificadores de acesso.  
✅ **Código Mais Seguro e Manutenível**: Ajuda a evitar erros comuns e melhora a legibilidade do código.  
✅ **Facilidade na Refatoração**: Com tipagem estática e boas ferramentas, é mais fácil modificar e escalar projetos grandes.  
✅ **Compatibilidade com JavaScript**: Pode ser adotado gradualmente em projetos existentes.  


## Objetivo do TypeScript
O TypeScript foi criado para resolver problemas de escala do JavaScript, tornando-o mais seguro e previsível. Em projetos grandes, a falta de tipagem no JavaScript pode levar a bugs difíceis de identificar e manter. O TypeScript reduz esse problema, garantindo que os desenvolvedores escrevam código mais confiável.

## Compilação e Tipagem
- O TypeScript não é interpretado diretamente pelos navegadores ou pelo Node.js. Ele precisa ser transpilado para JavaScript puro.
- O **TSC (TypeScript Compiler)** é o compilador oficial usado para converter TypeScript em JavaScript.
- A tipagem ocorre apenas em tempo de desenvolvimento/compilação, ou seja, não há verificação de tipos em tempo de execução.

### 📌 Exemplo de código TypeScript e sua conversão para JavaScript:
#### Código TypeScript:
```typescript
function soma(a: number, b: number): number {
  return a + b;
}
```

#### Código gerado em JavaScript após a compilação:
```javascript
function soma(a, b) {
  return a + b;
}
```

A tipagem (`: number`) desaparece no código final, pois o JavaScript não tem suporte nativo a tipos.

## Runtimes que suportam TypeScript
O TypeScript não é executado diretamente, mas pode ser rodado em vários ambientes que suportam JavaScript:
- **Node.js**: O runtime mais popular para execução de JavaScript no back-end.
- **Deno**: Uma alternativa ao Node.js que já possui suporte nativo ao TypeScript.
- **Bun**: Um runtime mais rápido que também suporta TypeScript.
- **Browsers**: TypeScript precisa ser compilado para JavaScript antes de ser executado em navegadores.

---

## Ferramentas e Ecossistema
TypeScript possui um ecossistema rico e pode ser usado com diversas ferramentas populares:
- **Frameworks Frontend**: React, Angular, Vue.js.
- **Frameworks Backend**:  Node.js, Nest.js.
- **Compiladores Alternativos**: esbuild, Babel (com preset TypeScript).
- **Ferramentas de Testes**: Jest, Mocha, Cypress.

