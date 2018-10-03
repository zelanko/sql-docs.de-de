---
title: Prüfen der Integrität von Datenbanken mit fehlerverdächtigen Seiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8fc6356b4a4325f394324f91e2e7f8e76e30f367
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170580"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Prüfen der Integrität von Datenbanken mit fehlerverdächtigen Seiten
  Diese Regel überprüft Benutzerdatenbanken, deren Datenbankstatus auf Fehlerverdächtig festgelegt ist. Wenn [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] eine Datenbankseite mit einem Fehler vom Typ 824 liest, wird die Seite als "fehlerverdächtig" betrachtet und ihre Seiten-ID in der suspect_pages-Tabelle der msdb-Datenbank aufgezeichnet. Der Status der Datenbank, die diese Seite enthält, wird auf Fehlerverdächtig festgelegt.  
  
 Der Fehler vom Typ 824 gibt an, dass ein logischer Konsistenzfehler während eines Lesevorgangs aufgetreten ist. Dieser Fehler gibt häufig eine von einer fehlerhaften E/A-Subsystem-Komponente verursachte Datenbeschädigung an. Dies ist ein schwerer Fehler, der die Datenbankintegrität bedroht und sofort behoben werden muss.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
  
-   Weitere Details zum Fehler des Typs 824 finden Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll dieser Datenbank.  
  
-   Führen Sie eine vollständige Datenbankkonsistenzprüfung ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)) aus.  
  
-   Implementieren Sie die Benutzeraktionen, die in [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397)definiert werden.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Verwalten der suspect_pages-Tabelle &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
