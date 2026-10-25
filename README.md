# Apuração ao vivo · 2º turno 2026

Dashboard interativo que acompanha a apuração das eleições em tempo real, lendo diretamente a **API oficial de divulgação de resultados do TSE**. Feito do zero, em um único arquivo, sem framework e sem build.

**Ao vivo:** https://piaulucas.github.io/dashboard-eleicao-2026/

![Tema Lula na frente](docs/01-tema-lula.jpg)

> Projeto independente, sem vínculo com o TSE nem com qualquer campanha. Apenas o TSE divulga o resultado oficial. As caricaturas foram geradas com IA. O visual partidário (vermelho do 13, verde e amarelo do 22) é um exercício de design de interface.

## O que ele faz

- **Placar em tempo real** para Presidente (Brasil, 27 UFs e exterior) e Governador (estados com 2º turno), com atualização automática a cada 60 s.
- **Interface que muda conforme quem lidera**: fundo, marca d'água (13 ou 22), cores e caricaturas trocam sozinhos. Quem lidera aparece sorrindo com a faixa; quem está atrás, chorando.

  ![Tema Flávio na frente](docs/02-tema-flavio.jpg)

- **Mapa do Brasil por estado**, colorido pelo partido de quem lidera (PT vermelho, PL azul), com intensidade proporcional à margem, tooltip e clique para detalhar.

  ![Mapa por estado](docs/03-mapa.jpg)

- **Tabela por estado** ordenável, **gráfico de evolução** do percentual e indicadores (válidos, brancos, nulos, comparecimento, abstenção).
- **Quadro de campeão** que só aparece com **100% das seções totalizadas**: tela cheia com confete e, depois, um card com o vencedor e o derrotado.

  ![Quadro de campeão (simulação)](docs/04-quadro-campeao-simulacao.jpg)

  *Print gerado no modo de demonstração (`?demo=fim`), que simula 100% apurado. Não é um resultado real.*

- **Responsivo**, com modo claro e escuro automáticos.

  ![Versão celular](docs/06-celular.jpg)

## Decisões técnicas e desafios

- **Descoberta da API.** O TSE não documenta os endpoints do 2º turno de 2026. Descobri o formato (`/oficial/ele2026/<eleição>/dados/<uf>/<uf>-c<cargo>-e<eleição>-u.json`) lendo o JavaScript do site oficial, e validei os números contra o próprio site e o Google.
- **Sem back-end.** A API do TSE libera CORS, então o navegador consulta direto. O cache da API é de cerca de 50 s, por isso o intervalo de 60 s.
- **Dados defasados e inconsistentes.** O TSE chegou a ficar mais de 1 h sem publicar (votação prorrogada), e os arquivos por estado são publicados em momentos diferentes do total nacional. O dashboard mostra a hora de geração do dado (horário de Brasília) e um aviso de defasagem, em vez de fingir que está "ao vivo".
- **Regra do campeão.** O vencedor só é declarado quando `seções totalizadas ≥ total de seções`, sem arredondamento de percentual.
- **Mapa sem biblioteca.** A malha de estados vem da API do IBGE e é projetada e desenhada em SVG puro no próprio código, com cache local.
- **Cores por partido** definidas por variáveis CSS, com variantes para o modo escuro.

## Tecnologias

HTML, CSS e JavaScript puros · SVG · API de resultados do TSE · API de malhas do IBGE · GitHub Pages.

## Como rodar

É um único `index.html`:

```sh
python3 -m http.server 8765
# abra http://localhost:8765
```

`?demo=fim` simula 100% apurado, para ver a tela de vitória.

## Autoria

Projeto de autoria de **Lucas Piau**.
