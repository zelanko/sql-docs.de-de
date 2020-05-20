---
title: sp_syscollector_upload_collection_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_upload_collection_set
- sp_syscollector_upload_collection_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_upload_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9302728bf93a53ce333dce5a38bfa7e046d38fe0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824237"
---
# <a name="sp_syscollector_upload_collection_set-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Startet das Hochladen von Sammlungssatzdaten, wenn der Sammlungssatz aktiviert ist.  
  
> [!IMPORTANT]  
>  Diese gespeicherte Prozedur kann nur für Sammlungssätze verwendet werden, die für die Datensammlung im Modus mit Zwischenspeicherung und den Upload konfiguriert werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_upload_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @collection_set_id = ] collection_set_id`Der eindeutige lokale Bezeichner für den Sammlungs Satz. *collection_set_id* ist vom *Datentyp* **int** und muss über einen Wert verfügen, wenn Name NULL ist.  
  
`[ @name = ] 'name'`Der Name des Sammlungs Satzes. *Name ist vom Datentyp* **vom Datentyp sysname** und muss über einen Wert verfügen, wenn *collection_set_id* NULL ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Entweder *collection_set_id* oder *Name* muss einen Wert haben. Beide dürfen nicht NULL sein.  
  
 Diese Prozedur kann zum Starten eines bedarfsgesteuerten Hochladens für einen ausgeführten Sammlungssatz verwendet werden. Sie kann nur für Sammlungssätze verwendet werden, die für die Datensammlung im Modus mit Zwischenspeicherung und den Upload konfiguriert werden. So kann ein Benutzer Daten zur Analyse erhalten, ohne auf ein geplantes Hochladen warten zu müssen.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieses Vorgangs ist die Mitgliedschaft in der Daten Bank Rolle **dc_operator** (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="example"></a>Beispiel  
 Führt ein bedarfsgesteuertes Hochladen eines Sammlungssatzes mit dem Namen `Simple Collection Set` aus.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_upload_collection_set @name = 'Simple Collection Set' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
