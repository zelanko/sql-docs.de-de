---
title: Sp_publisherproperty (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c4ba291619ae756fa9803606eda4427a155ae39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896494"
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt oder ändert Sie Verlegereigenschaften für nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber. Diese gespeicherte Prozedur wird auf dem Verteiler ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publisher** = ] **'***publisher***'**  
 Der Name des heterogenen Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@propertyname** =] **"***Propertyname***"**  
 Der Name der Eigenschaft, die festgelegt wird. *PropertyName* ist **Sysname**, und kann einen der folgenden Werte.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**xactsetbatching**|Gibt an, ob Transaktionen auf dem Verleger zur weiteren Verarbeitung gruppiert werden, in Mengen, die im Hinblick auf Transaktionen konsistent sind und als Xactsets bezeichnet werden. Der Wert **aktiviert** bedeutet, dass Xactsets erstellt werden können, dies ist die Standardeinstellung. Der Wert **deaktiviert** bedeutet, dass vorhandene Xactsets, jedoch keine neuen xactsets verarbeitet werden erstellt werden.|  
|**xactsetjob**|Gibt an, ob der Xactset-Auftrag zum Erstellen von Xactsets aktiviert ist. Der Wert **aktiviert** bedeutet, dass der Xactset-Auftrag regelmäßig ausgeführt wird, um Xactsets auf dem Verleger zu erstellen. Der Wert **deaktiviert** bedeutet, dass die Xactsets nur vom Protokolllese-Agent erstellt werden, wenn sie Änderungen vom Verleger abruft.|  
|**xactsetjobinterval**|Intervall zwischen den Ausführungsvorgängen des Xactset-Auftrags in Minuten.|  
  
 Wenn *Propertyname* fehlt alle festlegbare Eigenschaften zurückgegeben werden.  
  
 [ **@propertyvalue** =] **"***Propertyvalue***"**  
 Der neue Wert für die Eigenschafteneinstellung. *PropertyValue* ist **Sysname**, hat den Standardwert NULL. Wenn *Propertyvalue* weggelassen wird, wird die aktuelle Einstellung für die Eigenschaft zurückgegeben wird.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|Gibt die folgenden Veröffentlichungseigenschaften zurück, die festgelegt werden können:<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**PropertyValue**|**sysname**|Ist die aktuelle Einstellung für die Eigenschaft in der **Propertyname** Spalte.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_publisherproperty** wird verwendet, bei der Transaktionsreplikation für nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber.  
  
 Wenn nur *Verleger* angegeben ist, wird das Resultset enthält die aktuellen Einstellungen für alle Eigenschaften, die festgelegt werden können.  
  
 Wenn *Propertyname* angegeben ist, wird nur die benannte Eigenschaft, die im Resultset angezeigt wird.  
  
 Wenn alle Parameter angegeben werden, wird die Eigenschaft geändert und kein Resultset zurückgegeben.  
  
 Beim Ändern der **Xactsetjobinterval** -Eigenschaft für einen gerade ausgeführten Auftrag verwenden, müssen Sie neu starten des Auftrags für das neue Intervall wirksam wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle auf dem Verteiler **Sp_publisherproperty**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren des Transaktionssatz-Auftrags für einen Oracle-Verleger &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
