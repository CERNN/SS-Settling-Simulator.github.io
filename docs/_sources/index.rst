Documentação do Simulador de Sedimentação
=========================================

Essa é a descrição do projeto em python do `Simulador de Sedimentação de Adensantes <https://github.com/CERNN/SS-Settling-Simulator>`_.

O projeto é baseado na solução do modelo da **Teoria das Misturas da Mecânica do Contínuo**, e tem o objetivo de simular a sedimentação de partículas sólidas como adensantes de um fluido de perfuração.

A sedimentação de adensantes representa graves **riscos para a integridade estrutural** de um poço de perfuração, mais precisamente em relação a fase de abandono dos poços, pois todo o material sólido carregado pelo fluido durante o escoamento, tende a sedimentar quando a mistura se encontra em repouso. 

Uma descrição mais aprofundada do problema pode ser encontrada na seção `Problema <problema/index.rst>`_.

A modelagem da solução, matemática e numérica, é descrita na seção `Modelagem <modelagem/index.rst>`_.

O software em desenvolvimento pode ser encontrado no `Repositório GitHub <https://github.com/pabloharbar/Settling-Simulator>`_.

.. toctree::
   :maxdepth: 1
   :caption: Seções
   :hidden:

   Problema <problema/index.rst>
   Modelagem <modelagem/index.rst>
   Software <software/index.rst>