---
title: Was&#39;Neues in CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 45e4f0578d06eeafc545bea2b6374a37b8ef7cbc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874064"
---
# <a name="what39s-new-in-clr-integration"></a>Was&#39;Neues in CLR-Integration
  Die folgenden Funktionen sind neue CLR-Integrationsfunktionen in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   In Version 4 der CLR fangen CLR-Datenbankobjekte nicht länger Ausnahmen aufgrund eines beschädigten Status ab. Diese Ausnahmen werden jetzt in der CLR-Integrationshostingebene abgefangen. Diese Ausnahmen können immer noch durch die CLR-Datenbankkomponenten abgefangen werden, durch Festlegen einer Code-Attribut ([\<LegacyCorruptedStateExceptionsPolicy >-Element](https://go.microsoft.com/fwlink/?LinkId=204954)). Diese Vorgehensweise wird jedoch nicht empfohlen, da die Ergebnisse nicht zuverlässig sind, wenn eine Ausnahme aufgrund eines beschädigten Status auftritt.  
  
-   Wegen der strengen Sicherheitsanforderungen von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verwenden CLR-Datenbankkomponenten weiterhin das Codezugriffssicherheitsmodell, das in CLR, Version 2.0, definiert wurde.  
  
-   In CLR Version 4 generiert ein Formatfehler in einem `System.TimeSpan`-Wert eine `System.FormatExceptions`. Vor Version 4 der CLR wurde ein Formatfehler in einem `System.TimeSpan`-Wert ignoriert. Datenbankanwendungen, die das Verhalten vor Version 4 der CLR benötigen, sollten mit einem Datenbank-Kompatibilitätsgrad (`ALTER DATABASE Compatibility Level`) von 100 oder niedriger ausgeführt werden. Weitere Informationen finden Sie unter [< TimeSpan_LegacyFormatMode >-Element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Version 4 der CLR unterstützt Unicode 5.1. Sortiervorgänge, die Akzentzeichen und Symbole einschließen, werden verbessert. Wenn die Anwendung das Legacysortierverhalten benötigt, können Kompatibilitätsprobleme auftreten. Um die Legacysortierung zu aktivieren, muss der Datenbank-Kompatibilitätsgrad (`ALTER DATABASE Compatibility Level`) auf 100 oder niedriger festgelegt werden. Damit dies unterstützt wird, installiert [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] sort00001000.dll im .NET Framework 4-Verzeichnis (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Weitere Informationen finden Sie unter [ \<CompatSortNLSVersion >-Element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Die folgenden Spalten hinzugefügt wurden [dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`, `total_allocated_memory_kb`, und `survived_memory_kb`.  
  
  
