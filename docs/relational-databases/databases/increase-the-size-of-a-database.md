---
description: Erhöhen der Größe einer Datenbank
title: Erhöhen der Größe einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017'
ms.openlocfilehash: 2c218c75784c6244285b625a0adfa47b4a913702
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97474071"
---
# <a name="increase-the-size-of-a-database"></a>Erhöhen der Größe einer Datenbank
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Dieses Thema beschreibt, wie eine Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]vergrößert wird. Datenbanken können entweder durch Vergrößern von vorhandenen Daten- oder Protokolldateien oder durch Hinzufügen neuer Dateien erweitert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So erhöhen Sie die Größe einer Datenbank mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Sie können keine Dateien hinzufügen oder entfernen, während eine BACKUP-Anweisung ausgeführt wird.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-increase-the-size-of-a-database"></a>So erhöhen Sie die Größe einer Datenbank  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung zu einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf die zu vergrößernde Datenbank, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie unter **Datenbankeigenschaften** die Seite **Dateien** aus.  
  
4.  Ändern Sie den Wert in der Spalte **Anfangsgröße (MB)** der entsprechenden Datei, um die Größe einer vorhandenen Datei zu erhöhen. Sie müssen jedoch die Größe der Datenbank um mindestens 1 MB erhöhen.  
  
5.  Um die Größe der Datenbank durch das Hinzufügen einer neuen Datei zu erhöhen, klicken Sie auf **Hinzufügen** und geben die Werte für die neue Datei ein. Weitere Informationen finden Sie unter [Hinzufügen von Daten oder Protokolldateien mit einer Datenbank](../../relational-databases/databases/add-data-or-log-files-to-a-database.md).  
  
6.  Klicken Sie auf **OK**.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-increase-the-size-of-a-database"></a>So erhöhen Sie die Größe einer Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird die Größe der Datei `test1dat3`erhöht.  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../relational-databases/databases/codesnippet/tsql/increase-the-size-of-a-d_1.sql)]  
  
 Weitere Beispiele finden Sie unter [ALTER DATABASE-Optionen Datei und Dateigruppe &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Daten- oder Protokolldateien zu einer Datenbank](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [Verkleinern einer Datenbank](../../relational-databases/databases/shrink-a-database.md)  
  
  
