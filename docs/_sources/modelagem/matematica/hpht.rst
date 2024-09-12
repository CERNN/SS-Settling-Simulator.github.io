===========
Modelo HPHT
===========

Para incluir o efeito da temperatura e da pressão, pode-se adotar um modelo de **reologia HPHT** (*High Pressure High Temperature*).

Uma forma de incluir tais efeitos, é modelando funções de correção para temperatura e pressão **isoladamente**.
Por exemplo, utilizando o modelo de :footcite:t:`barus1893art`:

.. math::
    \eta \left(T,P,{\dot \gamma }_c \right) = f(T) g(P) \eta({\dot \gamma }_c)

.. math::
    f(T) = \exp [-a (T - T_0)]

.. math::
    g(P) = \exp [-\beta (P - P_0)]

.. footbibliography::