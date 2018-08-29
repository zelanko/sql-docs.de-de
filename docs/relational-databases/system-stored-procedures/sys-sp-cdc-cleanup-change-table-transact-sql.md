---
title: sp_cdc_cleanup_change_table (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cdc_cleanup_change_table
- sp_cdc_cleanup_change_table_TSQL
- sys.sp_cdc_cleanup_change_table
- sys.sp_cdc_cleanup_change_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_cleanup_change_tables
- sp_cdc_cleanup_change_tables
ms.assetid: 02295794-397d-4445-a3e3-971b25e7068d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8dcfb1d487b3dd977b9837723c49e7fdf14b9ae5
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43035089"
---
# <a name="sysspcdccleanupchangetable-transact-sql"></a>sys.sp_cdc_cleanup_change_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt Zeilen aus der Änderungstabelle in der aktuellen Datenbank, die auf der Grundlage der angegebenen *Low_water_mark* Wert. Diese gespeicherte Prozedur wird für Benutzer bereitgestellt, die den Cleanupprozess für Änderungstabellen direkt verwalten möchten. Da diese Prozedur alle Consumer der Änderungstabellendaten betrifft, sollte sie mit Vorsicht eingesetzt werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_cleanup_change_table   
  [ @capture_instance = ] 'capture_instance',   
  [ @low_water_mark = ] low_water_mark ,  
  [ @threshold = ]'delete threshold'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @capture_instance =] '*Capture_instance*"  
 Der Name der Aufzeichnungsinstanz, die der Änderungstabelle zugeordnet ist. *Capture_instance* ist **Sysname**, hat keinen Standardwert und darf nicht NULL sein.  
  
 *Capture_instance* müssen den Namen einer Aufzeichnungsinstanz, die in der aktuellen Datenbank vorhanden ist.  
  
 [ @low_water_mark =] *Low_water_mark*  
 Wird von eine protokollfolgenummer (LSN), die als neue untergrenzenmarkierung für die zu verwendende der *Aufzeichnungsinstanz*. *Low_water_mark* ist **Binary(10)-Wert**, hat keinen Standardwert.  
  
 Wenn der Wert ungleich NULL ist, muss es angezeigt werden als Start_lsn-Wert eines aktuellen Eintrags in der [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) Tabelle. Wenn andere Einträge in CDC. lsn_time_mapping als neue untergrenzenmarkierung identifizierte Eintrag die dieselbe Commitzeit verwenden, wird die kleinste LSN, die dieser Gruppe von Einträgen zugeordnet wie die untergrenzenmarkierung ausgewählt.  
  
 Wenn der Wert explizit, für NULL-Werte der aktuellen festgelegt ist *untergrenzenmarkierung* für die *Aufzeichnungsinstanz* wird verwendet, um die obere Grenze für den Cleanupvorgang definieren.  
  
 [ @threshold=] '*Löschgrenzwert*"  
 Die maximale Anzahl der Einträge, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können. *Delete_threshold* ist **Bigint**, hat den Standardwert von 5000.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 sys.sp_cdc_cleanup_change_table führt die folgenden Vorgänge aus:  
  
1.  Wenn die @low_water_mark Parameter nicht NULL ist, wird der Wert der Start_lsn für die *Aufzeichnungsinstanz* mit dem neuen *untergrenzenmarkierung*.  
  
    > [!NOTE]  
    >  Bei der neuen Untergrenzenmarkierung muss es sich nicht zwingend um die im Aufruf der gespeicherten Prozedur angegebene Untergrenzenmarkierung handeln. Wenn andere Einträge in der CDC. lsn_time_mapping-Tabelle, die dieselbe Commitzeit verwenden, wird der kleinste Start_lsn dargestellt, in der Gruppe von Einträgen als angepasste untergrenzenmarkierung ausgewählt. Wenn die @low_water_mark Parameter NULL ist oder die aktuelle untergrenzenmarkierung größer als die neue Lowwatermark, der Start_lsn-Wert für die Aufzeichnungsinstanz unverändert.  
  
2.  Änderungstabelleneinträge mit __ $Start_lsn-Werte kleiner als der untergrenzenmarkierung werden dann gelöscht. Der Schwellenwert zum Löschen wird verwendet, um die Anzahl gelöschter Zeilen in einer einzigen Transaktion zu begrenzen. Ein Fehler bezüglich des erfolgreichen Löschens von Einträgen wird gemeldet. Etwaige Änderungen an der Untergrenzenmarkierung der Aufzeichnungsinstanz, die aufgrund des Aufrufs vorgenommen wurden, werden davon jedoch nicht beeinflusst.  
  
 Verwenden Sie sp_cdc_cleanup_change_table in den folgenden Situationen:  
  
-   Der Auftrag des Cleanup-Agents meldet Löschfehler.  
  
     Ein Administrator kann diese gespeicherte Prozedur explizit ausführen, um einen fehlgeschlagenen Vorgang zu wiederholen. Um Cleanup für eine gegebene Aufzeichnungsinstanz zu wiederholen, führen Sie sp_cdc_cleanup_change_table aus, und geben Sie NULL für den @low_water_mark Parameter.  
  
-   Die vom Cleanup-Agentauftrag verwendete einfache beibehaltungsbasierte Richtlinie ist nicht ausreichend.  
  
     Da diese gespeicherte Prozedur ein Cleanup für eine einzelne Aufzeichnungsinstanz durchführt, kann sie verwendet werden, um eine benutzerdefinierte Cleanupstrategie zu erstellen, bei der die Cleanupregeln auf die jeweilige Aufzeichnungsinstanz zugeschnitten werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
## <a name="see-also"></a>Siehe auch  
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_get_min_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys.fn_cdc_increment_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)  
  
  
