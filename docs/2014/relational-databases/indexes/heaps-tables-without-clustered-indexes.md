---
title: Heaps (Tabellen ohne gruppierte Indizes) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- heaps
ms.assetid: df5c4dfb-d372-4d0f-859a-a2d2533ee0d7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: de71808c54264639aea82fe66cf23a7bfd6bd0ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63162152"
---
# <a name="heaps-tables-without-clustered-indexes"></a>Heaps (Tabellen ohne gruppierte Indizes)
  Ein Heap ist eine Tabelle ohne gruppierten Index. Ein oder mehrere nicht gruppierte Indizes können für Tabellen erstellt werden, die als Heap gespeichert sind. Daten werden ohne bestimmte Reihenfolge im Heap gespeichert. Normalerweise werden Daten anfänglich in der Reihenfolge gespeichert, in der die Zeilen in die Tabelle eingefügt werden. [!INCLUDE[ssDE](../../includes/ssde-md.md)] kann die Daten jedoch im Heap verschieben, um die Zeilen effizienter zu speichern; daher kann die Reihenfolge der Daten nicht vorhergesagt werden. Um die von einem Heap zurückgegebene Zeilenreihenfolge zu garantieren, müssen Sie die `ORDER BY`-Klausel verwenden. Um die Reihenfolge zum Speichern der Zeilen anzugeben, erstellen Sie für eine Tabelle einen gruppierten Index, damit es sich bei der Tabelle nicht um einen Heap handelt.  
  
> [!NOTE]  
>  In bestimmten Fällen gibt es gute Gründe, eine Tabelle als einen Heap zu belassen, statt einen gruppierten Index zu erstellen. Die effektive Verwendung von Heaps ist jedoch Benutzern mit fortgeschrittenen Kenntnissen vorbehalten. Die meisten Tabellen sollten über einen sorgfältig ausgewählten gruppierten Index verfügen, es sei denn, es gibt gute Gründe, die Tabelle als Heap beizubehalten.  
  
## <a name="when-to-use-a-heap"></a>Verwendungsbereiche für Heaps  
 Wenn eine Tabelle ein Heap ist und nicht über ungruppierte Indizes verfügt, muss die ganze Tabelle überprüft werden (mit einem Tabellenscan), um eine Zeile zu finden. Dies ist durchaus denkbar, wenn es sich um eine kleine Tabelle handelt, wie z. B. eine Liste der zwölf Niederlassungen eines Unternehmens.  
  
 Wenn eine Tabelle als Heap gespeichert wird, werden einzelne Zeilen durch einen Zeilenbezeichner (RID, Row Identifier) gekennzeichnet, der aus der Dateinummer, der Datenseitennummer und einem Slot auf der Seite besteht. Die Zeilen-ID ist eine kleine und effiziente Struktur. In einigen Fällen verwenden Datenarchitekten Heaps, wenn immer über nicht gruppierte Indizes auf Daten zugegriffen wird und die RID kleiner als ein Schlüssel des gruppierten Indexes ist.  
  
## <a name="when-not-to-use-a-heap"></a>Keine Verwendungsbereiche für Heaps  
 Verwenden Sie keinen Heap, wenn die Daten häufig in einer sortierten Reihenfolge zurückgegeben werden. Mit einem gruppierten Index für die Sortierspalte kann der Sortiervorgang vermieden werden.  
  
 Verwenden Sie keinen Heap, wenn die Daten häufig zusammen gruppiert werden. Daten müssen vor dem Gruppieren sortiert werden, und ein gruppierter Index für die Sortierspalte kann den Sortiervorgang vermeiden.  
  
 Verwenden Sie keinen Heap, wenn häufig Datenbereiche aus der Tabelle abgefragt werden.  Mit einem gruppierten Index für die Bereichsspalte kann der Sortiervorgang für den gesamten Heap vermieden werden.  
  
 Verwenden Sie keinen Heap, wenn keine nicht gruppierten Indizes vorhanden sind und die Tabelle sehr groß ist. In einem Heap müssen alle Zeilen des Heaps gelesen werden, um eine Zeile zu finden.  
  
## <a name="managing-heaps"></a>Verwalten von Heaps  
 Erstellen Sie zum Anlegen eines Heaps eine Tabelle ohne gruppierten Index. Alternativ dazu können Sie den gruppierten Index löschen, wenn die Tabelle bereits über einen gruppierten Index verfügt, damit die Tabelle wieder ein Heap ist.  
  
 Erstellen Sie zum Löschen eines Heaps auf dem Heap einen gruppierten Index.  
  
 Um einen Heap neu zu erstellen, damit nicht verwendeter Speicherplatz wieder genutzt werden kann, erstellen Sie auf dem Heap einen gruppierten Index und löschen den gruppierten Index dann wieder.  
  
> [!WARNING]  
>  Das Erstellen oder Löschen von gruppierten Indizes erfordert, dass die gesamte Tabelle neue geschrieben werden muss. Wenn die Tabelle über nicht gruppierte Indizes verfügt, müssen alle nicht gruppierten Indizes immer dann neu erstellt werden, wenn der gruppierte Index geändert wird. Aus diesem Grund kann es sehr lange dauern, von einem Heap zu einem gruppierten Index zu wechseln und umgekehrt, sowie viel Festplattenspeicher zum Neuordnen der Daten in tempdb erfordern.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [Beschreibung von gruppierten und nicht gruppierten Indizes](clustered-and-nonclustered-indexes-described.md)  
  
  
