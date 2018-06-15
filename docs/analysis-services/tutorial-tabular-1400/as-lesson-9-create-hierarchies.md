---
title: 'Analysis Services Tutorial Lektion 9: Erstellen von Hierarchien | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
ms.openlocfilehash: df99d05373d4d3087ef1d5fa5324ec645bf000b6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34042974"
---
# <a name="create-hierarchies"></a>Erstellen von Hierarchien

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion erstellen Sie Hierarchien. Hierarchien sind Gruppen von Spalten, die in Ebenen angeordnet sind. Z. B. möglicherweise eine Geography-Hierarchie Unterebenen für Land, Status, Landkreis und Ort. Hierarchien können getrennt von anderen Spalten in der Feldliste einer Clientanwendung zur Berichtserstellung angezeigt werden, sodass Clientbenutzer einfacher darin navigieren und sie in einen Bericht aufnehmen können. Weitere Informationen finden Sie unter [Hierarchien](../tabular-models/hierarchies-ssas-tabular.md)
  
Verwenden Sie zum Erstellen von Hierarchien im Modell-Designer in *Diagrammsicht*. Erstellen und Verwalten von Hierarchien wird in der Datensicht nicht unterstützt.  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil eines Lernprogramms zur tabellenmodellierung, das in Reihenfolge absolviert werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion, Sie sollten haben die vorherige Lektion abgeschlossen: [Lektion 8: Erstellen von Perspektiven](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Erstellen von Hierarchien  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>So erstellen Sie eine Kategoriehierarchie in der DimProduct-Tabelle  
  
1.  Im Modell-Designer (Diagrammsicht), mit der Maustaste die **DimProduct** Tabelle > **Hierarchie erstellen**. Eine neue Hierarchie wird am unteren Rand des Tabellenfensters angezeigt. Benennen Sie die Hierarchie **Kategorie**.  
  
2.  Klicken Sie auf, und ziehen Sie die **"productcategoryname"** Spalte mit dem neuen **Kategorie** Hierarchie.  
  
3.  In der **Kategorie** Hierarchie mit der rechten Maustaste **"productcategoryname"** > **umbenennen**, und geben Sie dann **Kategorie**.  
  
    > [!NOTE]  
    > Durch das Umbenennen einer Spalte in einer Hierarchie wird die betreffende Spalte in der Tabelle nicht umbenannt. Eine Spalte in einer Hierarchie ist nur eine Darstellung der Spalte in der Tabelle.  
  
4.  Klicken Sie auf, und ziehen Sie die **ProductSubcategoryName** Spalte die **Kategorie** Hierarchie. Benennen Sie sie **Subcategory**. 
  
5.  Mit der rechten Maustaste die **ModelName** Spalte > **Hierarchie hinzufügen**, und wählen Sie dann **Kategorie**. Benennen Sie sie **Modell**.

6.  Fügen Sie schließlich **EnglishProductName** der Kategoriehierarchie. Benennen Sie sie **Produkt**.  

    ![Kategorie als lesson9](../tutorial-tabular-1400/media/as-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Zum Erstellen von Hierarchien in der DimDate-Tabelle  
  
1.  In der **DimDate** Tabelle, erstellen Sie eine Hierarchie namens **Kalender**.  
  
3.  Fügen Sie die folgenden Spalten in Ordnung hinzu:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  In der **DimDate** Tabelle, erstellen Sie eine **Geschäftskalender** Hierarchie. Schließen Sie die folgenden Spalten in Ordnung:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Schließlich wird in der **DimDate** Tabelle, erstellen Sie eine **ProductionCalendar** Hierarchie. Schließen Sie die folgenden Spalten in Ordnung:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 10: Erstellen von Partitionen](../tutorial-tabular-1400/as-lesson-10-create-partitions.md). 
  
  
