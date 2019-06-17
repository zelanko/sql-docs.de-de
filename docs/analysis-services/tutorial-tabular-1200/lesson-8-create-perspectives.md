---
title: Lektion 8 Erstellen von Perspektiven | Microsoft-Dokumentation
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f68e51be75e84226dd0b1fd3e578fa4031eda04
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403522"
---
# <a name="lesson-8-create-perspectives"></a>Lektion 8: Erstellen von Perspektiven
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion erstellen Sie eine Perspektive mit dem Namen Internet Sales. Eine Perspektive definiert eine sichtbare Teilmenge eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte bereitstellt. Wenn ein Benutzer auf ein Modell mithilfe einer Perspektive herstellt, sehen sie nur die Modellobjekte (Tabellen, Spalten, Measures, Hierarchien und KPIs) als in dieser Perspektive definierten Felder.  
  
Perspektive für Internetverkäufer, die Sie in dieser Lektion erstellen, schließt das Objekt DimCustomer-Tabelle. Wenn Sie eine Perspektive erstellen, die bestimmte Objekte aus der Sicht ausschließt, ist dieses Objekt immer noch im Modell vorhanden. Es ist jedoch in keiner Feldliste eines Berichterstellungsdiensts sichtbar. In berechneten Spalten und Measures können Berechnungen mit ausgeschlossenen Objektdaten ausgeführt werden, unabhängig davon, ob die Spalten und Measures in einer Perspektive enthalten sind.  
  
In dieser Lektion wird beschrieben, wie Sie Perspektiven erstellen und sich mit den Erstellungstools der Tabellenmodelle vertraut machen. Wenn Sie später dieses Modell um zusätzliche Tabellen erweitern, können Sie zusätzliche Perspektiven, um verschiedene Blickpunkte des Modells, z. B. Inventur- und Sales definieren erstellen. Weitere Informationen finden Sie unter [Perspektiven](../tabular-models/perspectives-ssas-tabular.md).  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 7: Erstellen von Key Performance Indicators](lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Erstellen von Perspektiven  
  
#### <a name="to-create-an-internet-sales-perspective"></a>So erstellen Sie eine Internet Sales-Perspektive  
  
1.  Klicken Sie auf die **Modell** Menü > **Perspektiven** > **erstellen und verwalten**.  
  
2.  Klicken Sie im Dialogfeld **Perspektiven** auf **Neue Perspektive**.  
  
3.  Doppelklicken Sie auf die **neue Perspektive** Spaltenüberschrift, und klicken Sie dann benennen **Internetverkäufe**.  
  
4.  Wählen Sie alle Tabellen *außer* **DimCustomer**.  
  
    ![as-tabular-lesson8-perspectives](media/as-tabular-lesson8-perspectives.png)
  
    In einer späteren Lektion verwenden analysieren Funktion in Excel Sie diese Perspektive zu testen. Der Excel-PivotTable-Feldliste enthält alle Tabellen außer DimCustomer-Tabelle.  

## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 9: Erstellen von Hierarchien](lesson-9-create-hierarchies.md).
  
  
  
  
