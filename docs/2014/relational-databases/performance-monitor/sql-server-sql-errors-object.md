---
title: SQL Server, SQL Errors-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 39124cefec0dafb921c13209adfb46e6658e1546
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814626"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, SQL-Fehler-Objekt
  Durch das Objekt **SQLServer:SQL Errors** in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Indikatoren zum Überwachen von **SQL-Fehlern**zur Verfügung gestellt.  
  
 In dieser Tabelle werden die Leistungsindikatoren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL-Fehler** beschrieben.  
  
|Leistungsindikatoren von SQL-Fehler bei SQL Server|Description|  
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
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
