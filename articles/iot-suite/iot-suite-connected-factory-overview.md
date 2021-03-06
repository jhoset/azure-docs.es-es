---
title: "Información general de la fábrica conectada del Conjunto de aplicaciones de IoT de Azure | Microsoft Docs"
description: "Descripción de la solución preconfigurada de fábrica conectada del Conjunto de aplicaciones de IoT de Azure."
services: 
suite: iot-suite
documentationcenter: 
author: dominicbetts
manager: timlt
editor: 
ms.assetid: 
ms.service: iot-suite
ms.devlang: na
ms.topic: hero-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/24/2017
ms.author: dobett
ms.translationtype: Human Translation
ms.sourcegitcommit: 44eac1ae8676912bc0eb461e7e38569432ad3393
ms.openlocfilehash: 90ed1d5ca50bfb19a9d1c5d258e9588e05893270
ms.contentlocale: es-es
ms.lasthandoff: 05/17/2017


---
# <a name="get-started-with-the-connected-factory-preconfigured-solution"></a>Introducción a la solución preconfigurada de fábrica conectada

## <a name="introduction"></a>Introducción

Las [soluciones preconfiguradas][lnk-preconfigured-solutions] del Conjunto de aplicaciones de IoT de Azure combinan varios servicios de IoT de Azure para ofrecer soluciones integrales que implementan escenarios empresariales de IoT comunes. La solución preconfigurada *fábrica conectada* permite conectar y supervisar dispositivos industriales. Puede usar la solución para analizar el flujo de datos de los dispositivos y administrar la productividad y la rentabilidad de las operaciones.

Este tutorial muestra cómo aprovisionar la solución preconfigurada de fábrica conectada. También le guía por las características básicas de la solución preconfigurada. Puede acceder a muchas de estas características desde el *panel* de soluciones que se implementa como parte de la solución preconfigurada:

![panel de la solución preconfigurada de fábrica conectada][img-cf-home]

Para completar este tutorial, deberá tener una suscripción activa de Azure.

> [!NOTE]
> En caso de no tener ninguna, puede crear una cuenta de evaluación gratuita en tan solo unos minutos. Para más información, consulte la [evaluación gratuita de Azure][lnk_free_trial].
> 
> 

## <a name="provision-the-solution"></a>Aprovisionamiento de la solución

1. Inicie sesión en azureiotsuite.com con sus credenciales de la cuenta de Azure y haga clic en "**+**" para crear una solución.
2. Haga clic en **Seleccionar** en el icono **Fábrica conectada**.
3. Escriba un valor en **Nombre de la solución** para la solución preconfigurada de fábrica conectada.
4. Seleccione la **Suscripción** y **Región** que desea usar para aprovisionar la solución.
5. Haga clic en **Crear solución** para comenzar el proceso de aprovisionamiento. Este proceso normalmente tarda varios minutos en ejecutarse.

### <a name="while-you-wait-for-the-provisioning-process-to-complete"></a>Mientras espera a que se complete el proceso de aprovisionamiento

1. Haga clic en el icono de la solución con el estado **Aprovisionando**.
2. Observe los **estados de aprovisionamiento** , ya que los servicios de Azure se implementan en su suscripción de Azure.
3. Una vez que se complete el aprovisionamiento, el estado cambia a **Listo**.
4. Haga clic en el icono y verá los detalles de la solución en el panel derecho.

> [!NOTE]
> Si surgen problemas al implementar la solución preconfigurada, revise las secciones [Permisos en el sitio azureiotsuite.com][lnk-permissions] y [Preguntas más frecuentes][lnk-faq]. Si los problemas persisten, cree un vale de servicio en el [portal][lnk-portal].

