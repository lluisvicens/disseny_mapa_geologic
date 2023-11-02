# TUTORIAL PER A LA CREACIÓ D'UN MAPA GEOLÒGIC AMB QGIS

A continuació, s'explica com crear un mapa geològic pas a pas, utilizant el software **QGIS** i el complement **Open ICGC**.

## 1. Configurar QGIS

1. En primer lloc caldrà obrir QGIS, i crear un nou projecte en blanc tot configurant el sistema de referencia de coordenades amb el codi **EPSG 25831** (UTM 31N ETRS 89).

![fig1](_static/layout1.png "Configura el CRS del projecte")

2. A continuació, en cas que no ho hagis fet abans, caldrà instalar el complement **Open ICGC**. Per a fer-ho cal dirigir-se al menú *Plugins > Manage and Install pluguins...* i a la finestra emergent, dins de l'apartat *Search*, escriure **Open ICGC**. Una vegada filtrats els resultats, caldrà seleccionar el complement en qüestió i fer un clic sobre el botó *Install plugin*.

![fig2](_static/layout2.png "Instal·la el complement Open ICGC")

3. El nou complement apareixerà en forma de nova barra d'eines, a la interfície gràfica de QGIS.

![fig3](_static/layout3.png "Aparença del complement Open ICGC")

### 2. Descarregar la cartografia de treball

4. En primer lloc, caldrà descarregar la base municipal de tot Catalunya. Dirigeix-te a la barra d'eines que acabes d'instal·lar i fes un clic sobre el botó *Download tool* per accedir al catàleg de dades que ofereix el complement. Desplaça't pel menú *Download tool > Administrative divisions vectorial data (zip)*.

![fig4](_static/layout4.png "Obté dades")

5.  En la finestra emergent, fes un clic sobre el botó **Ok** per descarregar les dades de Catalunya, tot donant un nom (o deixant el que apareix per defecte) a la carpeta on es descarregaran les dades. Espera a que finalizi el procés de descàrrega.

6. Les dades relatives a les divisions administratives de Catalunya es mostraran al panell de capes de QGIS, on podràs veure que s'han descarregat els límits corresponents a municipis, comarques, vegueries, províncies i país. Desactiva totes les capes a excepció dels límits municipals:

7. Com que les capes están configurades per tal que es mostrin segons l'escala de visualització, és possible que no vegis res a la finestra de mapa. No cal que et preocupis doncs a continuació es mostraran. Ara centraràs la vista sobre el terme municipal de Vilobí d'Onyar. Per a dur a terme aquesta acció, cal que situis el cursor dins de la caixa de cerca (*search*) del complement, i escriguis el nom del municipi. A continuació, prem la tecla retorn per tal d'obtenir el resultat de la cerca, selecciona la primera opció: **Cap de municipi**. Per tal de confirmar la selecció i centrar la vista al municipi, fes un clic a **ok**.

![fig5](_static/layout5.png "Centra la vista a Vilobí d'Onyar")

8. A la finstra de mapa hi apareixerà el nom del municipi però no els límits, degut a que la vista està a escala 1:1.000, ara mateix. Si amb la rodeta central del ratolí allunyes la vista, veuràs com ara sí apareix el límit del municipi, així com de la resta de municipis veins.

![fig6](_static/layout6.png "Visualització dels límits municipals")
   
9. A continuació, caldrà que descarreguis la capa del mapa geològic 1:25.000 de Catalunya. Per a dur a terme aquesta acció, caldrà que a la barra d'eines del complement OpenICGC, facis un clic sobre la icona *Download tool* i accedeixis al menú *Geological map vectorial data > Geological map 1:25.000*. 

![fig7](_static/layout7.png "Descarrega el geològic")

10. Per finalitzar el procés de descàrrega, el complement et demanarà en quina carpeta vols desar les dades. Crea'n una, assigna-li el nom que creguis oportú, i selecciona-la. En finalitzar el procés de descàrrega, el geològic 25k es carregarà automàticament a la finestra de mapa.

### 3. Adequar l'extensió de les capes de geologia, a l'extensió del municipi

