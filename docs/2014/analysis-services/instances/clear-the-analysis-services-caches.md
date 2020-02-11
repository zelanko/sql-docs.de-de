---
title: Löschen der Analysis Services Caches | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6bf66fdd-6a03-4cea-b7e2-eb676ff276ff
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e35ee4b59c77c3d1b47db360d11a9b838106c1b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66080302"
---
# <a name="clear-the-analysis-services-caches"></a>Löschen des Zwischenspeichers von Analysis Services
  Zur Verbesserung der Abfrageleistung werden Daten von Analysis Services zwischengespeichert. In diesem Thema sind Empfehlungen für die Verwendung des XMLA ClearCache-Befehls enthalten. Der Befehl dient dazu, Zwischenspeicher zu leeren, die als Antwort auf eine MDX-Abfrage erstellt wurden. Die Auswirkungen der Ausführung von ClearCache sind abhängig davon, ob Sie ein tabellarisches oder ein mehrdimensionales Modell verwenden.  
  
 **Löschen des Caches für mehrdimensionale Modelle**  
  
 Für mehrdimensionale Datenbanken erstellen Analysis Services Zwischenspeicher in der Formular-Engine bei der Auswertung einer Berechnung und in der Speicher-Engine für die Ergebnisse von Dimensionsabfragen und Measuregruppenabfragen. Measuregruppenabfragen treten auf, wenn die Formel-Engine-Anforderungen Daten für eine Zellenkoordinate oder einen Teilcube abmessen. Beim Abfragen von unnatürlichen Hierarchien treten Dimensionsabfragen auf und beim Anwenden von Autoexist-Funktionen.  
  
 Beim Durchführen von Leistungstests empfiehlt es sich, den Zwischenspeicher zu löschen. Durch das Löschen des Zwischenspeichers zwischen Testläufen wird sichergestellt, dass das Zwischenspeichern die Testergebnisse nicht verzerrt, die die Auswirkungen auf eine Abfrageentwurfsänderung messen.  
  
 **Löschen des Caches für tabellarische Modelle**  
  
 Tabellarische Modelle werden im Allgemeinen im Arbeitsspeicher gespeichert, wo Aggregationen und andere Berechnungen beim Ausführen einer Abfrage ausgeführt werden. Der ClearCache-Befehl hat nur eingeschränkte Auswirkungen auf tabellarische Modelle. Bei einem tabellarischen Modell werden Daten möglicherweise dem Analysis Services-Zwischenspeicher hinzugefügt, wenn MDX-Abfragen ausgeführt werden. DAX-Measures (verwiesen durch MDX) und Autoexists-Vorgänge können im Einzelnen Ergebnisse im Formular- bzw. Dimensionszwischenspeicher zwischenspeichern. Beachten Sie jedoch, dass unnatürliche Hierarchien und Measuregruppenabfragen in der Speicher-Engine keine Ergebnisse zwischenspeichern. Darüber hinaus ist es wichtig zu wissen, dass DAX-Abfragen die Ergebnisse nicht im Formular- bzw. in der Speicher-Engine zwischenspeichern. Falls Caches als Ergebnis von MDX-Abfragen vorhanden sind, werden durch das Ausführen von ClearCache auf ein tabellarisches Modell alle zwischengespeicherten Daten vom System ungültig.  
  
 Durch das Ausführen von ClearCache wird auch der speicherinterne Cache in der xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) gelöscht. Die xVelocity-Engine behält einen kleinen Satz zwischengespeicherter Ergebnisse bei. Durch das Ausführen von ClearCache werden diese Zwischenspeicher in der xVelocity-Engine ungültig.  
  
 Schließlich werden durch das Ausführen von ClearCache auch restliche Daten entfernt, die im Arbeitsspeicher übrig sind, wenn ein tabellarisches Modell für den `DirectQuery`-Modus neu konfiguriert wird. Dies ist besonders wichtig, wenn das Modell sensible Daten enthält, die engen Kontrollen unterliegen. In diesem Fall ist das Ausführen von ClearCache eine vorbeugende Aktion, die Sie ergreifen können, um sicherzustellen, dass sensible Daten nur dort vorhanden sind, wo Sie sie erwarten. Das manuelle Löschen des Zwischenspeichers ist notwendig, wenn Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] verwenden, um das Modell bereitzustellen und den Abfragemodus zu ändern. Demgegenüber wird durch die Verwendung von [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] zur Bestimmung von `DirectQuery` auf dem Modell der Zwischenspeicher durch die Partitionen automatisch gelöscht, wenn Sie das Modell umschalten, um diesen Abfragemodus zu verwenden.  
  
 Verglichen mit den Empfehlungen zum Löschen von mehrdimensionalen Modellzwischenspeichern während der Leistungstests gibt es keine umfassende Empfehlung zum Löschen von tabellarische Modellzwischenspeichern. Wenn Sie die Bereitstellung eines tabellarischen Modells nicht verwalten, das sensible Daten enthält, gibt es keine bestimmte administrative Aufgabe, die erfordert, den Zwischenspeicher zu löschen.  
  
