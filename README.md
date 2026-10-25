# Apuração · 2º turno 2026

Dashboard interativo para acompanhar a apuração das eleições em tempo real, com dados da **API oficial de divulgação de resultados do TSE** (`resultados.tse.jus.br`).

Projeto de autoria de **Lucas Piau**. Projeto independente, sem vínculo com o TSE; apenas o TSE divulga o resultado oficial.

## O que tem
- Presidente (Brasil, 27 UFs e exterior) e Governador (estados com 2º turno)
- Placar, indicadores (válidos, brancos, nulos, comparecimento, abstenção), evolução do percentual e tabela por estado ordenável
- Atualização automática a cada 60 s (o cache da API é de ~50 s)
- Tema que muda conforme quem lidera (13 · PT / 22 · PL), caricaturas sorrindo/chorando e tela de vitória aos 100% apurados

## Como rodar
É um único `index.html`, sem build. Basta servir a pasta:

```sh
python3 -m http.server 8765
# abra http://localhost:8765
```

Para ver a tela de vitória antes do fim da apuração: `?demo=fim` e selecione "Brasil".

## API usada
`https://resultados.tse.jus.br/oficial/ele2026/<eleição>/dados/<uf>/<uf>-c<cargo>-e<eleição>-u.json`
(2º turno 2026: eleição `6258` = Presidente, `6260` = Governador). A lista de eleições está em `/oficial/comum/config/ele-c.json`.
