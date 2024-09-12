======================
Velocidade dos Sólidos
======================

Para obter a expressão para a velocidade da fase sólida, as **hipóteses** adotadas, em conjunto com a **Teoria Constitutiva**, são aplicadas na equação da **quantidade de movimento da fase sólida**.

De forma geral, a velocidade da fase sólida é definida pela expressão:

.. math::
    v_s = \left( \varphi_s (\rho_s - \rho_f) g - \frac{d P_s}{d \varphi_s} \frac{\partial \varphi_s}{\partial z} \right) \frac{K}{\eta_{susp}\left( {{{\dot \gamma }_c}} \right)} \frac{\rho_{susp}}{\rho_{susp} - \rho_s \varphi_0}

Onde o termo :math:`\eta_{susp}\left( {{{\dot \gamma }_c}} \right)` representa a viscosidade aparente da suspensão.
Essa viscosidade é avaliada em uma taxa de cisalhamento característica, definida a partir da **Teoria constitutiva**:

.. math::
    \eta_{susp}\left( {{{\dot \gamma }_c}} \right) = {\left( {\frac{{\tau \left( {{{\dot \gamma }_c}} \right)}}{{{{\dot \gamma }_c}}}} \right)_{susp}} = M {\dot \gamma }_c ^ \left(n - 1 \right)

.. math::
    {\dot \gamma }_c = \frac{v_s}{(1 - \varphi_s)} \frac{f(\phi)}{d_p}

Nota-se uma **relação implícita entre a velocidade de sedimentação, e a viscosidade aparente da suspensão**, dependente do valor da velocidade.
A fim de generalizar a expressão da velocidade, independente do modelo reológico, a taxa de cisalhamento pode ser avaliada usando a **velocidade do passo de tempo anterior**.
Dessa forma, a viscosidade aparente da suspensão pode ser tratada como uma constante na expressão:

.. math::
    {\dot \gamma }_c = \frac{v_s^{t-1}}{(1 - \varphi_s)} \frac{f(\phi)}{d_p}

Entretanto, existe a possibilidade de expandir a expressão da velocidade, aplicando um modelo reológico.
Aplicado para um fluido do **modelo de potência**:

.. math::
    {v_s} = {\left\{ {\frac{K(\varphi_s)}{{M{{\left( {1 - {\varphi _s}} \right)}^{1 - n}}}}{{\left[ {\frac{{{d_p}}}{{f \left( \phi  \right)}}} \right]}^{n - 1}}\left( {\frac{{{\rho _{susp}}}}{{{\rho _{susp}} - {\rho _s}{\varphi _{0}}}}} \right)\left[ {{\varphi _s}\left( {{\rho _s} - {\rho _f}} \right)g - \frac{{\partial {P_s}}}{{\partial {\varphi _s}}}\frac{{\partial {\varphi _s}}}{{\partial z}}} \right]} \right\}^{\frac{1}{n}}}

Dessa forma a velocidade calculada explicitamente resolve a dependência da velocidade no cálculo da viscosidade aparente.