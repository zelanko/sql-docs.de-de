---
title: sp_browsemergesnapshotfolder (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsemergesnapshotfolder
- sp_browsemergesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsemergesnapshotfolder
ms.assetid: e248642f-5fea-4ed7-be1a-36ff75abcfde
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c930347c18dc257b5a6c51d2b013d2429b269fe
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715986"
---
# <a name="sp_browsemergesnapshotfolder-transact-sql"></a>sp_browsemergesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt den vollständigen Pfad für die aktuellste Momentaufnahme zurück, der für eine Mergeveröffentlichung generiert wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_browsemergesnapshotfolder [@publication= ] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar (2000)**|Vollständiger Pfad zum Momentaufnahmeverzeichnis.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_browsemergesnapshotfolder** wird bei der Mergereplikation verwendet.  
  
 Wenn die Veröffentlichung so eingerichtet ist, dass sie Momentaufnahmedateien sowohl im Arbeitsverzeichnis als auch im Momentaufnahmeordner des Verlegers generiert, dann enthält das Resultset zwei Zeilen: Die erste Zeile enthält den Momentaufnahmeordner der Veröffentlichung, und die zweite Zeile enthält das Arbeitsverzeichnis des Verlegers.  
  
 **sp_browsemergesnapshotfolder** ist hilfreich, um das Verzeichnis zu ermitteln, in dem die Momentaufnahme Dateien der Momentaufnahmen generiert werden. Dieser Ordner/Pfad und sein Inhalt können dann auf Wechselmedien kopiert werden. Die Momentaufnahme kann dann dazu verwendet werden, ein Abonnement von einer alternativen Momentaufnahmeposition zu synchronisieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_browsemergesnapshotfolder**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
