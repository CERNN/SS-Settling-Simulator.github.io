====================
Parâmetros Numéricos
====================

Para simular utilizando o modelo baseado na **Teoria das Misturas da Mecânica do Contínuo**, é necessário definir alguns parâmetros de simulação.
Estes parâmetros podem ser dividios em **parâmetros de discretização**, e **parâmetros da Teoria Constitutiva**.

Os parâmetros de discretização, dizem respeito ao **tamanho do elemento de malha espacial**, e ao **tamanho do passo de tempo** adotado.

Já os parâmetros da Teoria Constitutiva, dizem respeito aos parâmetros das **equações da Teoria Constitutiva**, que serão abordados posteriormente.

Estabilidade
^^^^^^^^^^^^

Como qualquer método de solução discreto, assim como é o método dos volumes finitos, a qualidade e precisão dos resultados é **extremamente dependente dos parâmetros de simulação**, como resolução da malha espacial :math:`\Delta z`, e tamanho do passo de tempo :math:`\Delta t`. 

A condição de Courant-Friedrichs-Lewy (CFL) é um parâmetros que **indica a estabilidade da simulação**, e é definido com a razão entre o deslocamento de uma partícula em um passo de tempo pelo tamanho do elemento espacial:

.. math::
    CFL = \frac{v_s \Delta t} {\Delta z}

Para atingir o critério de estabilidade, esse coeficiente deve ser menor que 1, de modo que **garanta que nenhuma partícula salte um elemento de malha** em dado passo de tempo.

Parâmetros da Teoria Constitutiva
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Para cada equação da Teoria Constitutiva, existem alguns parâmetros numéricos que devem ser estimados com base em resultados experimentais.

Pressão nos Sólidos
*******************

A equação que descreve o **gradiente de pressão em relação a concentração de sólidos**, é a que segue:

.. math::
    \frac{d P_s (\varphi_s)}{\varphi_s} = \frac{P_{ref} \beta}{\varphi_s ^ 2} \exp \left[-\beta \left(\frac{1}{\varphi_s} - \frac{1}{\varphi_{ref}} \right) \right]

Os parâmetros :math:`P_{ref}`, :math:`\varphi_{ref}`, :math:`\beta` devem ser estimados numericamente com base nos perfis de concentração experimentais.

Permeabilidade
**************

A equação que descreve a **permeabilidade do sedimento**, é a que segue:

.. math::
    K\left( {{\varphi _s}} \right) = {k_0}d_p^2{\left( {\frac{{{\varphi _{\max }}}}{{{\varphi _s}}} - 1} \right)^\Lambda }

Os parâmetros :math:`k_0` e :math:`\Lambda` devem ser estimados numericamente com base nos perfis de concentração experimentais.

Modelo de Estimação de Parâmetros
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A dependência destes parâmetros é uma característica inerente do modelo.
Existem várias formas de estimar esses parâmetros, utilizando de algoritmos de otimização.

Devido a sua simplicidade, o algoritmo de otimização escolhido foi o *Particle Swarm Optimization* (PSO).
O PSO é um algoritmo de otimização inspirado no comportamento coletivo de animais.
Ele é utilizado para resolver **problemas de otimização contínuos e discretos**, explorando o espaço de busca por meio da interação de partículas que se movem influenciadas por suas próprias melhores posições (experiência individual) e pela melhor posição do enxame (experiência coletiva).

O PSO começa com a inicialização de um conjunto de partículas, onde **cada partícula representa uma solução** candidata no espaço de busca.
Cada partícula possui uma **posição e uma velocidade**. 
As partículas ajustam suas posições em cada iteração, levando em conta:

- A melhor posição já encontrada por si mesma (pbest)
- A melhor posição já encontrada por qualquer partícula do enxame (gbest)

A atualização da velocidade de cada partícula é dada pela fórmula:

.. math::
    v_i(t+1) = w . v_i(t) + c_1 . r_1 . (pbest_i - x_i(t)) + c_2 . r_2 . (gbest - x_i(t))

Onde:

- :math:`v_i(t)` é a velocidade da partícula i na iteração t,
- :math:`w` é o fator de inércia, que controla a contribuição da velocidade anterior,
- :math:`c_1` e :math:`c_2` são os coeficientes de aceleração que ponderam a atração da partícula por suas próprias melhores posições e pela melhor posição global, respectivamente,
- :math:`r_1` e :math:`r_2` são números aleatórios uniformemente distribuídos entre 0 e 1,
- :math:`pbest_i` é a melhor posição encontrada pela partícula i, :math:`gbest` é a melhor posição global encontrada por todo o enxame,
- :math:`x_i(t)` é a posição atual da partícula i na iteração t.

A posição da partícula é então atualizada utilizando a nova velocidade calculada:

.. math::
    x_i(t+1) = x_i(t) + v_i(t + 1)

Definição da Função Objetivo
****************************

A função objetivo é uma função matemática que **associa um valor numérico a cada ponto do espaço de busca**. 
Este valor representa a qualidade da solução naquele ponto, e o PSO procura a solução que **minimiza** esse valor.

No caso da sedimentação, o espaço de busca :math:`P_{ref}`, consiste nos parâmetros numéricos :math:`P_{ref}`, :math:`\beta`, :math:`\Lambda` e :math:`k_0`.
Embora seja possível considerar algum outro parâmetro do modelo como parâmetro livre, por exemplo adicionar a variável :math:`\varphi_{ref}` ao espaço de busca, a modo de otimizar seu valor.

A forma da função objetivo é a seguinte:

.. math::
    F_{obj} = \sum_{i=1}^{N_E} \sum_{j=1}^{N_P} \sqrt{\frac{(y_{ij}^e - y_{ij}^s(x_j^s, \theta)) ^ 2}{N_P (y_{ij}^e)^2}}

Onde :math:`N_E` e :math:`N_P` são o número de experimentos, ou sensores, e o número de pontos discretos, respectivamente,
o sobrescrito :math:`e` indica valores experimentais e :math:`s` indica valores simulados, 
:math:`x_j^s` são as variáveis de entrada para determinar os valores simulados e :math:`\theta` é o espaço de busca de parâmetros a serem estimados.