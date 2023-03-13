# Preguntas 

## Pregunta 2

### ¿Qué campos se deben tener en cuenta al momento de implementar una etiqueta de conversión para Google Ads?(etiqueta oficial de Tag Manager, no por HTML)

**Respuesta:**

> Se tienen los siguientes campos:
>
>   | Campo  | Valor |
>   | ------ |------|
>   | ID de conversión (Conversion ID) | Código único - se debe relacionar con Google Ads   |
>   | Etiqueta de conversión (Conversion Label)  | Identificador de la conversión - se debe relacionar con Google Ads  |
>   | Valor de conversión (Conversion Value)  | Valor ($$$) de conversión  |
>   | ID de transacción (Transaction ID)  | Identificador de la transacción (Para relacionar la conversión con una compra o relacionado con el tipo de conversión  |
>   | Código de moneda (Currency Code)  | Moneda de conversión (COP,USD,EUR)  |
> 
> Para extraer el ID de conversión y la etiqueta de conversión en Adwords
> Lo puedes hacer directamente en Adwords y en la configuración de la etiqueta saldrá un código como el siguiente:

>  ```js
>    <!-- Event snippet for Cart conversion page -->
>    <script>
>      gtag('event', 'conversion', {'send_to': 'AW-974057167/d6zmCNW-hpEYEM_du9AD'});
>    </script>
> 

> Siendo:
>
> ID de conversión (Conversion ID): **AW-974057167** - Tiende a ser el mismo para la cuenta de Google Ads
> 
> Etiqueta de conversión (Conversion Label): **d6zmCNW-hpEYEM_du9AD** - Varía por cada Etiqueta
>
> No olvidar incluir el Linker en GTM para evitar problemas de compatibilidad.

## Pregunta 3

#### Un nuevo cliente desea fortalecer su estrategia de web analytics, ya que está próximo a lanzar una campaña de nueva colección, cuyos objetivos de negocio están enfocados en la generación de tráfico, aumentar las ventas y registros. Sin embargo es necesario verificar e implementar nuevas funcionalidades mediante Google Tag Manager.

### 3.2.■.1 ¿Qué aspectos de medición técnicos en GTM son relevantes para conocer el estado actual de la cuenta?

**Respuesta:**

> Se deben tener en cuenta los siguientes aspectos:
> - La correcta instalación del Tag Manager, que se esté ejecutando en todas las páginas.
> - Hacer revisión de las content security policies (CSP), que el sitio web no tenga un bloqueo referente a ellas.
> - Entender la estructura de la página, cómo estarán distribuidos los pasos de las ventas, qué se espera del tráfico y de la captura de registros.
> - Sumado al punto anterior, entender los objetivos del negocio. Hay que tener en cuenta la marcación actual y revisar que tan efectiva ha sido la marcación para dichos objetivos, basado en ello hacer la gestión en GTM.
> - Si existe un Iframe, dar a entender las limitaciones de incluir mediciones por iframes, de ser necesario el uso de los mismos, hacer ajustes a través del "gtag config" para gestionar rutas y demás.
> - Tener claro si la página cuenta con Shadow-DOM o No. Para evitar limitantes e implementar el código adecuado.
> - De implementarse GA4 y no ser un SPA. GA4 genera una espera de 5 segundos y un almacenamiento de 5 eventos durante ese espacio de tiempo, si se llega a cerrar o dirigirse a otra página esos eventos no llegarían a Google Analytics. Hay que hacer configuraciones adicionales para llevarlo al localStorage y luego enviar esos eventos a GA4 teniendo en cuenta ese histórico.
> - Revisar previo a lanzar la campaña los valores de las UTMs y los parámetros que se van a usar en la URL, todo esto para no perder los datos que puedan dar valor a dicha estrategia.
> - Revisar temas de SEO y SEM para el posicionamiento y generar tráfico orgánico una vez finalice la campaña.
> - Opcional: En caso de una web híbrida, tener en cuenta la tecnología que se va a usar. Implementar GTM puede variar según la plataforma o el dispositivo. (De ser posible el uso de Firebase o un script personalizado de GTM para evitar bloqueos por no tener una url con HTTP/HTTPS - __Sucede con ionic__  -> en iOS)
> - Opcional: De ser un SPA, integrar dentro del aplicativo los llamados a GTM para visualizaciones/acciones que no puedan ser registradas a través de GTM. Evitar la sobrecarga de eventos es ideal para el correcto performance de los sitios.
>
> Generalmente sugiero contar con una guía de implementación previo al lanzamiento. Mostrar cómo será a partir de la integración de las herramientas de analítica la medición y lograr tener uno estándares básicos frente a toda la página web para lograrlo. Fuera de las configuraciones que se deben hacer en GTM, si hay algo del sitio que no se pueda ajustar se solventa desde GTM.


### 3.2.■.2 ¿Qué extensiones de Google Chrome utiliza para verificar la información de datalayers, pixelación y configuraciones adicionales?

**Respuesta:**

>
>   | Extensión  | Descripción | URL |
>   | ------ |------| ------ |
>   | Dataslayer | Ver eventos en Developer Tools | https://chrome.google.com/webstore/detail/dataslayer/ikbablmmjldhamhcldjjigniffkkjgpo |
>   | Google Tag Asistant  | Ver todos los tags que están corriendo en el sitio web  | https://chrome.google.com/webstore/detail/tag-assistant-legacy-by-g/kejbdjndbnbjgmefkgdddjlbokphdefk   ** https://tagassistant.google.com/ (Está migrando) |
>   | Disable Content-Security-Policy   | Saltar bloqueos del CSP  | https://chrome.google.com/webstore/detail/disable-content-security/ieelmcmcagommplceebfedjlakkhpden |
>   | Google Analytics Debugger | Ver los eventos en consola  | https://chrome.google.com/webstore/detail/google-analytics-debugger/jnkmfdileelhofjcijamephohjechhna |
>   | Meta Pixel Helper  | Para validar pixel de facebook | https://chrome.google.com/webstore/detail/meta-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc |
>   | Tag Assistant for Conversions Beta | Validar conversiones de Google Ads | https://chrome.google.com/webstore/detail/tag-assistant-for-convers/llpfnmnallbompdmklfkcibfpcfpncdd |
>   | Tag Assistant Companion | Debuggear Tag Assistant | https://chrome.google.com/webstore/detail/tag-assistant-companion/jmekfmbnaedfebfnmakmokmlfpblbfdm
>   | Adobe Experience Platform Debugger | Debuggear Adobe | https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob
>   | Wappalyzer | Ver con qué está construida la página y qué corre en ella | https://chrome.google.com/webstore/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg
> 
> Según la información o datos que se necesiten se puede utilizar puntualmente alguna de ellas, aunque mis favoritas son DataSlayer, Wappalyzer y Tag Asistant Companion. 
>
> Hay otras para otras para ver la captura de los píxeles/conversiones pero menciono sólo la de Facebook y Google Ads.
>
>
### 3.2.■.4 El cliente presenta una redirección del sitio web principal a una landing de registros, los cuales están en diferentes dominios, sin embargo desea tener medición unificada de tráfico.
* ¿Qué recomendaciones técnicas le propondría al cliente?
* Haga las implementaciones técnicas necesarias en Google Tag Manager, con datos de prueba para hacer esa vinculación de dominios.

**Respuesta:**

> Para el cliente le daría las siguientes recomendaciones:
> * Configurar la misma propiedad de GTM tanto en la web principal como el landing.
> * Se podría incluir un Cross Domain Linker, todo para identificar los clientes que viajan desde un sitio a la landing.
> * Generar ciertos parámetros en las urls para identificar el origen o para llevar información del cliente de un dominio a otro.
> * De ser posible migrar la landing al mismo dominio manejando micrositios.
> * Tener claro el objetivo de conversión del formulario de registros.
>
> #### Implementaciones técnicas ####
> Respecto a GTM lo único es integrar dentro de la variabe del dominio la misma propiedad de GA4.
> 
> Las implementaciones adicionales se hacen directamente en la configuración de la propiedad de GA4
>
> ### En Data Stream ###
> * Se incluyen ambos dominios
> * En el Stream del dominio principal se hace el Link entre los 2 dominios
>  * Se va a configurar ajustes del tag
>  * Configurar tus dominios -> Poner el dominio principal, seguido por el dominio de la landing.
>
> De esa manera todos los links que dirijan al landing van a tener la siguiente escructura:
> https://dominiolanding.com/landing?_gl=1*nvg38b*_ga*MTI2MTI2OTM2OS4xNjc4NjU3NDcy*_ga_LGBSYTM31L*MTY3ODcxNjUyMS40LjEuMTY3ODcxNzE1NS4wLjAuMA..
>
> Llevando principalmente la información del clientID y sessión.
> 
> Se podría incluir en los links parámetros específicos y llevarlos a una cookie, localstorage... para poder hacer seguimiento de las campañas y demás.
> 
> 

## Pregunta 4

####  Caso: Un cliente nuevo de retail en la industria de moda necesita conocer el estado actual de su herramientas de medición, y partir de esto, llevar su estrategia de analitica web un paso más adelante. Algunas consideraciones especiales del cliente: ####

* La plataforma de desarrollo usada es Magento.
* El cliente tiene ventas superiores a 5000 transacciones por mes.


### 4.1 ¿Qué aspectos de medición son relevantes para conocer el estado actual de la cuenta? ###

**Respuesta:**

> Ya que conocemos que hay 5000 transacciones al mes, debemos analizar la medición en los siguientes aspectos:
>
> * Cuánto trafico tiene mensual, hacer una revisión si es variable o es constante.
> * Conocer las fuentes de dónde provienen los usuarios.
> * Reconocer si son visitantes recurrentes y nuevos.
> * Entender el tiempo que duran los usuarios en su portal.
> * Analizar la tasa de rebote.
> * Rendimiento de las páginas, posiblemente tengamos que chequear con herramientas como lighthouse los tiempos de carga del sitio.
> * Comportamiento de los usuarios, conocer páginas o productos más visitados.
> * Revisar la configuración de las herramientas de analítica, Magento por ser ahora parte de Adobe puede generar mediciones adicionales desde AEM. También revisar la configuración correspondiente respecto a Google Tag Manager y Analytics.
> * Entender cuándo se dieron los picos más altos y si hubo una campaña de por medio


### 4.2 El usuario no conoce de dónde está llegando tráfico a su sitio web ¿Qué recomendaciones le daría al cliente para mejorar el entendimiento de las fuentes de tráfico? ###

**Respuesta:**

> Generalmente cuando se habla de fuentes de tráfico se hace referencia a seguimiento a través de UTM (Urchin Traffic Monitor). Hay que gestionar los enlaces hacia el sitio web y entender el origen de cada una de las visitas y comprender de una mejor manera el público de la página.
> 
> De la misma manera, tenemos una Consola de búsqueda en Google, que nos permite entender por qué palabras nos encuentran los usuarios y entran de manera orgánica a través del buscador.
> 
> Hay más fuentes como la directa, o redes sociales. Que también nos permiten entender de dónde llegan.
>
> Recomendación: Primero analizar cómo se han dado las visitas hasta la fecha, entender en dónde se quiere reforzar la captura o qué productos se quieren dar a conocer, si es necesario dar inicio a una campaña a través de las redes que según el estudio sea la más importante, cambiar los links en los medios de comunicación para que tengan una estructura correcta, analizar si google analytics está usando todas las funcionalidades para detectar las fuentes de tráfico.

### 4.3 El cliente presenta duplicidad en la información de transacciones, ¿Qué aspectos técnicos revisaría?, ¿Qué posibles soluciones le daría al cliente para mejorar la discrepancia en información? ###

**Respuesta:**

> ### Revisar ###
> * A través de las extensiones del navegador si hay múltiples gestores de etiquetas corriendo en su sitio.
> * Los triggers y los tags que se están disparando.
> * La propiedad de Google Analytics, hay usuarios que no se dan cuenta que tienen las métricas mejoradas y envían dos veces los eventos que ya se capturan por defecto.
> * La configuración de Magento, si hay alguna extensión que esté generando una marcación adicional a la que haya en GTM.
> * Los HTMLs dentro de los tags, hay veces que el código es tipo espaguetti y nadie logra entender qué está causando la duplicidad.
> 
> ### Soluciones ###
> * Eliminar extensiones innecesarias de Magento.
> * Seguir unos lineamientos para el etiquetado.
> * Hacer consultas a través de BigQuery para omitir los datos duplicados.
> * Ajustar GTM con un etiquetado claro y fundamentado.
> * Entender qué se busca resolver con el etiquetado, adicionalmente, conocer al cliente y el producto lleva un éxito para evitar errores en los datos capturados.

### 4.4 Actualmente está configurada la medición básicas de google analytics de comercio electrónico, es decir, medición de transacciones y rendimiento de productos, sin embargo se desea conocer todos los aspectos relacionado al comportamiento de compra del usuario, ¿Que implementaciones técnicas recomendarias para completar la información de comercio electrónico?¿Qué beneficios se obtienen a partir de esta implementación? ###

**Respuesta:**

> 1. Haría falta integrar eventos: 
>  * La parte de visualización e interacción con promociones
>  * Selección de productos
>  * Agregar al carro
>  * Seguimiento al proceso de compra.
> 2. Gestionar embudos de conversión.
> 3. Hacer un seguimiento de eventos para la compra.
> 4. Analisis de los segmentos de compra.
> 5. Posiblemente una integración con otras herramientas de CRM, remarketing, entre otros.
> 
> Con los __eventos__ podemos entender los comportamientos de compra de los clientes.
> 
> Teniendo todos los eventos dentro de la página, los __embudos de conversión__ hacen que se puedan identificar si hay problemas en el proceso de compra o hay oportunidades de mejora.
> 
> El __seguimiento a los eventos__ de compra puede generar nuevas estrategias para que los clientes recurrentes adquieran más productos dentro del flujo al que están acostumbrados.
> 
> Análisis de los __segmentos de compra__ para analizar los patrones según las diferentes ubicaciones o atributos que identifican a un grupo los clientes.
>
> __Herramientas de CRM/Remarketing/Otras__, para llegar de una manera más directa al cliente y poder hacer estratégias de compra directa o de recuperación en abandonos.

### 4.3 ¿Qué piensa de GA4?¿Qué aspectos considera destacados para esta nueva versión de analytics? ###

**Respuesta:**
> 
> Desde que manejaba universal yo pensaba en los __eventos__ como un atributo primario como ahora lo piensa GA4, muchas veces en las implementaciones se generaban custom dimensions que se referían a lo mismo. Ahora se ve de una manera más estructurada la captura de los eventos, puedes tener una jerarquía mejor establecida por cada evento, te da la posibilidad de tener eventos personalizados con características propias de ese evento, no tienes que enviar miles de custom dimensions para un único evento sino los específicos del mismo. Pero hay cosas que todavía no me parecen óptimas y es que si te vas por el lado de bigQuery al analizar los datos, cada elemento que creas te va a llenar la columna de nulls, eso hace que sea poco óptimo la extracción de la data. Un usuario podría jugar el papel de troll y crear miles de columnas que van a seguir apareciendo en tus consultas de bigQuery como null para todos los eventos. Adicionalmente, Los problemas asociados a la espera de 5 segundos para el envío de un evento a Google Analytics que se solucionan programando 5 minutos más. O el timestamp asociado a los eventos captados desde el servidor, muchos eventos podrían viajar al mismo tiempo y no podrías identificar el primero de ellos. Son cosas que hacen falta por mejorar pero es una apuesta a un futuro en el que identificar al usuario va a jugar un rol importante en un mundo sin cookies.


