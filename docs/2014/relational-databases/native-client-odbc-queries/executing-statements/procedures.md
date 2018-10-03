---
title: Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f429edc79227c815142dd0800363fcde8f20c6f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158960"
---
# <a name="procedures"></a>Vorgehensweisen
  Eine gespeicherte Prozedur ist ein vorkompiliertes ausführbares Objekt, das eine oder mehrere [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen enthält. Gespeicherte Prozeduren können Ein- und Ausgabeparameter enthalten und auch einen ganzzahligen Rückgabecode ausgeben. Eine Anwendung kann kann mithilfe von Katalogfunktionen verfügbare gespeicherte Prozeduren auflisten.  
  
 ODBC-Anwendungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sollten gespeicherte Prozeduren nur mithilfe der direkten Ausführung aufrufen. Beim Verbinden mit früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber implementiert [SQLPrepare-Funktion](http://go.microsoft.com/fwlink/?LinkId=59360) erstellen Sie eine temporäre gespeicherte Prozedur, die anschließend aufgerufen wird, auf **SQLExecute** . Fügt Aufwand haben **SQLPrepare** erstellen eine temporäre gespeicherte Prozedur, die nur Aufrufe das Ziel im Vergleich zur gespeicherten Prozedur direkt das Ziel ausführen Prozedur gespeicherten. Selbst bei einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] muss der Aufruf eines zusätzlichen Roundtrips durch das Netzwerk vorbereitet und ein Ausführungsplan, mit dem nur der Ausführungsplan der gespeicherten Prozedur aufgerufen wird, erstellt werden.  
  
 Beim Ausführen einer gespeicherten Prozedur sollten ODBC-Anwendungen die ODBC CALL-Syntax verwenden. Der Treiber ist für die Verwendung eines Remoteprozeduraufrufsmechanismus zum Aufrufen der Prozedur optimiert, sofern die ODBC CALL-Syntax verwendet wird. Dies ist effizienter als der Mechanismus, der verwendet wird, um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE-Anweisung an den Server zu senden.  
  
 Weitere Informationen finden Sie unter [Ausführen von gespeicherten Prozeduren](../../native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Anweisungen &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
