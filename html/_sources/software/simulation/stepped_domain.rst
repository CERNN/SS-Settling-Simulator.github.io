============================================
Simulações com Variação de seção transversal
============================================

Semelhante a simulação básica, o input para a simulação em domínios com variação de seção transversal é o arquivo de configuração

Arquivo de configuração
^^^^^^^^^^^^^^^^^^^^^^^

Para habilitar a simulação considerando um domínio anular 2D, é necessário preencher o campo *domain.annular_domain*:

.. literalinclude:: /_static/software/stepped_domain_config.yaml
    :caption: Arquivo de configuração da simulação com variação de seção transversal
    :language: yaml

A ilustração abaixo indica a relação entre a geometria construída e as transições informadas através do arquivo de configuração:

.. figure:: /_static/software/stepped_domain.png
    :width: 100 %
    :align: center

Dados de saída
^^^^^^^^^^^^^^

Os dados brutos das propriedades da suspensão, são idênticos ao caso padrão de simulação:

- Cell data: Dados nos centros dos volumes (Permeabilidade, Concentração).
- Point data: Dados nas fronteiras dos volumes (Velocidade e Gradientes).

A estrutura da pasta dos dados de saída da simulação é idêntica ao caso padrão de simulação.

.. toctree::
   :maxdepth: -1
   :hidden:

   Domínio anular <stepped_domain_simulation.ipynb>