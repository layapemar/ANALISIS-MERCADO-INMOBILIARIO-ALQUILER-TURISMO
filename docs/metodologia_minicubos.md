Los "cubos" son una técnica muy usada en business intelligence (no confundir con business analytics) que consiste básicamente en organizar la información en métricas (lo que se quiere analizar) y dimensiones (las vistas de análisis).

Y precalcular el resultado de las métricas en los cruces de las dimensiones.

Con el objetivo de que cuando se necesite un dato no se tenga que calcular en tiempo real, si no que simplemente se recupere del cubo y por tanto la experiencia de usuario sea mucho mejor.

Para business analytics podemos simplificar la técnica, haciendo un cubo unidimensional, es decir precalculando las métricas para cada dimensión, pero no para el cruce de dimensiones.

Y lo vamos a llamar minicubo.

El minicubo nos va a dar gran potencia de análisis y además va a ser la base de la técnica que aprenderemos después: el risk scorecard.

Para construir un minicubo:

Seleccionar qué variables serán la métricas y cuales las dimensiones
Pasar a transaccional las dimensiones
Agregar las métricas por "variable" y "valor" con las funciones deseadas (suma, conteo, etc)
Por ejemplo vamos a construir un minicubo para analizar Funded Amount por las dimensiones Country, Sector, Activity y Status.

#Paso 1: Seleccionar qué variables serán la métricas y cuales las dimensiones
metrica = ['Funded Amount']
dimensiones = ['Country','Sector','Activity','Status']

minicubo = df[dimensiones + metrica]
minicubo

#Paso 2: pasar a transaccional las dimensiones
minicubo = minicubo.melt(id_vars='Funded Amount')
minicubo

#Paso 3: Agregar las métricas por "variable" y "valor" con las funciones deseadas
minicubo = minicubo.groupby(['variable','value'])['Funded Amount'].agg(conteo = 'count', media = 'mean')
minicubo

A partir de aquí podemos usar el minicubo para obtener insights de forma muy rápida.

Por ejemplo: analiza el número de operaciones y la financiación media en cada sector.
minicubo.loc['Sector']

minicubo.loc['Sector'].plot.bar();

Podemos automatizar esto para todas las dimensiones de nuestro minicubo, mediante un for que recorra todas las variables 'variable' y genere un gráfico por cada una

# Obtener las dimensiones únicas del minicubo
dimensiones = minicubo.index.get_level_values('variable').unique()

# Recorrer cada dimensión
for dimension in dimensiones:
    # Extraer datos de esa dimensión
    data = minicubo.loc[dimension].sort_values('media', ascending=False)

    # Crear el gráfico
    data.plot.bar(figsize=(10, 4), title=f"{dimension} - Nº Operaciones y Financiación Media")
    plt.ylabel("Valor")
    plt.xticks(ha='right', fontsize=8)
    plt.tight_layout()
    plt.show()


También podemos usar el minicubo para encontrar rápidamente insights sobre "perfiles".

Por ejemplo encuentra los atributos de las operaciones que consiguen mayor financiación.
minicubo.media.nsmallest(10)