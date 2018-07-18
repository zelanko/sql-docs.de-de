---
title: Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a021ac1cfc442943b15ade737c54d0b9e227ef03
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982212"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Migrieren von SAP ASE-Datenbanken zu SQL Server – Azure SQL-Datenbank (SybaseToSQL)
SQL Server Migration Assistant (SSMA) für SAP Adaptive Server Enterprise (ASE) ist eine umfassende Umgebung, die Ihnen die schnelle Migration von SAP ASE-Datenbanken, um die hilft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL-Datenbank. SSMA für SAP ASE verwenden, Sie können überprüfen, Datenbankobjekte und Daten, Datenbanken für die Migration zu bewerten, migrieren Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL-Datenbank und migrieren Sie dann die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL-Datenbank.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Für eine erfolgreiche Migration von Objekten und Daten aus SAP ASE-Datenbanken, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL-Datenbank das folgende Verfahren verwenden:  
  
1.  [Erstellen Sie ein neues SSMA-Projekt](http://msdn.microsoft.com/11091d95-c488-48c3-891a-743cac94ac93).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die projektkonvertierung, Migration und Zuordnungsoptionen Typ festlegen. Weitere Informationen zu projekteinstellungen finden Sie unter [Setting Project Options Projektoptionen &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Informationen zum Anpassen der datentypzuordnungen finden Sie unter [Mapping Sybase ASE und SQL Server-Datentypen &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Verbinden mit einem der SAP ASE-Datenbankserver](http://msdn.microsoft.com/a45a2330-9175-4c9e-af38-ef920e350614).  
  
3.  [Herstellen einer Verbindung mit einer Instanz von SQL Server](http://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) oder [Herstellen einer Verbindung mit einer Instanz von Azure SQL-Datenbank](http://msdn.microsoft.com/9e77e4b0-40c0-455c-8431-ca5d43849aa7).  
  
4.  [Zuordnen von SAP ASE-Datenbankschemas in SQL Server / Azure SQL-Datenbank-Datenbankschemas](http://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Optional [erstellen Bewertungsberichte](http://msdn.microsoft.com/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) Datenbankobjekte für die Konvertierung zu bewerten und die Konvertierungszeit zu schätzen.  
  
6.  [Konvertieren von SAP ASE-Datenbankschemas in SQL Server / Azure SQL-Datenbank-Schemas](http://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Laden von konvertierten Datenbankobjekten in SQL Server / Azure SQL-Datenbank](http://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Entweder ein Skript zu speichern, und führen Sie es in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL-Datenbank oder die Datenbankobjekte synchronisieren.  
  
8.  [Migrieren von Daten zu SQL Server / Azure SQL-Datenbank](http://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Aktualisieren Sie bei Bedarf Ihrer datenbankanwendungen.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Erste Schritte mit SSMA für SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
