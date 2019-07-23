---
title: Rückgabe Codes | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994925"
---
# <a name="return-codes"></a>Rückgabecodes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn ein OLE DB Treiber für SQL Server Member-Funktion S_OK zurückgibt, wurde die Funktion erfolgreich ausgeführt.  
  
 Wenn eine Elementfunktion des OLE DB-Treibers für SQL Server nicht S_OK zurückgibt, ist das Entpacken von OLE/COM HRESULT fehlgeschlagen, und IS_ERROR-Makros können den Erfolg oder das Fehlschlagen einer Funktion bestimmen.  
  
 Wenn FAILED oder IS_ERROR den Wert TRUE zurückgibt, erkennt der OLE DB-Treiber für SQL Server, dass die Ausführung der Memberfunktion fehlgeschlagen ist. Wenn failed oder IS_ERROR false zurückgibt und HRESULT nicht gleich S_OK ist, wird der OLE DB-Treiber für SQL Server Consumer sichergestellt, dass die Funktion in gewisser Hinsicht erfolgreich war. Der Consumer kann ausführliche Informationen über diese „Erfolgsrückgabe mit Informationen“ von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server abrufen. Auch in Fällen, in denen eine Funktion vollständig fehlschlägt (und das FAILED-Makro den Wert TRUE zurückgibt), sind erweiterte Fehlerinformationen von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server verfügbar.  
  
 OLE DB Treiber für SQL Server Consumer stoßen häufig auf die HRESULT-Rückgabe des DB_S_ERRORSOCCURRED-Erfolgs mit Informationen. In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Der OLE DB-Treiber für SQL Server Member-Funktionen gibt den Erfolgs Code S_FALSE nicht zurück. Alle OLE DB Treiber für SQL Server Member-Funktionen geben immer S_OK zurück, um den Erfolg anzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
