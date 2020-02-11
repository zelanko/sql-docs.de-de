---
title: sp_dbmmonitordropalert (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitordropalert_TSQL
- sp_dbmmonitordropalert
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitordropalert
ms.assetid: fe4a134b-25bf-464e-a5c4-358de215b65a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4776e043505c787e74c9cecf766325d189c4f702
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108126"
---
# <a name="sp_dbmmonitordropalert-transact-sql"></a>sp_dbmmonitordropalert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht die Warnung für eine angegebene Leistungsmetrik durch Festlegen des Schwellenwertes auf NULL.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dbmmonitordropalert database_name   
    [ , alert_id ]   
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Gibt die Datenbank an, für die der angegebene Schwellenwert für Warnung gelöscht werden soll.  
  
 *alert_id*  
 Ein ganzzahliger Wert, der die zu löschende Warnung identifiziert. Wird das Argument nicht angegeben, werden alle Warnungen für die Datenbank gelöscht. Geben Sie einen der folgenden Werte an, um die Warnung für eine bestimmte Leistungsmetrik zu löschen:  
  
|value|Leistungsmetrik|Schwellenwert für Warnung|  
|-----------|------------------------|-----------------------|  
|1|Älteste, nicht gesendete Transaktion|Gibt die Menge an Transaktionen (in Anzahl Minuten) an, die sich in der Sendewarteschlange ansammeln dürfen, bevor auf der Prinzipalserverinstanz eine Warnung generiert wird. Diese Warnung bietet die Möglichkeit, die Wahrscheinlichkeit eines Datenverlusts im Hinblick auf die Zeit zu messen. Sie ist besonders relevant für den Modus für hohe Leistung. Die Warnung ist aber auch für den Modus für hohe Sicherheit relevant, wenn die Spiegelung angehalten oder unterbrochen wird, weil die Verbindung zwischen den Partnern getrennt wurde.|  
|2|Nicht gesendetes Protokoll|Gibt an, bei welcher Menge (in KB) an nicht gesendeten Protokolldaten eine Warnung auf der Prinzipalserverinstanz generiert wird. Diese Warnung bietet die Möglichkeit, die Wahrscheinlichkeit eines Datenverlusts in KB zu messen. Sie ist besonders relevant für den Modus für hohe Leistung. Die Warnung ist aber auch für den Modus für hohe Sicherheit relevant, wenn die Spiegelung angehalten oder unterbrochen wird, weil die Verbindung zwischen den Partnern getrennt wurde.|  
|3|Nicht wiederhergestelltes Protokoll|Gibt an, bei welcher Menge (in KB) an nicht wiederhergestellten Protokolldaten eine Warnung auf der Spiegelserverinstanz generiert wird. Diese Warnung ermöglicht die Messung der Failoverzeit. Die *Failoverzeit* besteht hauptsächlich aus der Zeit, die der frühere Spiegel Server benötigt, um ein Roll Forward für alle in der Wiederholungs Warteschlange verbleibenden Protokolle sowie eine kurze zusätzliche Zeit auszuführen.|  
|4|Spiegelungscommitaufwand|Gibt die durchschnittliche Verzögerung (in Anzahl der Millisekunden) pro Transaktion an, die toleriert wird, bevor auf dem Prinzipalserver eine Warnung generiert wird. Hierbei handelt es sich um die Verzögerung, die entsteht, während die Prinzipalserverinstanz darauf wartet, dass die Spiegelserverinstanz den Transaktionsprotokolldatensatz in die Wiederholungswarteschlange schreibt. Dieser Wert ist nur im Modus für hohe Sicherheit relevant.|  
|5|Aufbewahrungszeitraum|Metadaten, die steuern, wie lange Zeilen in der Datenbankspiegelungs-Statustabelle beibehalten werden.|  
  
> [!NOTE]  
>  Diese Prozedur löscht Warnungs Schwellenwerte, unabhängig davon, ob Sie mit **sp_dbmmonitorchangealert** oder Datenbankspiegelungs-Monitor angegeben wurden.  
  
 Informationen zu den Ereignis-IDs, die den Warnungen entsprechen, finden Sie unter [Verwenden von Warnungs Schwellenwerten und Warnungen für Spiegelungsleistungsmetriken &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Einstellung für die Beibehaltungsdauer der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank gelöscht.  
  
```  
EXEC sp_dbmmonitordropalert AdventureWorks2012, 5;  
```  
  
 Im folgenden Beispiel werden alle Schwellenwerte für Warnungen und die Beibehaltungsdauer der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank gelöscht.  
  
```  
EXEC sp_dbmmonitordropalert AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Daten Bank Spiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)  
  
  
