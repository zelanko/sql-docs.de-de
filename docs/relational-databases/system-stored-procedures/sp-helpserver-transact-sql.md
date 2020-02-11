---
title: sp_helpserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpserver
- sp_helpserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpserver
ms.assetid: e8f42de7-c738-41c3-8bf5-dbd559dc7184
author: stevestein
ms.author: sstein
ms.openlocfilehash: 844e96d765f9ed06f88b140b906b78eb4ea16ea0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997436"
---
# <a name="sp_helpserver-transact-sql"></a>sp_helpserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu einem bestimmten Remoteserver oder Replikationsserver oder zu beiden Servertypen zurück. Stellt den Servernamen, den Netzwerknamen des Servers, den Replikationsstatus des Servers, die ID des Servers und den Sortierungsnamen bereit. Gibt außerdem Timeoutwerte für die Verbindungsherstellung zu sowie Abfragen auf Verbindungsservern an.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpserver [ [ @server = ] 'server' ]   
  [ , [ @optname = ] 'option' ]   
  [ , [ @show_topology = ] 'show_topology' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server = ] 'server'`Gibt den Server an, über welche Informationen berichtet werden. Wenn *Server* nicht angegeben ist, meldet alle Server in **Master. sys. Servers**. *Server* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @optname = ] 'option'`Die Option, die den Server beschreibt. die Option ist vom Datentyp **varchar (** 35 **)**. der Standardwert ist NULL. die folgenden Werte sind *möglich* .  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**kompatibel mit Sortierung**|Betrifft die Ausführung verteilter Abfragen für Verbindungsserver. Wenn diese Option auf "true" festgelegt wird,|  
|**Datenzugriff**|Aktiviert und deaktiviert den Zugriff auf verteilte Abfragen für Verbindungsserver.|  
|**dist**|Verteiler|  
|**dpub ist**|Der Remoteverleger zu diesem Verteiler.|  
|**Verzögerte Schemaüberprüfung**|Lässt die Schemaüberprüfung von Remotetabellen zu Beginn der Abfrage aus.|  
|**Kneipe**|Gebers.|  
|**rpc**|Aktiviert RPC (Remote Procedure Call, Remoteprozeduraufruf) von dem angegebenen Server.|  
|**RPC-Ausgabe**|Aktiviert RPC zu dem angegebenen Server.|  
|**nationale**|Abonnenten.|  
|**Anlage**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Remote Sortierung verwenden**|Verwendet die Sortierung einer Remotespalte anstelle der des lokalen Servers.|  
  
`[ @show_topology = ] 'show_topology'`Die Beziehung des angegebenen Servers zu anderen Servern. *show_topology* ist vom Datentyp **varchar (** 1 **)** und hat den Standardwert NULL. Wenn *show_topology* nicht gleich **t** ist oder NULL ist, gibt **sp_helpserver** die im Resultsets-Abschnitt aufgelisteten Spalten zurück. Wenn *show_topology* neben den in den Resultsets aufgelisteten Spalten gleich **t**ist, gibt **sp_helpserver** auch die **TopX** -und **topy** -Informationen zurück.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Servername.|  
|**network_name**|**sysname**|Netzwerkname des Servers.|  
|**Stands**|**varchar (** 70 **)**|Server Status.|  
|**Name**|**char (** 4 **)**|ID des Servers.|  
|**collation_name**|**sysname**|Die Sortierung des Servers.|  
|**connect_timeout**|**int**|Der Timeout Wert für die Verbindung mit dem Verbindungs Server.|  
|**query_timeout**|**int**|Timeoutwert für Abfragen auf einem Verbindungsserver.|  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Server kann mehr als einen Status haben.  
  
## <a name="permissions"></a>Berechtigungen  
 Es werden keine Berechtigungen geprüft.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-information-about-all-servers"></a>A. Anzeigen von Informationen zu allen Servern  
 Im folgenden Beispiel werden Informationen zu allen Servern angezeigt. Dazu wird `sp_helpserver` ohne Parameter verwendet.  
  
```  
USE master;  
GO  
EXEC sp_helpserver;  
```  
  
### <a name="b-displaying-information-about-a-specific-server"></a>B. Anzeigen von Informationen zu einem bestimmten Server  
 Im folgenden Beispiel werden alle Informationen zum Server `SEATTLE2` angezeigt.  
  
```  
USE master;  
GO  
EXEC sp_helpserver 'SEATTLE2';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_addsubscriber &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_changesubscriber &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
