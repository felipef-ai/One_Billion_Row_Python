# Um Bilhão de Linhas
## Desafio BIG DATA

## INTRODUÇÃO

O objetivo deste projeto é demonstrar como processar eficientemente um arquivo de dados massivo contendo 1 bilhão de linhas. 
Especificamente para calcular estatísticas (Incluindo agregação e ordenação que são operações pesadas) utilizando Python. 

Este desafio foi inspirado no [The One Billion Row Challenge](https://github.com/gunnarmorling/1brc), originalmente proposto para Java.

## SOBRE O ARQUIVO
O arquivo de dados consiste em medições de temperatura de várias estações meteorológicas. Cada registro segue o formato `<string: nome da estação>;<double: medição>`, com a temperatura sendo apresentada com precisão de uma casa decimal.
Você encontra o arquivo weather_stations.csv e através dele, com Python, criaremos o measurements.txt que resultará 1Bilhão de linhas (~20GB).

Aqui estão dez linhas de exemplo do arquivo:

```
Hamburg;12.0
Bulawayo;8.9
Palembang;38.8
St. Johns;15.2
Cracow;12.6
Bridgetown;26.9
Istanbul;6.2
Roseau;34.4
Conakry;31.2
Istanbul;23.0

```
## DESAFIO

O desafio é desenvolver um programa Python capaz de ler esse arquivo e calcular a temperatura mínima, média (arredondada para uma casa decimal) e máxima para cada estação, exibindo os resultados em uma tabela ordenada por nome da estação.

| station      | min_temperature | mean_temperature | max_temperature |
|--------------|-----------------|------------------|-----------------|
| Abha         | -31.1           | 18.0             | 66.5            |
| Abidjan      | -25.9           | 26.0             | 74.6            |
| Abéché       | -19.8           | 29.4             | 79.9            |
| Accra        | -24.8           | 26.4             | 76.3            |
| Addis Ababa  | -31.8           | 16.0             | 63.9            |
| ...          | ...             | ...              | ...             |
| Yangon       | -23.6           | 27.5             | 77.3            |
| Yaoundé      | -26.2           | 23.8             | 73.4            |
| Zagreb       | -39.2           | 10.7             | 58.1            |
| Zanzibar City| -26.5           | 26.0             | 75.2            |
| Zürich       | -42.0           | 9.3              | 63.6            |
| Ürümqi       | -42.1           | 7.4              | 56.7            |
| İzmir        | -34.4           | 17.9             | 67.9            |

## NECESSIDADES

Para executar os scripts deste projeto, você precisará das seguintes bibliotecas:

* Polars: `0.20.3`
* DuckDB: `0.10.0`
* Dask[complete]: `^2024.2.0`

## RESULTADOS

Os testes foram realizados em um laptop equipado com um processador Corei7 Intel e 16GB de RAM. As implementações utilizaram abordagens com Python, Pandas, Dask e DuckDB. Utilizei o VsCode e o Git Bash em sistema operacional Windows para esse projeto. Os resultados de tempo de execução para processar o arquivo de 1 bilhão de linhas são apresentados abaixo:

| Implementação   |    Tempo    | Clasificação |
| -------------   | ----------- | ------------ |
| Python + Duckdb | 49.83 sec   | 1º Lugar     |
| Python + Dask   | 376.48 sec  | 2º Lugar     |
| Python + Pandas | 6003.14 sec | 3º Lugar     |
| Python (somente)| Sem sucesso | 4º lugar     |   
 

## CONCLUSÃO

Este desafio evidenciou a eficácia de diversas bibliotecas Python na manipulação de grandes volumes de dados. Enquanto métodos tradicionais, como somente o Python e até mesmo Python + Pandas, exigiram estratégias elaboradas para processar dados em lotes, bibliotecas como Dask e DuckDB se destacaram pela eficiência e simplicidade, graças à sua capacidade nativa de distribuir dados em streaming. Entre elas, o DuckDB apresentou o melhor desempenho, alcançando o menor tempo de execução devido à sua estratégia otimizada de processamento.

Esses resultados reforçam a importância de escolher a ferramenta certa para a análise de dados em larga escala. Eles demonstram que, com as bibliotecas adequadas, Python continua sendo uma solução poderosa e versátil para enfrentar desafios de big data.

## DIÁRIO DE BORDO

Para executar este projeto e reproduzir os resultados:

1. Clone esse repositório;
2. Definir a versao do Python usando o `pyenv local 3.13.1`;
3. Execute o comando `poetry env use 3.13.1`, `poetry install --no-root` e `poetry lock --no-update`;
4. Execute o comando `python src/create_measurements.py` para gerar o arquivo de teste;
5. Tenha paciência e vá fazer um café, vai demorar uns 10 minutos para gerar o arquivo;
6. Certifique-se de instalar as versões especificadas das bibliotecas;
7. Execute os scripts `python src/using_python.py`, `python src/using_pandas.py`, `python src/using_dask.py` e `python src/using_duckdb.py` através de um terminal ou ambiente de desenvolvimento que suporte Python.

## AGRADECIMENTOS

Ao Prof. Luciano Vasconcelos da Jornada de Dados e todos os colaboradores desse projeto.
Saiba mais em https://suajornadadedados.com.br/
Em pouco tempo de estudo, porém, com grande dedicação, consigui enfrentar todos os "Bugs", realizar os "Debugs", finalizar e formalizar esse primeiro projeto.
Este projeto destaca a versatilidade do ecossistema Python para tarefas de processamento de dados, oferecendo valiosas lições sobre escolha de ferramentas para análises em grande escala.