---
title: Rückgabe Codes | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 36f376710dbcdd09daf664e9eee20533c5372641
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790235"
---
# <a name="return-codes"></a>Rückgabecodes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Member-Funktion S_OK zurückgibt, wurde die Funktion erfolgreich ausgeführt.  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Mitglieds Funktion S_OK nicht zurückgibt, kann das OLE/com HRESULT-entpacken fehlschlagen und IS_ERROR Makros den Gesamterfolg oder Misserfolg einer Funktion ermitteln.  
  
 Wenn ein Fehler aufgetreten ist oder IS_ERROR true zurückgibt, wird der Consumer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters sichergestellt, dass die Ausführung der Mitglieds Funktion Wenn ein Fehler aufgetreten ist oder IS_ERROR false zurückgeben und das HRESULT nicht gleich S_OK ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Consumer sicher sein, dass die Funktion in gewisser Hinsicht erfolgreich war. Der Consumer kann ausführliche Informationen zu diesem "Erfolg mit Informationen" abrufen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieter-Fehler Schnittstellen zurückgegeben werden. Außerdem sind in dem Fall, in dem eine Funktion eindeutig fehlschlägt (das fehlerhafte Makro gibt true zurück), erweiterte Fehlerinformationen über die Fehler Schnittstellen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieters verfügbar.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer von Native Client OLE DB-Anbietern treten häufig die DB_S_ERRORSOCCURRED "Erfolg mit Informationen" auf, die HRESULT zurückgibt. In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Systemfunktionen von Native Client OLE DB-Anbieter geben den Erfolgs Code S_FALSE nicht zurück. Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieter-Mitglieds Funktionen geben immer S_OK zurück, um einen Erfolg anzugeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
