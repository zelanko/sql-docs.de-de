---
title: CONNECTIONPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: a5cf9d02986587ed3e5234343306d6d73c7203a7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832242"
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Für eine beim Server eingehende Anforderung gibt diese Funktion Informationen über die Verbindungseigenschaften der eindeutigen Verbindung zurück, die die betreffende Anforderung unterstützt.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>Argumente  
*property*  
Die Eigenschaft der Verbindung. *property* kann einen der folgenden Werte aufweisen:
  
|value|Datentyp|BESCHREIBUNG|  
|---|---|---|
|net_transport|**nvarchar(40)**|Gibt das physische Transportprotokoll zurück, das von dieser Verbindung verwendet wird. Dieser Wert lässt keine NULL-Werte zu. Mögliche Rückgabewerte:<br /><br /> **HTTP**<br /> **Named Pipe**<br /> **Sitzungskonsistenz**<br /> **Shared Memory**<br /> **SSL**<br /> **TCP**<br /><br /> and<br /><br /> **VIA**<br /><br /> Hinweis: Es wird stets **Session** zurückgegeben, wenn für eine Verbindung sowohl „mehrere aktive Resultsets“ (MARS) als auch Verbindungs-Pooling aktiviert ist.|  
|protocol_type|**nvarchar(40)**|Gibt den Nutzlast-Protokolltyp zurück. Zurzeit wird zwischen TDS (TSQL) und SOAP unterschieden. Lässt NULL-Werte zu.|  
|auth_scheme|**nvarchar(40)**|Gibt das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierungsschema einer Verbindung zurück. Das Authentifizierungsschema ist entweder Windows-Authentifizierung (NTLM, KERBEROS, DIGEST, BASIC, NEGOTIATE) oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung. Lässt keine NULL-Werte zu.|  
|local_net_address|**varchar(48)**|Gibt die IP-Adresse auf dem Server zurück, die die Zieladresse dieser spezifischen Verbindung ist. Ist nur für Verbindungen verfügbar, die den TCP-Transportanbieter verwenden. Lässt NULL-Werte zu.|  
|local_tcp_port|**int**|Gibt den Server-TCP-Port zurück, der der Zielport dieser Verbindung ist, falls die Verbindung den TCP-Transport verwendet. Lässt NULL-Werte zu.|  
|client_net_address|**varchar(48)**|Fragt nach der Adresse des Clients, der versucht, die Verbindung mit diesem Server herzustellen. Lässt NULL-Werte zu.|  
|physical_net_transport|**nvarchar(40)**|Gibt das physische Transportprotokoll zurück, das von dieser Verbindung verwendet wird. Genau, wenn für eine Verbindung Multiple Active Result Sets (MARS) aktiviert sind.|  
|\<beliebige andere Zeichenfolge>||Gibt NULL für ungültige Eingaben zurück.|  
  
## <a name="remarks"></a>Bemerkungen  
**local_net_address** und **local_tcp_port** geben in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] NULL zurück.
  
Die zurückgegebenen Werte stimmen mit den Optionen überein, die für die entsprechenden Spalten in der dynamischen Verwaltungssicht [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md) angezeigt werden. Beispiel:
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>Weitere Informationen
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
