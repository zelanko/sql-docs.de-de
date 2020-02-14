---
title: SQL Server, SQL Errors-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: b5f4b6a6d12f8f4eee929dfca59906fc418bfcd8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "67995663"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, SQL-Fehler-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Durch das Objekt **SQLServer:SQL Errors** in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Indikatoren zum Überwachen von **SQL-Fehlern**zur Verfügung gestellt.  
  
 Diese Tabelle enthält eine Beschreibung der **SQL Errors**-Zähler in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Leistungsindikatoren von SQL-Fehler bei SQL Server|Beschreibung|  
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
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
