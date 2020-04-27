---
title: Rückgabecodes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 625d56a38d88b3cccbea1c75ad88917af1a6f6dd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63228944"
---
# <a name="return-codes"></a>Rückgabecodes
  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Member-Funktion eines Native Client OLE DB-Anbieters S_OK zurückgibt, wurde die Funktion erfolgreich ausgeführt.  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Member des Native Client OLE DB-Anbieters S_OK nicht zurückgibt, kann das OLE/com HRESULT-entpacken fehlschlagen und IS_ERROR Makros den Gesamterfolg oder Misserfolg einer Funktion ermitteln.  
  
 Wenn ein Fehler aufgetreten ist oder IS_ERROR " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] true" zurückgibt, ist der Consumer des Native Client OLE DB Anbieters sicher, dass die Ausführung der Element Funktion Wenn ein Fehler aufgetreten ist oder IS_ERROR false zurückgeben und das HRESULT nicht gleich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] S_OK ist, wird der Consumer des Native Client OLE DB Anbieters sicher sein, dass die Funktion in gewisser Hinsicht erfolgreich war. Der Consumer kann ausführliche Informationen zu diesem "Erfolg mit Informationen" von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieter-Fehler Schnittstellen abrufen. Außerdem ist in dem Fall, in dem eine Funktion eindeutig fehlschlägt (das fehlgeschlagene Makro gibt true zurück), erweiterte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlerinformationen über die Fehler Schnittstellen des Native Client OLE DB Anbieters verfügbar.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Der Consumer des Native Client OLE DB-Anbieters stößt häufig auf die DB_S_ERRORSOCCURRED "Erfolg mit Informationen" HRESULT zurück. In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Element Funktionen des Native Client OLE DB-Anbieters geben den Erfolgs Code S_FALSE nicht zurück. Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Member von Native Client OLE DB-Anbieter Membern geben immer S_OK zurück, um einen Erfolg anzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mern](errors.md)  
  
  
