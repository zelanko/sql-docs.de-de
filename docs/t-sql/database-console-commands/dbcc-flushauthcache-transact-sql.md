---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: e313fac1b1a3db6c9a0caa8eb0434dff1ab22411
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618474"
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Leert den Cache für die Datenbankauthentifizierung mit Informationen zu Anmeldungen und Firewallregeln für die aktuelle Benutzerdatenbank in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Diese Anweisung gilt nicht für logische Masterdatenbanken, da die Masterdatenbank den physischen Speicher enthält, der für Informationen zu Anmeldungen und Firewallregeln bestimmt ist. Für den Benutzer, der die Anweisung ausführt, und andere zum aktuellen Zeitpunkt verbundene Benutzer wird weiterhin keine Verbindung hergestellt. (DBCC FLUSHAUTHCACHE wird derzeit für [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] nicht unterstützt.)
 
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
Keine.
  
## <a name="remarks"></a>Remarks  
Der Authentifizierungscache erstellt eine Kopie von Anmeldungen und Serverfirewallregeln, die in der Masterdatenbank gespeichert sind, und überträgt diese in den Arbeitsspeicher der Benutzerdatenbank.  Da Informationen zu Benutzern eigenständiger Datenbanken bereits in der Benutzerdatenbank gespeichert sind, werden diese Benutzer nicht im Authentifizierungscache gespeichert.
Ständig aktive Verbindungen mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] erfordern alle 10 Stunden eine erneute Authentifizierung, die von [!INCLUDE[ssDE](../../includes/ssde-md.md)] durchgeführt. Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] versucht, eine erneute Authentifizierung mit dem ursprünglich übermittelten Kennwort durchzuführen. Dabei ist keine Eingabe des Benutzers erforderlich. Aus Leistungsgründen wird die Verbindung nicht erneut authentifiziert, wenn ein Kennwort in der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] zurückgesetzt wird. Dies ist auch nicht der Fall, wenn die Verbindung aufgrund von Verbindungspooling zurückgesetzt wird. Dies unterscheidet sich von dem Verhalten eines lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn das Kennwort nach der ersten Authentifizierung der Verbindung geändert wurde, muss diese Verbindung beendet und eine neue unter Verwendung des neuen Kennworts hergestellt werden. Ein Benutzer mit der KILL DATABASE CONNECTION-Berechtigung kann eine Verbindung mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] explizit beenden, wenn er den Befehl [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md) verwendet.
  
## <a name="permissions"></a>Berechtigungen  
Erfordert das [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Administratorkonto.
  
## <a name="example"></a>Beispiel  
Die folgende Anweisung entfernt den Authentifizierungscache für die aktuelle Datenbank.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
