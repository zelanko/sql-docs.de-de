---
title: Änderungsnachverfolgungsfunktionen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8dc2dceec177922369fe2bbef74bafeeef2ca27c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042962"
---
# <a name="change-tracking-functions-transact-sql"></a>Änderungsnachverfolgungsfunktionen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Die Änderungsverfolgung zeichnet Einfüge-, Update- und Löschvorgänge auf, die an nachverfolgten Tabellen vorgenommen werden, und stellt Details zu den Änderungen in einem leicht verwendbaren relationalen Format bereit. Die folgenden Funktionen geben Informationen zu den Änderungen zurück.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[CHANGETABLE (CHANGES.)](../../relational-databases/system-functions/changetable-transact-sql.md)|Gibt Nachverfolgungsinformationen für alle Änderungen an einer Tabelle zurück, die seit einer angegebenen Version vorgenommen wurden.|  
|[CHANGETABLE (VERSION)](../../relational-databases/system-functions/changetable-transact-sql.md)|Gibt die letzten Änderungsnachverfolgungsinformationen für eine angegebene Zeile zurück.|  
|[CHANGE_TRACKING_MIN_VALID_VERSION()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|Gibt die Mindestversion, die zum Abrufen von änderungsnachverfolgungsinformationen aus der angegebenen Tabelle bei der Verwendung gültig ist die [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) Funktion.|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|Ruft eine Version ab, die mit der letzten Transaktion, für die Commit ausgeführt wurde, verknüpft ist. Sie können diese Version beim nächsten Aufzählen von Änderungen mit CHANGETABLE verwenden.|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|Interpretiert den SYS_CHANGE_COLUMNS-Wert, der von der CHANGETABLE(Changes...)-Funktion zurückgegeben wird.|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|Aktiviert die Spezifikation eines Änderungskontexts, z. B. eine Absender-ID, wenn Daten durch eine Anwendung geändert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Nachverfolgen von Datenänderungen &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
