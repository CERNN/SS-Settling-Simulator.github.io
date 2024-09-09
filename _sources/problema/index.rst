=================
Situação Problema
=================

A sedimentação expõe o poço de perfuração a dois principais, e severos, riscos estruturais, o **Annular Pressure Build-up** (APB), e o **desequilíbrio da pressão hidrostática**.

Annular Pressure Build-up (APB)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A sedimentação de adensantes pode gerar graves riscos de operação devido ao entupimento da abertura entre a região do fluido e a formação rochosa.

Essa abertura é utilizada como forma de mitigação da APB, de maneira que uma sapata aberta possibilite a fuga do fluido para a formação.
A APB é consequência do gradiente de temperatura do poço, originado pela fricção do fluido com o revestimento e, pelo fato de que o fluido está confinado a um volume constante.
Dessa forma, tem-se um aumento de pressão, que pode danificar válvulas, conexões e tubos.

.. figure:: /_static/problema/APB.png
    :width: 50 %
    :align: center

    Fonte: modificado e traduzido de :footcite:t:`calccada2016barite`.

Desequilíbrio da Pressão Hidrostática
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A sedimentação de adensantes também pode expor o poço a outro risco igualmente grave, de **influxo de fluidos da formação** para dentro de poços.

Esse fenômeno pode ocorrer devido ao **desequilíbrio da pressão hidrostática** do fluido. 
Conforme partículas sólidas do fluido de abandono temporário sedimentam, gera-se no poço um gradiente de concentração e, por sua vez, uma diminuição da pressão hidrostática em regiões de maior elevação.
A pressão hidrostática local pode se tornar insuficiente para conter os gases da formação, ocorrendo em **sérios riscos de blowout**. 

Síntese do problema
^^^^^^^^^^^^^^^^^^^

Inicialmente, considera-se uma **região anular genérica** que representa a região entre os revestimentos, preenchida com o fluido base contendo adensantes em suspensão.

O material sólido se encontra **uniformemente distribuído** no momento inicial. 
Posteriormente, este material sedimenta por ação gravitacional e forma um leito no fundo do anular com altura dependente do tempo :math:`h(t)`. 

.. figure:: /_static/problema/Problema.png
    :width: 100 %
    :align: center

É possível observar duas interfaces que delimitam o domínio em **3 regiões distintas**: 

#. Uma zona de **fluido clarificado** isento da presença de sólidos
#. Uma região **mistura homogênea**
#. Uma região de **sedimento**

.. footbibliography::