---
title: Erstellen von Diagrammen und Diagrammen mithilfe von SQL und R Functions-SQL Server Machine Learning
description: Tutorial, das zeigt, wie Diagramme und Diagramme mithilfe von R-Sprachfunktionen auf SQL Server erstellt werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f14005b8ba9d6f05d2b69deba29d83af5695f657
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470504"
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>Erstellen von Diagrammen und Plots mithilfe von SQL und R (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Teil der exemplarischen Vorgehensweise lernen Sie Techniken zum Erstellen von Diagrammen und Karten mithilfe von R mit SQL Server-Daten kennen. Sie erstellen ein einfaches Histogramm und entwickeln dann ein komplexeres Karten Diagramm.

## <a name="prerequisites"></a>Vorraussetzungen

Dieser Schritt setzt eine laufende R-Sitzung voraus, die auf vorherigen Schritten in dieser exemplarischen Vorgehensweise basiert. Dabei werden die Verbindungs Zeichenfolgen und Datenquellen Objekte verwendet, die in diesen Schritten erstellt werden. Die folgenden Tools und Pakete werden zum Ausführen des Skripts verwendet.

+ "Rgui. exe" zum Ausführen von R-Befehlen
+ Management Studio zum Ausführen von T-SQL
+ googMap
+ ggmap-Paket
+ mapproj-Paket

## <a name="create-a-histogram"></a>Erstellen eines Histogramms

1. Erstellen Sie die erste Zeichnung mithilfe der [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) -Funktion.  Die rxhistogram-Funktion bietet ähnliche Funktionen wie in Open-Source-R-Paketen, kann aber in einem Remote Ausführungs Kontext ausgeführt werden.

    ```R
    # Plot fare amount on SQL Server and return the plot
    start.time <- proc.time()
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate plot.", sep=""))
    ```

2. Das Bild wird im Grafikgerät von R für Ihre Entwicklungsumgebung zurückgegeben.  Klicken Sie z.B. in RStudio auf das Fenster **Plot** (Diagramm).  In [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]wird ein separates Grafikfenster geöffnet.

    ![Verwenden von rxHistogramm zum Darstellen von Fahrpreisen](media/rsql-e2e-rxhistogramresult.png "using rxHistogram to plot fare amounts")

    > [!NOTE]
    > Sieht das Diagramm anders aus?
    >  
    > Dies liegt daran, dass in _indatasource_ nur die obersten 1000 Zeilen verwendet werden. Die Reihenfolge von Zeilen, die Top verwenden, ist nicht deterministisch, wenn keine ORDER BY-Klausel vorhanden ist. Daher wird erwartet, dass die Daten und das resultierende Diagramm variieren können.
    > Dieses bestimmte Bild wurde mithilfe von ca. 10.000 Datenzeilen generiert. Wir empfehlen daher, mit einer unterschiedlichen Anzahl von Zeilen zu experimentieren, um verschiedene Diagramme zu erhalten. Beachten Sie, wie lange es dauert, bis die Ergebnisse in Ihrer Umgebung zurückgegeben werden.

## <a name="create-a-map-plot"></a>Erstellen eines Karten Diagramms

Datenbankserver blockieren in der Regel den Internet Zugriff. Dies kann unpraktisch sein, wenn R-Pakete verwendet werden, die Zuordnungen oder andere Bilder zum Generieren von Plots herunterladen müssen. Es gibt jedoch eine Problem Umgehung, die Sie beim Entwickeln Ihrer eigenen Anwendungen möglicherweise nützlich finden. Im Grunde generieren Sie die Kartendarstellung auf dem Client und überlagern dann die Punkte, die als Attribute in der SQL Server Tabelle gespeichert werden.

1. Definieren Sie die Funktion, mit der das R-Zeichnungsobjekt erstellt wird. Die benutzerdefinierte Funktion *mapplot* erstellt ein Punkt Diagramm, das die Taxi Abhol Orte verwendet, und gibt die Anzahl der Fahrten an, die von jedem Standort aus gestartet wurden. Dabei werden die Pakete **ggplot2** und **ggmap** verwendet, die bereits [installiert und geladen](walkthrough-data-science-end-to-end-walkthrough.md#add-packages)sein sollten.

    ```R
    mapPlot <- function(inDataSource, googMap){
        library(ggmap)
        library(mapproj)
        ds <- rxImport(inDataSource)
        p <- ggmap(googMap)+
        geom_point(aes(x = pickup_longitude, y =pickup_latitude ), data=ds, alpha =.5,
    color="darkred", size = 1.5)
        return(list(myplot=p))
    }
    ```

    + Die *mapplot* -Funktion erfordert zwei Argumente: ein vorhandenes Datenobjekt, das Sie zuvor mithilfe von rxsqlserverdata definiert haben, sowie die Kartendarstellung, die vom Client weitergegeben wurde.
    + In der Zeile, die mit der *DS* -Variablen beginnt, wird rximport verwendet, um Daten aus der zuvor erstellten Datenquelle *indatasource*in den Arbeitsspeicher zu laden. (Diese Datenquelle enthält nur 1000 Zeilen. Wenn Sie eine Zuordnung mit weiteren Datenpunkten erstellen möchten, können Sie eine andere Datenquelle ersetzen.)
    + Wenn Sie Open Source-R-Funktionen verwenden, müssen Daten in Datenrahmen im lokalen Arbeitsspeicher geladen werden. Durch Aufrufen der [rximport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) -Funktion können Sie jedoch im Arbeitsspeicher des remotecomputekontexts ausführen.

2. Ändern Sie den computekontext in local, und laden Sie die Bibliotheken, die zum Erstellen der Zuordnungen erforderlich sind.

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + Die Variable `gc` speichert mehrere Koordinaten für den Times Square, NY.

    + Die Zeile, die mit `googmap` beginnt, generiert eine Karte mit den angegebenen Koordinaten in der Mitte.

3. Wechseln Sie zum SQL Server computekontext, und Rendering Sie die Ergebnisse, indem Sie die plotfunktion in [rxexec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec) umschließt, wie hier gezeigt. Die rxexec-Funktion ist Teil des **revoscaler** -Pakets und unterstützt die Ausführung beliebiger R-Funktionen in einem remotecomputekontext.

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + Die Kartendaten in `googMap` werden als Argument an die Remote ausgeführte *mapplot*-Funktion übermittelt. Da die Zuordnungen in der lokalen Umgebung generiert wurden, müssen Sie an die-Funktion übermittelt werden, um das Diagramm im Kontext von SQL Server zu erstellen.

    + Wenn die Zeile, die `plot` mit beginnt, ausgeführt wird, werden die gerenderten Daten zurück in die lokale R-Umgebung serialisiert, sodass Sie Sie in Ihrem R-Client anzeigen können.

    > [!NOTE]
    > Wenn Sie SQL Server auf einem virtuellen Azure-Computer verwenden, erhalten Sie möglicherweise eine Fehlermeldung. Ein Fehler tritt auf, wenn die standardmäßige Firewallregel in Azure den Netzwerk Zugriff durch R-Code blockiert. Ausführliche Informationen zum Beheben dieses Fehlers finden Sie unter [Installieren von Machine Learning (R)-Diensten auf einem virtuellen Azure](../install/sql-machine-learning-azure-virtual-machine.md)-Computer.

4. In der folgenden Abbildung ist das ausgegebene Diagramm dargestellt. Die Taxi-Abholorte wurden zur Karte als rote Punkte hinzugefügt. Das Image sieht unter Umständen anders aus, je nachdem, wie viele Standorte in der von Ihnen verwendeten Datenquelle gespeichert sind.

    ![Zeichnen von Taxifahrten mithilfe einer benutzerdefinierten R-Funktion](media/rsql-e2e-mapplot.png "plotting taxi rides using a custom R function")

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von Datenfunktionen mithilfe von R und SQL](walkthrough-create-data-features.md)
