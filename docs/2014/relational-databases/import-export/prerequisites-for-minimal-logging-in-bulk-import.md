---
title: Voraussetzungen für die minimale Protokollierung beim Massenimport | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- minimal logging [SQL Server]
- logged bulk copy [SQL Server]
- logs [SQL Server], minimal logging
- minimally logged operations [SQL Server]
- bulk importing [SQL Server], minimal logging
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
caps.latest.revision: 46
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e59ede589492039cbcae511cba462111577efb0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061169"
---
# <a name="prerequisites-for-minimal-logging-in-bulk-import"></a>Voraussetzungen für die minimale Protokollierung beim Massenimport
  Für eine Datenbank, bei der das vollständige Wiederherstellungsmodell verwendet wird, werden alle beim Massenimport ausgeführten Vorgänge für das Einfügen von Zeilen vollständig im Transaktionsprotokoll protokolliert. Bei umfangreichen Datenimporten kann das Transaktionsprotokoll schnell aufgefüllt werden, wenn das vollständige Wiederherstellungsmodell verwendet wird. Im Gegensatz dazu reduziert die minimale Protokollierung von Massenimportvorgängen beim einfachen Wiederherstellungsmodell oder beim massenprotokollierten Wiederherstellungsmodell die Gefahr eines Überlaufs des Protokollspeichers durch einen Massenimportvorgang. Darüber hinaus ist die minimale Protokollierung effizienter als die vollständige Protokollierung.  
  
> [!NOTE]  
>  Das massenprotokollierte Wiederherstellungsmodell wurde entwickelt, um das vollständige Wiederherstellungsmodell während umfangreicher Massenvorgänge vorübergehend zu ersetzen.  
  
## <a name="table-requirements-for-minimally-logging-bulk-import-operations"></a>Tabellenanforderungen für die minimale Protokollierung bei Massenimportvorgängen  
 Für die minimale Protokollierung muss die Zieltabelle die folgenden Bedingungen erfüllen:  
  
-   Die Tabelle wird nicht repliziert.  
  
-   Eine Tabellensperre ist angegeben (mit TABLOCK).  
  
    > [!NOTE]  
    >  Obwohl Dateneinfügungen bei einem minimal protokollierten Massenimportvorgang nicht im Transaktionsprotokoll protokolliert werden, protokolliert das [!INCLUDE[ssDE](../../includes/ssde-md.md)] dennoch Blockzuordnungen, wenn der Tabelle ein neuer Block zugeordnet wird.  
  
-   Die Tabelle ist keine speicheroptimierte Tabelle.  
  
 Ob die minimale Protokollierung für eine Tabelle möglich ist, hängt auch davon ab, ob die Tabelle indiziert ist und, falls dies der Fall ist, ob die Tabelle leer ist:  
  
-   Wenn die Tabelle keine Indizes besitzt, werden die Datenseiten minimal protokolliert.  
  
-   Falls die Tabelle keinen gruppierten Index, aber mindestens einen nicht gruppierten Index aufweist, werden die Datenseiten immer minimal protokolliert. Wie Indexseiten protokolliert werden, hängt jedoch davon ab, ob die Tabelle leer ist:  
  
    -   Falls die Tabelle leer ist, werden Indexseiten minimal protokolliert.  
  
    -   Falls die Tabelle nicht leer ist, werden Indexseiten vollständig protokolliert.  
  
        > [!NOTE]  
        >  Wenn Sie mit einer leeren Tabelle beginnen und die Daten in mehreren Batches massenimportieren, werden für den ersten Batch sowohl Index- als auch Datenseiten minimal protokolliert. Ab dem zweiten Batch jedoch werden nur Datenseiten minimal protokolliert.  
  
-   Falls die Tabelle einen gruppierten Index aufweist und leer ist, werden Daten- und Indexseiten minimal protokolliert. Wenn dagegen eine Tabelle einen gruppierten Index aufweist und nicht leer ist, werden Daten- und Indexseiten unabhängig vom Wiederherstellungsmodell vollständig protokolliert.  
  
    > [!NOTE]  
    >  Wenn Sie mit einer leeren Tabelle beginnen und die Daten in Batches massenimportieren, werden für den ersten Batch sowohl Index- als auch Datenseiten minimal protokolliert. Ab dem zweiten Batch jedoch werden nur Datenseiten massenprotokolliert.  
  
> [!NOTE]  
>  Wenn die Transaktionsreplikation aktiviert ist, werden BULK INSERT-Vorgänge auch unter dem massenprotokollierten Wiederherstellungsmodell vollständig protokolliert.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  

  
## <a name="see-also"></a>Siehe auch  
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)   
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)   
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)  
  
  
