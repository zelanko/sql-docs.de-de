---
title: Migrieren von Zugriffsdaten in SQL Server Azure SQL-Datenbank (Access Token) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- bulk loading data
- data, loading into SQL Azure
- data, loading into SQL Server
- migrating databases, loading data
- migrating databases, options
- options, migrating data
- SQL Azure, migrating data into
- SQL Server, migrating data into
ms.assetid: f3b18af7-1af0-499d-a00d-a0af94895625
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 612fdc570ddafbf35ecba420574a5b25da844f08
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823832"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-database-accesstosql"></a>Migrieren von Zugriffsdaten in SQL Server Azure SQL-Datenbank (Access Token)
Nachdem Sie die Datenbankobjekte erfolgreich in erstellt haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie Daten von Access zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure migrieren.  
  
## <a name="setting-migration-options"></a>Festlegen von Migrations Optionen  
Überprüfen Sie vor dem Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure die Projekt Migrations Optionen im Dialogfeld **Projekteinstellungen** . In diesem Dialogfeld können Sie die Batch Größe für die Migration, das Sperren von Tabellen, die Einschränkungs Überprüfung, das Auslösen von Triggern, die Identitäts-und NULL-Wert Behandlung sowie die Behandlung von Datumsangaben, die außerhalb des Bereichs liegen, festlegen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Projekteinstellungen (Migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>Migrieren von Daten  
Beim Migrieren von Daten handelt es sich um einen Massen Ladevorgang, bei dem Daten Zeilen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Transaktionen verschoben oder in Transaktionen SQL Azure werden. Die Anzahl der Zeilen, die in jede Transaktion in geladen oder SQL Azure werden sollen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird in den Projekteinstellungen konfiguriert.  
  
Stellen Sie sicher, dass der Ausgabebereich angezeigt wird, um Migrations Meldungen anzuzeigen. Wenn dies nicht der Fall ist, wählen Sie im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So migrieren Sie Daten**  
  
1.  Stellen Sie sicher, dass Sie die Access-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure geladen haben.  
  
2.  Wählen Sie in Access Metadata Explorer die Objekte aus, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um Daten für eine gesamte Datenbank zu migrieren.  
  
    -   Wenn Sie Daten aus einzelnen Tabellen migrieren möchten, erweitern Sie die Datenbank, erweitern Sie **Tabellen**, und aktivieren Sie dann das Kontrollkästchen neben der Tabelle. Deaktivieren Sie das Kontrollkästchen, um Daten aus einzelnen Tabellen auszulassen.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Datenbanken** und dann auf **Daten migrieren**  
  
Sie können Daten auch außerhalb von SSMA migrieren, indem Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Befehlszeilen-Hilfsprogramm **bcp** oder verwenden [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Weitere Informationen zu diesen Tools finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Wenn Sie auf Datenbankanwendungen zugreifen möchten, die nach der Migration weiterhin verwendet werden sollen, verknüpfen Sie die Access-Datenbanktabellen mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen oder SQL Azure Tabellen. Weitere Informationen finden Sie unter [Verknüpfen von Access-Anwendungen mit SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Festlegen von Konvertierungs-und Migrations Optionen](setting-conversion-and-migration-options-accesstosql.md)  
  
