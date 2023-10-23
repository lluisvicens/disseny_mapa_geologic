# TUTORIAL PER A LA CREACIÓ D'UN MAPA GEOLÒGIC AMB QGIS

A continuació, s'explica com crear un mapa geològic pas a pas, utilizant el software **QGIS** i el complement **Open ICGC**.

## Configurar QGIS

1. En primer lloc caldrà obrir QGIS, i crear un nou projecte en blanc tot configurant el sistema de referencia de coordenades amb el codi **EPSG 25831** (UTM 31N ETRS 89).

![fig1](_static/fig1.png "Configura el CRS del projecte")

2. A continuació, en cas que no ho hagis fet abans, caldrà instalar el complement **Open ICGC**. Per a fer-ho cal dirigir-se al menú *Plugins > Manage and Install pluguins...* i a la finestra emergent, dins de l'apartat *Search*, escriure **Open ICGC**. Una vegada filtrats els resultats, caldrà seleccionar el complement en qüestió i fer un clic sobre el botó *Install plugin*.

![fig2](_static/fig2.png "Instal·la el complement Open ICGC")

3. El nou complement apareixerà en forma de nova barra d'eines, a la interfície gràfica de QGIS.

![fig3](_static/fig3.png "Aparença del complement Open ICGC")

### Descarregar la cartografia de treball

4. En primer lloc, caldrà descarregar la base municipal de tot Catalunya. Dirigeix-te a la barra d'eines que acabes d'instal·lar i fes un clic sobre el botó XXXX per accedir al catàleg de dades a les que es pot accedir. Desplaça't pel menú *Mapes de fons > Divisions administratives > Municipis > Municipis 1:5000*

![fig4](_static/fig4.png "Obten dades")
   
6. Seleccionar el municipi de Vilobí d'Onyar i exportar la selecció a una nova capa
7. Descarregar la base geològica escala 1:25000 de l'ICGC
8. Retallar la base geològica amb el contorn del límit municipal (batch process o procés per lots)
