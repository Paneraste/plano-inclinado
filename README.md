# Plano Inclinado Passo a Passo

![Visitas ao site](https://hits.sh/paneraste.github.io/plano-inclinado.svg?view=today-total&label=visitas%20ao%20site&color=1f4fd8)
![Visitas ao repositório](https://hits.sh/github.com/Paneraste/plano-inclinado.svg?view=today-total&label=visitas%20ao%20c%C3%B3digo&color=555555)

Simulação interativa de **diagrama de corpo livre no plano inclinado**, feita para aulas de Mecânica (Física I, Mecânica Geral, Dinâmica). Mostra as forças em ação, o que acontece com o corpo (sobe, desce, fica parado, patina, empina) e por quê, em linguagem que o aluno entende. Também traz um modo professor com as equações completas.

**Abrir agora (sem instalar nada):** https://paneraste.github.io/plano-inclinado/

É um único arquivo, `index.html`, sem instalação, sem servidor e sem dependências. Funciona offline: baixe e dê dois cliques.

---

## O que tem

| Cenário | O que mostra |
|---|---|
| **Modo professor** | Carro como corpo rígido em translação (α = 0): ΣFx = m·a, ΣFy = 0, ΣM<sub>G</sub> = 0, com os números da situação. Vetor m·a, medidas b, h e L, momentos em G. Inclui o **Exemplo 6/1 (Meriam & Kraige)**: caminhonete de 1500 kg, rampa de 10%, tração traseira. |
| **Bloco na rampa** | Peso, normal e atrito. Atrito estático e cinético, ângulo crítico (tanθ = μ), a massa não muda a aceleração. |
| **Carro na ladeira** | Acelerador, ponto morto, freio de mão, tração traseira, dianteira ou 4×4, tipo de piso e carga extra. Mostra a **transferência de carga** e quando as rodas patinam. |
| **Bondinho** | Cabine pendurada em um carrinho de duas rodas que corre sobre o cabo de apoio, puxada pelo cabo de tração. A cabine balança com a aceleração, e a roda de cima carrega mais (o contrário do carro). |

Em todos os cenários:
- **Experimentos prontos** com "o que observar" (um clique configura tudo).
- **Balanço de forças** (cabo de guerra): a parte do peso que puxa rampa abaixo × a força que empurra para cima, com o limite do atrito.
- **Etiquetas que não se sobrepõem**: um organizador afasta os rótulos e os liga à seta com uma linha-guia.
- Tema claro e escuro, tela cheia (bom para projetor) e layout para celular.

## Modelo físico (resumo)

- Ângulo θ, g = 9,81 m/s². Eixo x ao longo do plano e y perpendicular.
- **Carro**: ΣFy: N<sub>A</sub> + N<sub>B</sub> = mg·cosθ · ΣFx: F<sub>at</sub> − mg·senθ = m·a · ΣM<sub>G</sub>: N<sub>B</sub>(L−b) − N<sub>A</sub>·b + F<sub>at</sub>·h = 0.
  O atrito máximo é μ·N **só das rodas que puxam** (ou que freiam). Se a força pedida passa disso, a roda patina e vale μ<sub>k</sub>.
  Rampa máxima com velocidade constante: traseira tanθ = μ(L−b)/(L−μh) · dianteira tanθ = μb/(L+μh) · 4×4 tanθ = μ.
- **Bloco**: segura se mg·senθ ≤ μ<sub>s</sub>·N; senão desliza com μ<sub>k</sub>.
- **Bondinho**: T − mg·senθ = m·a · N<sub>A</sub> + N<sub>B</sub> = mg·cosθ · carrinho leve com ΣM no pino = 0 → N<sub>B</sub> − N<sub>A</sub> = 2·e·T/L. A cabine pendurada se alinha com a gravidade aparente (g − a).
- Não considera resistência ao rolamento, nem a do ar, nem a inércia das rodas.

## Como usar em aula

1. Abra o link (ou o `index.html`) no computador da sala e use **Tela cheia**.
2. Comece pelo **Bloco**, passe ao **Carro** e ao **Bondinho**, e use o **Modo professor** para escrever as equações junto com a turma.
3. Clique em um experimento, aperte **Soltar** e discuta a frase "o que observar".

## Como adaptar (para professores)

Tudo está no `index.html`, dentro do `<script>`. Pontos de ajuste:

| Quero mudar | Onde |
|---|---|
| Experimentos prontos (texto e valores) | objeto `EXPS` (uma lista por cenário: título, valores, texto "o que observar") |
| Valores iniciais de cada cenário | função `setTab` |
| Pisos e coeficientes de atrito | `PISO_BLOCO` e `PISO_CARRO` |
| Carga extra do carro | `CARGA` |
| Dimensões do bondinho (rodas, cabo, cabine) | `BONDE` |
| Faixas dos controles (mín./máx.) | função `buildControls` |
| Física | funções `solveBlock`, `solveCar` e `solveBonde` |
| Cores das forças e do tema | variáveis CSS no topo (`--cP` peso, `--cN` normal, `--cF` atrito, `--cT` cabo…) |

Não é preciso instalar nada: edite, salve e recarregue o navegador.

### Clonar

```bash
git clone https://github.com/Paneraste/plano-inclinado.git
```

Ou use **Code → Download ZIP** no GitHub, ou **Fork** para ter a sua própria cópia publicada no GitHub Pages (Settings → Pages → Deploy from branch → `main` / root).

## Créditos

- **Autor:** Arthur Vinagre, estudante de Engenharia Mecatrônica. Feito a partir da aula de Mecânica Geral II (cinética do corpo rígido em translação), em 2026-11.
- **Exemplo 6/1:** J. L. Meriam e L. G. Kraige, *Mecânica para Engenharia: Dinâmica*, 7ª ed., LTC.
- Desenvolvido com o auxílio do [Claude Code](https://claude.com/claude-code) (Anthropic).
- Fórmulas em LaTeX desenhadas com o [MathJax](https://www.mathjax.org/) 3.2.2 (licença Apache 2.0), copiado em `vendor/mathjax/` para funcionar offline.
- Fontes [IBM Plex Sans e IBM Plex Mono](https://github.com/IBM/plex) (SIL Open Font License), carregadas do Google Fonts. Offline, o navegador usa a fonte do sistema.

Se usar em aula ou adaptar, uma menção ao projeto é bem-vinda. Sugestões e correções: abra uma *issue* ou um *pull request*.

## Estatísticas e privacidade

O site publicado conta visitas para o autor acompanhar o uso do projeto:
- **Contador público** (hits.sh): visitas de hoje e total, no rodapé e no topo deste README.
- **Estatísticas anônimas** (GoatCounter, código aberto): páginas, origem das visitas, país, navegador e tamanho de tela, além de eventos de uso: qual cenário foi aberto (`aba/…`), qual experimento foi clicado (`experimento/…`), quando a simulação foi solta (`soltar/…`), troca de tema e tela cheia.

Não há cookies e nada do que é digitado ou ajustado é enviado. Só conta no endereço `*.github.io`: a cópia local (`index.html` aberto no computador) não envia nada. Se você publicar a sua própria cópia, troque ou apague a linha `data-goatcounter` no início do `index.html` e a linha do `hits.sh` no script.

## Licença

[MIT](LICENSE): pode usar, copiar, modificar e redistribuir, inclusive em aulas e materiais didáticos, mantendo o aviso de copyright.
