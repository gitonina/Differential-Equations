# Differential-Equations
A project to simulate how a population can change through the years given certain conditions

Planteamiento:
Considere el modelo de cuatro variables de relaci´on de la humanidad con la naturaleza siguiente: xC
representa a la poblaci´on de la ’gente com´un’ o ’comunes’, xE representa la poblaci´on de la ’´elite’,
y representa la ’naturaleza’ es decir todos los recursos naturales disponibles y la ´ultima variable a
representa el ’alimento’ que mantiene la poblaci´on humana.
El modelo se compone de cuatro EDOs de evoluci´on no lineales para t ≥ 0:
x
′
C = b1xC − a1xC
x
′
E = b2xE − a2xE
y
′ = ry(L − y) − DxCy
a
′ = DxCy − CC − CE
En el modelo, a1, a2 son tasas de desaparici´on, b1, b2 son tasas de nacimiento, r es un factor de
regeneraci´on de los recursos naturales, L es el l´ımite de carga de la naturaleza, D es la tasa en que la
gente com´un usa los recursos naturales para producir alimentos. Los valores CC y CE corresponden
a tasas de consumo de alimento de la gente com´un y de la ´elite, respectivamente. Definiremos ac
como el valor de bienestar cr´ıtico por debajo del cual se comienza a racionar el alimento. Este es:
ac = p · (xC + k · xE)
donde p es la cantidad de alimento m´ınima per capita y k es el factor de desigualdad entre la gente
com´un y la ´elite, por ejemplo si k = 10, entonces la ´elite consumir´ıa 10 veces m´as per c´apita que
los comunes. Con esto, CC y CE son funciones que vienen representadas por:
CC = s · xC · min 
1,
a
ac

CE = k · s · xE · min 
1,
a
ac

donde s es el salario de subsistencia per c´apita.
Las cantidades a1 y a2 quedan definidas como:
a1 = as + max 
0, 1 −
CC
sxC

(ah − as)
a2 = as + max 
0, 1 −
CE
sxE

(ah − as)
Donda as es la tasa de mortalidad cuando los estratos se encuentran condiciones saludables y ah la
tasa de mortalidad en condiciones de hambruna.
Por ´ultimo, definimos un colapso cuando alguna de las variables converge a 0 o logra el valor 0.
Cuando los valores tienden a un valor constante distinto de 0, decimos que es un equilibrio.
Considere los siguientes valores para las constantes y valores iniciales del problema:
as ah b1 b2 s p r L xC(0) y(0) a(0)
10−2 7 × 10−2 3 × 10−2 3 × 10−2 5 × 10−4 5 × 10−3 10−2 102 102 L 0
En cuanto a los valores de k, D y xE(0) estos ir´an variando en las distintas partes del an´alisis.
Parte 0: Pre´ambulos de programaci´on (10 puntos)
Importe las librer´ıas necesarias (Numpy, Matplotlib, Scipy) y primero defina todas las constantes
mencionadas anteriormente, excepto k, D y xE(0). Luego programe 5 funciones que calculen los
valores de ac, CC, CE, a1 y a2.
Parte 1: Modelo simplificado a una EDO (20 puntos)
Para esta parte trabajaremos con xE ≡ 0, y = 50, a = 250 constantes. Escriba la EDO resultante y
resu´elvala num´ericamente utilizando los m´etodos de Euler progresivo (puede ver esta c´apsula), Heun
(puede ver esta c´apsula) y Runge Kutta 4 (puede ver esta c´apsula). Para esto siga los siguientes
pasos:
1. Utilice D y k cualquiera. Adem´as de h = 1 medido en a˜nos. Programe una funci´on que calcule
el lado derecho de esta EDO.
2. Simule en el intervalo [0, 1000] medido en a˜nos y encuentre la soluci´on num´erica para xC con
cada m´etodo.
3. Grafique las soluciones obtenidas por cada m´etodo en un solo gr´afico. Recuerde colocar t´ıtulo
al gr´afico y a los ejes, adem´as de leyendas.
4. Vuelva a obtener soluciones ahora con pasos 2−1 y 2−2 y vuelva a graficar, debe hacer un solo
gr´afico para cada paso, en donde deben estar las soluciones dadas por cada m´etodo. Calcule
error de los m´etodos con respecto a una soluci´on num´erica obtenida con Runge Kutta de
orden 4 y paso temporal 2−8
, esto debe hacerlo para cada m´etodo y cada paso definido antes
(1, 2
−1
, 2
−2
). Note que esto implica restar 2 arreglos de largos distintos.
2
Sus gr´aficos para esta parte deber´ıan ser algo como esto:
Parte 2: Sociedad sin ´elites (10 puntos)
Para esta parte solo consideraremos xE ≡ 0, por lo que quedan solamente 3 ecuaciones y 3 inc´ognitas
en el sistema.
a) Escriba el sistema simplificado, imponiendo que xE ≡ 0. Programe una funci´on que calcule la
funci´on del lado derecho del sistema, si llamamos X(t) = (xC(t), y(t), a(t))T
, esta debe ser de
la forma F(t, X, args), en donde por args entendemos todas las constantes y par´ametros del
problema.
b) Si definimos e =
ah−b1
ah−as
, y definimos el l´ımite de carga de la naturaleza como:
χ =
r
D

