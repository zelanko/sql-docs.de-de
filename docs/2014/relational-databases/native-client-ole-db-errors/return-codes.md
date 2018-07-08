---
title: Rückgabecodes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00082a5c6053d8b9f0319c26ae8d72302c14d218
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407629"
---
# <a name="return-codes"></a>Rückgabecodes
  Auf der grundlegenden Ebene wird eine Elementfunktion entweder erfolgreich ausgeführt, oder sie schlägt fehl. Auf einer genaueren Ebene kann eine Funktion erfolgreich ausgeführt werden, ohne dass das Ergebnis dem entspricht, was vom Anwendungsentwickler beabsichtigt war.  
  
 Weitere Informationen zu OLE DB-Rückgabecodes finden Sie unter [Rückgabecodes (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Memberfunktion von Native Client OLE DB-Anbieters S_OK zurückgibt, die Funktion erfolgreich ausgeführt.  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Memberfunktion von Native Client OLE DB-Anbieters nicht S_OK zurückgibt, das Entpacken von OLE/COM HRESULT fehlgeschlagen, und IS_ERROR-Makros können den Erfolg oder das Fehlschlagen einer Funktion bestimmen.  
  
 Wenn FAILED oder IS_ERROR den Wert TRUE zurückgibt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer der Native Client OLE DB-Anbieter daran, dass die Ausführung der Elementfunktion fehlgeschlagen. Wenn FAILED oder IS_ERROR zurückgeben "false" und das HRESULT nicht S_OK, entspricht die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer der Native Client OLE DB-Anbieter daran, dass die Funktion in gewisser Weise war erfolgreich. Der Consumer kann ausführliche Informationen zu diesem "Erfolg mit Informationen" zurückgeben, aus Abrufen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fehlerschnittstellen für Native Client OLE DB-Anbieter. Darüber hinaus in der Fall, in denen eine Funktion (das FAILED-Makro gibt "true") vollständig fehlschlägt, steht erweiterte Fehlerinformationen aus der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fehlerschnittstellen für Native Client OLE DB-Anbieter.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters erhalten häufig die HRESULT-erfolgsrückgabe mit Informationen DB_S_ERRORSOCCURRED "Success". In der Regel definieren Elementfunktionen, die DB_S_ERRORSOCCURRED zurückgeben, einen oder mehrere Parameter, die Statuswerte an den Consumer übermitteln. Möglicherweise stehen dem Consumer nur die Fehlerinformationen zur Verfügung, die in Statuswertparametern zurückgegeben werden. Daher sollten Consumer Anwendungslogik implementieren, um Statuswerte abzurufen, wenn diese verfügbar sind.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Memberfunktionen geben den Erfolgscode S_FALSE nicht zurück. Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Memberfunktionen geben stets S_OK Erfolg zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](errors.md)  
  
  
