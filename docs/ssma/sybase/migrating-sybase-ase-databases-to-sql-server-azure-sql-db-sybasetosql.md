---
title: Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 96ade7125c0d03963e8e012ed72bdb8fdef492cf
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51662349"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Migrieren von SAP ASE-Datenbanken zu SQL Server – Azure SQL-Datenbank (SybaseToSQL)
SQL Server Migration Assistant (SSMA) für SAP Adaptive Server Enterprise (ASE) ist eine umfassende Umgebung, die Ihnen die schnelle Migration von SAP ASE-Datenbanken, um die hilft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. SSMA für SAP ASE verwenden, Sie können überprüfen, Datenbankobjekte und Daten, Datenbanken für die Migration zu bewerten, migrieren Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank und migrieren Sie dann die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Für eine erfolgreiche Migration von Objekten und Daten aus SAP ASE-Datenbanken, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank das folgende Verfahren verwenden:  
  
1.  [Erstellen Sie ein neues SSMA-Projekt](working-with-ssma-projects-sybasetosql.md).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die projektkonvertierung, Migration und Zuordnungsoptionen Typ festlegen. Weitere Informationen zu projekteinstellungen finden Sie unter [Setting Project Options Projektoptionen &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Informationen zum Anpassen der datentypzuordnungen finden Sie unter [Mapping Sybase ASE und SQL Server-Datentypen &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Verbinden mit einem der SAP ASE-Datenbankserver](connecting-to-sybase-ase-sybasetosql.md).  
  
3.  [Herstellen einer Verbindung mit einer Instanz von SQL Server](connecting-to-sql-server-sybasetosql.md) oder [Herstellen einer Verbindung mit einer Instanz von Azure SQL-Datenbank](connecting-to-azure-sql-db-sybasetosql.md).  
  
4.  [Zuordnen von SAP ASE-Datenbankschemas in SQL Server / Azure SQL-Datenbank-Datenbankschemas](https://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Optional [erstellen Bewertungsberichte](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) Datenbankobjekte für die Konvertierung zu bewerten und die Konvertierungszeit zu schätzen.  
  
6.  [Konvertieren von SAP ASE-Datenbankschemas in SQL Server / Azure SQL-Datenbank-Schemas](https://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Laden von konvertierten Datenbankobjekten in SQL Server / Azure SQL-Datenbank](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Entweder ein Skript zu speichern, und führen Sie es in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank oder die Datenbankobjekte synchronisieren.  
  
8.  [Migrieren von Daten zu SQL Server / Azure SQL-Datenbank](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Aktualisieren Sie bei Bedarf Ihrer datenbankanwendungen.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Erste Schritte mit SSMA für SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
