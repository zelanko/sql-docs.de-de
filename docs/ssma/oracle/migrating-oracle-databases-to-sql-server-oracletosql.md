---
title: Migrieren von Oracle-Datenbanken zu SQL Server (oracleto SQL) | Microsoft-Dokumentation
description: Verwenden Sie diesen empfohlenen Prozess zum Migrieren von Oracle-Datenbanken zu SQL Server oder Azure SQL-Datenbank mithilfe von SQL Server Migration Assistant (SSMA).
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 194d33d0b5318ca66494b838c7f59dfde5c72b88
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933441"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Migrieren von Oracle-Datenbanken zu SQL-Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für Oracle ist eine umfassende Umgebung, die Sie beim schnellen Migrieren von Oracle-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Azure SQL-Datenbank oder Azure SQL Data Warehouse unterstützt. Mithilfe von SSMA für Oracle können Sie Datenbankobjekte und-Daten überprüfen, Datenbanken für die Migration bewerten, Datenbankobjekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Azure SQL-Datenbank migrieren oder Azure SQL Data Warehouse und dann Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Azure SQL-Datenbank oder Azure SQL Data Warehouse migrieren. Beachten Sie, dass Sie keine sys-und System Oracle-Schemas migrieren können.
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Verwenden Sie den folgenden Prozess, um Objekte und Daten aus Oracle-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Azure SQL-Datenbank oder Azure SQL Data Warehouse erfolgreich zu migrieren:
  
1.  [Erstellen Sie ein neues SSMA-Projekt](working-with-ssma-projects-oracletosql.md).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die Optionen für die Projekt Konvertierung, die Migration und die Typzuordnung festlegen. Weitere Informationen zu Projekteinstellungen finden Sie unter [Festlegen von Projektoptionen &#40;oracleto SQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Weitere Informationen zum Anpassen von Datentyp Zuordnungen finden Sie unterzuordnen von [Oracle-und SQL Server-Datentypen &#40;oracletosql&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  Stellen [Sie eine Verbindung zum Oracle-Datenbankserver](connecting-to-oracle-database-oracletosql.md)her.  
  
3.  Stellen [Sie eine Verbindung mit einer Instanz von SQL Server](connecting-to-sql-server-oracletosql.md)her.  
  
4.  Ordnen [Sie Oracle-Datenbankschemas SQL Server Datenbankschemas zu](mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
5.  Erstellen Sie optional [Bewertungsberichte](assessing-oracle-schemas-for-conversion-oracletosql.md) , um die Datenbankobjekte zu konvertieren und die Konvertierungs Zeit einzuschätzen.  
  
6.  [Konvertieren Sie Oracle-Datenbankschemas in SQL Server Schemas](converting-oracle-schemas-oracletosql.md).  
  
7.  [Laden Sie die konvertierten Datenbankobjekte in SQL Server](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
    Wählen Sie dazu eine der folgenden Methoden:  
  
    -   Speichern Sie ein Skript, und führen Sie es in aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
8.  [Migrieren von Daten zu SQL Server](migrating-oracle-data-into-sql-server-oracletosql.md).  
  
9. Aktualisieren Sie ggf. Datenbankanwendungen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für Oracle &#40;oracleto SQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Informationen zu den ersten Schritten mit SSMA für Oracle &#40;oracleto SQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
