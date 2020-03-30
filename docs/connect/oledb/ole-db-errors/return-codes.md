---
title: Rückgabecodes | Microsoft-Dokumentation
description: Rückgabecodes
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a1deedd8903f69268ebc5e7f5caafaa79a7f7b18
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994925"
---
# <a name="return-codes"></a>Rückgabecodes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn eine Elementfunktion des OLE DB-Treibers für SQL Server S_OK zurückgibt, wurde die Funktion erfolgreich ausgeführt.  
  
 Wenn eine Elementfunktion des OLE DB-Treibers für SQL Server nicht S_OK zurückgibt, ist das Entpacken von OLE/COM HRESULT fehlgeschlagen, und IS_ERROR-Makros können den Erfolg oder das Fehlschlagen einer Funktion bestimmen.  
  
 Wenn FAILED oder IS_ERROR den Wert TRUE zurückgibt, erkennt der OLE DB-Treiber für SQL Server, dass die Ausführung der Memberfunktion fehlgeschlagen ist. Wenn FAILED oder IS_ERROR den Wert FALSE zurückgibt und HRESULT nicht S_OK entspricht, erkennt der OLE DB-Treiber für SQL Server, dass die Funktion zumindest teilweise erfolgreich war. Der Consumer kann ausführliche Informationen über diese „Erfolgsrückgabe mit Informationen“ von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server abrufen. Auch in Fällen, in denen eine Funktion vollständig fehlschlägt (und das FAILED-Makro den Wert TRUE zurückgibt), sind erweiterte Fehlerinformationen von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server verfügbar.  
  
 Bei Consumern des OLE DB-Treibers für SQL Server tritt häufig die HRESULT-"Erfolgsrückgabe mit Informationen" DB_S_ERRORSOCCURRED auf. In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Die Elementfunktionen des OLE DB-Treibers für SQL Server geben nicht den Erfolgscode S_FALSE zurück. Alle Elementfunktionen des OLE DB-Treibers für SQL Server geben immer S_OK zurück, um eine erfolgreiche Ausführung anzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
