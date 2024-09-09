===================
Módulo de Simulação
===================

Essa seção traz instruções de como executar uma simulação.

Arquivo de configuração
^^^^^^^^^^^^^^^^^^^^^^^

O único input para executar uma simulação, é a descrição dos parâmetros de entrada.
Isso é feito através do arquivo de configuração, como por exemplo:

.. literalinclude:: /_static/software/general_config.yaml
    :caption: Arquivo de configuração da simulação do caso de validação Rocha et. al (2020)
    :language: yaml

Uso
^^^

Todos os exemplos deste manual serão baseados no uso a partir de `Jupyter notebooks <https://jupyter.org/>`_.
Consultar o `notebook <simulation_example.ipynb>`_ referente ao exemplo de uma simulação.

Para automações de casos de teste, é conveniente poder rodar o software a partir da linha comando.
O comando para rodar o módulo de simulação a partir do terminal é:

.. code-block:: Bash

    poetry run python -m modules.simulation --c <CONFIG_PATH>

O argumento `--c` indica o caminho para o arquivo de configuração da simulação.

Dados de saída
^^^^^^^^^^^^^^

Os dados de saída da simulação se encontram em `Settling-Simulator/out/<NOME_DA_SIMULAÇÃO>`.

Nessa pasta, são salvos as séries temporais das propriedades da suspensão, no formato `.csv`, e também no formato `VTK <https://vtk.org/>`_.

Os dados brutos das propriedades da suspensão, estão divididos de acordo com o tipo de propriedade:

- Cell data: Dados nos centros dos volumes (Permeabilidade e Concentração).
- Point data: Dados nas fronteiras dos volumes (Velocidade e Gradientes).

A estrutura da pasta dos dados de saída da simulação é como se segue:

.. code-block:: Bash

    NOME_DA_SIMULAÇÃO/
        data/
            cell_data.csv # Dados brutos nos centros dos volumes
            point_data.csv # Dados brutos nas fronteiras dos volumes
        vtp/
            suspension.vtm # Arquivo multiblock (VTK)
            suspension/
                suspension_*.vtp # Série temporal polydata (VTK)
        config.yaml # Cópia do arquivo de configuração

.. toctree::
   :maxdepth: -1
   :hidden:

   Exemplo de simulação <simulation_example.ipynb>
   Simulação HPHT <hpht.rst>
   Variação de seção transversal <stepped_domain.rst>