11. Degut a que únicament t'interessen aquelles capes que pertanyen al municipi de Vilobí d'Onyar, i per tal de no sobrecarregar l'ordinador gestionant una capa molt més gran del necessari, hauràs d'aplicar un geoprocés conegut com a **retall** o **clip**. Fixa't que, el mapa geològic es composa de diverses capes i com que l'eina de retall només pot actuar d'una capa en una capa, el retall el duràs a terme aplicant un procés per lots, o en *batch*.

12. En primer lloc, però, cal que obtinguis una geometria de retall. I aquesta geometria de retall és el polígon que representa l'extensió del municipi. Així doncs, caldrà que seleccionis el polígon de Vilobí de la capa de límits municipals, i el desis en un nova capa. Per a fer això, només cal que tinguis seleccionada la capa de municipis al panell de capes, agafis l'eina de selecció, i facis un clic sobre el polígon per tal que quedi ressaltat de color groc.

![fig8](_static/layout8.gif "Selecciona el polígon")

13. A continuació, cal que facis un clic amb el botó dret del ratolí sobre el nom de la capa, visible al panell de capes i, al menú contextual, activis l'opció **Export > Save selected features as...*.

![fig9](_static/layout9.png "Exporta els elements seleccionats")

14. En el quadre de diàleg emergent, caldrà que seleccionis el format de sortida de la nova capa (**geojson**), una ubicació i un nom (p.e. **vilobi**). També caldrà indicar que el CRS de la capa ha de ser EPSG:25831. Finalment, assegurar-se que la casella *Add saved file to map* està activada.  

![fig10](_static/layout10.png "Configura la capa a exportar")

15. En finalitzar el procés, al panell de capes hi apareixerà una nova capa que durà per nom **vilobi** amb un únic polígon. A continuació, pots eliminar del panell de capes totes les capes a excepció de la que acabes de crear, així com les capes del mapa geològic.

![fig11](_static/layout11.gif "Organització del panell de capes")

16. Per tal de retallar les onze capes del geològic amb el contorn del terme municipal de vilobí, activa el menú *Vector > Geoprocessing tools > Clip...*. En la finestra emergent, fes un clic sobre el botó *Run as batch process*. Aquesta nova finestra compta amb tres columnes que caldria omplir adequadament per tal de poder fer tots els retalls a la vegada. Les columnes a parametritzar són *Input layer* (o la capa que es vol retallar), *Overlay layer* (o la capa que es vol fer servir com a contorn per al retall) i *Clipped* (que serà la capa de sortida una vegada aplicat el retall).

![fig12](_static/layout12.png "Aspecte original de l'eina de retall per lots")

17. Per començar, fes un clic sobre el botó *Autofill...* de la columna **[input layer]** i d'entre les diferents opcions, selecciona **Select from Open Layers**. A la finestra emergent, selecciona les onze capes del geològic, i accepta la selecció fent clic a **D'acord**. 

![fig13](_static/layout13.png "Selecció de les capes a retallar")

18. A continuació, a la columna *Overlay layer*, obre el desplegable de la primera línia, y selecciona la capa **vilobi**. A continuació, fes un clic sobre el botó *Autofill...* i selecciona la opció *Fill down*.

![fig14](_static/layout14.gif "Configuració de l'eina de retall per lots")

19. Per acabar, a la columna *Clipped*, fes un clic sobre el botó que mostra els tres punts i, a la finestra emergent, assigna el nom de la capa de sortida (indica que el format sigui un **geojson**). En realitat, el que faràs es definir un prefix (p.e. **vilobi_**) i en acceptar, a la nova finestra emergent (*Autofill settings*) caldrà que escullis l'opció *Fill with parameter values* i com a paràmetre a utilitzar, selecciona l'opció que duu per nom *Input layer*.

![fig15](_static/layout15.gif "Aspecte del quadre de diàleg de l'eina")

21. Una vegada configurada la totalitat de la finestra de l'eina, i abans de donar per finalitzat el procés, assegura't que tinguis activada la casella **Load layers on completion** i fixa't com molt probablement, la primera filera estigui repetida. Així doncs, caldrà que eliminis aquest primer registre i, a continuació, facis un clic sobre el botó **Run**.

![fig16](_static/layout16.gif "Aspecte del quadre de diàleg de l'eina")
