---
title: Was&#39;Neues in CLR-Integration | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
caps.latest.revision: 7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 55cb6537db540fb5d916b72cb1b469dc3846f419
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356212"
---
# <a name="clr-integration---what39s-new"></a>CLR-Integration: was&#39;neues
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die folgenden Funktionen sind neue CLR-Integrationsfunktionen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]:  
  
-   In Version 4 der CLR fangen CLR-Datenbankobjekte nicht länger Ausnahmen aufgrund eines beschädigten Status ab. Diese Ausnahmen werden jetzt in der CLR-Integrationshostingebene abgefangen. Diese Ausnahmen können immer noch durch die CLR-Datenbankkomponenten abgefangen werden, durch Festlegen einer Code-Attribut ([\<LegacyCorruptedStateExceptionsPolicy >-Element](http://go.microsoft.com/fwlink/?LinkId=204954)). Diese Vorgehensweise wird jedoch nicht empfohlen, da die Ergebnisse nicht zuverlässig sind, wenn eine Ausnahme aufgrund eines beschädigten Status auftritt.  
  
-   Wegen der strengen Sicherheitsanforderungen von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] verwenden CLR-Datenbankkomponenten weiterhin das Codezugriffssicherheitsmodell, das in CLR, Version 2.0, definiert wurde.  
  
-   In CLR, Version 4, ein Formatfehler in einem **System.TimeSpan** Wert generiert eine **System.FormatExceptions**. Vor Version 4 der CLR ein Formatfehler in einem **System.TimeSpan** Wert wurde ignoriert. Datenbankanwendungen, die auf das Verhalten vor Version 4 der CLR verlassen sollten mit der Datenbank-Kompatibilitätsgrad ausgeführt (**ALTER DATABASE Compatibility Level**) von 100 oder niedriger. Weitere Informationen finden Sie unter [< TimeSpan_LegacyFormatMode >-Element](http://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Version 4 der CLR unterstützt Unicode 5.1. Sortiervorgänge, die Akzentzeichen und Symbole einschließen, werden verbessert. Wenn die Anwendung das Legacysortierverhalten benötigt, können Kompatibilitätsprobleme auftreten. So aktivieren Sie die legacysortierung, Kompatibilitätsgrad der Datenbank (**ALTER DATABASE Compatibility Level**) muss auf 100 oder niedriger festgelegt werden. Damit dies unterstützt wird, installiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] sort00001000.dll im .NET Framework 4-Verzeichnis (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Weitere Informationen finden Sie unter [ \<CompatSortNLSVersion >-Element](http://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Die folgenden Spalten hinzugefügt wurden [dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **Total_processor_time_ms**, **Total_allocated_memory_kb**, und **Survived_ Memory_kb**.  
  
  
