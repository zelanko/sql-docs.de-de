---
title: SQL Server-Meldungsergebnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 577b609fd2f878e6c97010cac004e0b10b3a4e4e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300969"
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die [!INCLUDE[tsql](../../includes/tsql-md.md)] folgenden Anweisungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generieren keine nativen CLIENT-OLE-DB-Anbieterrowsets oder eine Anzahl der betroffenen Zeilen, wenn sie ausgeführt werden:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei erfolgreicher Ausführung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der native Client-OLE-DB-Anbieter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] S_OK zurück, und die Nachrichten sind für den Consumer des nativen Client-OLE-DB-Anbieters verfügbar.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt S_OK zurück und verfügt [!INCLUDE[tsql](../../includes/tsql-md.md)] über eine oder mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationsmeldungen, die nach der Ausführung vieler Anweisungen oder der Consumerausführung einer nativen Client-OLE-DB-Anbietermemberfunktion verfügbar sind.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer, der die dynamische Spezifikation von Abfragetext zulässt, sollte Fehlerschnittstellen nach jeder Memberfunktionsausführung unabhängig vom Wert des Rückgabecodes, dem Vorhandensein oder Fehlen eines zurückgegebenen **IRowset-** oder **IMultipleResults-Schnittstellenverweises** oder einer Anzahl betroffener Zeilen überprüfen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Errors](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
