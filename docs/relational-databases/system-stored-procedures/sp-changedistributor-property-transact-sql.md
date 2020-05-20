---
title: sp_changedistributor_property (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistributor_property_TSQL
- sp_changedistributor_property
helpviewer_keywords:
- sp_changedistributor_property
ms.assetid: 04f503a1-307c-4de0-bac6-e6e97d5b6940
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 55c7cd3e114da3d6a2bb318271717695bf768b7e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829607"
---
# <a name="sp_changedistributor_property-transact-sql"></a>sp_changedistributor_property (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert die Eigenschaften des Verteilers. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changedistributor_property [ [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @property = ] 'property'`Die-Eigenschaft für einen angegebenen Verteiler. *Property* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**heartbeat_interval**|Maximale Anzahl von Minuten, die ein Agent ohne Protokollierung einer Statusmeldung ausgeführt werden kann.|  
|NULL (Standard)|Alle verfügbaren *Eigenschafts* Werte werden gedruckt.|  
  
`[ @value = ] 'value'`Der Wert für die angegebene Verteiler Eigenschaft. der Wert ist vom Datentyp **varchar (255)** und hat den Standard *Wert* NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changedistributor_property** wird bei allen Replikations Typen verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/sp-changedistributor-pro_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_changedistributor_property**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern der Verteiler-und Verleger Eigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
