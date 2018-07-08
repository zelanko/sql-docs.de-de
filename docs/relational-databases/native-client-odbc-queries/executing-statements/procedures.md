---
title: Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a9e76e22cc64478493e9e75b712de29e8785e64d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430199"
---
# <a name="procedures"></a>Vorgehensweisen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Eine gespeicherte Prozedur ist ein vorkompiliertes ausführbares Objekt, das eine oder mehrere [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen enthält. Gespeicherte Prozeduren können Ein- und Ausgabeparameter enthalten und auch einen ganzzahligen Rückgabecode ausgeben. Eine Anwendung kann kann mithilfe von Katalogfunktionen verfügbare gespeicherte Prozeduren auflisten.  
  
 ODBC-Anwendungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sollten gespeicherte Prozeduren nur mithilfe der direkten Ausführung aufrufen. Beim Verbinden mit früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber implementiert [SQLPrepare-Funktion](http://go.microsoft.com/fwlink/?LinkId=59360) erstellen Sie eine temporäre gespeicherte Prozedur, die anschließend aufgerufen wird, auf **SQLExecute** . Fügt Aufwand haben **SQLPrepare** erstellen eine temporäre gespeicherte Prozedur, die nur Aufrufe das Ziel im Vergleich zur gespeicherten Prozedur direkt das Ziel ausführen Prozedur gespeicherten. Selbst bei einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] muss der Aufruf eines zusätzlichen Roundtrips durch das Netzwerk vorbereitet und ein Ausführungsplan, mit dem nur der Ausführungsplan der gespeicherten Prozedur aufgerufen wird, erstellt werden.  
  
 Beim Ausführen einer gespeicherten Prozedur sollten ODBC-Anwendungen die ODBC CALL-Syntax verwenden. Der Treiber ist für die Verwendung eines Remoteprozeduraufrufsmechanismus zum Aufrufen der Prozedur optimiert, sofern die ODBC CALL-Syntax verwendet wird. Dies ist effizienter als der Mechanismus, der verwendet wird, um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE-Anweisung an den Server zu senden.  
  
 Weitere Informationen finden Sie unter [Ausführen von gespeicherten Prozeduren](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Anweisungen &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
