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
manager: craigg
ms.openlocfilehash: eb70d7d495d88ee62e98bf27f2b92bf569c98387
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66078191"
---
# <a name="lesson-10-create-hierarchies"></a>Lektion 10: Erstellen von Hierarchien
  In dieser Lektion erstellen Sie Hierarchien. Hierarchien sind Gruppen von Spalten, die in Ebenen angeordnet werden. Beispielsweise könnte eine Geografiehierarchie Unterebenen für Land, Status, Landkreis und Stadt beinhalten. Hierarchien können getrennt von anderen Spalten in der Feldliste einer Clientanwendung zur Berichtserstellung angezeigt werden, sodass Clientbenutzer einfacher darin navigieren und sie in einen Bericht aufnehmen können. Weitere Informationen finden Sie unter [Hierarchien &#40;SSAS – tabellarisch&#41;](tabular-models/hierarchies-ssas-tabular.md).  
  
 Verwenden Sie zum Erstellen von Hierarchien den Modell-Designer in der *Diagrammsicht*. Das Erstellen und Verwalten von Hierarchien in der Datensicht des Modell-Designers wird nicht unterstützt.  
  
 Geschätzte Zeit zum Abschließen dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 9: Erstellen von Perspektiven](lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Erstellen von Hierarchien  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>So erstellen Sie in der Product-Tabelle eine Kategoriehierarchie  
  
1.  Klicken Sie im Modell-Designer auf die `Model` Menü, und klicken Sie dann auf, zeigen Sie auf **Modellansicht**, und klicken Sie dann auf **Diagrammansicht**.  
  
    > [!TIP]  
    >  Verwenden Sie die Steuerelemente der Miniaturkarte oben rechts im Modell-Designer, um die Sicht der Objekte in der Diagrammsicht je nach Bedarf zu ändern. Ordnen Sie Objekte in der Diagrammsicht neu an, wird diese Sicht beim Speichern des Projekts beibehalten.  
  
2.  Im Modell-Designer mit der Maustaste der `Product` Tabelle, und klicken Sie dann auf **Hierarchie erstellen**. Eine neue Hierarchie wird am unteren Rand des Tabellenfensters angezeigt.  
  
3.  Benennen Sie in den Hierarchienamen die Hierarchie durch Eingabe `Category`, und drücken Sie dann die EINGABETASTE.  
  
4.  In der `Product` Tabelle, klicken Sie auf die **Product Category Name** Spalte ziehen Sie dann auf die `Category` Hierarchie, und lassen Sie auf der die `Category` Name.  
  
5.  In der `Category` Hierarchie mit der rechten Maustaste die **Product Category Name** Spalte, klicken Sie dann auf **umbenennen**, und geben Sie dann `Category`.  
  
    > [!NOTE]  
    >  Durch das Umbenennen einer Spalte in einer Hierarchie wird die betreffende Spalte in der Tabelle nicht umbenannt. Eine Spalte in einer Hierarchie ist nur eine Darstellung der Spalte in der Tabelle.  
  
6.  In der `Product` Tabelle der rechten Maustaste auf die **Product Subcategory Name** Spalte, klicken Sie dann im Kontextmenü, zeigen Sie auf **zur Hierarchie hinzufügen**, und klicken Sie dann auf `Category`.  
  
7.  Benennen Sie **Product Subcategory Name** zu `Subcategory`.  
  
8.  Durch Klicken und ziehen oder mithilfe der **zur Hierarchie hinzufügen** Befehl im Kontextmenü, fügen Sie der **Modellname** und **Product Name** Spalten (in Reihenfolge) und platzieren Sie sie unterhalb der **Product Subcategory Name** Spalte. Benennen Sie diese Spalten `Model` und `Product`bzw.  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a>So erstellen Sie Hierarchien in der Date-Tabelle  
  
1.  Klicken Sie im Modell-Designer mit der rechten Maustaste auf die Tabelle **Date** und anschließend auf **Hierarchie erstellen**.  
  
2.  Benennen Sie die Hierarchie in **Calendar**(Kalender) um.  
  
3.  Fügen Sie die folgenden Spalten in der entsprechenden Reihenfolge hinzu, und benennen Sie sie dann um:  
  
    |Spalte|Umbenennen in:|  
    |------------|----------------|  
    |Calendar Year|Year|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|Day|  
  
4.  Wiederholen Sie in der Tabelle **Date** die oben genannten Schritte, und erstellen Sie die Hierarchie **Fiscal** , einschließlich der folgenden Spalten:  
  
    |Spalte|Umbenennen in:|  
    |------------|----------------|  
    |Fiscal Year|Year|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|Day|  
  
5.  Wiederholen Sie abschließend in der Tabelle **Date** die oben genannten Schritte, und erstellen Sie die Hierarchie **Production Calendar** (Produktionskalender), einschließlich der folgenden Spalten:  
  
    |Spalte|Umbenennen in:|  
    |------------|----------------|  
    |Calendar Year|Year|  
    |Week Number Of Year|Week|  
    |Day Of Week|Day|  
  
## <a name="next-steps"></a>Nächste Schritte  
 Um dieses Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 11: Erstellen von Partitionen](lesson-10-create-partitions.md).  
  
  
