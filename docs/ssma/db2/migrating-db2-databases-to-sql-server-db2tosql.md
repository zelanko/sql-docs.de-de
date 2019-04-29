---
title: Migrieren von DB2-Datenbanken zu SQLServer (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8ee6e9cca2e16a180f869df7bcec07bb7b09e390
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63071146"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Migrieren von DB2-Datenbanken zu SQLServer (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für DB2 ist eine umfassende Umgebung, die Sie schnell zu DB2-Datenbanken migrieren kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. SSMA für DB2 verwenden, Sie können überprüfen, Datenbankobjekte und Daten, Datenbanken für die Migration zu bewerten, migrieren Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, und migrieren Sie dann die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Beachten Sie, dass Sie nicht SYS und SYSTEM DB2 Schemas migrieren können.  
  
## <a name="recommended-migration-process"></a>Empfohlene Migrationsprozess  
Für eine erfolgreiche Migration von Objekten und Daten aus DB2-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, verwenden Sie den folgenden Prozess:  
  
1.  [Neues SSMA-Projekt](https://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die projektkonvertierung, Migration und Zuordnungsoptionen Typ festlegen. Weitere Informationen zu projekteinstellungen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;DB2ToSQL&#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) und Verwandte Abschnitte. Informationen dazu, wie Sie die replikationsdatentyp-Zuordnungen anpassen, finden Sie unter [Zuordnen von DB2- und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  [Verbinden mit der DB2-Datenbank](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
3.  [Herstellen einer Verbindung mit SQLServer](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
4.  [Zuordnen von DB2-Schemas zu SQL Server-Schemas](https://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a).  
  
5.  Optional [Bewertungsberichte](https://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de) Datenbankobjekte für die Konvertierung zu bewerten und die Konvertierungszeit zu schätzen.  
  
6.  [Konvertieren von DB2 Schemas](https://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0).  
  
7.  [Laden von konvertierten Datenbankobjekten in SQL Server](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
    Dies ist in einem der folgenden Arten möglich:  
  
    -   Speichern Sie ein Skript, und führen Sie es in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
8.  [Migrieren von DB2-Daten in SQLServer](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
9. Bei Bedarf datenbankanwendungen zu aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Erste Schritte mit SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
