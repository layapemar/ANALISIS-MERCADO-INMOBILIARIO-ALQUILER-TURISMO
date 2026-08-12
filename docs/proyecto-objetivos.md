# DISEÑO DEL PROYECTO

Este caso simula que somos una **empresa inmobiliaria** que invierte en grandes ciudades comprando inmuebles para **alquilarlos como apartamentos turísticos**.

La dirección ha decidido invertir en **Madrid** y nos ha encargado analizar los datos que el líder del sector **Airbnb** hace públicos para identificar los **tipos de inmuebles con mayor potencial comercial** para el alquiler turístico.

Como entregable principal esperan:
- La **tipología** (o tipologías) de inmuebles que el equipo de valoraciones debe buscar entre las oportunidades existentes en la ciudad.
- Los **principales barrios o zonas geográficas** en los que focalizarse.

> Para cumplir con el objetivo aplicaremos la **metodología de Discovery** y las **técnicas de Business Analytics (BA)** aprendidas.

Aunque este caso esté centrado en el **alquiler turístico**, el mismo enfoque se puede usar en situaciones con alto componente de **ubicación**:

- apertura y cierre de tiendas  
- reducción de capacidad instalada  
- expansión de franquicias  
- etc.

---

## OBJETIVO

**Localizar el perfil (o perfiles) de inmuebles que maximizan el potencial comercial** en el mercado del alquiler turístico y las **principales zonas** donde buscarlos.

---

## PALANCAS

Tras hablar con el equipo de valoraciones, las palancas con más impacto en la **rentabilidad** son:

- **Precio de alquiler:** cuanto más se pueda cobrar por noche, mayor es la rentabilidad.  
- **Ocupación:** cuantos más días al año se alquile, mayor es la rentabilidad.  
- **Precio del inmueble:** cuanto más barata sea la adquisición, mayor es la rentabilidad.

---

## KPIs

En este ejemplo los KPIs son directos:

- **Ocupación:** número de **días anuales** que el inmueble se puede alquilar.  
- **Precio del alquiler:** **precio por noche (€)** según Airbnb.  
- **Precio del inmueble:** **m² × precio medio del m²** en su zona, **aplicando un 25% de descuento** sobre el precio oficial por la capacidad de negociación del equipo de compras.

---

## DATOS

Ir a https://insideairbnb.com/get-the-data/ y elegir la ciudad de interés.

Buscar los archivos listings.csv y 	listings.csv.gz y crear otro archivo urls_datos.md en docs con sus urls.

---

## PREGUNTAS SEMILLA

### Sobre el **precio del alquiler**
- ¿Cuál es el **precio medio**? ¿y el **rango de precios**? ¿Y por **distritos**? ¿Y por **barrios**?  
- ¿Cuál es el **ranking** de distritos y barrios por **precio medio de alquiler**?  
- ¿Qué **factores** (aparte de la localización) **determinan el precio** del alquiler?  
- ¿Cuál es la **relación** entre el **tamaño** del inmueble y el **precio** por el que se puede alquilar?  
- ¿Cómo influye la **competencia** (número de inmuebles disponibles por barrio) en el **precio** del alquiler?  
- ¿Cómo varían los precios por **tipo de alquiler** (piso completo, habitación privada, habitación compartida)?

### Sobre la **ocupación**
- ¿Cuál es la **ocupación media**? ¿Y por **distritos**? ¿Y por **barrios**?  
- ¿Qué **probabilidad** tiene cada **nivel de ocupación** en cada distrito?  
- ¿Cuál es el **ranking** de distritos y barrios por **ocupación**?  
- ¿Qué **factores** (aparte de la localización) **determinan la ocupación**?  
- ¿Cuál es la **relación** entre el **tamaño** del inmueble y su **grado de ocupación**?  
- ¿Cómo influye la **competencia** (número de inmuebles disponibles por barrio) en la **ocupación**?

### Sobre el **precio de compra**
- ¿Cuál es el **ranking** de **precio por m²** por distrito?  
- ¿Cuál es el **ranking** de **precio del inmueble** (m² × tamaño medio) por distrito?  
- ¿Cuál es la **relación** entre el **precio del inmueble** y el **precio del alquiler** por distrito?  
- ¿Cuál es la **relación** entre el **precio del inmueble** y la **ocupación** por distrito?

