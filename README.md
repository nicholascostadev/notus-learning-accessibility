# Notus Learning

## Acessibilidade

Feito para exemplificar a apresentação

Divido entre seções

### Tornando divs clicáveis, acessíveis

Cada exemplo é uma continuação do primeiro exemplo, sempre melhorando aos poucos

1. Div com click
2. Div com click + clique no teclado
3. Div com click + clique no teclado + possível focar com "TAB"
4. Div com click + clique no teclado + possível focar com "TAB" + role

### Ícones clicáveis (aria-label)

1. Tornando um botão que é um ícone, acessível, adicionando aria-label
2. Tornando um botão que é um ícone, acessível, adicionando texto para screen-readers

### Seções e sua importância

1. Duas `"divs"` que dividem conteúdo em duas partes, mostrando como funciona o leitor de tela nesse caso.
2. Duas `sections` que dividem o conteúdo em duas partes, mostrando como o leitor de tela identifica cada seção e como fica melhor a sua separação para uma pessoa que tenha que usar o leitor de tela.

### Modal acessível

1. Exemplo de um modal bem pensado pra acessibilidade.
   - Foco apenas internamente.
   - aria-label para o modal
   - role para o modal (role="dialog") pra mostrar como o leitor de tela deve interpretar esse elemento
   - aria-modal pra mostrar que ele se comporta como um modal [W3 docs](https://www.w3.org/TR/wai-aria-1.1/#aria-modal)

### Links utilizados para aprendizado

1. [W3](https://www.w3.org/WAI/fundamentals/accessibility-principles/)
2. [W3 aria-modal](https://www.w3.org/TR/wai-aria-1.1/#aria-modal)
3. [Aria by Mozilla](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)
4. [Github Eslint Plugin para acessibilidade](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y/tree/main/docs/rules)