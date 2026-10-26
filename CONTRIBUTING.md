# Como contribuir

Obrigado pelo interesse! Sugestões, correções e melhorias são bem-vindas. Ao participar, você concorda com o [Código de Conduta](CODE_OF_CONDUCT.md).

## Antes de começar

- **Bug ou ideia?** Abra uma [issue](../../issues/new/choose) descrevendo o que viu ou propõe. Para bugs, informe navegador, aparelho e, se possível, um print.
- **Dúvida sobre um número?** Compare com o site oficial ([resultados.tse.jus.br](https://resultados.tse.jus.br)). O dashboard só exibe o que o TSE publica; se o número bater com o TSE, o dado está correto.

## Rodando localmente

O projeto é um único `index.html`, sem build nem dependências:

```sh
python3 -m http.server 8765
# abra http://localhost:8765
```

Parâmetros úteis para testar:

- `?t=1` abre no 1º turno;
- `?demo=fim` simula 100% apurado (tela de vitória);
- `?demo=eleito` simula governadores eleitos (aviso no topo).

Teste sempre em tela larga e em celular (≈ 390 px), nos **dois turnos**, em **Presidente e Governador**, e nos modos claro e escuro.

## Enviando um pull request

1. Faça um *fork* e crie uma branch (`git checkout -b minha-melhoria`).
2. Mantenha o estilo do código existente (JavaScript puro, sem frameworks, comentários curtos em português).
3. Descreva no PR o que mudou e por quê, com prints se for visual.
4. Confira que a página abre sem erros no console e que os dados continuam carregando.

## Regras do projeto

- **Dados:** vêm sempre da API oficial do TSE (e da malha do IBGE para o mapa). Não inclua números "fixos" ou de outras fontes sem sinalizar claramente.
- **Neutralidade:** o dashboard não pode favorecer candidato nenhum na apuração dos números. O visual por partido é só apresentação.
- **Regra do "matematicamente eleito":** declarar um vencedor errado é o pior erro possível. Mudanças em `matematicoEleito` precisam manter a garantia do pior cenário (todos os eleitores restantes votando no adversário) e vir com a explicação do raciocínio e exemplos reais no PR.
- **Gênero e identidade:** não deduza gênero de candidatos para desenhar personagens; sem o dado, use as iniciais.
- **Imagens:** não envie imagens de pessoas reais sem licença clara de uso. As caricaturas atuais são geradas por IA e não estão cobertas pela MIT (veja o [README](README.md#licença)).
- **Licença:** ao contribuir, você concorda que seu código será licenciado sob a [MIT](LICENSE).
