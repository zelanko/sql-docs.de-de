---
description: sp_OAStop (Transact-SQL)
title: sp_OAStop (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAStop
- sp_OAStop_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAStop
ms.assetid: aa9eab66-c4f7-4ec7-9f0d-5d24d16da654
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d30bd1bfc143f18f67465b2d1ec71f7c4c97a9d2
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534918"
---
# <a name="sp_oastop-transact-sql"></a>sp_OAStop (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Beendet die serverweite Ausführungsumgebung für gespeicherte Prozeduren der OLE-Automatisierung.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OAStop      
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [Rückgabecodes und Fehlerinformationen der OLE-Automatisierung](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Hinweise  
 Eine einzige Ausführungsumgebung wird von allen Clients, die die gespeicherten Prozeduren der OLE-Automatisierung verwenden, gemeinsam genutzt. Wenn **sp_OAStop** durch einen Client aufgerufen wird, wird die freigegebene Ausführungsumgebung für alle Clients beendet. Nach dem Beenden der Ausführungsumgebung wird diese durch Aufrufen von **sp_OACreate** neu gestartet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder die EXECUTE-Berechtigung direkt für diese gespeicherte Prozedur. `Ole Automation Procedures` die Konfiguration muss **aktiviert** sein, um alle System Prozeduren für OLE-Automatisierung verwenden zu können.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die freigegebene Ausführungsumgebung der OLE-Automatisierung beendet.  
  
```  
EXEC sp_OAStop;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte OLE-Automatisierungs Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
