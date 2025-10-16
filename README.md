# Hostnames
El objetivo es generar un dataset de hostnames, construir un DataFrame de Pandas y producir visualizaciones con Matplotlib siguiendo las reglas y funciones
Programación Python (Avanzado) — Práctica

🎯 Objetivos de la práctica

Generar hostnames aleatorios cumpliendo reglas de formato y proporciones por SO, entorno y país.

Construir un DataFrame a partir de dichos hostnames.

Exportar el DataFrame a CSV y validarlo con una lectura posterior.

Crear gráficas (barras, barras horizontales y tarta) para responder a preguntas de distribución.

✅ Requisitos y puntuación (resumen)

Importar librerías necesarias (+0,15).

Inicializar variables base (+0,15).

set_hostnames(number_of_hosts: int): generar hostnames con reglas (+1,5).

get_os(hostname: str): obtener SO (+0,5).

get_enviroment(hostname: str): obtener entorno (+0,5).

get_country(hostname: str): obtener país (+0,5).

set_dataframe(count: int): crear DataFrame global df (+1).

Invocar set_dataframe(1500) y comprobar df (+0,2).

Guardar a CSV y validar lectura (+0,5).

Gráfico único: country vs enviroment (unstack, kind=bar) (+0,5).

Figura con 4 subgráficos (2×2), detalles abajo (+4,5).

Se admite entrega parcial (aprobado ≥ 5 puntos).

🔤 Reglas del hostname

Longitud: 8 caracteres alfanuméricos (letras mayúsculas).

1er carácter = SO: L (Linux), S (Solaris), A (AIX), H (HP-UX).

Proporciones: Linux 40%, Solaris 30%, AIX 20%, HP-UX 10%.

2º carácter = Entorno: D (Development), I (Integration), T (Testing), S (Staging), P (Production).

Proporciones: 10%, 10%, 25%, 25%, 30% respectivamente.

3º–5º carácter = País: NOR, FRA, ITA, ESP, DEU, IRL.

Proporciones: NOR 6%, FRA 9%, ITA 16%, ESP 16%, DEU 23%, IRL 30%.

6º–8º carácter = número de nodo incremental 001–999 por combinación (SO, entorno, país).

🧩 Funciones implementadas

set_hostnames(number_of_hosts: int) -> list[str]
Genera la lista de hostnames cumpliendo formato y proporciones. Gestiona el contador de nodo por clave (SO-ENV-PAÍS).

get_os(hostname: str) -> str
Devuelve Linux|Solaris|AIX|HP-UX según 1ª letra; en caso no válido, Unknow.

get_enviroment(hostname: str) -> str
Devuelve Development|Integration|Testing|Staging|Production según 2ª letra; si no corresponde, Unknow.

get_country(hostname: str) -> str
Devuelve Norway|Germany|Italy|Spain|Ireland|France según posiciones 3–5; si no corresponde, Unknow.

set_dataframe(count: int) -> None
Declara global df, construye dataset (lista de dicts) con campos:
hostname, os, enviroment, country, node, y asigna df (Pandas).

📦 Dependencias

Python 3.9+, Jupyter Notebook/Colab.

pandas, matplotlib (y opcionalmente seaborn).
Instalación rápida:

pip install pandas matplotlib seaborn


🧪 Esquema de datos (DataFrame df)

hostname (str), p. ej. LDIRL003

os (str), p. ej. Linux

enviroment (str), p. ej. Development

country (str), p. ej. Ireland

node (int), p. ej. 3


📊 Visualizaciones requeridas

Country vs Enviroment
Agrupar por country y enviroment, usar unstack y plot(kind='bar').

Figura 2×2 (subplots)

Sup. izquierda: Type of OS grouped by country → groupby(['country','os']).size().unstack().plot(kind='barh').

Sup. derecha: Total Operating Systems → df['os'].groupby(df['os']).size().plot(kind='pie', labels=..., legend=True) incluyendo número y porcentaje por SO.

Inf. izquierda: Total hosts by country → df['country'].value_counts() en barras horizontales, ejes etiquetados (x: Number of hosts, y: Country), anotar el total al final de cada barra y ajustar xlim al máximo + 100.

Inf. derecha: Hosts by country grouped by enviroment → groupby(['country','enviroment']).size().unstack(0).plot(kind='bar') con etiqueta del eje y Number of hosts.

Ajustar espacios con fig.tight_layout().


🧱 Buenas prácticas

Validar entradas y manejar casos no estándar devolviendo Unknow en funciones de mapeo.

Comentar el código y mantener nombres descriptivos.

Fijar semillas aleatorias si se necesita reproducibilidad de proporciones.
