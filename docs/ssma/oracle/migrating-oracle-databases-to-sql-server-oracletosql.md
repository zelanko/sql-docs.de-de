---
title: Migrieren von Oracle-Datenbanken zu SQLServer (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: f20b7271932cbbcc0538fc9923e45b2fc029f646
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983202"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Migrieren von Oracle-Datenbanken zu SQLServer (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) für Oracle ist eine umfassende Umgebung, die Ihnen die schnelle Migration von Oracle-Datenbanken in hilft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], Azure SQL-Datenbank oder Azure SQL Data Warehouse. SSMA für Oracle verwenden, Sie können überprüfen, Datenbankobjekte und Daten, Datenbanken für die Migration zu bewerten, migrieren Datenbankobjekte, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], Azure SQL-Datenbank oder Azure SQL Data Warehouse, und migrieren Sie dann die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], Azure SQL-Datenbank oder Azure SQL-Daten Das Warehouse. Beachten Sie, dass Sie nicht SYS und SYSTEM-Oracle-Schemas migrieren können.
  
## <a name="recommended-migration-process"></a>Empfohlene Migrationsprozess  
Für eine erfolgreiche Migration von Objekten und Daten aus Oracle-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], Azure SQL-Datenbank oder Azure SQL Data Warehouse, verwenden Sie den folgenden Prozess:
  
1.  [Erstellen Sie ein neues SSMA-Projekt](http://msdn.microsoft.com/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die projektkonvertierung, Migration und Zuordnungsoptionen Typ festlegen. Weitere Informationen zu projekteinstellungen finden Sie unter [Setting Project Options Projektoptionen &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Informationen dazu, wie Sie die replikationsdatentyp-Zuordnungen anpassen, finden Sie unter [Zuordnen von Oracle- und SQL Server-Datentypen &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Verbinden mit dem Oracle-Datenbankserver](http://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
3.  [Verbinden mit einer Instanz von SQL Server](http://msdn.microsoft.com/1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
4.  [Zuordnen von Oracle-Datenbank-Schemas zu SQL Server-Datenbankschemas](http://msdn.microsoft.com/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc).  
  
5.  Optional [erstellen Bewertungsberichte](http://msdn.microsoft.com/4de9bcf6-1346-4740-87f9-7f24a8226357) Datenbankobjekte für die Konvertierung zu bewerten und die Konvertierungszeit zu schätzen.  
  
6.  [Konvertieren von Oracle-Datenbankschemas in SQL Server-Schemas](http://msdn.microsoft.com/e021182d-31da-443d-b110-937f5db27272).  
  
7.  [Laden von konvertierten Datenbankobjekten in SQL Server](http://msdn.microsoft.com/a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
    Dies ist in einem der folgenden Arten möglich:  
  
    -   Speichern Sie ein Skript, und führen Sie es in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
8.  [Migrieren von Daten zu SQL Server](http://msdn.microsoft.com/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
9. Bei Bedarf datenbankanwendungen zu aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Erste Schritte mit SSMA für Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