## <a name="clear-the-cache-for-analysis-services-models"></a>Löschen des Zwischenspeichers für Analysis Services-Modelle  
 Verwenden Sie XMLA und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], um den Zwischenspeicher zu löschen. Sie können den Zwischenspeicher auf Datenbank-, Cube-, Dimensions-, Tabellen- oder Measuregruppenebene löschen. Die folgenden Schritte zum Löschen des Zwischenspeichers auf Datenbankebene gelten für mehrdimensionale und tabellarische Modelle.  
  
> [!NOTE]  
>  Rigorose Leistungstests könnten einen umfassenderen Ansatz zum Löschen des Zwischenspeichers erfordern. Anweisungen zum Leeren von Analysis Services- und Dateisystemzwischenspeichern finden Sie im Abschnitt zum Löschen von Zwischenspeichern im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539).  
  
 Sowohl für mehrdimensionale als auch für tabellarische Modelle kann das Löschen dieser Zwischenspeicher ein zweistufiger Vorgang sein. Durch das Ausführen von ClearCache wird der Zwischenspeicher zunächst ungültig, und anschließend wird der Zwischenspeicher geleert, wenn die nächste Abfrage erhalten wird. Eine Verkleinerung an Arbeitsspeichernutzung ist nur offensichtlich, nachdem der Zwischenspeicher tatsächlich geleert wurde.  
  
 Zum Löschen des Zwischenspeichers müssen Sie einen Objektbezeichner für die `ClearCache`-Anweisung in einer XMLA-Abfrage bereitstellen. Im ersten Schritt in diesem Thema erfahren Sie, wie ein Objektbezeichner abgerufen wird.  
  
#### <a name="step-1-get-the-object-identifier"></a>Schritt 1: Abrufen des Objektbezeichners  
  
1.  Klicken Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]mit der rechten Maustaste auf ein Objekt, wählen Sie **Eigenschaften**aus, und kopieren Sie den Wert aus der ID-Eigenschaft im Bereich **Eigenschaften** . Dieser Ansatz funktioniert für die Datenbank, Cube, Dimension oder Tabelle.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Measuregruppe, und wählen Sie **Skript für Measuregruppe als**aus, um die Measuregruppen-ID abzurufen. Wählen Sie entweder **Erstellen** oder **Ändern**, und senden Sie die Abfrage an ein Fenster. Die ID der Measuregruppe ist in der Objektdefinition sichtbar. Kopieren Sie die ID der Objektdefinition.  
  
#### <a name="step-2-run-the-query"></a>Schritt 2: Ausführen der Abfrage  
  
1.  Klicken Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]mit der rechten Maustaste auf eine Datenbank, zeigen Sie auf **Neue Abfrage**, und wählen Sie anschließend **XMLA**aus.  
  
2.  Kopieren Sie das folgende Codebeispiel in das XMLA-Abfragefenster. Ändern Sie `DatabaseID` in die ID der Datenbank auf der aktuellen Verbindung.  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
      </Object>  
    </ClearCache>  
  
    ```  
  
     Alternativ können Sie einen Pfad eines untergeordneten Objekts, z. B. eine Measuregruppe, angeben, um den Zwischenspeicher nur für dieses Objekt zu löschen.  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
            <CubeID>Adventure Works</CubeID>  
            <MeasureGroupID>Fact Currency Rate</MeasureGroupID>  
      </Object>  
    </ClearCache>  
    ```  
  
3.  Drücken Sie F5, um die Abfrage auszuführen. Es sollte Folgendes angezeigt werden:  
  
    ```  
    <return xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty" />  
    </return>  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Skripterstellung für administrative Aufgaben in Analysis Services](../script-administrative-tasks-in-analysis-services.md)   
 [Überwachen einer Instanz von Analysis Services](monitor-an-analysis-services-instance.md)  
  
  
