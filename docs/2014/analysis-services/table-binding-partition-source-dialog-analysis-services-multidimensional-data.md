---
title: Tabellenbindungsdetail (Dialogfeld Partitionsquelle) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e615df2adea50f2ee6d0d0741d6d885b87311ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757825"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Tabellenbindungsdetail (Dialogfeld 'Partitionsquelle') (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Option **Tabellenbindung** im Dialogfeld **Partitionsquelle** können Sie die Faktentabelle angeben, die die Daten für die Partition bereitstellt. Sie können diesen Bereich anzeigen, indem Sie im Dialogfeld **Partitionsquelle** unter **Bindungstyp** die Option **Tabellenbindung** auswählen.  
  
## <a name="options"></a>Optionen  
 **Measuregruppe**  
 Zeigt die Measuregruppe für diese Partition an.  
  
 **Look in**  
 Wählen Sie die Datenquelle oder Datenquellensicht mit den Quelltabellen für die Partition aus. Die durch die ausgewählte Measuregruppe verwendete Datenquellensicht wird standardmäßig ausgewählt.  
  
 **Filtertabellen**  
 Geben Sie die Zeichenfolge ein, die verwendet werden soll, um die unter **Verfügbare Tabellen**angezeigten Tabellen auf der Grundlage des Tabellennamens einzuschränken.  
  
 **Suchen von Tabellen**  
 Wählen Sie diese Option aus, um die Liste der Tabellen unter **Verfügbare Tabellen**zu aktualisieren und die Liste weiter einzuschränken, falls in **Tabellenfilter**eine Zeichenfolge eingegeben wurde.  
  
 **Verfügbare Tabellen**  
 Klicken Sie auf die Option, um die Tabelle auszuwählen, die als Quelltabelle für die Partition verwendet werden soll.  
  
 Wenn in **Tabellenfilter**kein Filter angegeben wird, werden alle Tabellen aufgelistet, die in der unter **Suchen in** angegebenen Datenquelle oder Datenquellensicht enthalten sind, und deren Struktur der Faktentabelle gleicht, die von der unter **Measuregruppe** angegebenen Measuregruppe verwendet wird.  
  
 Wenn in **Tabellenfilter**ein Filter angegeben wird, wird die Liste weiter eingeschränkt, indem der Filter mit den Tabellennamen verglichen wird, die die oben genannten Kriterien erfüllen. Nur die Tabellen, die die in **Tabellenfilter** angegebene Zeichenfolge enthalten, werden angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Partitions-Datenquelle (Dialogfeld) &#40;Analysis Services – mehrdimensionale Daten&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
