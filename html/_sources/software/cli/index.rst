=============
Interface CLI
=============

O software de sedimentação pode ser utilizado de diversas maneiras.
A arquitetura dos módulos permite **integrar o software** importando do pacote *modules*.
Os exemplos dos notebooks desta seção demonstram formas de uso do software de forma integrada.

Entretanto, alguns usuários podem utilizar a **aplicação via CLI** (*command line interface*).
Para ver quais comandos estão disponíveis:

.. code-block::
    
    poetry run python -m cli --help

Rodar simulação via CLI
^^^^^^^^^^^^^^^^^^^^^^^

O comando para rodar uma simulação a partir da aplicação CLI é:

.. code-block::
    
    poetry run python -m cli run-simulation

O aplicativo requisitará ao usuário alguns inputs, como o caminho de saída para salvar os resultados, e o caminho do arquivo de configuração.
Abaixo é possível consultar um exemplo de interação com a aplicação ao rodar uma simulação:

.. code-block::
    :emphasize-lines: 1,15

    PS A:\CERNN\Settling-Simulator> poetry run python -m cli run-simulation

    Entre com o caminho do arquivo de configuração: A:\CERNN\Settling-Simulator\fixtures\general_config.yaml
    Informe o caminho da pasta para salvar os resultados: ./out

    Vtps exportados ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:00:00

    Deseja exportar os resultados em vtp (vtkPolydata)? [y/n]: y
    Qual a frequência de export para vtkPolydata? (1): 100

    Vtps exportados ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:00:00

    Dados da simulação exportados ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:00:00

                Simulation Report
    ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━┓
    ┃ Propriedade               ┃    Valor    ┃
    ┡━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━┩
    │ Tempo total de simulação  │ 20.896137 s │
    │ Número de elementos       │     220     │
    │ Número de passos de tempo │    31536    │
    │ Modelo HPHT               │    False    │
    │ Domínio Escalonado        │    False    │
    └───────────────────────────┴─────────────┘

.. important::
    O processo que roda a simulação **será encerrado caso o usuário feche o terminal** onde o processo foi criado!

Para desvincular o processo do terminal, basta usar o comando abaixo, que desvincula o processo e redireciona a saída para um arquivo (válido para sistemas Unix):

.. code-block::
    
    setsid poetry run python -m modules.simulation --c <CONFIG_PATH> > output.log 2>&1

Rodar estimação via CLI
^^^^^^^^^^^^^^^^^^^^^^^

O comando para rodar o caso de uso de estimação de parâmetros a partir da aplicação CLI é:

.. code-block::
    
    poetry run python -m cli run-estimation

Assim como no caso da simulação, o aplicativo requisitará ao usuário alguns inputs, como o caminho de saída para salvar os resultados, e o caminho do arquivo de configuração.
Abaixo é possível consultar um exemplo de interação com a aplicação ao rodar a estimação de parâmetros:

.. code-block::
    :emphasize-lines: 1,7,17

    PS A:\CERNN\Settling-Simulator> poetry run python -m cli run-estimation

    Entre com o caminho do arquivo de configuração: A:\CERNN\Settling-Simulator\fixtures\estimation_config.yaml
    Informe o caminho da pasta para salvar os resultados: ./out/new_estimation

    Estimação completa! ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:00:00
                Estimation Report
    ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━┓
    ┃ Propriedade                     ┃  Valor   ┃
    ┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━┩
    │ Tempo total de estimação        │ 128.87 s │
    │ Tempo médio por simulação       │ 21.48 s  │
    │ Número de iterações             │    3     │
    │ Número de partículas            │    2     │
    │ Número de simulações executadas │    6     │
    └─────────────────────────────────┴──────────┘
    Best simulation parameters 
    ┏━━━━━━━━━━━━━━━━━┳━━━━━━━━┓
    ┃ Propriedade     ┃ Valor  ┃
    ┡━━━━━━━━━━━━━━━━━╇━━━━━━━━┩
    │ Função objetivo │ 0.1002 │
    │ sim_id          │   0    │
    │ f_obj           │  0.10  │
    │ k0 (m²)         │ 64.43  │
    │ delta           │  0.51  │
    │ beta            │  0.38  │
    │ p_ref (Pa)      │ 71.51  │
    └─────────────────┴────────┘

.. important::
    O processo que roda a estimação **será encerrado caso o usuário feche o terminal** onde o processo foi criado!

Para desvincular o processo do terminal, basta usar o comando abaixo, que desvincula o processo e redireciona a saída para um arquivo (válido para sistemas Unix):

.. code-block::
    
    setsid poetry run python -m modules.estimation --c <CONFIG_PATH> --d <DATA_PATH> --o <OUTPUT_PATH> > output.log 2>&1