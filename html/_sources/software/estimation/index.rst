===================
Módulo de Estimação
===================

Essa seção aborda os parâmetros e como utilizar o módulo de estimação.

O módulo de estimação serve para **calcular os parâmetros numéricos**, :math:`\beta` e :math:`p_{ref}` da equação para a pressão nos sólidos, e :math:`\Lambda` e :math:`k_0` da equação para a permeabilidade, constituintes da teoria constitutiva.

O cálculo dos parâmetros depende de um **resultado conhecido da evolução temporal do perfil de sedimentação** :math:`\varphi(z,t)`, normalmente obtidos a partir de experimentos.

PSO
^^^

Para estimar os parâmetros foi utilizado o algoritmo de **Particle Swarm Optimization (PSO)**.

O método consiste em criar um arranjo inicial de partículas, e calcular um erro individual denominado de função objetivo.

E iterar progressivamente em busca da **minimização da função objetivo**.

Parâmetros do PSO
*****************

- **Número de partículas:** O número de partículas no enxame. Mais partículas podem ajudar a explorar o espaço de busca de forma mais abrangente, mas também podem aumentar o tempo de computação.
  
- **Número de dimensões:** O número de dimensões no espaço de busca, que corresponde ao número de parâmetros no seu problema de otimização.
  
- **Peso de inércia:** Um parâmetro que equilibra o trade-off entre exploração e exploração. Um peso de inércia mais alto permite que as partículas se movam mais rapidamente pelo espaço de busca, promovendo a exploração, enquanto um peso de inércia mais baixo incentiva a exploração ao focar nas melhores soluções atuais.
  
- **Parâmetro cognitivo:** Um parâmetro que controla a influência da melhor posição pessoal de uma partícula em seu movimento. Ele governa a tendência da partícula de se mover em direção à sua melhor posição pessoal.
  
- **Parâmetro social:** Um parâmetro que controla a influência da melhor posição global no movimento de cada partícula. Ele governa a tendência da partícula de se mover em direção à melhor posição global encontrada pelo enxame.
  
- **Topologia:** Especifica a estrutura do enxame, determinando quais partículas influenciam o movimento de outras partículas. As topologias comuns incluem estrela, anel e aleatória.
  
- **Limites:** Define os limites para cada parâmetro no espaço de busca, restringindo o movimento das partículas a regiões viáveis.
  
- **Número máximo de iterações:** O número máximo de iterações ou gerações que o algoritmo executará antes de parar.

Arquivo de configuração
^^^^^^^^^^^^^^^^^^^^^^^

O único input para executar a rotina de estimação, é a descrição dos parâmetros de simulação e estimação, no mesmo arquivo.
Isso é feito através do arquivo de configuração, como por exemplo:

.. literalinclude:: /_static/software/estimation_config.yaml
    :caption: Arquivo de configuração de um processo de estimação de parâmetros
    :language: yaml

Uso
^^^

Todos os exemplos deste manual serão baseados no uso a partir de `Jupyter notebooks <https://jupyter.org/>`_.
Consultar o `notebook <estimation_example.ipynb>`_ referente ao exemplo para estimação de parâmetros.

Para automações de casos de teste, é conveniente poder rodar o software a partir da linha comando.
O comando para rodar o módulo de estimação a partir do terminal é:

.. code-block:: Bash

    poetry run python -m modules.estimation --c <CONFIG_PATH> --d <DATA_PATH> --o <OUTPUT_PATH>

O argumento `--c` indica o caminho para o arquivo de configuração da estimação, `--d` indica o caminho até os resultados de calibração, e `--o` indica o caminho de saída.

Estrutura dos resultados de calibração
**************************************

Para que seja corretamente carregado, os dados para os perfis de referência devem seguir algumas regras de formatação.

- Utilizar o formato .csv, com duas colunas: "t" para os intervalos de tempo, **em segundos**, e "concentration" para a coluna da concentração.
- API suporta diferentes tipos de separador, entretanto por padrão utiliza-se "," como separador entre colunas.
- Separar cada perfil em um arquivo

Depois de formatados, os arquivos são carregados a partir da especificação do arquivo de configuração.

Dados de saída
^^^^^^^^^^^^^^

Os dados de saída da estimação se encontram no caminho fornecido ao programa na variável `<OUTPUT_PATH>`.

Nessa pasta, são salvos os parâmetros utilizados por cada partícula em cada iteração do ciclo do PSO.
O formato de saída é uma tabela `.csv`, que contém a relação entre identificador da partícula, parâmetros utilizados e valor da função objetivo.

O resultado esperado segue o formato:

.. list-table:: Resultados da rotina de estimação de parâmetros
   :widths: 15 15 15 15 15 15 15
   :header-rows: 1

   * - sim_lbl
     - sim_id
     - f_obj
     - k0
     - delta
     - beta
     - p_ref
   * - sim_0
     - 0
     - 0.037079
     - 20.750728
     - 0.502287
     - 0.126178
     - 11.816403
   * - sim_1
     - 1
     - 0.032316
     - 24.709681
     - 0.598801
     - 0.155802
     - 69.425181
   * - sim_2
     - 2
     - 0.091844
     - 32.317797
     - 0.649955
     - 0.091361
     - 44.646439
   * - sim_3
     - 3
     - 0.025147
     - 26.961249
     - 0.512466
     - 0.144410
     - 85.989529
   * - sim_4
     - 4
     - 0.105951
     - 23.780054
     - 0.621423
     - 0.121908
     - 59.328319

.. toctree::
   :maxdepth: -1
   :hidden:

   Exemplo de estimação <estimation_example.ipynb>
   Análise dos resultados <estimation_analysis.ipynb>