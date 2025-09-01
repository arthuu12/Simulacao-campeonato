🏆 Simulação de Campeonato Brasileiro
Este projeto oferece uma simulação estatística completa do Campeonato Brasileiro de Futebol (Série A), utilizando a distribuição de Poisson para gerar resultados de partidas de forma realista. O simulador considera atributos individuais para cada time, como força de ataque, defesa e um sistema de "confiança" que varia dinamicamente com os resultados, tornando a competição imprevisível.

📋 Índice
Funcionalidades

Como Funciona

Tecnologias Utilizadas

Como Executar

Estrutura do Código

Exemplo de Saída

✨ Funcionalidades
Atributos de Time: Cada clube possui valores de ataque e defesa pré-definidos.

Fator Casa: Times jogando em casa recebem um bônus em seus atributos de ataque e defesa.

Sistema de Confiança: A confiança de um time aumenta com vitórias e diminui com derrotas, impactando diretamente seu desempenho em campo.

Simulação Estatística: Os gols de cada partida são calculados usando a distribuição de Poisson, com base na força relativa dos times.

Tabela de Classificação: Ao final da simulação, uma tabela completa é gerada, com pontuação, vitórias, empates, derrotas, gols e saldo de gols, seguindo as regras de desempate.

⚙️ Como Funciona
O placar de cada jogo é determinado pela geração de um número aleatório a partir de uma distribuição de Poisson. A média (λ - lambda) dessa distribuição é calculada para cada time antes da partida, com base nos seguintes fatores:

Força de Ataque vs. Força de Defesa: A lambda de um time é proporcional à sua força de ataque e inversamente proporcional à força de defesa do adversário.

Bônus de Jogo em Casa: O time mandante recebe um incremento em seus atributos.

Confiança Dinâmica: O nível de confiança atual do time também ajusta seus valores de ataque e defesa, tornando sequências de vitórias ou derrotas um fator relevante.

Após cada partida, as estatísticas dos times (pontos, gols, etc.) e seus níveis de confiança são atualizados para os jogos seguintes.

🛠️ Tecnologias Utilizadas
Python: Linguagem principal do projeto.

SciPy: Biblioteca utilizada para os cálculos estatísticos com a distribuição de Poisson (scipy.stats.poisson).

Google Colab / Jupyter Notebook: Ambiente utilizado para desenvolver e executar o código.

▶️ Como Executar
Ambiente: O projeto foi projetado para rodar em um ambiente como Google Colab ou qualquer sistema com Python e as bibliotecas necessárias instaladas.

Instalação de Dependências: A única dependência externa é a scipy, que pode ser instalada com o pip:

Bash

pip install scipy
Execução: Abra o notebook (Simulacao_Brasileirao_IA.ipynb) e execute todas as células em sequência. A simulação será iniciada e, ao final, a tabela de classificação será impressa.

📂 Estrutura do Código
O código é organizado nas seguintes partes:

Classe Time: Modela cada time, armazenando seus atributos (ataque, defesa, confiança) e estatísticas no campeonato (pontos, vitórias, gols).

calcular_lambdas_gols(time_casa, time_fora): Calcula a média de gols esperada para cada time em uma partida.

simular_jogo(time_casa, time_fora): Simula uma única partida usando a distribuição de Poisson para determinar o placar.

atualizar_tabela(...): Atualiza as estatísticas e a confiança dos times após um jogo.

exibir_tabela(times): Formata e imprime a tabela de classificação final, ordenando os times pelos critérios de desempate.

simular_campeonato(times): Orquestra toda a simulação, gerando todos os jogos de ida e volta e chamando as outras funções.

📊 Exemplo de Saída
Ao final da execução, o programa exibe a classificação completa do campeonato:

======================================== TABELA DE CLASSIFICAÇÃO FINAL ========================================
Pos Time                 P    V    E    D    GP   GC   SG   Conf
----------------------------------------------------------------------------------------------------
1   Palmeiras            76   23   7    8    66   34   32   8.0
2   Atlético-MG          68   20   8    10   63   40   23   10.0
3   Internacional        66   18   12   8    54   41   13   8.0
4   Flamengo             65   17   14   7    56   36   20   10.0
5   Vitória              65   17   14   7    59   43   16   9.0
... (restante da tabela)
====================================================================================================

SIMULAÇÃO DO CAMPEONATO FINALIZADA!
