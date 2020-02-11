---
title: 'Lektion 9: Erstellen von Perspektiven | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd395e605bfde9d34ed0dc4f16060812464efb56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078253"
---
# <a name="lesson-9-create-perspectives"></a>Lektion 9: Erstellen von Perspektiven
  In dieser Lektion erstellen Sie eine Perspektive mit dem Namen Internet Sales. Durch eine Perspektive ist ein anzeigbarer Teil eines Modells definiert, in dem konzentrierte, geschäfts- oder anwendungsspezifische Sichtweisen geboten werden. Wenn ein Benutzer unter Verwendung einer Perspektive eine Verbindung mit einem Modell herstellt, werden ihm nur die als Felder in dieser Perspektive definierten Modellobjekte (Tabellen, Spalten, Measures, Hierarchien und KPIs) angezeigt.  
  
 Die Internet Sales-Perspektive, die Sie in dieser Lektion erstellen, enthält nicht das Customer-Tabellenobjekt. Wenn Sie eine Perspektive erstellen, bei der bestimmte Objekte von der Ansicht ausgeschlossen sind, bleiben diese Objekte im Modell vorhanden; sie sind allerdings nicht in der Feldliste eines Berichterstellungsclients sichtbar. Berechnete Spalten und Measures, die in einer Perspektive entweder enthalten oder nicht enthalten sind, können immer noch Berechnungen aus ausgeschlossenen Objektdaten vornehmen.  
  
 In dieser Lektion soll beschrieben werden, wie Sie Perspektiven erstellen und sich mit den tabellarischen Modellerstellungstools vertraut machen können. Wenn Sie später dieses Modell erweitern, um zusätzliche Tabellen einzufügen, können Sie weitere Perspektiven erstellen, um verschiedene Blickpunkte des Modells zu definieren, beispielsweise Inventar und Außendienst.  
  
 Weitere Informationen finden Sie unter [Perspektiven &#40;SSAS – tabellarisch&#41;](tabular-models/perspectives-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der vorgegebenen Reihenfolge durchgeführt werden sollte. Sie sollten vor dem Ausführen der Tasks in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 8: Erstellen von Leistungskennzahlen](lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Erstellen von Perspektiven  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Erstellen einer Perspektive für Internetverkäufe  
  
1.  Klicken Sie im Modell-Designer auf das Menü **Modell** und dann auf **Perspektiven**.  
  
2.  Klicken Sie im Dialogfeld **Perspektiven** auf **Neue Perspektive**.  
  
3.  Um die Perspektive umzubenennen, doppelklicken Sie auf die Spaltenüberschrift **neue Perspektive 1** , `Internet Sales`und geben Sie dann ein.  
  
4.  Wählen Sie unter **Felder**die folgenden Tabellen **Date**, **geography**, **Product**, **Product Category**, **Product Subcategory**und `Internet Sales`aus.  
  
     Beachten Sie, dass Sie die Tabelle Customer und alle ihre Spalten aus dieser Perspektive ausgeschlossen haben. In Lektion 12 testen Sie dann diese Perspektive mit der Funktion In Excel analysieren. Die PivotTable-Feldliste von Excel enthält jede Tabelle außer der Tabelle Customer.  
  
5.  Überprüfen Sie Ihre Auswahl, stellen Sie sicher, dass die Tabelle **Customer** nicht markiert ist, und klicken Sie anschließend auf **OK**  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 10: Erstellen von Hierarchien](lesson-9-create-hierarchies.md).  
  
  
