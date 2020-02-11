---
title: Ausführen von Skripts während der Synchronisierung (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2565eb2be68c1e964b82d46d9aa8fc9f39a01f70
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74165023"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Ausführen von Skripts während der Synchronisierung (Replikationsprogrammierung mit Transact-SQL)
  Die Replikation unterstützt die bedarfsgesteuerte Ausführung von Skripts für Abonnenten von Transaktions- und Mergeveröffentlichungen. Diese Funktionalität kopiert das Skript in das Replikationsarbeitsverzeichnis und wendet das Skript dann mithilfe von **sqlcmd** auf dem Abonnenten an. Standardmäßig wird der Verteilungs-Agent beendet, wenn beim Anwenden des Skripts auf ein Abonnement für eine Transaktionsveröffentlichung ein Fehler auftritt. Mithilfe von gespeicherten Replikationsprozeduren können Sie ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript angeben, das programmgesteuert ausgeführt werden soll.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>So geben Sie ein Skript an, das für alle Abonnenten einer Momentaufnahme-, Transaktions- oder Mergeveröffentlichung ausgeführt werden soll  
  
1.  Erstellen und testen Sie das [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript, das bedarfsgesteuert ausgeführt wird.  
  
2.  Speichern Sie die Skriptdatei an einem Speicherort, auf den der Momentaufnahme-Agent für die Veröffentlichung zugreifen kann.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql) aus. Geben ** \@** Sie die Veröffentlichung, den Namen der Skriptdatei mit dem vollständigen UNC-Pfad, der in Schritt 2 für ** \@scriptfile**erstellt wurde, und einen der folgenden Werte für ** \@"SkipError**" an:  
  
    -   **0** &ndash; der Agent beendet die Ausführung des Skripts, wenn ein Fehler auftritt.  
  
    -   **1** &ndash; der Agent protokolliert Fehler und setzt die Ausführung des Skripts fort, wenn Fehler auftreten.  
  
4.  Das angegebene Skript wird auf jedem Abonnenten ausgeführt, wenn der Agent das nächste Mal zur Synchronisierung des Abonnements ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Synchronisieren von Daten](synchronize-data.md)  
  
  
