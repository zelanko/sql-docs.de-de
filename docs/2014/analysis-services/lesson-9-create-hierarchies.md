---
title: 'Lektion 10: Erstellen von Hierarchien | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: ea741676f07020291c2aa94d130c2f595a50f323
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046789"
---
# <a name="lesson-10-create-hierarchies"></a>Lektion 10: Erstellen von Hierarchien
  In dieser Lektion erstellen Sie Hierarchien. Hierarchien sind Gruppen von Spalten, die in Ebenen angeordnet werden. Beispielsweise könnte eine Geografiehierarchie Unterebenen für Land, Status, Landkreis und Stadt beinhalten. Hierarchien können getrennt von anderen Spalten in der Feldliste einer Clientanwendung zur Berichtserstellung angezeigt werden, sodass Clientbenutzer einfacher darin navigieren und sie in einen Bericht aufnehmen können. Weitere Informationen finden Sie unter [Hierarchien &#40;SSAS – tabellarisch&#41;](tabular-models/hierarchies-ssas-tabular.md).  
  
 Verwenden Sie zum Erstellen von Hierarchien den Modell-Designer in der *Diagrammsicht*. Das Erstellen und Verwalten von Hierarchien in der Datensicht des Modell-Designers wird nicht unterstützt.  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige, [Lektion 9: Erstellen von Perspektiven](lesson-8-create-perspectives.md), abgeschlossen haben.  
  
## <a name="create-hierarchies"></a>Erstellen von Hierarchien  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>So erstellen Sie in der Product-Tabelle eine Kategoriehierarchie  
  
1.  Im Modell-Designer, klicken Sie auf die `Model` Menü, zeigen Sie dann auf **Modellansicht**, und klicken Sie dann auf **Diagrammsicht**.  
  
    > [!TIP]  
    >  Verwenden Sie die Steuerelemente der Miniaturkarte oben rechts im Modell-Designer, um die Sicht der Objekte in der Diagrammsicht je nach Bedarf zu ändern. Ordnen Sie Objekte in der Diagrammsicht neu an, wird diese Sicht beim Speichern des Projekts beibehalten.  
  
2.  Im Modell-Designer mit der Maustaste die `Product` Tabelle, und klicken Sie dann auf **Hierarchie erstellen**. Eine neue Hierarchie wird am unteren Rand des Tabellenfensters angezeigt.  
  
3.  Benennen Sie den Hierarchienamen die Hierarchie dazu `Category`, und drücken Sie dann die EINGABETASTE.  
  
4.  In der `Product` Tabelle, klicken Sie auf die **Product Category Name** Spalte ziehen Sie dann auf die `Category` Hierarchie, und lassen Sie auf der Basis von der `Category` Name.  
  
5.  In der `Category` Hierarchie mit der rechten Maustaste die **Product Category Name** Spalte, klicken Sie dann auf **umbenennen**, und geben Sie dann `Category`.  
  
    > [!NOTE]  
    >  Durch das Umbenennen einer Spalte in einer Hierarchie wird die betreffende Spalte in der Tabelle nicht umbenannt. Eine Spalte in einer Hierarchie ist nur eine Darstellung der Spalte in der Tabelle.  
  
6.  In der `Product` Tabelle der rechten Maustaste auf die **Product Subcategory Name** Spalte, zeigen Sie dann im Kontextmenü auf **Hierarchie hinzufügen**, und klicken Sie dann auf `Category`.  
  
7.  Benennen Sie **Product Subcategory Name** auf `Subcategory`.  
  
8.  Mittels Klick und ziehen oder mithilfe der **Hierarchie hinzufügen** Befehl im Kontextmenü, fügen Sie der **Modellname** und **Produktname** Spalten (in entsprechender Reihenfolge) und platzieren Sie sie unterhalb der **Product Subcategory Name** Spalte. Benennen Sie diese Spalten `Model` und `Product`zugeordnet.  
  
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
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 11: Erstellen von Partitionen](lesson-10-create-partitions.md).  
  
  