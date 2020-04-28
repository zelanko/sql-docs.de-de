---
title: SQLSTATE (ODBC-Fehler Codes) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8c7f3fbdf690989830cff2a41028ee0c1e2c9f37
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81291520"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC-Fehlercodes)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLSTATE stellt ausführliche Informationen über die Ursache einer Warnung oder eines Fehlers bereit. Bei Fehlern, die in der von der Datenquelle erkannten und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von zurück [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gegebenen Datenquelle auftreten, ordnet der Native Client ODBC-Treiber die zurückgegebene systemeigene Fehlernummer dem entsprechenden SQLSTATE zu. Wenn eine systemeigene Fehlernummer keinen ODBC-Fehlercode aufweist, der zugeordnet werden kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gibt der Native Client-ODBC-Treiber SQLSTATE 42000 ("Syntax Fehler oder Zugriffsverletzung") zurück. Für Fehler, die vom Treiber erkannt werden, generiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client-ODBC-Treiber den entsprechenden SQLSTATE.  
  
 Weitere Informationen über Statusfehlercodes finden Sie unter folgenden Themen:  
  
-   [Anhang A: ODBC-Fehlercodes](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [SQLSTATE-Zuordnungen](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
