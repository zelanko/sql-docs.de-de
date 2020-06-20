---
title: Ausführen von Onlineindexvorgängen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d09bd99a0eaec5fdb433bd8c33351d7622957a2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049865"
---
# <a name="perform-index-operations-online"></a>Ausführen von Onlineindexvorgängen
  In diesem Thema wird beschrieben, wie Sie Indizes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]online erstellen, neu erstellen oder löschen. Die ONLINE-Option ermöglicht, dass Benutzer während dieser Indexvorgänge gleichzeitig auf die dem Index zugrunde liegende Tabelle oder auf Daten eines gruppierten Indexes sowie auf alle eventuell damit verbundenen nicht gruppierten Indizes zugreifen können. Während beispielsweise ein gruppierter Index von einem Benutzer neu erstellt wird, kann dieser Benutzer – und alle anderen Benutzer – weiterhin die dem Index zugrunde liegenden Daten aktualisieren oder abfragen. Wenn Sie DDL-Vorgänge (Datendefinitionssprache) wie das Erstellen oder Neuerstellen eines gruppierten Indexes offline ausführen, richten diese Vorgänge exklusive Sperren für die dem Index zugrunde liegenden Daten und damit verbundene Indizes ein. Damit werden Änderungen und Abfragen der zugrunde liegenden Daten verhindert, bis der Indexvorgang abgeschlossen ist.  
  
> [!NOTE]  
>  Onlineindexvorgänge sind nicht in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **Onlineneuerstellung eines Indexes mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Onlineindexvorgänge werden in Geschäftsumgebungen empfohlen, die rund um die Uhr und 7 Tage die Woche aktiv sind, für die also eine gleichzeitige Benutzeraktivität während Indexvorgängen unabdingbar ist.  
  
-   Die ONLINE-Option ist in folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verfügbar:  
  
    -   [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql)  
  
    -   [ALTER INDEX](/sql/t-sql/statements/alter-index-transact-sql)  
  
    -   [DROP INDEX](/sql/t-sql/statements/drop-index-transact-sql)  
  
    -   [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (zum Hinzufügen oder Löschen von UNIQUE- oder PRIMARY KEY-Einschränkungen mit der CLUSTERED-Indexoption)  
  
-   Weitere Einschränkungen und Einschränkungen im Zusammenhang mit der Onlineerstellung, -neuerstellung und -löschung von Indizes finden Sie unter [Richtlinien für Onlineindexvorgänge](guidelines-for-online-index-operations.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung in der Tabelle oder Sicht.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rebuild-an-index-online"></a>Sie erstellen Sie einen Index online neu  
  
1.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um die Datenbank mit der Tabelle zu erweitern, in der Sie einen Index online neu erstellen möchten.  
  
2.  Erweitern Sie den Ordner **Tabellen** .  
  
3.  Klicken Sie auf das Pluszeichen, um die Tabelle zu erweitern, für die Sie einen Index online neu erstellen möchten.  
  
4.  Erweitern Sie den Ordner **Indizes** .  
  
5.  Klicken Sie mit der rechten Maustaste auf den Index, den Sie online neu erstellen möchten, und wählen Sie **Eigenschaften**aus.  
  
6.  Wählen Sie unter **Seite auswählen**die Option **Optionen**aus.  
  
7.  Wählen Sie **DML-Onlineverarbeitung zulassen**aus, und wählen Sie dann in der Liste **True** aus.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie mit der rechten Maustaste auf den Index, den Sie online neu erstellen möchten, und wählen Sie **Neu erstellen**aus.  
  
10. Überprüfen Sie im Dialogfeld **Indizes neu erstellen** , dass der richtige Index im Raster **Neu zu erstellende Indizes** ausgewählt ist, und klicken sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a>So können Sie einen Index online erstellen, neu erstellen oder löschen  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im folgenden Beispiel wird ein vorhandener Index online neu erstellt.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     Im folgenden Beispiel wird ein gruppierter Index online gelöscht, und die daraus resultierende Tabelle (Heap) wird in die Dateigruppe `NewGroup` verschoben, wofür die `MOVE TO` -Klausel verwendet wird. Die Katalogsichten `sys.indexes`, `sys.tables`und `sys.filegroups` werden abgefragt, um die Platzierung von Index und Tabelle in den Dateigruppen vor und nach der Verschiebung zu prüfen.  
  
     [!code-sql[IndexDDL#DropIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/dropindex.sql#dropindex4)]  
  
 Weitere Informationen finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
  
