---
title: Migrieren von DB2-Datenbanken zu SQL Server (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 79cc961148add0bf2096a716b669199360a565b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68084653"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Migrieren von DB2-Datenbanken zu SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für DB2 ist eine umfassende Umgebung, die Sie bei der schnellen Migration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2-Datenbanken zu oder Azure SQL-Datenbank unterstützt. Mithilfe von SSMA für DB2 können Sie Datenbankobjekte und-Daten überprüfen, Datenbanken für die Migration bewerten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankobjekte zu oder Azure SQL-Datenbank migrieren und dann Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank migrieren. Beachten Sie, dass Sie keine sys-und System DB2-Schemas migrieren können.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Verwenden Sie den folgenden Prozess, um Objekte und Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus DB2-Datenbanken zu oder Azure SQL-Datenbank erfolgreich zu migrieren:  
  
1.  [Neues SSMA-Projekt](https://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die Optionen für die Projekt Konvertierung, die Migration und die Typzuordnung festlegen. Weitere Informationen zu Projekteinstellungen finden Sie unter [Project Settings &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) und Related Abschnitts. Weitere Informationen zum Anpassen von Datentyp Zuordnungen finden Sie unterzuordnen von [DB2-und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  Stellen [Sie eine Verbindung zur DB2-Datenbank](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844)her.  
  
3.  [Verbindung mit SQL Server](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e)wird hergestellt.  
  
4.  Ordnen [Sie DB2-Schemas SQL Server Schemas zu](https://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a).  
  
5.  Sie können auch [Bewertungsberichte](https://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de) zum Bewerten von Datenbankobjekten für die Konvertierung und zum Schätzen der Konvertierungs Zeit auswerten.  
  
6.  [Konvertieren von DB2-Schemas](https://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0).  
  
7.  [Laden Sie die konvertierten Datenbankobjekte in SQL Server](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
    Wählen Sie dazu eine der folgenden Methoden:  
  
    -   Speichern Sie ein Skript, und führen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sie es in aus.  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
8.  [Migrieren von DB2-Daten in SQL Server](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
9. Aktualisieren Sie ggf. Datenbankanwendungen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Informationen zu den ersten Schritten mit SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
