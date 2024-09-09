====================
Modelagem Matemática
====================

O modelo adotado para resolver o problema de sedimentação de adensantes é baseado no modelo de :footcite:t:`d1978modelo`.

A principal característica deste modelo é a maneira que o sistema particulado é modelado, como um **fluido hipotético**.
Dessa forma, a partícula sólida perde a sua individualidade e a suspensão, então, é considerada como um **meio contínuo**.

A origem do equacionamento para sistemas sólido-líquido se dá a partir do **Teorema do Transporte de Reynolds**.

Hipóteses
^^^^^^^^^

Algumas hipóteses são adotadas para a simplificação do modelo matemático:

#. Domínio Unidimensional :math:`\varphi (t)`
#. Mistura encontra-se inicialmente homogeinizada :math:`\varphi (t=0) = \varphi_0`
#. Meio isotrópico

.. important::
   Apesar do modelo matemático adotar a hipótese de domínio unidimensional, o efeito da variação de seção transversal ainda pode ser incluido a partir de **condições de salto**. Consultar a seção `Discretização espacial <../numerica/espacial.rst>`_ para mais informações.

Equacionamento
^^^^^^^^^^^^^^

O conjunto de equações que descrevem o problema é composto pelas regras de **conservação de massa e de quantidade de movimento**.

Aplicando o Teorema do Transporte de Reynolds para a propriedade volumétrica de **concentração mássica**, para a **fase sólida**, resulta em:

.. math::
   \frac{\partial \varphi_s}{\partial t} + \frac{\partial (\varphi_s v_s)}{\partial z} = 0

Onde :math:`\varphi_s` é a **concentração volumétrica** da fase sólida, e :math:`v_s` é a **velocidade** da fase sólida.

Para descrever o movimento das partículas, a expressão para a **velocidade da fase sólida** é derivada a partir da aplicação da equação de transporte para a propriedade de **quantidade de movimento**:

.. math::
   {\rho _s}{\varphi _s}\left[ {\frac{{\partial {v_s}}}{{\partial t}} + {v_s}\frac{{\partial {v_s}}}{{\partial z}}} \right] = \frac{{\partial {T_s}}}{{\partial z}} + m + {\varphi _s}\left( {{\rho _s} - {\rho _f}} \right)g

Entretanto é necessário adotar expressões para modelar a **interação fluido-sólido** :math:`m` e a **tensão nos sólidos** :math:`T_s`.
Essas expressões são caracterizadas como parte da **Teoria Constitutiva** do modelo de D'Ávila.

.. note:: Para mais detalhes, os modelos adotados estão descritos na seção `Teoria Constitutiva <teoria_constitutiva.rst>`_.

Uma simplificação importante da Teoria Constitutiva, é a **desconsideração dos termos de aceleração e transporte convectivo**, para a fase sólida:

.. math::
    \frac{{\partial {v_s}}}{{\partial t}} + {v_s}\frac{{\partial {v_s}}}{{\partial z}} \cong 0

Conforme reiterado por :footcite:t:`damasceno1992contribuiccao`, os termos são desprezíveis para **escoamentos lentos em fluidos viscososos**. 
Assim, a equação de transporte de quantidade de movimento, pode ser simplificada para:

.. math::
   \frac{{\partial {T_s}}}{{\partial z}} + m + {\varphi _s}\left( {{\rho _s} - {\rho _f}} \right)g = 0


.. footbibliography::

.. toctree::
   :maxdepth: -1
   :hidden:

   Teoria Constitutiva <teoria_constitutiva.rst>
   Reologia <reologia.rst>
   Velocidade dos Sólidos <velocidade_solidos.rst>
   Lista de símbolos <lista_simbolos.rst>