¿Hay detalles que esperaría ver que no aparezcan para su solución? Puede sugerirnos nuevas características en [User Voice](https://feedback.azure.com/forums/321918-azure-iot)(La voz del usuario).

## <a name="scenario-overview"></a>Información general de escenario

Al implementar la solución preconfigurada de fábrica conectada, esta se rellena previamente con los recursos que le permiten recorrer un escenario industrial común. En este escenario, varias fábricas conectadas a la solución informan de los valores de datos necesarios para calcular la eficiencia general de los equipos (OEE) y los indicadores clave de rendimiento (KPI). Las secciones siguientes le indicarán cómo:

* Supervisar los valores de la fábrica, las líneas de producción, el valor de OEE de las estaciones y los valores de KPI
* Analizar los datos de telemetría generados por estos dispositivos con Azure Time Series Insights
* Actuar sobre las alertas para solucionar problemas

Una característica clave de este escenario es que se pueden realizar todas estas acciones de forma remota desde el panel de la solución. No es necesario el acceso físico a los dispositivos.

## <a name="view-the-solution-dashboard"></a>Visualización del panel de soluciones

El panel de la solución permite administrar la solución implementada. Es una representación jerárquica de una configuración de fábrica global. Por ejemplo, puede ver los valores de OEE y KPI, publicar nuevos nodos para telemetría y actuar sobre las alertas.

1. Cuando se haya completado el aprovisionamiento y el icono de la solución preconfigurada indique **Listo**, seleccione **Iniciar** para abrir el portal de la solución de fábrica conectada en una nueva pestaña.

    ![Iniciar la solución preconfigurada][img-launch-solution]

1. De forma predeterminada, el portal de la solución muestra el *panel*. Use el menú del lado izquierdo de la página para navegar a otras áreas del portal.

    ![Panel de la solución preconfigurada de fábrica conectada][cf-img-menu]

El panel muestra la siguiente información:

* Un panel **Lista de fábricas** que muestra el estado, la ubicación y la configuración actual de producción de la solución. La primera vez que se ejecuta la solución hay una serie de dispositivos simulados. La simulación de la línea de producción se compone de tres servidores OPC UA reales por línea de producción que realizan tareas simuladas y comparten datos. 
* Un **mapa** que muestra la ubicación de cada dispositivo conectado a la solución. La solución puede utilizar la API de Bing Maps para trazar la información en el mapa. Si la suscripción está habilitada para la API de Bing Maps Enterprise, esta característica se usa automáticamente. Si no es así, consulte las [preguntas más frecuentes][lnk-faq] para obtener información sobre cómo hacer que el mapa se vuelva dinámico.
* Un panel de **Alertas**, que muestra las alertas generadas cuando un valor de OEE, KPI o telemetría supera un umbral específico.
* Un panel **Eficiencia general de los equipos** que muestra los valores de OEE para toda la empresa o para la fábrica, línea de producción o estación que esté visualizando. Este valor se agrega desde la vista de estación hasta el nivel de empresa. La cifra de OEE y sus elementos constituyentes se pueden analizar aún más.
* Un panel de **Indicadores clave de rendimiento** que muestra el número de unidades producidas y energía usada por toda la empresa o por la fábrica, línea de producción o estación que esté visualizando. Estos valores se agregan desde la vista de estación hasta el nivel de empresa.

## <a name="view-factories"></a>Visualización de fábricas

El panel *Fábricas* muestra la ubicación geográfica de todas las fábricas incluidas en la solución, su estado y la configuración de producción actual. En la lista de ubicaciones, puede navegar a los otros niveles de la jerarquía de la solución. Las filas de la lista son hipervínculos que vinculan los detalles de las líneas de producción en esa ubicación. Así es posible profundizar en los detalles de la línea de producción y descender hasta la vista de estación. También puede aplicar un filtro a la lista.

![Fábricas de la solución preconfigurada de fábrica conectada][cf-img-factories] 

1. El **panel Fábrica** muestra la lista de fábricas para esta solución.

2. La lista de fábricas muestra inicialmente seis fábricas creadas por el proceso de aprovisionamiento, pero se pueden agregar más dispositivos simulados y físicos a la solución.

3. Para ver los detalles de una fábrica, haga clic en la fila de la lista de fábricas.

4. Para ver los detalles de una línea de producción, haga clic en la fila de la lista.

5. Para ver los nodos OPC UA publicados de una estación de la línea de producción, haga clic en la fila en la lista.

6. Para ver los detalles en un nodo específico de la estación, haga clic en la fila en la lista. Esta acción inicia el panel de contexto con visualizaciones de Time Series Insights. Haga clic en estos gráficos para realizar más análisis en el entorno del explorador de Time Series Insights.

## <a name="view-map"></a>Visualización de mapas

Si su suscripción tiene acceso a la API de Bing Maps, el mapa *Fábricas* muestra la ubicación geográfica y el estado de todas las fábricas incluidas en la solución. Haga clic en las ubicaciones que se muestran en el mapa para profundizar en los detalles de ubicación.

![Mapa de la solución preconfigurada de fábrica conectada][cf-img-map]

## <a name="view-alerts"></a>Visualización de alertas

El historial del panel **Alerta** muestra las alertas que se están generando debido a que un valor notificado o un valor calculado de OEE o KPI supera el umbral configurado. Este panel muestra las alertas en cada nivel de la jerarquía, desde la vista de nivel de estación a la vista global. Las alertas contienen una descripción de la alerta, fecha, hora, ubicación y número de repeticiones. Puede obtener más información de los datos que provocaron la alerta usando los datos de Time Series Insights. Los datos de Time Series Insights se visualizan en las alertas, si procede. Si es un administrador, puede realizar acciones predeterminadas en las alertas, tales como:

* Cierre la alerta.
* Confirme la alerta.

Si lo desea, puede realizar acciones más complejas. Por ejemplo, para el nodo Presión de OPC UA del ensamblado, podría:

* Cargar una página web en una nueva ventana del explorador para mostrar información de soporte técnico.
* Llamar a un método de OPC UA en el dispositivo que mitigue la causa de la alerta.
* Suprimir la disponibilidad de las acciones predeterminadas.

    ![Alertas de la solución preconfigurada de fábrica conectada][cf-img-alerts]

> [!NOTE]
> Estas alertas las generan las reglas que se especifican en un archivo de configuración de la solución preconfigurada. Estas reglas pueden generar alertas cuando las cifras de OEE o KPI o los valores de nodo OPC UA superan el umbral configurado.

1. El **Panel de alertas** muestra las alertas generadas en esta solución.

2. Para ver los detalles de una alerta, haga clic en la alerta en el panel de alertas.

3. Para analizar con mayor profundidad los datos de alerta, haga clic en el gráfico en el panel de alertas para abrir el entorno del explorador de Time Series Insights.

4. Para resolver la alerta, hay disponibles varias acciones en el panel de alertas. Elija la opción adecuada y haga clic en el botón del comando para ejecutar la acción.

## <a name="view-overall-equipment-efficiency"></a>Ver la eficiencia general de equipos

OEE evalúa la eficiencia del proceso de fabricación usando parámetros de operaciones clave relacionadas con la producción. OEE es una medida estándar de la industria que se calcula multiplicando la tasa de disponibilidad, la tasa de rendimiento y la tasa de calidad: OEE = disponibilidad x rendimiento x calidad.

![OEE de la solución preconfigurada de fábrica conectada][cf-img-oee]

1. Para ver el valor de OEE en cualquier nivel de la jerarquía, vaya a la vista específica que necesite. En esa vista, el valor de OEE se muestra en el panel junto con cada uno de los elementos que componen el porcentaje de OEE.

2. Para analizar con mayor profundidad el valor de OEE de cualquier nivel de los datos de la jerarquía, haga clic en el porcentaje de OEE, el porcentaje de disponibilidad, el porcentaje de rendimiento o el porcentaje de calidad. Aparece un panel de contexto con visualizaciones proporcionadas por Time Series Insights que muestra datos de la última hora, las últimas 24 horas y los últimos 7 días.

    ![Visualización TSI de la solución preconfigurada de fábrica conectada][cf-img-tsi-visualization]

3. Para analizar con mayor profundidad los datos de las alertas, haga clic en el gráfico en el panel de alertas. Esta acción abre el entorno de explorador de Time Series Insights.

    ![Explorador de TSI de la solución preconfigurada de fábrica conectada][cf-img-tsi-explorer]

## <a name="view-key-performance-indicators"></a>Visualización de los indicadores clave de rendimiento

La solución proporciona dos indicadores clave de rendimiento, *unidades por hora* y *energía utilizada en kWh*.

![KPI de la solución preconfigurada de fábrica conectada][cf-img-kpi]

1. Para ver las unidades por hora o la energía usada de cualquier nivel de la jerarquía, vaya a la vista específica que necesite. Las unidades por hora y la energía usada se muestran en el panel.

2. Para analizar con mayor profundidad las unidades por hora o la energía usada en cualquier nivel de los datos de la jerarquía, haga clic en el medidor de unidades producidas o en el medidor de energía usada del panel **Indicadores clave de rendimiento**. Aparece un panel de contexto con las visualizaciones proporcionadas por Time Series Insights que permite ver los datos de la última hora, las últimas 24 horas y los últimos 7 días.

## <a name="scenario-review"></a>Revisión del escenario

En este escenario, ha supervisado los valores de OEE y KPI de las fábricas en el panel. A continuación, ha utilizado Time Series Insights para proporcionar más información para ayudar a profundizar en los datos de telemetría de OEE y KPI, y ayudar a detectar anomalías. También ha utilizado el panel de alertas para visualizar los problemas en las fábricas y ha utilizado las acciones disponibles para resolver la alerta.

## <a name="other-features"></a>Otras características

Las secciones siguientes describen algunas características adicionales de la solución preconfigurada de fábrica conectada que no se han descrito como parte del escenario anterior.

## <a name="apply-filters"></a>Aplicación de filtros

1. Haga clic en las **comillas angulares** para mostrar una lista de los filtros disponibles en el panel de ubicaciones de fábrica o en el panel de alertas.

2. Se muestra el panel de filtros. 

    ![Filtros de la solución preconfigurada de fábrica conectada][cf-img-alert-filter]

3. Elija el filtro que necesite; también es posible escribir texto en los campos de filtro si lo necesita.

4. A continuación, se aplica el filtro. El estado del filtro se muestra en el panel mediante un embudo que se muestra en las tablas de fábricas y alertas.

    ![Filtros de la solución preconfigurada de fábrica conectada][cf-img-alert-filter-funnel]

    > [!NOTE]
    > Un filtro activo no afecta a los valores de OEE y KPI mostrados, solo se filtra el contenido de la lista.

5. Para borrar un filtro, haga clic en el embudo y haga clic en el filtro en el panel de contexto de filtro. Se muestra el texto **Todos** en las tablas de fábricas y alertas.

## <a name="browse-an-opc-ua-server"></a>Examinar un servidor de OPC UA

Al implementar la solución preconfigurada, se aprovisionan automáticamente los servidores de OPC UA simulados que se pueden examinar mediante el explorador de la solución. Estos servidores son *servidores de OPC UA simulados*. Los servidores simulados facilitan la experimentación de la solución preconfigurada sin necesidad de implementar servidores físicos reales. Si quiere conectar un servidor de OPC UA real a la solución, consulte cómo [conectar su dispositivo OPC UA a la solución preconfigurada de fábrica conectada][lnk-connect-cf].

1. Haga clic en el **icono de fábrica** en la barra de navegación del panel.

    ![Explorador de servidores de la solución preconfigurada de fábrica conectada][cf-img-server-browser]

2. Elija uno de los servidores de la lista preconfigurada. Esta lista muestra los servidores que se implementan en la solución preconfigurada.

    ![Selección del servidor de la solución preconfigurada de fábrica conectada][cf-img-server-choice]

3. Haga clic en **Conectar**; aparece un cuadro de diálogo de seguridad. Para la simulación, es seguro hacer clic en **Continuar**.

4. Haga clic en cualquiera de los nodos del árbol de servidores para expandirlo. Los nodos que publican telemetría tienen una marca de verificación junto a ellos.

    ![Árbol de servidores de la solución preconfigurada de fábrica conectada][cf-img-server-tree]

5. Haga clic con el botón derecho para leer, escribir, publicar o llamar a ese nodo. Las acciones disponibles dependen de los permisos y los atributos del nodo. La opción de lectura muestra un panel de contexto que muestra el valor de un nodo específico. La opción de escritura muestra un panel de contexto donde puede escribir un nuevo valor. La opción de llamada muestra un nodo donde puede especificar los parámetros para la llamada.

## <a name="publish-a-node"></a>Publicación de un nodo

Cuando se examina un *servidor de OPC UA simulado*, también puede elegir publicar nuevos nodos. Puede analizar la telemetría de estos nodos en la solución. Estos *servidores de OPC UA simulados* facilitan la experimentación de la solución preconfigurada sin necesidad de implementar dispositivos físicos reales.

1. Vaya a un nodo en el árbol del explorador de servidores de OPC UA que desea publicar.

2. Haga clic con el botón derecho en el nodo.

3. Elija **Publicar**.

    ![Nodo de publicación de fábrica conectada][cf-img-publish-node]

4. Aparece un panel de contexto que le indica que la publicación se ha realizado correctamente. El nodo aparece en la vista de nivel de estación con una marca de verificación junto a él.

    ![Publicación correcta en la solución preconfigurada de fábrica conectada][cf-img-publish-success]

## <a name="command-and-control"></a>Comando y control

La fábrica conectada le permite enviar órdenes y controlar los dispositivos industriales directamente desde la nube. Puede utilizar esta característica para responder a las alertas generadas por el dispositivo. Por ejemplo, podría enviar un comando al dispositivo desde la nube. Puede encontrar los comandos disponibles en el nodo **StationCommands** del árbol del explorador de servidores de OPC UA. En este escenario, se abre una válvula de despresurización en la estación de ensamblado de una línea de producción en Munich. Para usar la funcionalidad de comando y control, debe estar en el rol **Administrador** en la implementación de la solución preconfigurada.

1. Vaya al nodo **StationCommands** del árbol del explorador de servidores de OPC UA.

2. Elija el comando que desea usar.

3. Haga clic con el botón derecho en el nodo.

4. Elija **Llamada**.

    ![Comando de llamada de la solución preconfigurada de fábrica conectada][cf-img-call-command]

5. Aparece un panel de contexto que le informa del método al que va a llamar, y, en su caso, los detalles de los parámetros.

6. Elija **Llamada**.

    ![Contexto de llamada de la solución preconfigurada de fábrica conectada][cf-img-call-context]

7. El panel de contexto se actualiza para informarle de que la llamada al método se realizó correctamente. Para comprobar que la llamada se realizó correctamente, lea el valor del nodo de presión que se ha actualizado como resultado de la llamada.

    ![Llamada correcta de la solución preconfigurada de fábrica conectada][cf-img-call-success]


## <a name="behind-the-scenes"></a>Entre bambalinas

Al implementar una solución preconfigurada, el proceso de implementación crea varios recursos en la suscripción de Azure seleccionada. Dichos recursos se pueden ver en Azure [Portal][lnk-portal]. El proceso de implementación crea un **grupo de recursos** cuyo nombre se basa en el nombre que eligió para la solución preconfigurada:

![Solución preconfigurada en el portal de Azure][img-cf-portal]

Para ver la configuración de cada recurso, selecciónelo en la lista de recursos del grupo de recursos.

También puede ver el código fuente de la solución preconfigurada. El código fuente de la solución preconfigurada de fábrica conectada está en el repositorio de GitHub [azure-iot-connected-factory][lnk-cfgithub]:

Cuando haya terminado, puede eliminar la solución preconfigurada de la suscripción de Azure en el sitio [azureiotsuite.com][lnk-azureiotsuite]. Este sitio le permite eliminar fácilmente todos los recursos que se aprovisionaron cuando creó la solución preconfigurada.

> [!NOTE]
> Para asegurarse de eliminar todo lo relacionado con la solución preconfigurada, elimínelo en el sitio [azureiotsuite.com][lnk-azureiotsuite]. No elimine el grupo de recursos en el portal.

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha implementado una solución preconfigurada de trabajo, puede continuar su introducción al Conjunto de aplicaciones de IoT con la lectura de los artículos siguientes:

* [Tutorial de la solución preconfigurada de fábrica conectada][lnk-rm-walkthrough]
* [Conexión del dispositivo a la solución preconfigurada de fábrica conectada][lnk-connect-cf]
* [Permisos en el sitio azureiotsuite.com][lnk-permissions]

[img-cf-home]:media/iot-suite-connected-factory-overview/cf-dashboard.png
[img-launch-solution]: media/iot-suite-connected-factory-overview/launch-cf.png
[cf-img-menu]: media/iot-suite-connected-factory-overview/cf-dashboard-menu.png
[cf-img-factories]:media/iot-suite-connected-factory-overview/cf-dashboard-factory.png
[cf-img-map]:media/iot-suite-connected-factory-overview/cf-dashboard-map.png
[cf-img-alerts]:media/iot-suite-connected-factory-overview/cf-dashboard-alerts.png
[cf-img-oee]:media/iot-suite-connected-factory-overview/cf-dashboard-oee.png
[cf-img-kpi]:media/iot-suite-connected-factory-overview/cf-dashboard-kpi.png
[cf-img-tsi-visualization]:media/iot-suite-connected-factory-overview/cf-dashboard-tsi.png
[cf-img-tsi-explorer]:media/iot-suite-connected-factory-overview/tsi-explorer.png
[cf-img-server-browser]: media/iot-suite-connected-factory-overview/cf-dashboard-browser.png
[cf-img-server-choice]: media/iot-suite-connected-factory-overview/cf-select-server.png
[cf-img-server-tree]:media/iot-suite-connected-factory-overview/cf-server-tree.png
[cf-img-publish-node]:media/iot-suite-connected-factory-overview/cf-publish-node1.png
[cf-img-publish-success]:media/iot-suite-connected-factory-overview/cf-publish-success.png
[cf-img-call-command]:media/iot-suite-connected-factory-overview/cf-command-and-control-call.png
[cf-img-call-context]:media/iot-suite-connected-factory-overview/cf-command-and-control-call-button.png
[cf-img-call-success]:media/iot-suite-connected-factory-overview/cf-command-and-control-succeed.png
[img-cf-portal]:media/iot-suite-connected-factory-overview/cf-resource-group.png
[cf-img-alert-filter]:media/iot-suite-connected-factory-overview/cf-filter.png
[cf-img-alert-filter-funnel]:media/iot-suite-connected-factory-overview/cf-filter-funnel.png

[lnk_free_trial]: http://azure.microsoft.com/pricing/free-trial/
[lnk-preconfigured-solutions]: iot-suite-what-are-preconfigured-solutions.md
[lnk-azureiotsuite]: https://www.azureiotsuite.com
[lnk-portal]: http://portal.azure.com/
[lnk-cfgithub]: https://github.com/Azure/azure-iot-connected-factory
[lnk-rm-walkthrough]: iot-suite-connected-factory-sample-walkthrough.md
[lnk-connect-cf]: iot-suite-connected-factory-gateway-deployment.md
[lnk-permissions]: iot-suite-permissions.md
[lnk-faq]: iot-suite-faq.md
