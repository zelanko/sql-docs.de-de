---
description: Ergebnisse der SQL Server Native Client Nachricht
title: SQL Server Nachrichten Ergebnisse (Native Client-OLE DB Anbieter)
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7fe5f2711334f371831bc76d60b5b74ef6b9a417
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467631"
---
# <a name="sql-server-native-client-message-results"></a>Ergebnisse der SQL Server Native Client Nachricht
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Die folgenden- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen generieren keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-anbietedatasets oder die Anzahl betroffener Zeilen, wenn Sie ausgeführt werden:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei erfolgreicher Ausführung gibt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieter S_OK zurück, und die Nachrichten sind für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer des Native Client-OLE DB Anbieters verfügbar.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt S_OK zurück und verfügt über eine oder mehrere Informationsmeldungen, die nach der Ausführung vieler- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen oder der Consumer-Ausführung einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Member-Funktion verfügbar sind.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer des Native Client OLE DB-Anbieters, der die dynamische Angabe von Abfragetext zulässt, sollte Fehler Schnittstellen nach jeder Ausführung der Element Funktion unabhängig vom Wert des Rückgabecodes, dem vorhanden sein oder Fehlen eines zurückgegebenen **IRowset** -oder **IMultipleResults** -Schnittstellen Verweises oder der Anzahl betroffener Zeilen überprüfen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
