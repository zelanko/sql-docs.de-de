---
title: Migrieren von Oracle-Datenbanken zu SQLServer (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 9e746d1df201349011d24fc0de007c74ba0073b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651188"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Migrieren von Oracle-Datenbanken zu SQL-Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für Oracle ist eine umfassende Umgebung, die Ihnen die schnelle Migration von Oracle-Datenbanken in hilft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Azure SQL-Datenbank oder Azure SQL Data Warehouse. SSMA für Oracle verwenden, Sie können überprüfen, Datenbankobjekte und Daten, Datenbanken für die Migration zu bewerten, migrieren Datenbankobjekte, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Azure SQL-Datenbank oder Azure SQL Data Warehouse, und migrieren Sie dann die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Azure SQL-Datenbank oder Azure SQL-Daten Das Warehouse. Beachten Sie, dass Sie nicht SYS und SYSTEM-Oracle-Schemas migrieren können.
  
## <a name="recommended-migration-process"></a>Empfohlene Migrationsprozess  
Für eine erfolgreiche Migration von Objekten und Daten aus Oracle-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Azure SQL-Datenbank oder Azure SQL Data Warehouse, verwenden Sie den folgenden Prozess:
  
1.  [Erstellen Sie ein neues SSMA-Projekt](working-with-ssma-projects-oracletosql.md).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die projektkonvertierung, Migration und Zuordnungsoptionen Typ festlegen. Weitere Informationen zu projekteinstellungen finden Sie unter [Setting Project Options Projektoptionen &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Informationen dazu, wie Sie die replikationsdatentyp-Zuordnungen anpassen, finden Sie unter [Zuordnen von Oracle- und SQL Server-Datentypen &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Verbinden mit dem Oracle-Datenbankserver](connecting-to-oracle-database-oracletosql.md).  
  
3.  [Verbinden mit einer Instanz von SQL Server](connecting-to-sql-server-oracletosql.md).  
  
4.  [Zuordnen von Oracle-Datenbank-Schemas zu SQL Server-Datenbankschemas](mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
5.  Optional [erstellen Bewertungsberichte](assessing-oracle-schemas-for-conversion-oracletosql.md) Datenbankobjekte für die Konvertierung zu bewerten und die Konvertierungszeit zu schätzen.  
  
6.  [Konvertieren von Oracle-Datenbankschemas in SQL Server-Schemas](converting-oracle-schemas-oracletosql.md).  
  
7.  [Laden von konvertierten Datenbankobjekten in SQL Server](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
    Dies ist in einem der folgenden Arten möglich:  
  
    -   Speichern Sie ein Skript, und führen Sie es in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
8.  [Migrieren von Daten zu SQL Server](migrating-oracle-data-into-sql-server-oracletosql.md).  
  
9. Bei Bedarf datenbankanwendungen zu aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Erste Schritte mit SSMA für Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
