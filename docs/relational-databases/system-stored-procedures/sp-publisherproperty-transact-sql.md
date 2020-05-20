---
title: sp_publisherproperty (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cf03396170972cf1e0c44a7a668e3651385579fc
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820376"
---
# <a name="sp_publisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Zeigt Verleger Eigenschaften für nicht--Verleger an oder ändert diese [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Diese gespeicherte Prozedur wird auf dem Verteiler ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des heterogenen Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @propertyname = ] 'propertyname'`Der Name der Eigenschaft, die festgelegt wird. *propertyName* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**xactsetbatching**|Gibt an, ob Transaktionen auf dem Verleger zur weiteren Verarbeitung gruppiert werden, in Mengen, die im Hinblick auf Transaktionen konsistent sind und als Xactsets bezeichnet werden. Der Wert **aktiviert** bedeutet, dass Xactsets erstellt werden können. Dies ist die Standardeinstellung. Der Wert **deaktiviert** bedeutet, dass vorhandene Xactsets verarbeitet werden, ohne dass neue Xactsets erstellt werden.|  
|**xactsetjob**|Gibt an, ob der Xactset-Auftrag zum Erstellen von Xactsets aktiviert ist. Der Wert **aktiviert** bedeutet, dass der Xactset-Auftrag regelmäßig ausgeführt wird, um Xactsets auf dem Verleger zu erstellen. Der Wert **deaktiviert** bedeutet, dass die Xactsets nur vom Protokolllese-Agent erstellt werden, wenn der Verleger nach Änderungen abfragt.|  
|**xactsetjobinterval**|Intervall zwischen den Ausführungsvorgängen des Xactset-Auftrags in Minuten.|  
  
 Wenn *propertyName* ausgelassen wird, werden alle festleg baren Eigenschaften zurückgegeben.  
  
 `[ @propertyvalue = ] 'propertyvalue'`  
 Der neue Wert für die Eigenschafteneinstellung. *PropertyValue* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *PropertyValue* weggelassen wird, wird die aktuelle Einstellung für die Eigenschaft zurückgegeben.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|Gibt die folgenden Veröffentlichungseigenschaften zurück, die festgelegt werden können:<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**PropertyValue**|**sysname**|Ist die aktuelle Einstellung für die Eigenschaft in der **propertyName** -Spalte.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_publisherproperty** wird bei der Transaktions Replikation für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger verwendet.  
  
 Wenn nur *Publisher* angegeben ist, enthält das Resultset die aktuellen Einstellungen für alle Eigenschaften, die festgelegt werden können.  
  
 Wenn *propertyName* angegeben ist, wird nur die benannte Eigenschaft im Resultset angezeigt.  
  
 Wenn alle Parameter angegeben werden, wird die Eigenschaft geändert und kein Resultset zurückgegeben.  
  
 Beim Ändern der **xactsetjobinterval** -Eigenschaft für einen laufenden Auftrag müssen Sie den Auftrag neu starten, damit das neue Intervall wirksam wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler können **sp_publisherproperty**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des Transaktions Satz-Auftrags für einen Oracle-Verleger &#40;Replikations Programmierung mit Transact-SQL&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
