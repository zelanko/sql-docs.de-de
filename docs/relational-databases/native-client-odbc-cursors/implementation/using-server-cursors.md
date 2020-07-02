---
title: Verwenden von Server Cursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 962a8879d53f9cf7f0f59ba4c79ba63063f79ecc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730383"
---
# <a name="using-server-cursors"></a>Verwenden von Servercursorn
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Wenn eine ODBC-Anwendung ODBC-Cursor Attribute auf andere als die Standardwerte festlegt, fordert der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber den Server auf, einen API-Server Cursor desselben Typs zu implementieren. Durch die Verwendung von API-Servercursorn wird auf dem Client Arbeitsspeicher freigegeben, und zudem kann der Netzwerkdatenverkehr zwischen dem Client und dem Server erheblich reduziert werden.  
  
 Ein potenzieller Nachteil von API-Servercursorn liegt darin, dass sie zurzeit nicht alle SQL-Anweisungen unterstützen. API-Servercursor können nicht verwendet werden, um Folgendes auszuführen:  
  
-   Batches oder gespeicherte Prozeduren, die mehrere Resultsets zurückgeben  
  
-   SELECT-Anweisungen, die die Klauseln COMPUTE, COMPUTE BY, FOR BROWSE oder INTO enthalten  
  
-   Eine EXECUTE-Anweisung, die auf eine remote gespeicherte Prozedur verweist  
  
 Wenn eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] besteht, führt die Ausführung einer Anweisung mit diesen Merkmalen mithilfe eines Servercursors dazu, dass der Cursor in ein Standardresultset konvertiert wird. Wenn eine Verbindung zu früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt ist, verursacht sie einen Fehler.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
