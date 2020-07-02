---
title: sys. sp_cdc_cleanup_change_table (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 061321d6fdefb52890a54fb7e18aa0a618cd986f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85626250"
---
# <a name="syssp_cdc_cleanup_change_table-transact-sql"></a>sys.sp_cdc_cleanup_change_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Entfernt Zeilen aus der Änderungs Tabelle in der aktuellen Datenbank auf Grundlage des angegebenen *low_water_mark* Werts. Diese gespeicherte Prozedur wird für Benutzer bereitgestellt, die den Cleanupprozess für Änderungstabellen direkt verwalten möchten. Da diese Prozedur alle Consumer der Änderungstabellendaten betrifft, sollte sie mit Vorsicht eingesetzt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_cleanup_change_table   
  [ @capture_instance = ] 'capture_instance',   
  [ @low_water_mark = ] low_water_mark ,  
  [ @threshold = ]'delete threshold'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @capture_instance =] '*capture_instance*'  
 Der Name der Aufzeichnungsinstanz, die der Änderungstabelle zugeordnet ist. *capture_instance* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
 *capture_instance* müssen eine Aufzeichnungs Instanz benennen, die in der aktuellen Datenbank vorhanden ist.  
  
 [ @low_water_mark =] *low_water_mark*  
 Eine Protokoll Folge Nummer (Log Sequence Number, LSN), die als neue Untergrenzenmarkierung für die *Aufzeichnungs Instanz*verwendet werden soll. *low_water_mark* ist **Binary (10)** und hat keinen Standardwert.  
  
 Wenn der Wert nicht NULL ist, muss er als start_lsn Wert eines aktuellen Eintrags in der [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) -Tabelle angezeigt werden. Wenn andere Einträge in CDC. lsn_time_mapping dieselbe commitzeitzeit wie der durch die neue Untergrenzenmarkierung identifizierte Eintrag gemeinsam verwenden, wird die kleinste LSN, die dieser Gruppe von Einträgen zugeordnet ist, als Untergrenzenmarkierung ausgewählt.  
  
 Wenn der Wert explizit auf NULL festgelegt ist, wird die aktuelle *Untergrenzenmarkierung* für die *Aufzeichnungs Instanz* verwendet, um die obere Grenze für den Cleanupvorgang zu definieren.  
  
 [ @threshold =] '*Schwellenwert löschen*'  
 Die maximale Anzahl der Einträge, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können. *delete_threshold* ist vom Datentyp **bigint**und hat den Standardwert 5000.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 sys.sp_cdc_cleanup_change_table führt die folgenden Vorgänge aus:  
  
1.  Wenn der- @low_water_mark Parameter nicht NULL ist, wird der Wert start_lsn für die *Aufzeichnungs Instanz* auf die neue Untergrenzenmarkierung festgelegt. *low watermark*  
  
    > [!NOTE]  
    >  Bei der neuen Untergrenzenmarkierung muss es sich nicht zwingend um die im Aufruf der gespeicherten Prozedur angegebene Untergrenzenmarkierung handeln. Wenn andere Einträge in der Tabelle cdc. lsn_time_mapping dieselbe comdtzeit gemeinsam verwenden, wird der kleinste start_lsn, der in der Gruppe von Einträgen dargestellt wird, als angepasste Untergrenzenmarkierung ausgewählt. Wenn der- @low_water_mark Parameter NULL ist oder die aktuelle Untergrenzenmarkierung größer als das neue lowwatermark ist, bleibt der start_lsn Wert für die Aufzeichnungs Instanz unverändert.  
  
2.  Änderungs Tabelleneinträge mit __ $ start_lsn Werte, die niedriger als die Untergrenzenmarkierung sind, werden dann gelöscht. Der Schwellenwert zum Löschen wird verwendet, um die Anzahl gelöschter Zeilen in einer einzigen Transaktion zu begrenzen. Ein Fehler bezüglich des erfolgreichen Löschens von Einträgen wird gemeldet. Etwaige Änderungen an der Untergrenzenmarkierung der Aufzeichnungsinstanz, die aufgrund des Aufrufs vorgenommen wurden, werden davon jedoch nicht beeinflusst.  

 Verwenden Sie sys. sp_cdc_cleanup_change_table unter folgenden Umständen:  
  
-   Der Auftrag des Cleanup-Agents meldet Löschfehler.  
  
     Ein Administrator kann diese gespeicherte Prozedur explizit ausführen, um einen fehlgeschlagenen Vorgang zu wiederholen. Führen Sie sys. sp_cdc_cleanup_change_table aus, und geben Sie für den Parameter NULL an, um die Bereinigung für eine bestimmte Aufzeichnungs Instanz zu wiederholen @low_water_mark .  
  
-   Die vom Cleanup-Agentauftrag verwendete einfache beibehaltungsbasierte Richtlinie ist nicht ausreichend.  
  
     Da diese gespeicherte Prozedur ein Cleanup für eine einzelne Aufzeichnungsinstanz durchführt, kann sie verwendet werden, um eine benutzerdefinierte Cleanupstrategie zu erstellen, bei der die Cleanupregeln auf die jeweilige Aufzeichnungsinstanz zugeschnitten werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
## <a name="see-also"></a>Weitere Informationen  
 [CDC. fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys. fn_cdc_get_min_lsn &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys.fn_cdc_increment_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)  
  
  
