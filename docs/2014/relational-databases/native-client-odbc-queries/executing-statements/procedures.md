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
ms.openlocfilehash: d030d4fb12ce9217bbdb88f501a0b0674c5a5828
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206752"
---
# <a name="procedures"></a>Prozeduren
  Eine gespeicherte Prozedur ist ein vorkompiliertes ausführbares Objekt, das eine oder mehrere [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen enthält. Gespeicherte Prozeduren können Ein- und Ausgabeparameter enthalten und auch einen ganzzahligen Rückgabecode ausgeben. Eine Anwendung kann kann mithilfe von Katalogfunktionen verfügbare gespeicherte Prozeduren auflisten.  
  
 ODBC-Anwendungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sollten gespeicherte Prozeduren nur mithilfe der direkten Ausführung aufrufen. Bei einer Verbindung mit früheren Versionen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]von implementiert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Native Client-ODBC-Treiber die [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360) , indem eine temporäre gespeicherte Prozedur erstellt wird, die dann für **SQLExecute**aufgerufen wird. Es erhöht den Aufwand, damit **SQLPrepare** eine temporäre gespeicherte Prozedur erstellt, die nur die gespeicherte Ziel Prozedur aufruft und die gespeicherte Ziel Prozedur direkt ausführt. Selbst bei einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] muss der Aufruf eines zusätzlichen Roundtrips durch das Netzwerk vorbereitet und ein Ausführungsplan, mit dem nur der Ausführungsplan der gespeicherten Prozedur aufgerufen wird, erstellt werden.  
  
 Beim Ausführen einer gespeicherten Prozedur sollten ODBC-Anwendungen die ODBC CALL-Syntax verwenden. Der Treiber ist für die Verwendung eines Remoteprozeduraufrufsmechanismus zum Aufrufen der Prozedur optimiert, sofern die ODBC CALL-Syntax verwendet wird. Dies ist effizienter als der Mechanismus, der verwendet wird, um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE-Anweisung an den Server zu senden.  
  
 Weitere Informationen finden Sie unter [Ausführen gespeicherter Prozeduren](../../native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](executing-statements-odbc.md)  
  
  
