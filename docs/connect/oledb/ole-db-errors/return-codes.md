---
title: Rückgabecodes (OLE DB-Treiber)
description: Erfahren Sie mehr über Rückgabecodes für OLE DB-Treiber für SQL Server-Memberfunktionen und wie Sie neben „Erfolg“ weitere Informationen zu Ergebnissen erhalten.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe59f14e43a32d6c6b3239c24f1be665e7bbad82
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727181"
---
# <a name="return-codes"></a>Rückgabecodes
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](/previous-versions/windows/desktop/ms725451(v=vs.85)).  
  
 Wenn eine Elementfunktion des OLE DB-Treibers für SQL Server S_OK zurückgibt, wurde die Funktion erfolgreich ausgeführt.  
  
 Wenn eine Elementfunktion des OLE DB-Treibers für SQL Server nicht S_OK zurückgibt, ist das Entpacken von OLE/COM HRESULT fehlgeschlagen, und IS_ERROR-Makros können den Erfolg oder das Fehlschlagen einer Funktion bestimmen.  
  
 Wenn FAILED oder IS_ERROR den Wert TRUE zurückgibt, erkennt der OLE DB-Treiber für SQL Server, dass die Ausführung der Memberfunktion fehlgeschlagen ist. Wenn FAILED oder IS_ERROR den Wert FALSE zurückgibt und HRESULT nicht S_OK entspricht, erkennt der OLE DB-Treiber für SQL Server, dass die Funktion zumindest teilweise erfolgreich war. Der Consumer kann ausführliche Informationen über diese „Erfolgsrückgabe mit Informationen“ von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server abrufen. Auch in Fällen, in denen eine Funktion vollständig fehlschlägt (und das FAILED-Makro den Wert TRUE zurückgibt), sind erweiterte Fehlerinformationen von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server verfügbar.  
  
 Bei Consumern des OLE DB-Treibers für SQL Server tritt häufig die HRESULT-"Erfolgsrückgabe mit Informationen" DB_S_ERRORSOCCURRED auf. In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Die Elementfunktionen des OLE DB-Treibers für SQL Server geben nicht den Erfolgscode S_FALSE zurück. Alle Elementfunktionen des OLE DB-Treibers für SQL Server geben immer S_OK zurück, um eine erfolgreiche Ausführung anzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
