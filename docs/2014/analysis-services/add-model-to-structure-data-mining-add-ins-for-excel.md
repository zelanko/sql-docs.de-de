---
title: Hinzufügen eines Modells zu einer Struktur (Data Mining-Add-ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, creating
ms.assetid: 8efd5bf4-4e6a-4ee8-971a-6efaed5f3b76
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce68071f27897e181063299e561dfaa7d9f8aab7
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66062874"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a>Hinzufügen eines Modells zu einer Struktur (Data Mining-Add-Ins für Excel)
  ![Hinzufügen eines Modells zu einer Struktur Schaltfläche](media/dmc-addmodel.gif "Modell einer Struktur Schaltfläche hinzufügen")  
  
 Beim Klicken auf **Modell einer Struktur hinzufügen**, ein Assistent gestartet, die Ihnen hilft, erstellen ein neues Miningmodell für die Verwendung mit einer vorhandenen Miningstruktur. Diese Option ist hilfreich, da sie die Möglichkeit bietet, Modelle zu vergleichen, die auf denselben Daten basieren, oder benutzerdefinierte Modelle zu erstellen.  
  
 Wenn die Instanz von Analysis Services bereits die keine Daten Sie benötigen, verwenden Sie die [Create Mining Structure &#40;SQL Server Data Mining-Add-ins&#41; ](create-mining-structure-sql-server-data-mining-add-ins.md) Assistenten zum Einrichten einer Miningstruktur. Alternativ können Sie einen der Modellierungs-Assistenten starten und der mit dem Assistenten erstellten Struktur ein neues Modell hinzufügen.  
  
 Um erweiterte Modelle mithilfe von Algorithmen, die nicht unterstützt, indem Sie den Assistenten zu erstellen, erstellen Sie eine Miningstruktur, und fügen Sie dann auf ein Modell mithilfe der **erweiterten Editor für Data Mining**.  
  
## <a name="add-a-new-model-to-an-existing-structure"></a>Hinzufügen eines neuen Modells zu einer vorhandenen Struktur  
  
1.  Auf der **Data Mining** des Menübands, klicken Sie auf den Pfeil unter **erweitert**, und wählen Sie dann **Modell einer Struktur hinzufügen**.  
  
2.  In der **Struktur auswählen** Dialogfeld Wählen Sie die Struktur, die Daten enthält, Sie verwenden möchten, und klicken Sie dann auf **Weiter**.  
  
     **Tipp**: Wenn Sie nicht sicher sind, welche Miningstruktur die Daten werden müssen, verwenden die **Dokumentmodell** Assistenten, um die Spalten und grundlegende Statistiken zu den Daten anzuzeigen.  
  
     Wenn Sie eine Miningstruktur nicht finden, überprüfen Sie die Verbindung, die Sie derzeit verwenden. Möglicherweise müssen Sie eine Verbindung mit einem anderen Server herstellen.  
  
3.  In der **Miningalgorithmus auswählen** Dialogfeld Wählen ein Mining-Algorithmus in das neue Miningmodell verwenden.  
  
     Beachten Sie, dass Sie das Dialogfeld bietet noch viel mehr Optionen als Sie in den Assistenten sehen werden. Sie können ein Modell mit einem beliebigen, auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server unterstützten Algorithmus erstellen, sofern die Daten kompatibel sind.  
  
4.  Es wird empfohlen, dass Sie auch auf die **Parameter** die Schaltfläche, um die **Algorithmusparameter** Dialogfeld Feld und Parameter für den Algorithmus anpassen. Mit dieser Option können am einfachsten benutzerdefinierte Miningmodelle erstellt werden.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  In der **Select Columns** Dialogfeld überprüfen Sie die Liste der Spalten, und ändern Sie ggf. die Verwendung der Spalten auf einen der folgenden Werte:  
  
    -   **Eingabe**. Gibt an, dass die Spalte Variablen enthält, die das Ergebnis beeinflussen können und als Eingaben für das Modell verwendet werden sollten.  
  
    -   **Eingabe und Vorhersage**. Gibt an, dass die Daten als Eingabe verwendet werden sollen und dass Sie diese Werte zusätzlich vorhersagen möchten.  
  
    -   **Nur Vorhersagen**. Gibt an, dass die Daten nicht als Eingabe für das Modell verwendet werden sollen.  
  
    -   **Schlüssel**. Jedes Modell erfordert mindestens einen Schlüssel. Abhängig vom Modelltyp, Sie auch möglicherweise die Möglichkeit, zusätzliche spezielle Schlüssel verwenden, wie z. B. die **SequenceKey** oder **TimeKey**.  
  
    -   **Verwenden Sie keine**. Gibt an, dass die Daten nicht im Modell verwendet werden sollen, selbst wenn sie in der Struktur vorhanden sind.  
  
7.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)**  die Schaltfläche, um die **Spaltenmodellflags festlegen** Dialogfeld.  
  
     Stellen Sie in einer kurzen Überprüfung sicher, dass der Verwendungstyp der einzelnen Datenspalten für das Modell geeignet ist. Durch diesen wichtigen Schritt wird verhindert, dass beim Verarbeiten des Modells Fehler auftreten.  
  
     Beispiel: Wenn Sie eine Struktur, die für ein Entscheidungsstrukturmodell erstellt wurde, wiederverwenden, und den Naïve Bayes-Algorithmus darauf anwenden, müssen Spalten mit dem Datentyp `Numeric` und dem Inhaltstyp `Continuous` klassifiziert oder in diskrete Variablen geändert werden.  
  
     Wenn Spalten in der Struktur für den neuen Algorithmus nicht gelten, können Sie diese umgehen, indem Sie die Auswahl **verwenden Sie keine**.  
  
8.  In der **Spaltenmodellflags festlegen** Dialogfeld überprüfen oder festlegen, die die Modellierungsflags, sofern vorhanden.  
  
     Mit Modellierungsflags können Sie u. a. steuern, auf welche Weise NULL-Werte behandelt werden. Weitere Informationen finden Sie unter [Modellierungsflags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).  
  
     Klicken Sie auf **OK** Abschluss, um das Dialogfeld zu schließen.  
  
9. In der **Fertig stellen** Dialogfeld geben einen Namen und Beschreibung für das neue Miningmodell.  
  
     Je nach dem erstellten Modelltyp stehen Ihnen zusätzlich möglicherweise folgende Optionen zur Verfügung:  
  
    -   Durchsuchen des fertigen Miningmodells nach der Erstellung.  
  
    -   Verwenden von Drillthroughs vom Modell zu den Quelldaten.  
  
         Weitere Informationen finden Sie unter [Drillthrough für Miningmodelle](data-mining/drillthrough-on-mining-models.md).  
  
10. Klicken Sie auf **Fertig stellen** zum Speichern der Änderungen. Danach wird das neue Modell auf dem Server bereitgestellt und verarbeitet.  
  
### <a name="related-options"></a>Zugehörige Optionen  
  
|Option|Kommentare|  
|------------|--------------|  
|**Struktur oder Modell auswählen** (Dialogfeld)|Wählen Sie eine vorhandene Miningstruktur aus, um sie als Grundlage für ein neues Modell zu verwenden.  Die ausgewählte Struktur muss für die aktive Verbindung verfügbar sein. Falls nicht, ändern Sie Verbindungen mit dem [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41; ](connect-to-source-data-data-mining-client-for-excel.md) Tool.|  
|**Wählen Sie die Mining-Algorithmus** Dialogfelds|Die Liste der Data Mining-Algorithmen hängt davon ab, mit welchem Server Sie verbunden sind. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt in der Standard und Enterprise Edition verschiedene Algorithmen bereit. Ihr Administrator verfügt möglicherweise auch über zusätzliche benutzerdefinierte Algorithmen.<br /><br /> Wenn Sie keine Algorithmen angezeigt werden, stellen Sie sicher, dass Sie mit einer Instanz von verbunden sind [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|**Algorithmusparameter** (Dialogfeld)|Mithilfe dieser Einstellungen können Sie die einzelnen Algorithmen mit Parametern anpassen, die spezifisch für die analytische Methode sind. Sie können auch einen Ausgangswert festlegen, um sicherzustellen, dass die Ergebnisse des Modells in mehreren Trainingsdurchläufen reproduziert werden können.<br /><br /> Weitere Informationen finden Sie unter [Algorithmusparameter &#40;SQL Server Data Mining-Add-ins&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).|  
|**Spaltenmodellflags festlegen** (Dialogfeld)|Mithilfe von Modellierungsflags können Sie ein Modell verbessern, indem Sie angeben, wie fehlende Daten behandelt werden sollen. Weitere Informationen finden Sie unter [Modellierungsflags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).|  
  
###  <a name="Bkmk_mdlcolumn"></a> Festlegen der Spaltenverwendung  
 Wenn Sie einer vorhandenen Struktur ein neues Miningmodell hinzufügen, müssen Sie angeben, wie das Modell die einzelnen Datenspalten in der Miningstruktur verwendet. Sie bemerken möglicherweise, dass die Optionen in diesem Assistenten wesentlich ausführlicher als die Optionen für die Miningstruktur sind. Warum?  
  
 Dies hat folgende Ursache: Wenn Sie ein Modell zusammen mit einer Struktur unter Verwendung eines Assistenten erstellen, werden zahlreiche Optionen, die steuern, wie Daten vom Algorithmus verwendet werden, automatisch festgelegt. Wenn Sie einem vorhandenen Modell jedoch ein neues Modell hinzufügen, müssen Sie diese Optionen manuell überprüfen und angeben, ob Daten für die Analyse verwendet werden sollen, ob der Datentyp richtig ist usw.  
  
 Beim Anwenden neuer Algorithmen auf vorhandene Daten können Fehlermeldungen ausgegeben werden. Diese Meldungen enthalten in der Regel jedoch ausführliche Informationen zu den Korrekturen, die vorgenommen werden müssen, damit das Modell verarbeitet werden kann. Typische Probleme sind:  
  
-   Das Modell erwartet einen anderen Datentyp, als in der Struktur enthalten ist.  
  
     Einige Algorithmen funktionieren nur mit Zahlen, andere nur mit Text. Wenn die Daten für das neue Modell den falschen Typ aufweisen, müssen Sie u. U. die Struktur ändern, damit das Modell verarbeitet werden kann.  
  
-   Die Miningstruktur enthält kein vorhersagbares Attribut.  
  
     Clustermodelle können ohne vorhersagbaren Wert erstellt werden, andere Modelle erfordern jedoch im Allgemeinen, dass eine einzelne Spalte für die Vorhersage angegeben wird.  
  
-   Die Zusammensetzung der Daten ist nicht kompatibel mit dem Algorithmus, die Sie ausgewählt haben.  
  
     Einige Analysetypen erfordern Daten, die entsprechend eindeutigen Regeln sorgfältig strukturiert sind. Dies gilt beispielsweise für Vorhersagemodelle und Zuordnungsmodelle. Sie können einfach neue Modelle desselben Typs hinzufügen, die über Anpassungen verfügen können, möglicherweise funktionieren die Daten jedoch nicht mit anderen Algorithmen.  
  
### <a name="requirements"></a>Anforderungen  
 Zum Erstellen von Data Mining-Modellen müssen Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt haben. Weitere Informationen zum Erstellen oder Ändern einer Verbindungs finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Falls die gewünschte Data Mining-Struktur nicht angezeigt wird, kann dies daran liegen, dass die betreffende Struktur in einer anderen Instanz oder einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank gespeichert wurde. Weitere Informationen zur Verwendung in eine andere Datamining-Verbindung ändern, finden Sie unter [Herstellen einer Verbindung mit einem Data Mining-Server](connect-to-a-data-mining-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)   
