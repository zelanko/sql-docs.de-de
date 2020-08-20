---
description: Änderungsnachverfolgungsfunktionen (Transact-SQL)
title: Änderungsnachverfolgung-Funktionen (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 69a301c266ce546733ef1fb26bf1479a5c2d8a2f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498233"
---
# <a name="change-tracking-functions-transact-sql"></a>Änderungsnachverfolgungsfunktionen (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Die Änderungsverfolgung zeichnet Einfüge-, Update- und Löschvorgänge auf, die an nachverfolgten Tabellen vorgenommen werden, und stellt Details zu den Änderungen in einem leicht verwendbaren relationalen Format bereit. Die folgenden Funktionen geben Informationen zu den Änderungen zurück.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[CHANGETABLE (changes)](../../relational-databases/system-functions/changetable-transact-sql.md)|Gibt Nachverfolgungsinformationen für alle Änderungen an einer Tabelle zurück, die seit einer angegebenen Version vorgenommen wurden.|  
|[CHANGETABLE (Version)](../../relational-databases/system-functions/changetable-transact-sql.md)|Gibt die letzten Änderungsnachverfolgungsinformationen für eine angegebene Zeile zurück.|  
|[CHANGE_TRACKING_MIN_VALID_VERSION ()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|Gibt die minimale Version zurück, die zum Abrufen von Änderungs nach Verfolgungs Informationen aus der angegebenen Tabelle gültig ist, wenn Sie die [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) -Funktion verwenden.|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|Ruft eine Version ab, die mit der letzten Transaktion, für die Commit ausgeführt wurde, verknüpft ist. Sie können diese Version beim nächsten Aufzählen von Änderungen mit CHANGETABLE verwenden.|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|Interpretiert den SYS_CHANGE_COLUMNS Wert, der von der CHANGETABLE (changes...)-Funktion zurückgegeben wird.|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|Aktiviert die Spezifikation eines Änderungskontexts, z. B. eine Absender-ID, wenn Daten durch eine Anwendung geändert werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nachverfolgen von Datenänderungen &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
