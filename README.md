# 🏆 Simulação de Campeonato Brasileiro com IA

## Visão Geral

Este projeto é um simulador do Campeonato Brasileiro de futebol que utiliza um modelo estatístico para prever os resultados das partidas. O código define atributos para cada time (ataque, defesa, confiança) e usa a distribuição de Poisson para gerar placares realistas, culminando em uma tabela de classificação final.

## Problema

Simular uma temporada completa (380 jogos) do campeonato, onde o resultado de cada partida é influenciado pela força relativa dos times, o mando de campo e um fator de "confiança" dinâmico, para então gerar a classificação final.

## Tecnologias Utilizadas

* **Python:** Linguagem de programação principal.
* **SciPy:** Biblioteca utilizada para o cálculo da distribuição de Poisson (`poisson.rvs`).
* **Google Colab:** Ambiente de notebook para desenvolvimento e execução.

## Estrutura do Código

O notebook é organizado de forma sequencial e modular, com as seguintes etapas:

1.  **Setup do Ambiente:**
    * Importação das bibliotecas `random` e `scipy.stats.poisson`.

2.  **Definição da Classe `Time`:**
    * A classe `Time` é o molde para cada clube.
    * **Atributos Iniciais:** `nome`, `ataque`, `defesa`, `confianca`.
    * **Atributos de Desempenho:** `pontos`, `vitorias`, `empates`, `derrotas`, `gols_pro`, `gols_contra`.
    * **Controle de Mando:** A propriedade `jogando_em_casa` é usada para aplicar bônus durante a simulação.

3.  **Lógica da Simulação:**
    * **`calcular_lambdas_gols(time_casa, time_fora)`:**
        * Esta é a função central que define a média de gols (lambda) esperada para cada time na partida.
        * Aplica um bônus de ataque e defesa para o time da casa.
        * Ajusta a força dos times com base no atributo `confianca`.
        * Retorna as médias de gols para o time da casa e o visitante.
    * **`simular_jogo(time_casa, time_fora)`:**
        * Chama `calcular_lambdas_gols` para obter as médias.
        * Utiliza `poisson.rvs(mu=lambda)` para sortear o número de gols de cada time.
        * Retorna o placar final da partida.
    * **`atualizar_tabela(...)`:**
        * Recebe os times e o placar do jogo.
        * Atualiza pontos, vitórias/empates/derrotas e estatísticas de gols.
        * Ajusta a `confianca` dos times: +1 para o vencedor, -1 para o perdedor.

4.  **Execução e Visualização:**
    * **`simular_campeonato(times)`:**
        * Cria a lista de todos os 380 jogos (ida e volta).
        * Embaralha a ordem dos jogos com `random.shuffle()`.
        * Itera sobre cada jogo, chamando `simular_jogo` e `atualizar_tabela`.
    * **`exibir_tabela(times)`:**
        * Ordena a lista final de times usando os critérios de desempate (pontos, saldo de gols, gols pró).
        * Imprime a tabela de classificação final de forma formatada.

