---
title: Was&#39;Neues in CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
caps.latest.revision: 6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 47566d2f3557202370a1b6be25a759f9cea3af17
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352502"
---
# <a name="what39s-new-in-clr-integration"></a>Was&#39;Neues in CLR-Integration
  Die folgenden Funktionen sind neue CLR-Integrationsfunktionen in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   In Version 4 der CLR fangen CLR-Datenbankobjekte nicht länger Ausnahmen aufgrund eines beschädigten Status ab. Diese Ausnahmen werden jetzt in der CLR-Integrationshostingebene abgefangen. Diese Ausnahmen können immer noch durch die CLR-Datenbankkomponenten abgefangen werden, durch Festlegen einer Code-Attribut ([\<LegacyCorruptedStateExceptionsPolicy >-Element](http://go.microsoft.com/fwlink/?LinkId=204954)). Diese Vorgehensweise wird jedoch nicht empfohlen, da die Ergebnisse nicht zuverlässig sind, wenn eine Ausnahme aufgrund eines beschädigten Status auftritt.  
  
-   Wegen der strengen Sicherheitsanforderungen von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verwenden CLR-Datenbankkomponenten weiterhin das Codezugriffssicherheitsmodell, das in CLR, Version 2.0, definiert wurde.  
  
-   In CLR Version 4 generiert ein Formatfehler in einem `System.TimeSpan`-Wert eine `System.FormatExceptions`. Vor Version 4 der CLR wurde ein Formatfehler in einem `System.TimeSpan`-Wert ignoriert. Datenbankanwendungen, die das Verhalten vor Version 4 der CLR benötigen, sollten mit einem Datenbank-Kompatibilitätsgrad (`ALTER DATABASE Compatibility Level`) von 100 oder niedriger ausgeführt werden. Weitere Informationen finden Sie unter [< TimeSpan_LegacyFormatMode >-Element](http://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Version 4 der CLR unterstützt Unicode 5.1. Sortiervorgänge, die Akzentzeichen und Symbole einschließen, werden verbessert. Wenn die Anwendung das Legacysortierverhalten benötigt, können Kompatibilitätsprobleme auftreten. Um die Legacysortierung zu aktivieren, muss der Datenbank-Kompatibilitätsgrad (`ALTER DATABASE Compatibility Level`) auf 100 oder niedriger festgelegt werden. Damit dies unterstützt wird, installiert [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] sort00001000.dll im .NET Framework 4-Verzeichnis (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Weitere Informationen finden Sie unter [ \<CompatSortNLSVersion >-Element](http://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Die folgenden Spalten hinzugefügt wurden [dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`, `total_allocated_memory_kb`, und `survived_memory_kb`.  
  
  
