---
title: Hinzufügen eines Modells zu einer Struktur (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062874"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a>Hinzufügen eines Modells zu einer Struktur (Data Mining-Add-Ins für Excel)
  ![Schaltfläche "Modell einer Struktur hinzufügen"](media/dmc-addmodel.gif "Schaltfläche "Modell einer Struktur hinzufügen"")  
  
 Wenn Sie auf **Modell zu Struktur hinzufügen**klicken, wird ein Assistent gestartet, mit dem Sie ein neues Mining Modell für die Verwendung mit einer vorhandenen Mining Struktur erstellen können. Diese Option ist hilfreich, da sie die Möglichkeit bietet, Modelle zu vergleichen, die auf denselben Daten basieren, oder benutzerdefinierte Modelle zu erstellen.  
  
 Wenn die Instanz von Analysis Services nicht bereits die benötigten Daten enthält, verwenden Sie den Assistenten zum [Erstellen einer Mining Struktur &#40;SQL Server Data Mining-Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) , um eine Mining Struktur einzurichten. Alternativ können Sie einen der Modellierungs-Assistenten starten und der mit dem Assistenten erstellten Struktur ein neues Modell hinzufügen.  
  
 Zum Erstellen erweiterter Modelle mithilfe von Algorithmen, die von den Assistenten nicht unterstützt werden, erstellen Sie eine Mining Struktur und fügen dann mithilfe des **erweiterten Data Mining-Abfrage-Editors**ein Modell hinzu.  
  
## <a name="add-a-new-model-to-an-existing-structure"></a>Hinzufügen eines neuen Modells zu einer vorhandenen Struktur  
  
1.  Klicken Sie im **Data Mining** -Menüband auf den Pfeil unter **erweitert**, und wählen Sie dann **Modell zu Struktur hinzufügen**aus.  
  
2.  Wählen Sie im Dialogfeld **Struktur auswählen** die Struktur aus, die die Daten enthält, die Sie verwenden möchten, und klicken Sie dann auf **weiter**.  
  
     **Tipp**: Wenn Sie nicht sicher sind, welche Mining Struktur die benötigten Daten enthält, können Sie mit dem **Dokument Modell** -Assistenten die Spalten und grundlegenden Statistiken zu den Daten anzeigen.  
  
     Wenn Sie keine Mining Struktur finden, überprüfen Sie die derzeit verwendete Verbindung. Möglicherweise müssen Sie eine Verbindung mit einem anderen Server herstellen.  
  
3.  Wählen Sie im Dialogfeld **Mining Algorithmus auswählen** einen Mining Algorithmus aus, der im neuen Mining Modell verwendet werden soll.  
  
     Beachten Sie, dass das Dialogfeld viel mehr Optionen bietet, als Sie in den Assistenten sehen werden. Sie können ein Modell mit einem beliebigen, auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server unterstützten Algorithmus erstellen, sofern die Daten kompatibel sind.  
  
4.  Wir empfehlen, dass Sie auch auf die Schaltfläche **Parameter** klicken, um das Dialogfeld **Algorithmusparameter** zu öffnen und Parameter für den Algorithmus anzupassen. Mit dieser Option können am einfachsten benutzerdefinierte Miningmodelle erstellt werden.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Überprüfen Sie im Dialogfeld **Spalten auswählen** die Liste der Spalten, und ändern Sie ggf. die Verwendung der Spalten in einen der folgenden Werte:  
  
    -   **Eingabe**. Gibt an, dass die Spalte Variablen enthält, die das Ergebnis beeinflussen können und als Eingaben für das Modell verwendet werden sollten.  
  
    -   **Eingabe und Vorhersage**. Gibt an, dass die Daten als Eingabe verwendet werden sollen und dass Sie diese Werte zusätzlich vorhersagen möchten.  
  
    -   **Nur Vorhersagen**. Gibt an, dass die Daten nicht als Eingabe für das Modell verwendet werden sollen.  
  
    -   **Schlüssel**. Jedes Modell erfordert mindestens einen Schlüssel. Abhängig vom Modelltyp haben Sie möglicherweise auch die Möglichkeit, zusätzliche Sonderschlüssel zu erhalten, z. b. **sequencekey** oder **TimeKey**.  
  
    -   **Verwenden Sie nicht**. Gibt an, dass die Daten nicht im Modell verwendet werden sollen, selbst wenn sie in der Struktur vorhanden sind.  
  
7.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** , um das Dialogfeld **Spalten modellflags festlegen** zu öffnen.  
  
     Stellen Sie in einer kurzen Überprüfung sicher, dass der Verwendungstyp der einzelnen Datenspalten für das Modell geeignet ist. Durch diesen wichtigen Schritt wird verhindert, dass beim Verarbeiten des Modells Fehler auftreten.  
  
     Beispiel: Wenn Sie eine Struktur, die für ein Entscheidungsstrukturmodell erstellt wurde, wiederverwenden, und den Naïve Bayes-Algorithmus darauf anwenden, müssen Spalten mit dem Datentyp `Numeric` und dem Inhaltstyp `Continuous` klassifiziert oder in diskrete Variablen geändert werden.  
  
     Wenn Spalten in der Struktur nicht auf den neuen Algorithmus anwendbar sind, können Sie Sie umgehen, indem Sie **nicht verwenden**auswählen.  
  
8.  Überprüfen oder legen Sie im Dialogfeld **spaltenmodellflags festlegen** die Modellierungsflags (sofern vorhanden) fest.  
  
     Mit Modellierungsflags können Sie u. a. steuern, auf welche Weise NULL-Werte behandelt werden. Weitere Informationen finden Sie unter [Modellierungsflags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).  
  
     Klicken Sie abschließend auf **OK** , um das Dialogfeld zu schließen.  
  
9. Geben Sie im Dialogfeld **Fertig** stellen einen Namen und eine Beschreibung für das neue Mining Modell ein.  
  
     Je nach dem erstellten Modelltyp stehen Ihnen zusätzlich möglicherweise folgende Optionen zur Verfügung:  
  
    -   Durchsuchen des fertigen Miningmodells nach der Erstellung.  
  
    -   Verwenden von Drillthroughs vom Modell zu den Quelldaten.  
  
         Weitere Informationen finden Sie unter [Drillthrough für Mining Modelle](data-mining/drillthrough-on-mining-models.md).  
  
10. Klicken Sie auf **Fertig stellen**, um Ihre Änderungen zu speichern. Danach wird das neue Modell auf dem Server bereitgestellt und verarbeitet.  
  
### <a name="related-options"></a>Zugehörige Optionen  
  
|Option|Kommentare|  
|------------|--------------|  
|**Struktur oder Modell auswählen** (Dialogfeld)|Wählen Sie eine vorhandene Miningstruktur aus, um sie als Grundlage für ein neues Modell zu verwenden.  Die ausgewählte Struktur muss für die aktive Verbindung verfügbar sein. Wenn dies nicht der Grund ist, ändern Sie die Verbindungen mithilfe des Tools [Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) .|  
|**Mining Algorithmus auswählen** (Dialogfeld)|Die Liste der Data Mining-Algorithmen hängt davon ab, mit welchem Server Sie verbunden sind. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt in der Standard und Enterprise Edition verschiedene Algorithmen bereit. Ihr Administrator verfügt möglicherweise auch über zusätzliche benutzerdefinierte Algorithmen.<br /><br /> Wenn keine Algorithmen angezeigt werden, vergewissern Sie sich, dass Sie mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]verbunden sind.|  
|**Algorithmusparameter** Dialog Feld|Mithilfe dieser Einstellungen können Sie die einzelnen Algorithmen mit Parametern anpassen, die spezifisch für die analytische Methode sind. Sie können auch einen Ausgangswert festlegen, um sicherzustellen, dass die Ergebnisse des Modells in mehreren Trainingsdurchläufen reproduziert werden können.<br /><br /> Weitere Informationen finden Sie unter [Algorithmusparameter &#40;SQL Server Data Mining-Add-ins&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).|  
|**Spalten modellflags festlegen** Dialog Feld|Mithilfe von Modellierungsflags können Sie ein Modell verbessern, indem Sie angeben, wie fehlende Daten behandelt werden sollen. Weitere Informationen finden Sie unter [Modellierungsflags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).|  
  
###  <a name="setting-column-usage"></a><a name="Bkmk_mdlcolumn"></a>Festlegen der Spalten Verwendung  
 Wenn Sie einer vorhandenen Struktur ein neues Miningmodell hinzufügen, müssen Sie angeben, wie das Modell die einzelnen Datenspalten in der Miningstruktur verwendet. Sie werden wahrscheinlich bemerken, dass die Optionen in diesem Assistenten weitaus ausführlicher sind als die Optionen in der Mining Struktur. Warum?  
  
 Dies hat folgende Ursache: Wenn Sie ein Modell zusammen mit einer Struktur unter Verwendung eines Assistenten erstellen, werden zahlreiche Optionen, die steuern, wie Daten vom Algorithmus verwendet werden, automatisch festgelegt. Wenn Sie einem vorhandenen Modell jedoch ein neues Modell hinzufügen, müssen Sie diese Optionen manuell überprüfen und angeben, ob Daten für die Analyse verwendet werden sollen, ob der Datentyp richtig ist usw.  
  
 Beim Anwenden neuer Algorithmen auf vorhandene Daten können Fehlermeldungen ausgegeben werden. Diese Meldungen enthalten in der Regel jedoch ausführliche Informationen zu den Korrekturen, die vorgenommen werden müssen, damit das Modell verarbeitet werden kann. Typische Probleme sind:  
  
-   Das Modell erwartet einen anderen Datentyp, als in der Struktur enthalten ist.  
  
     Einige Algorithmen funktionieren nur mit Zahlen, andere nur mit Text. Wenn die Daten für das neue Modell den falschen Typ aufweisen, müssen Sie u. U. die Struktur ändern, damit das Modell verarbeitet werden kann.  
  
-   Die Miningstruktur enthält kein vorhersagbares Attribut.  
  
     Clustermodelle können ohne vorhersagbaren Wert erstellt werden, andere Modelle erfordern jedoch im Allgemeinen, dass eine einzelne Spalte für die Vorhersage angegeben wird.  
  
-   Die Zusammensetzung der Daten ist mit dem von Ihnen ausgewählten Algorithmus nicht kompatibel.  
  
     Einige Analysetypen erfordern Daten, die entsprechend eindeutigen Regeln sorgfältig strukturiert sind. Dies gilt beispielsweise für Vorhersagemodelle und Zuordnungsmodelle. Sie können einfach neue Modelle desselben Typs hinzufügen, die über Anpassungen verfügen können, möglicherweise funktionieren die Daten jedoch nicht mit anderen Algorithmen.  
  
### <a name="requirements"></a>Anforderungen  
 Zum Erstellen von Data Mining-Modellen müssen Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hergestellt haben. Weitere Informationen zum Erstellen oder Ändern einer Verbindung finden Sie unter Herstellen einer Verbindung [mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Falls die gewünschte Data Mining-Struktur nicht angezeigt wird, kann dies daran liegen, dass die betreffende Struktur in einer anderen Instanz oder einer anderen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank gespeichert wurde. Weitere Informationen zum Wechseln zu einer anderen Data Mining Verbindung finden Sie unter Herstellen einer Verbindung [mit einem Data Mining-Server](connect-to-a-data-mining-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)   
