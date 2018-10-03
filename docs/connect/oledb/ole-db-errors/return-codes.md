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
manager: craigg
ms.openlocfilehash: 994011062b36f028157c3f70b3f2ed3c335d526f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612908"
---
# <a name="return-codes"></a>Rückgabecodes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn ein OLE DB-Treiber für SQL Server-Memberfunktion S_OK zurückgibt, wurde die Funktion erfolgreich.  
  
 Wenn eine Elementfunktion des OLE DB-Treibers für SQL Server nicht S_OK zurückgibt, ist das Entpacken von OLE/COM HRESULT fehlgeschlagen, und IS_ERROR-Makros können den Erfolg oder das Fehlschlagen einer Funktion bestimmen.  
  
 Wenn FAILED oder IS_ERROR den Wert TRUE zurückgibt, erkennt der OLE DB-Treiber für SQL Server, dass die Ausführung der Memberfunktion fehlgeschlagen ist. Wenn FAILED oder IS_ERROR zurückgeben entspricht "false" und das HRESULT nicht S_OK, der OLE DB-Treiber für SQL Server-Consumer die Funktion erfolgreich ausgeführt, in gewisser Weise gewährleistet werden kann. Der Consumer kann ausführliche Informationen über diese „Erfolgsrückgabe mit Informationen“ von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server abrufen. Auch in Fällen, in denen eine Funktion vollständig fehlschlägt (und das FAILED-Makro den Wert TRUE zurückgibt), sind erweiterte Fehlerinformationen von den Fehlerschnittstellen des OLE DB-Treibers für SQL Server verfügbar.  
  
 OLE DB-Treiber für SQL Server-Consumer kommen häufig die HRESULT-erfolgsrückgabe mit Informationen DB_S_ERRORSOCCURRED "Success". In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Der OLE DB-Treiber für SQL Server-Memberfunktionen nicht den Erfolgscode S_FALSE nicht zurück. Alle OLE DB-Treiber für SQL Server-Memberfunktionen immer gibt S_OK zurück, um den Erfolg mitzuteilen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
