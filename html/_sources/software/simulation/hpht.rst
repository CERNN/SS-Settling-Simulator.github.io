================================================
Simulações HPHT (High Pressure High Temperature)
================================================

Semelhante a simulação básica, o input para a simulação em condições HPHT é o arquivo de configuração

Arquivo de configuração
^^^^^^^^^^^^^^^^^^^^^^^

Para habilitar a simulação considerando condições HPHT, é necessário preencher o campo HPHT:

.. literalinclude:: /_static/software/HPHT_config.yaml
    :caption: Arquivo de configuração da simulação habilitando condições HPHT
    :language: yaml


Dados de saída
^^^^^^^^^^^^^^

Os dados brutos das propriedades da suspensão, são idênticos ao caso padrão de simulação, com algumas propriedades extras:

- Cell data: Dados nos centros dos volumes (Permeabilidade, Concentração, Temperatura, Pressão hidrostática e o valor da correção da viscosidade).
- Point data: Dados nas fronteiras dos volumes (Velocidade e Gradientes).

A estrutura da pasta dos dados de saída da simulação é idêntica ao caso padrão de simulação.

.. note::
    Consultar a `seção de simulação <index.rst>`_ para mais detalhes sobre a simulação básica de sedimentação.

.. toctree::
   :maxdepth: -1
   :hidden:

   Efeito da pressão <HPHT_simulation_pressure.ipynb>
   Efeito da temperatura <HPHT_simulation_temperature.ipynb>
   Efeito combinados <HPHT_simulation.ipynb>