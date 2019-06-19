---
title: 'Lektion 2: Hinzufügen von Miningmodellen zur Market Basket-Miningstruktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d96a7a7d-35d7-4b34-abb5-f0822c256253
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b9573d9359983e33cf23533787c26039572710ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63204721"
---
# <a name="lesson-2-adding-mining-models-to-the-market-basket-mining-structure"></a>Lektion 2: Hinzufügen von Miningmodellen zur Market Basket-Miningstruktur
  In dieser Lektion fügen Sie zwei Miningmodelle, die Market Basket-Miningstruktur, die Sie in erstellt [Lektion 1: Erstellen der Market Basket-Miningstruktur](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md). Diese Miningmodelle ermöglichen es Ihnen, Vorhersagen zu erstellen.  
  
 Um die Arten von Produkten vorherzusagen, die Kunden tendenziell gleichzeitig kaufen, erstellen Sie zwei Miningmodelle, die mit der [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) und zwei verschiedene Werte für die *MINIMUM_PROBABILTY* Parameter.  
  
 *MINIMUM_PROBABILTY* ist eine [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus-Parameter, der hilft, um die Anzahl der Regeln zu bestimmen, die ein Miningmodell enthalten soll, durch die mindestwahrscheinlichkeit an, die eine Regel angeben. Wenn Sie für diesen Wert beispielsweise 0,4 eingeben, wird festgelegt, dass eine Regel nur erzeugt werden kann, wenn die Kombination der von der Regel beschriebenen Produkte eine Auftrittswahrscheinlichkeit von mindestens vierzig Prozent aufweist.  
  
 Zeigen Sie an, die Auswirkungen der Änderung der *MINIMUM_PROBABILTY* Parameter in einer späteren Lektion.  
  
## <a name="alter-mining-structure-statement"></a>ALTER MINING STRUCTURE-Anweisung  
 Um ein Miningmodell hinzuzufügen, die einer Miningstruktur eine geschachtelte Tabelle enthält, verwenden Sie die [ALTER MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:  
  
-   Identifizieren der Miningstruktur  
  
-   Benennen des Miningmodells  
  
-   Definieren der Schlüsselspalte  
  
-   Definieren der Eingabespalten und vorhersagbaren Spalten  
  
-   Definieren der Spalten der geschachtelten Tabellen  
  
-   Identifizieren der Algorithmus- und Parameteränderungen  
  
 Im Folgenden finden Sie ein allgemeines Beispiel der `ALTER MINING STRUCTURE`-Anweisung, das einer Struktur mit geschachtelten Tabellenspalten ein Miningmodell hinzufügt:  
  
```  
ALTER MINING STRUCTURE [<Mining Structure Name>]  
ADD MINING MODEL [<Mining Model Name>]  
(  
    [<key column>],  
    <mining model column> <usage>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
) USING <algorithm>( <algorithm parameters> )  
```  
  
 Die erste Codezeile identifiziert die vorhandene Miningstruktur, der das Miningmodell hinzugefügt wird:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 Die nächste Codezeile benennt das Miningmodell, das zur Miningstruktur hinzugefügt wird:  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Informationen zum Benennen eines Objekts in Data Mining Extensions (DMX) finden Sie unter [Bezeichner &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächsten Codezeilen definieren Spalten in der Miningstruktur, die vom Miningmodell verwendet werden:  
  
```  
[<key column>],  
<mining model columns> <usage>,  
```  
  
 Sie können nur Spalten verwenden, die bereits in der Miningstruktur vorhanden sind.  
  
 Die erste Spalte in der Liste der Miningmodellspalten muss die Schlüsselspalte in der Miningstruktur sein. Sie sind jedoch keine Eingabe `KEY` hinter der Schlüsselspalte Nutzung an. Dies liegt daran, dass Sie die Spalte bereits bei der Erstellung der Miningstruktur als Schlüsselspalte definiert haben.  
  
 Die übrigen Zeilen geben die Verwendung der Spalten im neuen Miningmodell an. Mithilfe der folgenden Syntax können Sie angeben, dass eine Spalte im Miningmodell zur Vorhersage verwendet werden soll:  
  
```  
<column name> PREDICT,  
```  
  
 Wenn Sie die Verwendung nicht festlegen, brauchen Sie der Liste keine Data Mining-Strukturspalte hinzufügen. Alle Spalten, die von der Data Mining-Struktur verwendet werden, auf die verwiesen wird, stehen automatisch den Miningmodellen zur Verfügung, die auf dieser Struktur basieren. Das Modell verwendet die Spalten jedoch nicht für das Training, es sei den, Sie geben die Verwendung an.  
  
 Die letzte Codezeile definiert den Algorithmus und die Algorithmusparameter, die zum Generieren des Miningmodells verwendet werden.  
  
```  
) USING <algorithm>( <algorithm parameters> )  
```  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Hinzufügen eines Association-Miningmodells zur Struktur mithilfe der Standardwahrscheinlichkeit  
  
-   Hinzufügen eines Association-Miningmodells zur Struktur mithilfe einer geänderten Wahrscheinlichkeit  
  
## <a name="adding-an-association-mining-model-to-the-structure-using-the-default-minimumprobability"></a>Hinzufügen eines Association-Miningmodells zur Struktur mithilfe des MINIMUM_PROBABILITY-Standardwerts  
 Die erste Aufgabe besteht darin, fügen Sie der Market Basket-Miningstruktur ein neues Miningmodell basierend auf den [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus, mit dem Standardwert für *MINIMUM_PROBABILITY*.  
  
#### <a name="to-add-an-association-mining-model"></a>So fügen Sie ein Association-Miningmodell hinzu  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
    > [!NOTE]  
    >  Um eine DMX-Abfrage für eine bestimmte [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank zu erstellen, klicken Sie mit der rechten Maustaste auf die Datenbank anstatt auf die Instanz.  
  
2.  Kopieren Sie das Standardbeispiel der `ALTER MINING STRUCTURE`-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure name>   
    ```  
  
     durch:  
  
    ```  
    [Market Basket]  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model name>   
    ```  
  
     durch:  
  
    ```  
    [Default Association]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    [<key column>],  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     durch:  
  
    ```  
    OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     In diesem Fall wurde die Tabelle `[Products]` als vorhersagbare Spalte festgelegt`.` Außerdem wurde die Spalte `[Model]` in die Liste der geschachtelten Tabellenspalten eingefügt, da sie die Schlüsselspalte der geschachtelten Tabelle ist.  
  
    > [!NOTE]  
    >  Beachten Sie, dass sich ein geschachtelter Schlüssel von einem Fallschlüssel unterscheidet. Ein Fallschlüssel ist ein eindeutiger Bezeichner des Falles, während ein geschachtelter Schlüssel ein Attribut ist, dass Sie modellieren möchten.  
  
6.  Ersetzen Sie Folgendes:  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     durch:  
  
    ```  
    Using Microsoft_Association_Rules  
    ```  
  
     Die resultierende Anweisung sollte wie folgt aussehen:  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Default Association]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    Using Microsoft_Association_Rules  
    ```  
  
7.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
8.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Default_Association_Model.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
## <a name="adding-an-association-mining-model-to-the-structure-changing-the-default-minimumprobability"></a>Hinzufügen eines Association-Miningmodells zur Struktur, indem der Standardwert für MINIMUM_PROBABILITY geändert wurde  
 Im nächsten Schritt fügen Sie der Market Basket-Miningstruktur auf der Grundlage des [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus ein neues Miningmodell hinzu und ändern den Standardwert für MINIMUM_PROBABILITY in 0,01. Das Ändern des Parameters bewirkt, dass der [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus mehr Regeln erstellt.  
  
#### <a name="to-add-an-association-mining-model"></a>So fügen Sie ein Association-Miningmodell hinzu  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das Standardbeispiel der `ALTER MINING STRUCTURE`-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure name>   
    ```  
  
     durch:  
  
    ```  
    Market Basket  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model name>   
    ```  
  
     durch:  
  
    ```  
    [Modified Association]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     durch:  
  
    ```  
    OrderNumber,  
    [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     In diesem Fall wurde die Tabelle `[Products]` als vorhersagbare Spalte festgelegt. Außerdem wurde der Liste die Spalte `[MODEL]` hinzugefügt, da sie in der geschachtelten Tabelle die Schlüsselspalte ist.  
  
6.  Ersetzen Sie Folgendes:  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     durch:  
  
    ```  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
     Die resultierende Anweisung sollte wie folgt aussehen:  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Modified Assocation]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
7.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
8.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Modified Association_Model.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
 In der nächsten Lektion verarbeiten Sie die Market Basket-Miningstruktur zusammen mit den ihr zugeordneten Miningmodellen.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Verarbeiten der Market Basket-Miningstruktur](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
  
  
