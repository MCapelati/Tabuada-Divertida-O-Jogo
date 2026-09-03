# Tabuada Divertida — O Jogo ✖️🌈

Um joguinho web para ajudar crianças (por volta dos 10 anos) a **decorar a tabuada de 2 a 9**
de um jeito leve e divertido.

👉 **Jogue online:** <https://claude.ai/code/artifact/8bb7ed18-dfde-41fd-b070-f5c6a911b5d5>

## Por que este aplicativo existe

Decorar a tabuada costuma ser uma tarefa repetitiva e sem graça — lista de contas, repetição
em voz alta, folha de exercícios. A ideia aqui foi transformar esse treino em uma brincadeira
curta, com recompensa imediata:

- **Rapidez vira pontos.** Cada pergunta começa com 60 segundos e os segundos que sobram quando
  a criança acerta viram pontuação. Isso incentiva a *lembrar* a resposta em vez de contar nos
  dedos, que é justamente o objetivo de "decorar".
- **Sessões curtas.** São 10 perguntas por rodada. Dá para jogar em poucos minutos, várias
  vezes ao dia, sem cansar.
- **Erro não pune, ensina.** Ao errar (ou deixar o tempo acabar), o jogo mostra a conta correta
  antes de seguir para a próxima.
- **Visual convidativo.** Cores em tom pastel, fontes grandes e arredondadas, animações suaves —
  pensado para o público infantil, não para uma planilha de escola.
- **Sem cadastro, sem dados salvos.** Abriu, clicou em "Começar", jogou. Cada visita recomeça do
  zero e o recorde vale só para a sessão atual. Nada é armazenado.

## Como jogar

1. Clique em **Começar** (o contador só dispara aí).
2. Aparece uma conta, por exemplo `7 × 5 = ?`.
3. Escolha entre as 5 opções — clicando/tocando ou pelas **teclas 1 a 5**.
4. Quanto mais rápido acertar, mais pontos.
5. Ao fim das 10 perguntas, veja seu placar e escolha jogar de novo.

## Como executar localmente

Não há build, dependências nem servidor. O aplicativo inteiro é o `index.html`.

```
# Windows
start index.html
```

Ou simplesmente abra o arquivo `index.html` no navegador.

## Tecnologia

HTML, CSS e JavaScript puros, tudo em um único arquivo. A única dependência externa é a fonte
[Baloo 2](https://fonts.google.com/specimen/Baloo+2) via Google Fonts, com alternativa local
caso não haja internet.

## Licença

Uso livre para fins educativos.
