---
title: SQL Server, SQL Errors-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f36cd694756544a44df657d97fd84e1967167b55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63183006"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, SQL-Fehler-Objekt
  Durch das Objekt **SQLServer:SQL Errors** in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Indikatoren zum Überwachen von **SQL-Fehlern**zur Verfügung gestellt.  
  
 Diese Tabelle enthält eine Beschreibung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Errors **-Zähler in** .  
  
|Leistungsindikatoren von SQL-Fehler bei SQL Server|BESCHREIBUNG|  
|------------------------------------|-----------------|  
|**Fehler/Sekunde**|Anzahl der Fehler/Sekunde.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Element|Definition|  
|----------|----------------|  
|**_Total**|Informationen zu allen Fehlern.|  
|**DB Offline Errors**|Es werden schwere Fehler nachverfolgt, die dazu führen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Datenbank offline schaltet.|  
|**Info Errors**|Informationen, die sich auf Fehlermeldungen beziehen, die den Benutzern als Informationen zur Verfügung gestellt werden, verursachen jedoch keine Fehler.|  
|**Kill Connection Errors**|Es werden schwere Fehler nachverfolgt, die dazu führen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die aktuelle Verbindung unterbricht.|  
|**User Errors**|Informationen zu Benutzerfehlern.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
