---
title: In-Database Python Analytics für SQL-Entwickler | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 26703f73312b5531490afc7d01319d4ac290bebe
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806760"
---
# <a name="in-database-python-analytics-for-sql-developers"></a>In-Database Python Analytics für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Das Ziel dieser exemplarischen Vorgehensweise ist bereitstellen, SQL-Programmierer praktische Erfahrungen mit der Erstellung eines Machine learning-Lösung mit Python, die in SQL Server ausgeführt wird. In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie gespeicherte Prozeduren Python-Code hinzu, und führen Sie gespeicherte Prozeduren zum Erstellen und Vorhersagen aus Modellen.

> [!NOTE]
> Bevorzugen Sie R? Finden Sie unter [in diesem Tutorial](sqldev-in-database-r-for-sql-developers.md), die bietet eine ähnlichen Lösung aber werden mit R und in SQL Server 2016 oder SQL Server 2017 ausgeführt werden können.

## <a name="overview"></a>Übersicht

Der Prozess der Erstellung einer Machine Learning-Lösung ist ein komplexes, die mehrere Tools und die Koordination von Experten in mehreren Phasen umfassen können:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und Erstellen von Features, die für die Modellierung hilfreich.
+ Trainieren und Optimieren des Modells
+ Bereitstellung in der Produktion

**Der Schwerpunkt dieser exemplarischen Vorgehensweise liegt auf erstellen und Bereitstellen einer Lösung, die mithilfe von SQL Server.**

Die Daten stammen aus das bekannte NYC Taxi-DataSet. Um diese exemplarische Vorgehensweise schnell und einfach zu machen, ist die Daten entnommen. Erstellen Sie ein binäres klassifizierungsmodell, das vorhersagt, ob eine bestimmte Fahrt ein Trinkgeld oder nicht, erhalten Sie wahrscheinlich basierend auf Spalten wie z. B. den Zeitpunkt der Tag, Entfernung und einstiegsort.

Alle Vorgänge erfolgen mit [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]


- [Untersuchen und Visualisieren von Daten mithilfe von Python](sqldev-py3-explore-and-visualize-the-data.md)

    Führen Sie grundlegende datenuntersuchungen und Visualisierung von aufrufenden Python aus [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren.

- [Erstellen von Datenfunktionen mit Python in T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Erstellen Sie neue Features mit benutzerdefinierten SQL-Funktionen.
  
- [Trainieren und Speichern eines Python-Modells mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Erstellen Sie und speichern Sie die Machine Learning-Modells mithilfe von Python in gespeicherten Prozeduren.
  
    Diese exemplarische Vorgehensweise veranschaulicht, wie Sie eine binäre klassifikationsaufgabe ausführen; die Daten können auch um Modelle für Regressions- oder buchstabenerkennung bei Klassifizierung zu erstellen.

  
-  [ Operationalisieren des Modells für Python](sqldev-py6-operationalize-the-model.md)

    Nachdem das Modell in der Datenbank gespeichert wurde, rufen Sie das Modell für die Verwendung von Vorhersageabfragen [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="requirements"></a>Anforderungen

### <a name="prerequisites"></a>Erforderliche Komponenten

+ Installieren Sie eine Instanz von SQL Server 2017 mit Machine Learning-Dienste und Python aktiviert. Weitere Informationen finden Sie unter [installieren Sie SQL Server 2017 Machine Learning Services (Datenbankintern)](../install/sql-machine-learning-services-windows-install.md).
+ Die Anmeldung, die Sie für diese exemplarische Vorgehensweise verwenden, muss über Berechtigungen zum Erstellen von Datenbanken und anderer Objekte, zum Hochladen von Daten, Auswählen von Daten und Ausführen von gespeicherten Prozeduren verfügen.

### <a name="experience-level"></a>Kenntnisstand

Sie sollten mit grundlegenden Datenbankvorgängen, wie z. B. das Erstellen von Datenbanken und Tabellen, Importieren von Daten in Tabellen und Erstellen von SQL-Abfragen vertraut sein.

Ein erfahrener SQL-Programmierer sollte in der Lage sein, diese exemplarische Vorgehensweise mit [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder durch Ausführen der bereitgestellten PowerShell-Skripts abzuschließen.

Python: Grundlegende Kenntnisse ist nützlich, aber nicht erforderlich. Alle Python-Code wird bereitgestellt.

Einige Kenntnisse über PowerShell ist hilfreich.

### <a name="tools"></a>Tools

In diesem Tutorial sind davon ausgegangen, dass Sie in der Bereitstellungsphase erreicht haben. Sie Bereinigen von Daten erhalten haben, führen Sie die T-SQL-Code für das Feature engineering und den Python-Code arbeiten. Aus diesem Grund können Sie dieses Tutorial mit SQL Server Management Studio oder ein anderes Tool, das SQL-Anweisungen unterstützt abschließen.

+ [Übersicht über SQL Server-tools](https://docs.microsoft.com/sql/tools/overview-sql-tools) 

Wenn Sie möchten Ihre eigenen Python-Code entwickeln und testen oder Debuggen eine Python-Projektmappe, empfehlen wir, einer dedizierten Umgebung:

+ **Visual Studio 2017** unterstützt sowohl R und [Python](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/). Es wird empfohlen die [Data Science-Workload](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/), R und f# auch unterstützt.
+ Wenn Sie eine frühere Version von Visual Studio haben [Python-Erweiterungen für Visual Studio](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio) erleichtert das Verwalten mehrerer Python-Umgebungen.
+ PyCharm ist eine beliebte IDE für Python-Entwickler.

    > [!NOTE]
    > Im Allgemeinen vermeiden, schreiben oder testen neuen Python-Code in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Wenn der Code, den Sie in einer gespeicherten Prozedur einbetten, Probleme aufweist, sind die Informationen, die von der gespeicherten Prozedur zurückgegeben wird in der Regel nicht die Ursache des Fehlers zu ermitteln.

Verwenden Sie die folgenden Ressourcen können Sie die Planung und Durchführung eines erfolgreichen maschinelles lernen Projekt:

+ [Team Data Science-Prozess](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/overview)

### <a name="estimated-time-required"></a>Geschätzte Zeit

|Schritt| Zeit (Stunden)|
|----|----|
|Herunterladen der Beispieldaten| 0:15|
|Importieren von Daten in SQL Server mithilfe von PowerShell|0:15|
|Untersuchen und Visualisieren von Daten|0:20|
|Erstellen von Datenfunktionen mit T-SQL|0:30|
|Trainieren und Speichern eines Modells mit T-SQL|0:15|
|Operationalisieren des Modells|0:40|

## <a name="get-started"></a>Erste Schritte

  [Schritt 1: Herunterladen der Beispieldaten](demo-data-nyctaxi-in-sql.md)
