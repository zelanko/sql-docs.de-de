---
title: Verwenden von Servercursorn | Microsoft-Dokumentation
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
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4bab91e4b952b808564da4d04b1ce400bf448c14
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43079151"
---
# <a name="using-server-cursors"></a>Verwenden von Servercursorn
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Wenn eine ODBC-Anwendung eines ODBC-Cursorattribut auf etwas anderes als die Standardeinstellungen, setzt der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber fordert der Server ein API-Servercursor desselben Typs zu implementieren. Durch die Verwendung von API-Servercursorn wird auf dem Client Arbeitsspeicher freigegeben, und zudem kann der Netzwerkdatenverkehr zwischen dem Client und dem Server erheblich reduziert werden.  
  
 Ein potenzieller Nachteil von API-Servercursorn liegt darin, dass sie zurzeit nicht alle SQL-Anweisungen unterstützen. API-Servercursor können nicht verwendet werden, um Folgendes auszuführen:  
  
-   Batches oder gespeicherte Prozeduren, die mehrere Resultsets zurückgeben  
  
-   SELECT-Anweisungen, die die Klauseln COMPUTE, COMPUTE BY, FOR BROWSE oder INTO enthalten  
  
-   Eine EXECUTE-Anweisung, die auf eine remote gespeicherte Prozedur verweist  
  
 Wenn eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] besteht, führt die Ausführung einer Anweisung mit diesen Merkmalen mithilfe eines Servercursors dazu, dass der Cursor in ein Standardresultset konvertiert wird. Wenn eine Verbindung zu früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt ist, verursacht sie einen Fehler.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