L − e
s
D

demuestre que existe un Db para el cual se maximiza χ y este es:
Db =
2e · s
L
Y que la carga l´ımite ´optima es:
χM =
rL
2Db
Ahora buscaremos una soluci´on para el modelo, siga los siguientes pasos:
1. Utilice D = Db y un valor de k cualquiera.
2. Simule en el intervalo [0, 1000] medido en a˜nos y encuentre soluciones para xC, y, a con
el m´etodo que usted prefiera.
3. Grafique las soluciones para xC, y y a en un mismo gr´afico junto al valor de χ correspondiente. Amplifique y por 8L y a por 2L. Recuerde colocar t´ıtulo al gr´afico y a los ejes,
adem´as de leyendas.
4. Describa qu´e es lo que ocurre.
3
¿Que puede observar si cambia el valor de k? Explique por qu´e ocurre esto. Esta pregunta no
la responda para las partes posteriores.
c) Utilice ahora D = 5.5Db. Resuelva con un solver en Python de su preferencia (se le recomienda
visitar esta c´apsula). Para obtener una soluci´on ´optima, agregue un par´ametro a esta soluci´on
llamado rtol, comience con un valor de 10−3 y vaya disminuyendo este hasta 10−12. Describa
que es lo que ocurre cuando disminuye este valor. Grafique, solo para rtol = 10−3
, 10−12 (un
gr´afico por cada rtol), amplificando y y a por L. Describa qu´e es lo que ocurre.
Parte 3: Sociedad igualitaria (10 puntos)
Aqu´ı consideraremos que xE ̸= 0, en donde xC y xE consumen la misma tasa de alimento, pero el
estrato xE no trabaja y por tanto no participa directamente en la depredaci´on de la naturaleza.
Entonces llamaremos a xC como los trabajadores y a xE como los no trabajadores. Por tanto
tomaremos k = 1 y adem´as elegiremos xE(0) = 25.
a) Programe una funci´on que calcule la funci´on del lado derecho del sistema, si llamamos X(t) =
(xC(t), xE(t), y(t), a(t))T
, esta debe ser de la forma F(t, X, args), en donde por args entendemos todas las constantes y par´ametros del problema.
b) Si ahora definimos φ =
xE(0)
xC (0) , la carga l´ımite queda definida por:
χ =
r
D

L − e
s
D
(1 + φ)

(1 + φ)
demuestre que el De que maximiza χ es:
De =
2e · s
L
(1 + φ)
Y su valor ´optimo es:
χM = (φ + 1) rL
2De
Utilice D = De y encuentre las soluciones con el m´etodo que usted prefiera para xC, xE, y, a
entre 0 y 1000 a˜nos y graf´ıquelas en un mismo gr´afico, amplifique y por 8L y a por 2L.
Describa qu´e es lo que ocurre.
c) Repita lo mismo de la parte anterior, pero con D = 5De. Resuelva con un solver y siga pasos
similares a P2.c). Grafique amplificando y por 8L y a por L/2. Describa qu´e es lo que ocurre.
Parte 4: Sociedad desigual (10 puntos)
En esta parte consideraremos que k ≫ 1, es decir un escenario en que la ´elite consume muchos m´as
alimentos que los comunes.
a) Utilice D = 6.35 × 10−6 y k = 10, encuentre las soluciones con el m´etodo num´erico que usted
prefiera para xC, xE, y, a entre 0 y 1000 a˜nos y graf´ıquelas amplificando solo a por L/2. No
incluya χ en su gr´afico. Describa qu´e es lo que ocurre.
b) Repita lo mismo de la parte anterior con D = 10−4
. Para el gr´afico amplifique y por 8L y a
por L/2. No incluya χ en su gr´afico. Describa qu´e es lo que ocurre.
