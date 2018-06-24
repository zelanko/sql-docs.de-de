---
title: Rückgabecodes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 37f3326aacd601dd9b52f0f55e146fa1b17cdcc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046433"
---
# <a name="return-codes"></a>Rückgabecodes
  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Memberfunktion für Native Client OLE DB-Anbieter S_OK zurückgibt, die Funktion erfolgreich ausgeführt.  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Memberfunktion nicht S_OK zurückgibt, das Entpacken von OLE/COM HRESULT fehlgeschlagen, und IS_ERROR-Makros können den Erfolg oder das Fehlschlagen einer Funktion bestimmen.  
  
 Wenn FAILED oder IS_ERROR gibt "true", die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter daran, dass die Ausführung der Elementfunktion fehlgeschlagen. Wenn FAILED oder IS_ERROR Rückgabecode "false" und das HRESULT nicht S_OK, entspricht die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter daran, dass die Funktion in gewisser Hinsicht erfolgreich war. Der Consumer kann detaillierte Informationen, die auf diesem "Success mit Informationen" zurückgeben aus Abrufen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fehlerschnittstellen für Native Client OLE DB-Anbieter. Außerdem im Fall, in dem eine Funktion eindeutig ein Fehler auftritt (das FAILED-Makro gibt "true") steht erweiterte Fehlerinformationen aus dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fehlerschnittstellen für Native Client OLE DB-Anbieter.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters erhalten häufig die HRESULT-erfolgsrückgabe mit Informationen DB_S_ERRORSOCCURRED "Success". In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Memberfunktionen geben den Erfolgscode S_FALSE nicht zurück. Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Memberfunktionen geben stets S_OK Erfolg zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](errors.md)  
  
  