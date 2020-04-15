---
title: Rückgabecodes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 09056c9d4964ad10b2b25f63ef5991a1a7742cab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301022"
---
# <a name="return-codes"></a>Rückgabecodes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Native Client OLE DB-Anbietermemberfunktion S_OK zurückgibt, war die Funktion erfolgreich.  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine native Client-OLE-DB-Anbietermemberfunktion S_OK nicht zurückgibt, können die OLE/COM HRESULT-Entpackung von FAILED und IS_ERROR Makros den Gesamterfolg oder Fehler einer Funktion bestimmen.  
  
 Wenn FAILED oder IS_ERROR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] TRUE zurückgibt, wird dem Consumer des nativen Client-OLE-DB-Anbieters versichert, dass die Ausführung der Memberfunktion fehlgeschlagen ist. Wenn FAILED oder IS_ERROR FALSE zurückgeben und das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] HRESULT nicht S_OK entspricht, ist dem Consumer des nativen Client-OLE-DB-Anbieters versichert, dass die Funktion in gewissem Sinne erfolgreich war. Der Consumer kann detaillierte Informationen zu dieser "Erfolg [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit Informationen"-Rückgabe von den Fehlerschnittstellen des Native Client OLE DB-Anbieters abrufen. Wenn eine Funktion eindeutig fehlschlägt (das FAILED-Makro gibt TRUE zurück), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind erweiterte Fehlerinformationen über die Fehlerschnittstellen des Native Client OLE DB-Anbieters verfügbar.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB-Anbieter-Verbraucher stoßen häufig auf die DB_S_ERRORSOCCURRED "Erfolg mit Informationen" HRESULT-Rückgabe. In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Memberfunktionen des nativen Client-OLE-DB-Anbieters geben den Erfolgscode nicht S_FALSE zurück. Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbietermemberfunktionen geben immer S_OK zurück, um den Erfolg anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Errors](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
