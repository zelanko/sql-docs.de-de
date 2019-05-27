---
title: Quellinformationen angeben (Partitions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifydsvandfacttables.f1
ms.assetid: b6c13587-c690-45d9-af90-b3d652afc55b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aca14c9462d847d91ae2b51dfdf179650ee06732
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66068170"
---
# <a name="specify-source-information-partition-wizard"></a>Quellinformationen angeben (Partitions-Assistent)
  Auf der Seite **Quellinformationen angeben** können Sie die Measuregruppe, in der die Partition erstellt werden soll, und die Datenquellensicht und die Filtertabellen für die Partition auswählen.  
  
> [!CAUTION]  
>  Wenn Sie unter **Verfügbare Tabellen** eine Tabelle angeben, die auch von einer anderen Partition verwendet wird, müssen Sie auf der Seite **Zeilen einschränken** eine Abfrage bereitstellen, da andernfalls die Gefahr besteht, dass die Daten im Cube dupliziert werden.  
  
## <a name="options"></a>Optionen  
 **Measuregruppe**  
 Wählen Sie für die Partition eine Measuregruppe aus.  
  
 **Look in**  
 Wählen Sie die Datenquelle oder Datenquellensicht mit den Quelltabellen für die Partition aus. Die durch die Measuregruppe verwendete Datenquellensicht wird standardmäßig ausgewählt.  
  
 **Filtertabellen**  
 Geben Sie die Zeichenfolge ein, die verwendet werden soll, um die unter **Verfügbare Tabellen**angezeigten Tabellen auf der Grundlage des Tabellennamens einzuschränken.  
  
 **Suchen von Tabellen**  
 Wählen Sie diese Option aus, um die Liste der Tabellen unter **Verfügbare Tabellen**zu aktualisieren und die Liste weiter einzuschränken, falls in **Tabellenfilter**eine Zeichenfolge eingegeben wurde.  
  
 **Verfügbare Tabellen**  
 Wählen Sie die Tabellen aus, die als Quelltabellen für Partitionen verwendet werden sollen. Durch **Partitions-Assistent** wird für jede der in **Verfügbare Tabellen**ausgewählten Tabellen eine Partition erstellt.  
  
 Wenn in **Tabellenfilter**kein Filter angegeben wird, werden mit dieser Option alle Tabellen aufgelistet, die in der in **Suchen in** angegebenen Datenquelle oder Datenquellensicht enthalten sind, und deren Struktur der Faktentabelle gleicht, die von der in **Measuregruppe**angegebenen Measuregruppe verwendet wird.  
  
 Wenn in **Tabellenfilter**ein Filter angegeben wird, wird die Liste weiter eingeschränkt, da der Filter mit den Tabellennamen verglichen wird, die die zuvor angegebenen Kriterien bereits erfüllen. Nur die Tabellen, die die in **Tabellenfilter** angegebene Zeichenfolge enthalten, werden angezeigt.  
  
> [!NOTE]  
>  Wenn mehrere Tabellen ausgewählt werden, kann die Seite **Zeilen einschränken** nicht angezeigt werden, und die Zeilen können nicht für die von den ausgewählten Tabellen erstellten Partitionen eingeschränkt werden. Um die Zeilen für die einzelnen Partitionen einzuschränken, führen Sie den Partitions-Assistenten einmal für jede Tabelle aus, von der eine Partition erstellt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
