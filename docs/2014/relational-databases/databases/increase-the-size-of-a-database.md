---
title: Erhöhen der Größe einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 02a34ba1e0f441b665c239d60f6398afa4247102
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808992"
---
# <a name="increase-the-size-of-a-database"></a>Erhöhen der Größe einer Datenbank
  Dieses Thema beschreibt, wie eine Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]vergrößert wird. Datenbanken können entweder durch Vergrößern von vorhandenen Daten- oder Protokolldateien oder durch Hinzufügen neuer Dateien erweitert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So erhöhen Sie die Größe einer Datenbank mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Sie können keine Dateien hinzufügen oder entfernen, während eine BACKUP-Anweisung ausgeführt wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-increase-the-size-of-a-database"></a>So erhöhen Sie die Größe einer Datenbank  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung zu einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf die zu vergrößernde Datenbank, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie unter **Datenbankeigenschaften**die Seite **Dateien** aus.  
  
4.  Ändern Sie den Wert in der Spalte **Anfangsgröße (MB)** der entsprechenden Datei, um die Größe einer vorhandenen Datei zu erhöhen. Sie müssen jedoch die Größe der Datenbank um mindestens 1 MB erhöhen.  
  
5.  Um die Größe der Datenbank durch das Hinzufügen einer neuen Datei zu erhöhen, klicken Sie auf **Hinzufügen** und geben die Werte für die neue Datei ein. Weitere Informationen finden Sie unter [Hinzufügen von Daten oder Protokolldateien mit einer Datenbank](add-data-or-log-files-to-a-database.md).  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-increase-the-size-of-a-database"></a>So erhöhen Sie die Größe einer Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird die Größe der Datei `test1dat3` erhöht.  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 Weitere Beispiele finden Sie unter [ALTER DATABASE-Optionen Datei und Dateigruppe &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Daten- oder Protokolldateien zu einer Datenbank](add-data-or-log-files-to-a-database.md)   
 [Verkleinern einer Datenbank](shrink-a-database.md)  
  
  
