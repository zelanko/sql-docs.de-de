---
description: sp_check_for_sync_trigger (Transact-SQL)
title: sp_check_for_sync_trigger (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1e55fd24c9d4df46cb4703af31d2eda802a458ca
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486208"
---
# <a name="sp_check_for_sync_trigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Bestimmt, ob ein benutzerdefinierter Trigger oder eine benutzerdefinierte gespeicherte Prozedur im Kontext eines Replikationstriggers aufgerufen wird, der für sofort aktualisierbare Abonnements verwendet wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank oder auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>Argumente  
 [** @tabid =** ] '*tabid*'  
 Die Objekt-ID der Tabelle, die auf sofort aktualisierbare Trigger überprüft wird. *tabid* ist vom Datentyp **int** und hat keinen Standard.  
  
 [** @trigger_op =** ] '*trigger_output_parameters*' Ausgabe  
 Gibt an, ob der Ausgabeparameter den Typ von Trigger zurückgeben muss, mit dem er aufgerufen wird. *trigger_output_parameters* ist vom Typ **char (10)** . die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**ELine**|INSERT-Trigger|  
|**Upd**|UPDATE-Trigger|  
|**ENTF**|DELETE-Trigger|  
|NULL (Standard)||  
  
`[ @fonpublisher = ] fonpublisher` Gibt den Speicherort an, an dem die gespeicherte Prozedur ausgeführt wird. *fonpublisher* ist vom Typ **Bit**und hat den Standardwert 0. Bei 0 findet die Ausführung auf dem Abonnenten und bei 1 auf dem Verleger statt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 zeigt an, dass die gespeicherte Prozedur nicht im Kontext eines sofort aktualisierbaren Triggers aufgerufen wird. 1 gibt an, dass Sie im Kontext eines sofort aktualisierbaren Auslösers aufgerufen wird, und ist der Typ des in * \@ trigger_op*zurückgegebenen Auslösers.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_check_for_sync_trigger** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 **sp_check_for_sync_trigger** wird zum koordinieren zwischen Replikations-und benutzerdefinierten Triggern verwendet. Diese gespeicherte Prozedur bestimmt, ob sie im Kontext eines Replikationstriggers aufgerufen wird. Beispielsweise können Sie die Prozedur **sp_check_for_sync_trigger** im Text eines benutzerdefinierten Auslösers aufzurufen. Wenn **sp_check_for_sync_trigger** **0**zurückgibt, wird die Verarbeitung des benutzerdefinierten-Auslösers fortgesetzt. Wenn **sp_check_for_sync_trigger** **1**zurückgibt, wird der benutzerdefinierte-Wert beendet. So wird sichergestellt, dass der benutzerdefinierte Trigger nicht ausgelöst wird, wenn der Replikationstrigger die Tabelle aktualisiert.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird Code dargestellt, der in einem Trigger in der Abonnententabelle verwendet werden kann.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>Beispiel  
 Der Code kann auch einem-auslösertyp auf dem Verleger hinzugefügt werden. der Code ist ähnlich, aber der Aufrufen von **sp_check_for_sync_trigger** enthält einen zusätzlichen Parameter.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>Berechtigungen  
 **sp_check_for_sync_trigger** gespeicherte Prozedur kann von jedem Benutzer mit SELECT-Berechtigungen in der [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Systemsicht ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
