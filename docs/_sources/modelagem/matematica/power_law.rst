==================
Modelo de Potência
==================

Fluidos Power Law são uma subclasse de fluidos não-Newtonianos que obedecem ao Modelo de Potência de :footcite:t:`ostwald1925theorie`.

A relação reológica entre a **tensão viscosa** e a **taxa de cisalhamento** é expressa como:

.. math::
    \tau \left( {{{\dot \gamma }}} \right) = M {\dot \gamma } ^ n

O comportamento dos fluidos representados pelo modelo de potência é fortemente dependente do parâmetro :math:`n`.
De tal forma que ele possa ser caracterizado de acordo com os intervalos:

#. :math:`n=1`: Comportamento Newtoniano
#. :math:`n<1`: Comportamento Pseudoplástico (Shear-Thinning)
#. :math:`n>1`: Comportamento Dilatante (Shear-Thickening)

Assim, é possível definir uma expressão para a viscosidade aparente da suspensão:

.. math::
    {\left( {\frac{{\tau \left( {{{\dot \gamma }_c}} \right)}}{{{{\dot \gamma }_c}}}} \right)_{susp}} = M {\dot \gamma }_c ^ \left(n - 1 \right)
    
.. footbibliography::
