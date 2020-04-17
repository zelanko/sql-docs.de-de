---
title: Was ist neu in clR Integration | Microsoft Docs
description: Microsoft SQL Server, der CLR hostet, wird als CLR-Integration bezeichnet. In diesem Artikel werden neue Funktionen in der CLR-Integration in SQL Server 2012 beschrieben.
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: d27bf0d925d3a98dda488fb85aff7446434cc8ad
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488089"
---
# <a name="clr-integration---what39s-new"></a>CLR-Integration - Was&#39;ist neu
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die folgenden Funktionen sind neue CLR-Integrationsfunktionen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]:  
  
-   In Version 4 der CLR fangen CLR-Datenbankobjekte nicht länger Ausnahmen aufgrund eines beschädigten Status ab. Diese Ausnahmen werden jetzt in der CLR-Integrationshostingebene abgefangen. Diese Ausnahmen können weiterhin von den CLR-Datenbankkomponenten abgefangen werden, indem ein Codeattribut ([\<legacyCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)) gesetzt wird. Diese Vorgehensweise wird jedoch nicht empfohlen, da die Ergebnisse nicht zuverlässig sind, wenn eine Ausnahme aufgrund eines beschädigten Status auftritt.  
  
-   Wegen der strengen Sicherheitsanforderungen von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] verwenden CLR-Datenbankkomponenten weiterhin das Codezugriffssicherheitsmodell, das in CLR, Version 2.0, definiert wurde.  
  
-   In CLR Version 4 generiert ein Formatfehler in einem **System.TimeSpan-Wert** einen **System.FormatExceptions**. Vor Version 4 der CLR wurde ein Formatfehler in einem **System.TimeSpan-Wert** ignoriert. Datenbankanwendungen, die sich auf das Verhalten vor Version 4 der CLR verlassen, sollten mit einer Datenbankkompatibilitätsstufe (**ALTER DATABASE Compatibility Level**) von 100 oder niedriger ausgeführt werden. Weitere Informationen finden Sie unter [<TimeSpan_LegacyFormatMode> Element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Version 4 der CLR unterstützt Unicode 5.1. Sortiervorgänge, die Akzentzeichen und Symbole einschließen, werden verbessert. Wenn die Anwendung das Legacysortierverhalten benötigt, können Kompatibilitätsprobleme auftreten. Um die Legacysortierung zu aktivieren, muss die Datenbankkompatibilitätsstufe (**ALTER DATABASE Compatibility Level**) auf 100 oder niedriger festgelegt werden. Damit dies unterstützt wird, installiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] sort00001000.dll im .NET Framework 4-Verzeichnis (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Weitere Informationen finden Sie unter [ \<CompatSortNLSVersion> Element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Die folgenden Spalten wurden [zu sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md)hinzugefügt: **total_processor_time_ms**, **total_allocated_memory_kb**und **survived_memory_kb**.  
  
  
