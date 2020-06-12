---
title: 'Lektion 10: Erstellen von Hierarchien | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
ms.openlocfilehash: b6b57669eed30abf010b9d2775950bf0cd6c6e67
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542152"
---
# <a name="lesson-10-create-hierarchies"></a>Lektion 10: Erstellen von Hierarchien
  In dieser Lektion erstellen Sie Hierarchien. Hierarchien sind Gruppen von Spalten, die in Ebenen angeordnet werden. Beispielsweise könnte eine Geografiehierarchie Unterebenen für Land, Status, Landkreis und Stadt beinhalten. Hierarchien können in einer Feldliste einer Berichterstellungsclientanwendung getrennt von anderen Spalten auftreten. So können Clientbenutzer leichter durch diese navigieren und sie in Berichte einbeziehen. Weitere Informationen finden Sie unter [Hierarchien &#40;SSAS – tabellarisch&#41;](tabular-models/hierarchies-ssas-tabular.md).  
  
 Verwenden Sie zum Erstellen von Hierarchien den Modell-Designer in der *Diagrammsicht*. Das Erstellen und Verwalten von Hierarchien in der Datensicht des Modell-Designers wird nicht unterstützt.  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der richtigen Reihenfolge absolviert werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige, [Lektion 9: Erstellen von Perspektiven](lesson-8-create-perspectives.md), abgeschlossen haben.  
  
## <a name="create-hierarchies"></a>Erstellen von Hierarchien  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>So erstellen Sie in der Product-Tabelle eine Kategoriehierarchie  
  
1.  Klicken Sie im Modell-Designer auf das `Model` Menü, zeigen Sie auf **Modell Ansicht**, und klicken Sie dann auf **Diagramm Sicht**.  
  
    > [!TIP]  
    >  Verwenden Sie die Steuerelemente der Miniaturkarte oben rechts im Modell-Designer, um die Sicht der Objekte in der Diagrammsicht je nach Bedarf zu ändern. Ordnen Sie Objekte in der Diagrammsicht neu an, wird diese Sicht beim Speichern des Projekts beibehalten.  
  
2.  Klicken Sie im Modell-Designer mit der rechten Maustaste auf die `Product` Tabelle, und klicken Sie dann auf **Hierarchie erstellen**. Eine neue Hierarchie wird am unteren Rand des Tabellenfensters angezeigt.  
  
3.  Benennen Sie im Hierarchienamen die Hierarchie um `Category` , indem Sie eingeben, und drücken Sie dann die EINGABETASTE.  
  
4.  `Product`Klicken Sie in der Tabelle auf die Spalte **Product Category Name** , ziehen Sie Sie in die `Category` Hierarchie, und geben Sie dann oberhalb des `Category` namens frei.  
  
5.  `Category`Klicken Sie in der Hierarchie mit der rechten Maustaste auf die Spalte **Product Category Name** , klicken Sie dann auf **Umbenennen**, und geben Sie ein `Category` .  
  
    > [!NOTE]  
    >  Durch das Umbenennen einer Spalte in einer Hierarchie wird die betreffende Spalte in der Tabelle nicht umbenannt. Eine Spalte in einer Hierarchie ist nur eine Darstellung der Spalte in der Tabelle.  
  
6.  `Product`Klicken Sie in der Tabelle mit der rechten Maustaste auf die Spalte **Product Subcategory Name** , zeigen Sie im Kontextmenü auf **zur Hierarchie hinzufügen**, und klicken Sie dann auf `Category` .  
  
7.  Benennen Sie **Product Subcategory Name** in um `Subcategory` .  
  
8.  Fügen Sie mithilfe von klicken und ziehen oder mithilfe des Befehls **zur Hierarchie hinzufügen** im Kontextmenü die Spalten **Model Name** und **Product Name** (in der angegebenen Reihenfolge) hinzu, und platzieren Sie Sie unterhalb der Spalte **Product Subcategory Name** . Benennen Sie diese Spalten um `Model` `Product` bzw. um.  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a>So erstellen Sie Hierarchien in der Date-Tabelle  
  
1.  Klicken Sie im Modell-Designer mit der rechten Maustaste auf die Tabelle **Date** und anschließend auf **Hierarchie erstellen**.  
  
2.  Benennen Sie die Hierarchie in **Calendar**(Kalender) um.  
  
3.  Fügen Sie die folgenden Spalten in der entsprechenden Reihenfolge hinzu, und benennen Sie sie dann um:  
  
    |Column|Umbenennen in:|  
    |------------|----------------|  
    |Calendar Year|Jahr|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Monat|  
    |Day Of Month|Tag|  
  
4.  Wiederholen Sie in der Tabelle **Date** die oben genannten Schritte, und erstellen Sie die Hierarchie **Fiscal** , einschließlich der folgenden Spalten:  
  
    |Column|Umbenennen in:|  
    |------------|----------------|  
    |Fiscal Year|Jahr|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Monat|  
    |Day Of Month|Tag|  
  
5.  Wiederholen Sie abschließend in der Tabelle **Date** die oben genannten Schritte, und erstellen Sie die Hierarchie **Production Calendar** (Produktionskalender), einschließlich der folgenden Spalten:  
  
    |Column|Umbenennen in:|  
    |------------|----------------|  
    |Calendar Year|Jahr|  
    |Week Number Of Year|Woche|  
    |Day Of Week|Tag|  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 11: Erstellen von Partitionen](lesson-10-create-partitions.md).  
  
  
