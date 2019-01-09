---
title: Anzeigen von Kollokations Informationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9cb0f104d1555b18d18df38027c240a392d2ac66
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52784002"
---
# <a name="view-collation-information"></a>Anzeigen von Sortierungsinformationen
    
##  <a name="Top"></a> Sie können die Sortierung eines Servers, einer Datenbank oder Spalte in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mithilfe der Menüoptionen des Objekt-Explorers oder mit [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen.  
  
##  <a name="Procedures"></a> So zeigen Sie eine Sortierungseinstellung an  
 Sie können eine der folgenden Anwendungen verwenden:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 **So zeigen Sie eine Sortierungseinstellung für einen Server (Instanz von SQL Server) im Objekt-Explorer an**  
  
1.  Stellen Sie mithilfe im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.   Klicken Sie mit der rechten Maustaste auf die Spalte, und wählen Sie **Eigenschaften**aus.  
  
 **So zeigen Sie eine Sortierungseinstellung für eine Datenbank im Objekt-Explorer an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf die Datenbank, und wählen Sie **Eigenschaften**aus.  
  
 **So zeigen Sie eine Sortierungseinstellung für eine Spalte im Objekt-Explorer an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, die Datenbank und anschließend **Tabellen**.  
  
3.  Erweitern Sie die Tabelle, die die Spalte enthält, und erweitern Sie dann **Spalten**.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Spalte, und wählen Sie **Eigenschaften**aus. Wenn die Sortierungseigenschaft leer ist, ist die Spalte nicht vom Zeichendatentyp.  
  
###  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So zeigen Sie die Sortierungseinstellung eines Servers an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
2.  Geben Sie im Abfragefenster die folgende Anweisung ein, die die SERVERPROPERTY-Systemfunktion verwendet:  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  Alternativ können Sie die gespeicherte Systemprozedur "sp_helpsort" verwenden.  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 **So zeigen Sie alle von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
2.  Geben Sie im Abfragefenster die folgende Anweisung ein, die die SERVERPROPERTY-Systemfunktion verwendet:  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 **So zeigen Sie die Sortierungseinstellung einer Datenbank an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
2.  Geben Sie im Abfragefenster die folgende Anweisung ein, die die sys.databases-Systemkatalogsicht verwendet.  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  Alternativ können Sie die DATABASEPROPERTYEX-Systemfunktion verwenden.  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 **So zeigen Sie die Sortierungseinstellung einer Spalte an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
2.  Geben Sie im Abfragefenster die folgende Anweisung ein, die die sys.columns-Systemkatalogsicht verwendet.  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)   
 [Rangfolge von Sortierungen &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql)   
 [sp_helpsort &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsort-transact-sql)  
  
  
