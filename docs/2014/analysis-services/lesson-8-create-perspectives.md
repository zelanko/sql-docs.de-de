---
title: 'Lektion 9: Erstellen von Perspektiven | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 83d9b10af87926a26b2a671ff162163d3c8fa62f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163610"
---
# <a name="lesson-9-create-perspectives"></a>Lektion 9: Erstellen von Perspektiven
  In dieser Lektion erstellen Sie eine Perspektive mit dem Namen Internet Sales. Eine Perspektive definiert eine sichtbare Teilmenge eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte bereitstellt. Wenn ein Benutzer unter Verwendung einer Perspektive eine Verbindung mit einem Modell herstellt, werden ihm nur die als Felder in dieser Perspektive definierten Modellobjekte (Tabellen, Spalten, Measures, Hierarchien und KPIs) angezeigt.  
  
 Die Internet Sales-Perspektive, die Sie in dieser Lektion erstellen, enthält nicht das Customer-Tabellenobjekt. Wenn Sie eine Perspektive erstellen, die bestimmte Objekte aus der Sicht ausschließt, ist dieses Objekt immer noch im Modell vorhanden. Es ist jedoch in keiner Feldliste eines Berichterstellungsdiensts sichtbar. In berechneten Spalten und Measures können Berechnungen mit ausgeschlossenen Objektdaten ausgeführt werden, unabhängig davon, ob die Spalten und Measures in einer Perspektive enthalten sind.  
  
 In dieser Lektion wird beschrieben, wie Sie Perspektiven erstellen und sich mit den Erstellungstools der Tabellenmodelle vertraut machen. Wenn Sie später dieses Modell erweitern, um zusätzliche Tabellen einzufügen, können Sie weitere Perspektiven erstellen, um verschiedene Blickpunkte des Modells zu definieren, beispielsweise Inventar und Außendienst.  
  
 Weitere Informationen finden Sie unter [Perspektiven &#40;SSAS – tabellarisch&#41;](tabular-models/perspectives-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Sie sollten vor dem Ausführen der Tasks in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 8: Erstellen von Leistungskennzahlen](lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Erstellen von Perspektiven  
  
#### <a name="to-create-an-internet-sales-perspective"></a>So erstellen Sie eine Internet Sales-Perspektive  
  
1.  Klicken Sie im Modell-Designer auf die **Modell** , und klicken Sie dann auf **Perspektiven**.  
  
2.  Klicken Sie im Dialogfeld **Perspektiven** auf **Neue Perspektive**.  
  
3.  Um die Perspektive umzubenennen, doppelklicken Sie auf die **neue Perspektive 1** Spaltenüberschrift, und geben Sie dann `Internet Sales`.  
  
4.  In **Felder**, wählen Sie die folgenden Tabellen **Datum**, **Geography**, **Produkt**, **Product Category**, **Produktunterkategorie**, und `Internet Sales`.  
  
     Beachten Sie, dass Sie die Tabelle Customer und alle ihre Spalten aus dieser Perspektive ausgeschlossen haben. In Lektion 12 testen Sie dann diese Perspektive mit der Funktion In Excel analysieren. Die PivotTable-Feldliste von Excel enthält jede Tabelle außer der Tabelle Customer.  
  
5.  Überprüfen Sie Ihre Auswahl, stellen Sie sicher, dass die Tabelle **Customer** nicht markiert ist, und klicken Sie anschließend auf **OK**  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 10: Erstellen von Hierarchien](lesson-9-create-hierarchies.md).  
  
  
