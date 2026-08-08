# Planee Lab IA — site institucional

Página única de apresentação da empresa. **Não é uma página de captação:** não tem
formulário, botão de contato nem redes sociais. O objetivo é a impressão que fica em
quem abre o link depois de uma conversa, indicação ou reunião.

## Como ver

Abra `index.html` no navegador — duplo clique basta. Não precisa de servidor nem de
instalação. A única coisa que vem de fora é a fonte Satoshi.

Para servir localmente:

```bash
python -m http.server 8123
```

## Estrutura

Nove blocos, na ordem canônica de sites institucionais de tecnologia, extraída da
análise de cinco referências do setor (Tryolabs, Ateliware, Objective, Zup, Codeminer42):

| # | Bloco | Função |
|---|-------|--------|
| 01 | Autodefinição | O que a empresa é, em uma frase |
| 02 | O cenário | Ocupa a posição que nas referências é de prova social |
| 03 | Áreas de atuação | As quatro frentes |
| 04 | Princípios de engenharia | Autoridade por critério |
| 05 | Metodologia | Do diagnóstico à operação |
| 06 | Tecnologia | O que sustenta as entregas |
| 07 | A empresa | Por que laboratório |
| 08 | Modelos de atuação | Ocupa a posição do contato |
| 09 | Encerramento | Marca |

Como não há clientes citáveis nem métricas próprias divulgáveis, o bloco 02 usa dados
públicos de mercado — Asana, McKinsey e Gartner — com a fonte visível na página. Eles
montam o problema; os princípios do bloco 04 são a resposta.

## Design

Preto sobre dourado sobre a tipografia Satoshi. O dourado (`#C9A227`) aparece **apenas
onde a página indica estado ativo**: barra de progresso, linha da metodologia, marcadores
acesos, espinha dos princípios, filete do card sob o cursor e as fontes dos dados. Títulos,
texto e números permanecem em branco-osso — se tudo recebe cor, nada é destacado.

A base é preta por necessidade técnica, não só estética: esse dourado sobre branco fica em
2,4:1, abaixo do mínimo legível. Sobre preto, 8,3:1.

## Movimento

Texto revela na entrada. **A estrutura é amarrada à rolagem** — avança e retrocede com o
dedo: os números contam e descontam, a espinha dos princípios se desenha, a linha da
metodologia atravessa acendendo cada etapa, as colunas deslizam em parallax e a marca do
rodapé é revelada até fechar exatamente no fim da página.

Com `prefers-reduced-motion` ativo, ou quando não há rolagem possível (janela mais alta que
o conteúdo, ou a página dentro de um quadro esticado), tudo vai direto ao estado final.

## A marca

`planee-marca.svg` foi vetorizado a partir do PNG original por traçado de contorno, com
98,65% de sobreposição contra a máscara de origem. Proporção 100 × 125,84. Usa
`fill="currentColor"`, então herda a cor do CSS — é assim que ela aparece clara na barra e
dourada na marca-d'água.

## Detalhes técnicos

Arquivo único, ~33 KB, sem nenhuma biblioteca. Animações em JavaScript puro: progresso por
`getBoundingClientRect` dentro de um `requestAnimationFrame`, revelações por
`IntersectionObserver`. Sem build, sem dependências para instalar.

Responsivo a partir de 360 px. Contraste conferido: texto principal 17,9:1, apoio 6,2:1,
dourado 8,3:1 — todos acima do mínimo de acessibilidade.
