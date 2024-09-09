===================
Teoria Constitutiva
===================

A Teoria Constitutiva define de que forma será incorporada a **tensão nos sólidos**, que caracteriza a interação sólido-sólido, e a forma da **força resistiva**, que caracteriza a interação fluido-sólido.

++++++++++++++++++
Tensão nos sólidos
++++++++++++++++++

Partindo da hipótese básica de que a suspensão é um **meio isotrópico**, :footcite:t:`d1977equaccoes` indicaram uma representação para o **tensor tensão**, com as seguintes considerações:

* O tensor possui apenas componentes normais (pressão estática) à superfície de contato entre as partículas, dependendo da porosidade do meio.
* O componente da tensão extra depende apenas da concentração da mistura, idêntica a porosidade do meio

Assim o tensor de **tensão nos sólidos** é escrito como:

.. math::
    T_s = T_s (\varphi _s) = -P_s (\varphi _s) I

Ainda é preciso de uma equação para descrever a **pressão nos sólidos em função da porosidade do meio**.

Pressão nos sólidos
^^^^^^^^^^^^^^^^^^^

A equação utilizada nas zonas de sedimentação onde a **interação sólido-sólido é significativa**, é uma reparametrização proposta por :footcite:t:`rocha2020settling`:

.. math::
    {P_s} = {P_{ref}}\exp \left[ { - \beta \left( {\frac{1}{{{\varphi _s}}} - \frac{1}{{{\varphi _{ref}}}}} \right)} \right]

Onde :math:`P_{ref}` e :math:`\beta` são parâmetros da teoria constitutiva da pressão nos sólidos, e :math:`\varphi _{ref}` é a concentração de referência.

Dessa forma, o tensor de **tensão nos sólidos** pode ser derivado usando a regra da cadeia:

.. math::
    \frac{\partial T_s (\varphi_s)}{\partial z} = - \frac{d P_s (\varphi_s)}{\varphi_s} \frac{\partial \varphi_s}{\partial z} 

.. math::
    \frac{d P_s (\varphi_s)}{\varphi_s} = \frac{P_{ref} \beta}{\varphi_s ^ 2} \exp \left[-\beta \left(\frac{1}{\varphi_s} - \frac{1}{\varphi_{ref}} \right) \right]

+++++++++++++++
Força Resistiva
+++++++++++++++

Com base no modelo de interação sólido-líquido de :footcite:t:`silva1979escoamento`, a força resistiva entre as fases é função da viscosidade aparente da suspensão :math:`\eta_{susp}`, da permeabiliade do meio :math:`K`, e da velocidade da fase sólida :math:`v_s`, na forma de:

.. math::
    m = - \frac{\eta_{susp} v_s}{K}

:footcite:t:`rocha2020settling` propuseram uma forma para a **força resistiva**, combinado com o conceito de viscosidade global de uma mistura de :footcite:t:`burger2000phenomenological`, com base na taxa de cisalhamento característica e tensão cisalhante:

.. math::
    m = - \frac{1}{K}{\left( {\frac{{\tau \left( {{{\dot \gamma }_c}} \right)}}{{{{\dot \gamma }_c}}}} \right)_{susp}}\left( {1 - \frac{{{\rho _s}{\varphi _{s0}}}}{{{\rho _{susp}}}}} \right) v_s

.. note::
    Esse modelo é dependente de uma expressão para calcular a **permeabilidade do meio poroso**, e da **tensão viscosa**.

Permeabilidade
^^^^^^^^^^^^^^

A **permeabilidade do meio poroso**, é calculada através da equação modificada de :footcite:t:`tiller1980basic`, proposta por :footcite:t:`rocha2020settling`:

.. math::
    K\left( {{\varphi _s}} \right) = {k_0}d_p^2{\left( {\frac{{{\varphi _{\max }}}}{{{\varphi _s}}} - 1} \right)^\Lambda }

Tensão Viscosa
^^^^^^^^^^^^^^

Para completar a teoria constitutiva, é necessário caracterizar o **modelo reológico** do fluido através dos termos de **tensão viscosa** e **taxa de cisalhamento característica**, que representam a viscosidade aparente da suspensão.

Uma forma para calcular a **viscosidade aparente**, é baseada em dois aspectos:

* O primeiro é a definição da **taxa de cisalhamento característica** para fluidos não-Newtonianos, conforme :footcite:t:`silva1979escoamento`.
* O segundo, é a adoção do **modelo reológico**.

A expressão para a taxa de cisalhamento característica, considera a **esfericidade da partícula** da fase sólida, de tal forma que possa ser escrita como:

.. math::
    {\dot \gamma }_c = \frac{v_s}{(1 - \varphi_s)} \frac{f(\phi)}{d_p}

Onde a função de esfericidade :math:`f(\phi)`, definida por :footcite:t:`laruccia1990velocidade`, tem a seguinte forma:

.. math::
    f(\phi) = -3.45 \phi ^ 2 + 5.25 \phi - 1.41

Para determinar a **tensão viscosa**, deve ser adotado um **modelo reológico** que melhor represente o comportamento da suspensão.

.. note:: Para mais informações sobre a definição de um **modelo reológico**, consultar a seção `Reologia <reologia.rst>`_.

.. footbibliography::