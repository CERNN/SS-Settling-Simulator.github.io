========
Reologia
========

A reologia do fluido, define como ele se comportará sob diferentes tensões, a partir da relação entre a tensão de cisalhamento em diferentes taxas de cisalhamento.
Utiliza-se de modelos reológicos para representar o comportamento do fluido em diferentes taxas de cisalhamento.

Entre os tipos de fluidos não newtonianos, podem ser classificados entre: fluidos pseudoplásticos; e fluidos dilatantes. 
Fluidos pseudoplásticos apresentam **diminuição da viscosidade com o aumento da taxa de cisalhamento**. 
Em contrapartida, fluidos dilatantes exibem o efeito oposto, tornando-se **mais viscosos conforme o cisalhamento aumenta**. 
Além disso, há também os fluidos viscoplásticos, que requerem uma tensão limite de escoamento, para que o fluido seja cisalhado e comece a escoar.

Para descrever esses comportamentos complexos, diferentes modelos reológicos são empregados.
O modelo de potência é utilizado para descrever matematicamente fluidos pseudoplásticos e dilatantes.
Já o modelo de Bingham é aplicado para fluidos viscoplásticos, onde o comportamento do fluido cisalhado é newtoniano. 

.. note::
   Atualmente, o único modelo reológico disponível no software é o de potência, devido a ausência de dados experimentais para calibração de outros modelos. Estes modelos, tais como fluidos Herschel-Bulkley por exemplo, podem ser incluídos futuramente.

.. toctree::
   :maxdepth: -1
   :hidden:

   Modelo de Potência <power_law.rst>
   Modelo HPHT <hpht.rst>