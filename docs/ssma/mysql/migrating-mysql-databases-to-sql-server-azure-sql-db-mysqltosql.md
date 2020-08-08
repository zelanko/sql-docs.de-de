---
title: Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank | Microsoft-Dokumentation
description: Verwenden Sie diesen empfohlenen Vorgang zum Migrieren von MySQL-Datenbanken zu SQL Server oder Azure SQL-Datenbank mithilfe von SQL Server Migration Assistant (SSMA).
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 7f42e460be6dd4f4b36b0ddaf3c52880775df8e0
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935259"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-database-mysqltosql"></a>Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank (mysqlto SQL)
SQL Server Migration Assistant (SSMA) für MySQL ist eine umfassende Umgebung, die Sie beim schnellen Migrieren von MySQL-Datenbanken zu SQL Server oder SQL Azure unterstützt. Mithilfe von SSMA für MySQL können Sie Datenbankobjekte und-Daten überprüfen, Datenbanken für die Migration bewerten, Datenbankobjekte zu SQL Server oder SQL Azure migrieren und dann Daten zu SQL Server oder SQL Azure migrieren.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Verwenden Sie den folgenden Prozess, um Objekte und Daten aus MySQL-Datenbanken erfolgreich zu SQL Server oder SQL Azure zu migrieren:  
  
1.  [Arbeiten mit SSMA-Projekten &#40;mysqlto SQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die Optionen für die Projekt Konvertierung, die Migration und die Typzuordnung festlegen. Weitere Informationen zu Projekteinstellungen finden Sie unter [Festlegen von Projektoptionen &#40;mysqlto SQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). Weitere Informationen zum Anpassen von Datentyp Zuordnungen finden Sie unterzuordnen von [MySQL-und SQL Server-Datentypen &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [Herstellen einer Verbindung mit MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [Herstellen einer Verbindung mit SQL Server &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Zuordnung von MySQL-Datenbanken zu SQL Server Schemas &#40;mysqlto SQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  Optional: [bewerten der MySQL-Datenbanken für die Konvertierung &#40;mysqltoisql&#41;](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) , um Datenbankobjekte für die Konvertierung zu bewerten und die Konvertierungs Zeit einzuschätzen.  
  
7.  [MySQL-Datenbanken &#40;mysqlto SQL-&#41;werden umgerechnet](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Synchronisierung](loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
9. Wählen Sie dazu eine der folgenden Methoden:  
  
    -   Speichern Sie ein Skript, und führen Sie es auf SQL Server oder SQL Azure aus.  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
10. [Migrieren von MySQL-Daten in SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. Aktualisieren Sie ggf. Datenbankanwendungen.  
  
> [!NOTE]  
> Information_schema-und MySQL-Schemas können nicht migriert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für MySQL &#40;mysqldesql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Informationen zu den ersten Schritten mit SSMA für MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
