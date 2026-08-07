# Planee Lab IA — site de apresentação

Página única de apresentação da empresa. **Não é uma página de captação:** não tem formulário,
botão de contato nem redes sociais. O objetivo é a impressão que fica em quem abre o link
depois de uma conversa, indicação ou reunião.

## Como ver

Abra o arquivo `index.html` no navegador — é só dar duplo clique. Não precisa de servidor,
instalação nem internet (a única coisa que vem de fora é a fonte).

Se preferir servir localmente:

```bash
python -m http.server 8123
```

E acesse `http://localhost:8123`.

## O que observar

O site é uma narrativa em sete cenas, contada pela rolagem. Vale rolar **devagar**:
quase tudo está amarrado à posição do scroll, então rolar rápido passa por cima das transições.

| # | Cena | O que acontece |
|---|------|----------------|
| 1 | Caos → ordem | Fragmentos do trabalho manual se alinham numa grade e o título emerge |
| 2 | Manifesto | O texto compila caractere a caractere, de código para frase |
| 3 | A fábrica | Itens crus atravessam o símbolo da Planee e saem como produtos |
| 4 | Anatomia | As cinco camadas de todo sistema, com o dado percorrendo a pilha |
| 5 | A corrida | A mesma tarefa, manual e automatizada, lado a lado |
| 6 | Modelos de trabalho | As formas de nos envolvermos num projeto |
| 7 | Assinatura | A logo se desenha e fecha o ciclo |

A **cena 5 é a única que roda sozinha**, no tempo dela, sem depender da rolagem — a seção
sobre coisas que funcionam sem você é a única que funciona sem você. Ao chegar nela,
pare e assista por uns 15 segundos até o ciclo completar.

## O que ainda não está fechado

- **Os textos são propostas**, não versão final — inclusive os doze passos da cena da corrida.
  Se o público-alvo não fecha relatório mensal, essa tarefa deve ser trocada por algo que ele
  reconheça no próprio dia a dia.
- **O símbolo da logo é uma aproximação** desenhada em SVG a partir da imagem da marca.
  Precisa ser substituído pelo arquivo oficial (aparece em quatro lugares).
- **A fonte Satoshi** carrega do Fontshare. Hospedá-la junto com o site deixaria mais rápido
  e removeria a última dependência externa.

## Detalhes técnicos

Arquivo único, ~40 KB, sem nenhuma biblioteca. As animações são escritas à mão em JavaScript:
o progresso de cada cena vem de `getBoundingClientRect`, suavizado por interpolação dentro de um
`requestAnimationFrame`, e a fixação das seções usa `position: sticky` nativo. Sem GSAP, sem
Lenis, sem build, sem dependências para instalar.

Funciona em telas a partir de 360 px de largura, respeita `prefers-reduced-motion`
(as animações desligam e a página vira estática) e todos os textos passam no contraste mínimo
de acessibilidade nos dois temas.
