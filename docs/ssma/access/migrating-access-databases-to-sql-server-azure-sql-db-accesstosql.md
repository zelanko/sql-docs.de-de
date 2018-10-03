---
title: Migrieren von Access-Datenbanken zu SQLServer – Azure SQL-Datenbank | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instructions, migration
- migrating databases, overview
- overview, migration process
- procedure, migration
- recommended migration process
ms.assetid: 76a3abcf-2998-4712-9490-fe8d872c89ca
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: b15ecd732acf373dbc5cee817983305c1d792fe4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683708"
---
# <a name="migrating-access-databases-to-sql-server---azure-sql-db-accesstosql"></a>Migrieren von Access-Datenbanken zu SQL Server – Azure SQL-Datenbank (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) ist ein Tool, das eine umfassende Umgebung bereitstellt, mit dem Sie die schnelle Migration von Access-Datenbanken können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Mit SSMA, Sie können den Zugriff überprüfen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekte, die Access-Datenbank für die Migration zu bewerten, konvertieren den Zugriff auf Datenbankobjekte, laden Sie diese in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, und klicken Sie dann die Daten migrieren.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Für eine erfolgreiche Migration von Objekten und Daten aus den Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, das folgende Verfahren verwenden:  
  
1.  [Erstellen Sie ein neues SSMA-Projekt](creating-and-managing-projects-accesstosql.md). Nachdem Sie das Projekt erstellt haben, können Sie [Festlegen von Projektoptionen](setting-conversion-and-migration-options-accesstosql.md), einschließlich Optionen für die Migrationsoptionen und geben Sie datentypzuordnungen.  
  
2.  [Hinzufügen von Access-Datenbankdateien](adding-and-removing-access-database-files-accesstosql.md) zum Projekt.  
  
    Sie können einzelne Dateien, einschließlich der Dateien, die Sie finden auf dem Computer oder Netzwerk hinzufügen.  
  
3.  [Herstellen einer Verbindung mit der Zielinstanz von SQL Server](connecting-to-sql-server-accesstosql.md) oder [Herstellen einer Verbindung mit der Zielinstanz von SQL Azure](connecting-to-azure-sql-db-accesstosql.md).  
  
    Sie können entweder in SQL Server oder SQL Azure verbinden.  
  
4.  Zum Anpassen der Zuordnung zwischen einer oder mehreren Access-Datenbanken und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Schemas, [die Quell- und Zieldatenbanken zuordnen](mapping-source-and-target-databases-accesstosql.md).  
  
5.  Optional können Sie [erstellen Sie ein Bewertungsbericht](assessing-access-database-objects-for-conversion-accesstosql.md) zu bestimmen, ob die Zugriff auf Datenbankobjekte erfolgreich konvertiert werden können, können Sie auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
6.  [Konvertieren Sie den Zugriff auf Datenbankobjekte](converting-access-database-objects-accesstosql.md) zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objektdefinitionen.  
  
7.  [Laden von konvertierten Datenbankobjekten in SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
    Sie können entweder die Datenbankobjekte in laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure mithilfe von SSMA, oder Sie können speichern [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts.  
  
8.  [Migrieren Sie den Zugriff auf Daten in SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
    > [!NOTE]  
    > Sie können zu konvertieren, laden und Migrieren von Schemas und Daten in einem Schritt. Um nur einem Klick Migration durchzuführen, klicken Sie auf die **konvertieren, laden und migrieren** Schaltfläche.  
  
9. Wenn Sie möchten, dass die Access-Anwendungen, die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, Verwendung [die zugreifen auf Tabellen mit SQL Server-Tabellen verknüpfen](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
Der Migrations-Assistent können auch, die Sie durch diesen Vorgang führen. Weitere Informationen finden Sie unter [Migrations-Assistent](migration-wizard-accesstosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Erste Schritte mit SQL Server Migration Assistant für Access](getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Access-Datenbanken vorbereitet für die Migration.](preparing-access-databases-for-migration-accesstosql.md)
