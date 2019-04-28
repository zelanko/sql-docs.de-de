---
title: Anzeigen oder Ändern der Eigenschaften einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10ad92286011f6f81fbaff5ab4908007e16bdd45
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870950"
---
# <a name="view-or-change-the-properties-of-a-database"></a>Anzeigen oder Ändern der Eigenschaften einer Datenbank
  In diesem Thema wird die Vorgehensweise zum Anzeigen oder Ändern der Eigenschaften einer Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]beschrieben. Nachdem Sie eine Datenbankeigenschaft geändert haben, tritt die Änderung sofort in Kraft.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So zeigen Sie die Eigenschaften einer Datenbank an oder ändern diese mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Ist AUTO_CLOSE auf ON festgelegt, geben einige Spalten in der [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) -Katalogsicht sowie die DATABASEPROPERTYEX-Funktion den Wert NULL zurück, da die Datenbank nicht für den Abruf der Daten verfügbar ist. Führen Sie eine USE-Anwendung zum Öffnen der Datenbank aus, um dieses Problem zu beheben.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a>So zeigen Sie die Eigenschaften einer Datenbank an oder ändern diese  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung zu einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf die anzuzeigende Datenbank, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie im Dialogfeld **Datenbankeigenschaften** eine anzuzeigende Seite aus, um die entsprechenden Informationen anzuzeigen. Wählen Sie z. B. die Seite **Dateien** aus, um Daten- und Protokolldateiinformationen anzuzeigen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a>So zeigen Sie eine Eigenschaft einer Datenbank mit DATABASEPROPERTYEX an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird die Systemfunktion [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) verwendet, um den Status der AUTO_SHRINK-Datenbankoption in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank zurückzugeben. Der Rückgabewert 1 bedeutet, dass die Option auf ON festgelegt ist, und der Rückgabewert 0 bedeutet, dass die Option auf OFF festgelegt ist.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a>So zeigen Sie die Eigenschaften einer Datenbank durch das Abfragen von sys.databases an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird die [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) -Katalogsicht abgefragt, um mehrere Eigenschaften der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank anzuzeigen. In diesem Beispiel wird die Datenbank-ID-Nummer (`database_id`), der Schreibschutz- oder Lese-/Schreibstatus der Datenbank (`is_read_only`), die Sortierung für die Datenbank (`collation_name`) und der Datenbank-Kompatibilitätsgrad (`compatibility_level`) zurückgegeben.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a>So ändern Sie die Eigenschaften einer Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, und fügen Sie es in das Abfragefenster ein. Im Beispiel wird der Momentaufnahmen-Isolationsstatus für die Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] bestimmt und der Zustand der Eigenschaft geändert. Anschließend wird die Änderung überprüft.  
  
     Um den Momentaufnahmen-Isolationsstatus zu bestimmen, wählen Sie die erste `SELECT` -Anweisung aus und klicken auf **Ausführen**.  
  
     Um den Momentaufnahmen-Isolationsstatus zu ändern, wählen Sie die `ALTER DATABASE` -Anweisung aus und klicken auf **Ausführen**.  
  
     Um die Änderung zu überprüfen, wählen Sie die zweite `SELECT` -Anweisung aus und klicken auf **Ausführen**.  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a>Siehe auch  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)   
 [ALTER DATABASE-Datenbankspiegelung &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)   
 [ALTER DATABASE-Optionen für Dateien und Dateigruppen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  
