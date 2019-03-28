---
title: Erstellen von Graphen und Diagrammen mit SQL und R-Funktionen – SQL Server-Machine Learning
description: 'Tutorial: Erstellen von Graphen und Diagrammen mit R-Sprache-Funktionen in SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0ed226a4c11c002d048572f58a75c0c04bdf936c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513167"
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>Erstellen von Graphen und Diagrammen mit SQL und R (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Teil der exemplarischen Vorgehensweise erfahren Sie, Verfahren zum Erstellen von Diagrammen und Karten, die mithilfe von R mit SQL Server-Daten. Sie erstellen ein einfaches Histogramm, und klicken Sie dann eine komplexere kartenzeichnung zu entwickeln.

## <a name="prerequisites"></a>Erforderliche Komponenten

Dieser Schritt setzt voraus, eine laufende R-Sitzung basierend auf den vorherigen Schritten in dieser exemplarischen Vorgehensweise. Er verwendet die Zeichenfolgen und Data Source Verbindungsobjekte in diesen Schritten erstellt haben. Die folgenden Tools und Pakete werden verwendet, um das Skript auszuführen.

+ Rgui.exe zum Ausführen von R-Befehlen
+ Management Studio zum Ausführen von T-SQL
+ googMap
+ Ggmap-Paket
+ Mapproj-Paket

## <a name="create-a-histogram"></a>Erstellen eines Histogramms

1. Erstellen Sie die erste Zeichnung mithilfe der [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) -Funktion.  Die RxHistogram-Funktion in Open-Source-R-Pakete, die ähnliche Funktionen bietet, aber Sie können in einem remoten Ausführungskontext ausgeführt.

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
    > Aussehen Ihr Diagramm anders?
    >  
    > Der Grund dafür ist _InDataSource_ verwendet nur die ersten 1000 Zeilen. Die Reihenfolge der Zeilen mit TOP ist nicht deterministisch in Abwesenheit einer ORDER BY-Klausel so, dass die Daten und das resultierende Diagramm variieren erwartet wird.
    > Dieses bestimmte Bild wurde mithilfe von ca. 10.000 Datenzeilen generiert. Wir empfehlen daher, mit einer unterschiedlichen Anzahl von Zeilen zu experimentieren, um verschiedene Diagramme zu erhalten. Beachten Sie, wie lange es dauert, bis die Ergebnisse in Ihrer Umgebung zurückgegeben werden.

## <a name="create-a-map-plot"></a>Erstellen einer kartenzeichnung

In der Regel blockieren Datenbankserver den Zugriff auf das Internet. Dies kann umständlich sein, bei Verwendung von R-Pakete, die zum Herunterladen von Zuordnungen oder anderen Bildern um Plots generieren müssen. Es ist jedoch eine problemumgehung, die hilfreich sein könnten bei der Entwicklung Ihrer eigenen Anwendungen. Im Grunde Sie die kartendarstellung auf dem Client zu generieren, und klicken Sie dann auf der Karte überlagert die Punkte, die als Attribute in der SQL Server-Tabelle gespeichert werden.

1. Definieren Sie die Funktion, die das R-Diagrammobjekt erstellt. Die benutzerdefinierte Funktion *MapPlot* erstellt ein Punktdiagramm, das die abholorte des Taxis verwendet, und zeichnet die Anzahl der Fahrten an, die von jedem Standort gestartet. Er verwendet den **"ggplot2"** und **Ggmap** -Pakete, die bereits liegen [installiert und geladen](walkthrough-data-science-end-to-end-walkthrough.md#add-packages).

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

    + Die *MapPlot* Funktion akzeptiert zwei Argumente: ein vorhandenes Datenobjekt, das Sie zuvor mithilfe von RxSqlServerData definiert, und die kartendarstellung, die vom Client übergeben wurde.
    + In der Zeile, beginnend mit der *ds* Variable RxImport wird verwendet, um in Memory-Daten aus der zuvor erstellten Datenquelle laden *InDataSource*. (Diese Datenquelle nur 1000 Zeilen enthält, wenn Sie eine Karte mit der Anzahl von Datenpunkten erstellen möchten, können Sie eine andere Datenquelle ersetzen.)
    + Wenn Sie Open-Source-R-Funktionen verwenden, müssen Daten in Datenrahmen im lokalen Arbeitsspeicher geladen werden. Allerdings durch Aufrufen der [RxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) -Funktion, die Sie ausführen können, im Arbeitsspeicher des dem entfernten computekontext.

2. Ändern Sie den computekontext lokalen aus, und Laden Sie die Bibliotheken, die zum Erstellen von Zuordnungen erforderlich sind.

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + Die Variable `gc` speichert mehrere Koordinaten für den Times Square, NY.

    + Die Zeile, die mit `googmap` beginnt, generiert eine Karte mit den angegebenen Koordinaten in der Mitte.

3. Wechseln Sie zu den SQL Server-computekontext, und Rendern Sie die Ergebnisse, indem Sie die Zeichnungsfunktion in [RxExec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec) wie hier gezeigt. Die RxExec-Funktion ist Teil der **RevoScaleR** -Paket und unterstützt die Ausführung beliebiger R-Funktionen in einem remotecomputekontext.

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + Die Kartendaten in `googMap` als Argument übergeben wird, die an die Remote ausgeführte Funktion *MapPlot*. Da die Zuordnungen in Ihrer lokalen Umgebung generiert wurden, müssen sie an die Funktion übergeben werden, um das Diagramm im Kontext von SQL Server zu erstellen.

    + Wenn die Zeile ab `plot` ausgeführt wird, der gerenderten Daten zurück an die lokale R-Umgebung serialisiert wird, sodass Sie sie in Ihrem R-Client sehen können.

    > [!NOTE]
    > Wenn Sie SQL Server in virtuellen Azure-Computer verwenden, Sie erhalten möglicherweise einen Fehler an diesem Punkt. Ein Fehler tritt auf, wenn die Firewall-Standardregel in Azure Netzwerkzugriff durch R-Code blockiert wird. Weitere Informationen darüber, wie Sie diesen Fehler zu beheben, finden Sie unter [Installieren von Machine Learning (R)-Dienste auf einer Azure-VM](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

4. In der folgenden Abbildung ist das ausgegebene Diagramm dargestellt. Die Taxi-Abholorte wurden zur Karte als rote Punkte hinzugefügt. Ihr Image sieht möglicherweise anders, je nach Anzahl der Standorte in der Datenquelle, die Sie verwendet zu werden.

    ![Zeichnen von Taxifahrten mithilfe einer benutzerdefinierten R-Funktion](media/rsql-e2e-mapplot.png "plotting taxi rides using a custom R function")

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von Datenfunktionen mit R und SQL.](walkthrough-create-data-features.md)
