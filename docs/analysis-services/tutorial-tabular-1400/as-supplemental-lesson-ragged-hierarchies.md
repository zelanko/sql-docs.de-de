---
title: 'Analysis Services Tutorial ergänzende Lektion: Unregelmäßige Hierarchien | Microsoft-Dokumentation'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 39f8bcc63b7e5344f70a6d4a3b6c44ae3e69e108
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685397"
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>Ergänzende Lektion: unregelmäßige Hierarchien

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser ergänzenden Lektion beheben Sie ein häufiges Problem beim Pivotieren von Hierarchien, die leere Werte (Member) auf verschiedenen Ebenen enthalten. Beispielsweise muss eine Organisation, in dem eine hochrangigen Führungskraft sowohl Abteilungsleiter als auch ohne Führungskompetenzen unterstellt ist. Oder geografische Hierarchien bestehen Country-Region-Stadt, in denen einige Städte ein Bundesland / Kanton untergeordnet, z. B. Washington d. c., Vatikanstadt fehlt. Wenn eine Hierarchie leere Member aufweist, verzweigt es häufig zu anderen oder unregelmäßigen Ebenen.

![as-lesson-detail-ragged-hierarchies-table](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

Tabellarische Modelle mit Kompatibilitätsgrad 1400 verfügen über eine zusätzliche **Member ausblenden** -Eigenschaft für Hierarchien. Die **Standard** Einstellung wird vorausgesetzt, es sind keine leeren Mitglieder auf jeder Ebene. Die **leere Member ausblenden** Einstellung schließt leere Member aus der Hierarchie, wenn eine PivotTable oder ein Bericht hinzugefügt.  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In diesem Artikel ergänzende Lektion ist Teil einer Tutorials zur tabellenmodellierung. Vor dem Ausführen der Aufgaben in dieser ergänzenden Lektion an, Sie sollten abgeschlossen haben alle vorherige Lektionen oder über einen abgeschlossenen Adventure Works Internet Sales-Beispiel-Modellprojekt. 

Wenn Sie das AW Internet Sales-Projekt als Teil des Tutorials erstellt haben, Ihr Modell noch keine Daten oder Hierarchien, die unregelmäßig sind. Um diese ergänzende Lektion durchführen zu können, müssen Sie zuerst erstellen das Problem, indem einige weiteren Tabellen hinzufügen, Beziehungen, berechnete Spalten, ein Measure und eine neue Organisationshierarchie zu erstellen. Dies nimmt etwa 15 Minuten. Anschließend können Sie es in wenigen Minuten zu lösen.  

## <a name="add-tables-and-objects"></a>Hinzufügen von Tabellen und Objekte
  
### <a name="to-add-new-tables-to-your-model"></a>Auf dem Modell neue Tabellen hinzufügen
  
1.  Erweitern Sie im tabellarischen Modell-Explorer **Datenquellen**, die Verbindung per Rechtsklick > **neue Tabelle importieren**.
  
2.  Wählen Sie im Navigator **DimEmployee** und **FactResellerSales**, und klicken Sie dann auf **OK**.

3.  Klicken Sie im Abfrage-Editor **importieren**

4.  Erstellen Sie die folgende [Beziehungen](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | Tabelle 1           | Spalte       | Filterrichtung   | Tabelle 2     | Spalte      | Active |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | Standard            | DimDate     | date        | Ja    |
    | FactResellerSales | DueDate      | Standard            | DimDate     | date        | Nein     |
    | FactResellerSales | ShipDateKey  | Standard            | DimDate     | date        | Nein     |
    | FactResellerSales | ProductKey   | Standard            | DimProduct  | ProductKey  | Ja    |
    | FactResellerSales | EmployeeKey  | Für beide Tabellen | DimEmployee | EmployeeKey | Ja    |

5. In der **DimEmployee** Tabelle, erstellen Sie die folgende [berechnete Spalten](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

    **Pfad** 
    ```
    =PATH([EmployeeKey],[ParentEmployeeKey])
    ```

    **FullName** 
    ```
    =[FirstName] & " " & [MiddleName] & " " & [LastName]
    ```

    **Level1** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],1,1)) 
    ```

    **Level2** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],2,1)) 
    ```

    **Level3** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],3,1)) 
    ```

    **Level4** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],4,1)) 
    ```

    **Level5** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],5,1)) 
    ```

6.  In der **DimEmployee** Tabelle, erstellen Sie eine [Hierarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md) mit dem Namen **Organisation**. Fügen Sie die folgenden Spalten in dieser Reihenfolge hinzu: **Level1**, **Level2**, **Level3**, **Level4**, **Level5**.

7.  In der **FactResellerSales** Tabelle, erstellen Sie die folgende [Measure](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  Verwendung [in Excel analysieren](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md) öffnen Sie Excel und erstellen Sie automatisch eine PivotTable.

9.  In **PivotTable Fields**, Hinzufügen der **Organisation** -Hierarchie aus der **DimEmployee** Tabelle **Zeilen**, und die  **ResellerTotalSales** measure aus der **FactResellerSales** Tabelle **Werte**.

    ![as-lesson-detail-ragged-hierarchies-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    Wie Sie in der PivotTable sehen, zeigt die Hierarchie unregelmäßige Zeilen an. Es gibt viele Zeilen, in denen leere Member angezeigt werden.

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>Unregelmäßige Hierarchien zu beheben, indem Sie Member ausblenden Eigenschaft festlegen.

1.  In **tabellarischer Modell-Explorer**, erweitern Sie **Tabellen** > **DimEmployee** > **Hierarchien**  >  **Organisation**.

2.  In **Eigenschaften** > **Member ausblenden**Option **leere Member ausblenden**. 

    ![As-Lesson-Detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  Aktualisieren Sie die PivotTable in Excel. 

    ![as-lesson-detail-ragged-hierarchies-pivottable-refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    Das sieht doch sehr viel besser!

## <a name="see-also"></a>Siehe auch   
[Lektion 9: Erstellen von Hierarchien](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[Ergänzende Lektion – dynamische Sicherheit](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Ergänzende Lektion – Detailzeilen](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  
