---
title: sp_helpmergealternatepublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: af9ccd6d8c5a97166fcaf45342de3efbbe5b6290
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82818215"
---
# <a name="sp_helpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste aller Server zurück, die als alternative Verleger für Mergeveröffentlichungen aktiviert sind. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des alternativen Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|Name des alternativen Verlegers.|  
|**alternate_publisher_db**|**sysname**|Der Name der Veröffentlichungs Datenbank.|  
|**alternate_publication**|**sysname**|Name der Veröffentlichung.|  
|**alternate_distributor**|**sysname**|Der Name des Verteilers.|  
|**friendly_name**|**nvarchar(255)**|Die Beschreibung des alternativen Verlegers.|  
|**wodurch**|**bit**|Gibt an, ob der Server ein alternativer Verleger ist. der Wert **1** gibt an, dass der Verleger als alternativer Verleger aktiviert ist. der Wert **0** gibt an, dass er nicht aktiviert ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpmergealternatepublisher** wird bei der Mergereplikation verwendet.  
  
 Während jeder Mergesitzung fragt das System sowohl den Verleger als auch den Abonnenten nach ihren Listen alternativer Verleger ab. Der Mergeprozess fügt der Liste der alternativen Verleger Einträge hinzu bzw. entfernt Einträge aus der Liste, sodass die Liste der alternativen Verleger auf dem Abonnenten mit derjenigen auf dem Verleger übereinstimmt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der Veröffentlichungs Zugriffsliste für die Veröffentlichung können **sp_helpmergealternatepublisher**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
