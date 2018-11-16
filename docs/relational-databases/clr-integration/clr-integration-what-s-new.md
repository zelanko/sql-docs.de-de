---
title: Was&#39;Neues in CLR-Integration | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 09cce119f74bcdf858887078c0a78046dedde7d2
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677979"
---
# <a name="clr-integration---what39s-new"></a>CLR-Integration: was&#39;neues
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die folgenden Funktionen sind neue CLR-Integrationsfunktionen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]:  
  
-   In Version 4 der CLR fangen CLR-Datenbankobjekte nicht länger Ausnahmen aufgrund eines beschädigten Status ab. Diese Ausnahmen werden jetzt in der CLR-Integrationshostingebene abgefangen. Diese Ausnahmen können immer noch durch die CLR-Datenbankkomponenten abgefangen werden, durch Festlegen einer Code-Attribut ([\<LegacyCorruptedStateExceptionsPolicy >-Element](https://go.microsoft.com/fwlink/?LinkId=204954)). Diese Vorgehensweise wird jedoch nicht empfohlen, da die Ergebnisse nicht zuverlässig sind, wenn eine Ausnahme aufgrund eines beschädigten Status auftritt.  
  
-   Wegen der strengen Sicherheitsanforderungen von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] verwenden CLR-Datenbankkomponenten weiterhin das Codezugriffssicherheitsmodell, das in CLR, Version 2.0, definiert wurde.  
  
-   In CLR, Version 4, ein Formatfehler in einem **System.TimeSpan** Wert generiert eine **System.FormatExceptions**. Vor Version 4 der CLR ein Formatfehler in einem **System.TimeSpan** Wert wurde ignoriert. Datenbankanwendungen, die auf das Verhalten vor Version 4 der CLR verlassen sollten mit der Datenbank-Kompatibilitätsgrad ausgeführt (**ALTER DATABASE Compatibility Level**) von 100 oder niedriger. Weitere Informationen finden Sie unter [< TimeSpan_LegacyFormatMode >-Element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Version 4 der CLR unterstützt Unicode 5.1. Sortiervorgänge, die Akzentzeichen und Symbole einschließen, werden verbessert. Wenn die Anwendung das Legacysortierverhalten benötigt, können Kompatibilitätsprobleme auftreten. So aktivieren Sie die legacysortierung, Kompatibilitätsgrad der Datenbank (**ALTER DATABASE Compatibility Level**) muss auf 100 oder niedriger festgelegt werden. Damit dies unterstützt wird, installiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] sort00001000.dll im .NET Framework 4-Verzeichnis (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Weitere Informationen finden Sie unter [ \<CompatSortNLSVersion >-Element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Die folgenden Spalten hinzugefügt wurden [dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **Total_processor_time_ms**, **Total_allocated_memory_kb**, und **Survived_ Memory_kb**.  
  
  
