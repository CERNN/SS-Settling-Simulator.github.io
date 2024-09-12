===============
Casos de estudo
===============

Para avaliar as features do software, foram executados casos de estudo: variando o perfil de temperatura do poço; e variando a geometria (seção) do poço.

Variação da temperatura
^^^^^^^^^^^^^^^^^^^^^^^

Procurou-se avaliar o efeito da temperatura na evolução temporal do perfil de concentração.
De acordo com o modelo HPHT, a viscosidade deve diminuir exponencialmente proporcional ao fator :math:`a`, visto que esse fator assume valores positivos.

O estudo de caso foram considerados quatro cenários. Abaixo estão os arquivos de configuração de cada caso:

.. literalinclude:: /_static/software/temperature_uniform_25.yaml
    :caption: Perfil uniforme de temperatura :math:`T=T_{ref}`
    :language: yaml

.. literalinclude:: /_static/software/temperature_uniform_50.yaml
    :caption: Perfil uniforme de temperatura :math:`T=50°C`
    :language: yaml

.. literalinclude:: /_static/software/temperature_uniform_100.yaml
    :caption: Perfil uniforme de temperatura :math:`T=100°C`
    :language: yaml

.. literalinclude:: /_static/software/temperature_linear_4_120.yaml
    :caption: Perfil linear de temperatura :math:`T(z=0)=100°C; T(z=h)=4°C`
    :language: yaml

.. csv-table:: Casos de estudo - variação do regime de temperatura do poço
   :file: /_static/software/study_cases_temperatura.csv
   :header-rows: 1

.. figure:: /_static/software/study_cases_temperatura.png
    :width: 40 %
    :align: center

    Ilustração do domínio e o perfil de temperatura do poço de cada simulação deste caso.



Variação de seção do poço
^^^^^^^^^^^^^^^^^^^^^^^^^

Procurou-se avaliar o efeito da transição de seções na evolução temporal do perfil de concentração.
De acordo com a condição de salto do modelo, o efeito da transição é proporcional a razão entre a área imediatamente acima e abaixo da discontinuidade.
Para razões menores que 1, o efeito é de diluição da suspensão abaixo da discontinuidade.
Para valores maiores que 1, o efeito é do aumento da concentração na região acima da discontinuidade.

O estudo de caso foram considerados quatro cenários. Abaixo estão os arquivos de configuração de cada caso:

.. literalinclude:: /_static/software/poco_reto.yaml
    :caption: Poço reto
    :language: yaml

.. literalinclude:: /_static/software/2_fases.yaml
    :caption: 2 seções
    :language: yaml

.. literalinclude:: /_static/software/4_fases.yaml
    :caption: 4 seções
    :language: yaml

.. csv-table:: Casos de estudo - variação de seção do poço
   :file: /_static/software/study_cases_secao.csv
   :header-rows: 1

.. figure:: /_static/software/study_cases_secao.png
    :width: 80 %
    :align: center

    Ilustração do domínio e as transições de seção do poço de cada simulação deste caso.


.. toctree::
   :maxdepth: -1
   :hidden:

   Variação de seção do poço <secao.ipynb>
   Variação de regime de temperatura do poço <temperatura.ipynb>