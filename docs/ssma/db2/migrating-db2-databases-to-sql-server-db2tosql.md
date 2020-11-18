---
title: Migrieren von DB2-Datenbanken zu SQL Server (DB2ToSQL) | Microsoft-Dokumentation
description: Verwenden Sie diesen empfohlenen Vorgang zum Migrieren von DB2-Datenbanken zu SQL Server oder Azure SQL-Datenbank mithilfe von SQL Server Migration Assistant (SSMA).
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: e31d4b1d31cb186276d8424f8c49450cb4ce9406
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869528"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Migrieren von DB2-Datenbanken zu SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für DB2 ist eine umfassende Umgebung, die Sie bei der schnellen Migration von DB2-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank unterstützt. Mithilfe von SSMA für DB2 können Sie Datenbankobjekte und-Daten überprüfen, Datenbanken für die Migration bewerten, Datenbankobjekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank migrieren und dann Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank migrieren. Beachten Sie, dass Sie keine sys-und System DB2-Schemas migrieren können.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Verwenden Sie den folgenden Prozess, um Objekte und Daten aus DB2-Datenbanken zu oder Azure SQL-Datenbank erfolgreich zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  [Neues SSMA-Projekt](./new-project-db2tosql.md).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die Optionen für die Projekt Konvertierung, die Migration und die Typzuordnung festlegen. Weitere Informationen zu Projekteinstellungen finden Sie unter [Project Settings &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) und Related Abschnitts. Weitere Informationen zum Anpassen von Datentyp Zuordnungen finden Sie unterzuordnen von [DB2-und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  Stellen [Sie eine Verbindung zur DB2-Datenbank](./connecting-to-db2-database-db2tosql.md)her.  
  
3.  [Verbindung mit SQL Server](./connecting-to-sql-server-db2tosql.md)wird hergestellt.  
  
4.  Ordnen [Sie DB2-Schemas SQL Server Schemas zu](./mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
5.  Sie können auch [Bewertungsberichte](./assessment-report-db2tosql.md) zum Bewerten von Datenbankobjekten für die Konvertierung und zum Schätzen der Konvertierungs Zeit auswerten.  
  
6.  [Konvertieren von DB2-Schemas](./converting-db2-schemas-db2tosql.md).  
  
7.  [Laden Sie die konvertierten Datenbankobjekte in SQL Server](./loading-converted-database-objects-into-sql-server-db2tosql.md).  
  
    Wählen Sie dazu eine der folgenden Methoden:  
  
    -   Speichern Sie ein Skript, und führen Sie es in aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
8.  [Migrieren von DB2-Daten in SQL Server](./migrating-db2-data-into-sql-server-db2tosql.md).  
  
9. Aktualisieren Sie ggf. Datenbankanwendungen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Informationen zu den ersten Schritten mit SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
