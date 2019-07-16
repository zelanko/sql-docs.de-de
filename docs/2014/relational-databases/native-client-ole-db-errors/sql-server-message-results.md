---
title: SQL Server-Meldungsergebnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff604f4c5d66a5742868e25ba05ca6b4528ddb1a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206707"
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
  Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen generieren keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters erlauben oder die Anzahl der betroffenen Zeilen zurück, wenn ausgeführt:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei einer erfolgreichen Ausführung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt S_OK zurück, und die Nachrichten stehen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt S_OK zurück, und verfügt über eine oder mehrere informationsmeldungen nach der Ausführung von vielen [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen oder Ausführung der Consumer eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Element -Funktion.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Consumer ermöglicht die dynamische Angabe von Abfragetext sollte fehlerschnittstellen überprüfen Sie nach jeder Ausführung der Elementfunktion unabhängig vom Wert von den Rückgabecode, das Vorhandensein oder fehlen einer zurückgegebenen **IRowset** oder **IMultipleResults** -Schnittstellenverweises oder die Anzahl der betroffenen Zeilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](errors.md)  
  
  
