---
title: SQLSTATE (ODBC-Fehlercodes) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291520"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC-Fehlercodes)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLSTATE stellt ausführliche Informationen über die Ursache einer Warnung oder eines Fehlers bereit. Bei Fehlern, die in der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erkannten und zurückgegebenen Datenquelle auftreten, ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client ODBC-Treiber die zurückgegebene systemeigene Fehlernummer der entsprechenden SQLSTATE zu. Wenn eine systemeigene Fehlernummer keinen ODBC-Fehlercode [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufweist, dem zugeordnet werden kann, gibt der native Client-ODBC-Treiber SQLSTATE 42000 zurück ("Syntaxfehler oder Zugriffsverletzung"). Bei Fehlern, die vom Treiber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkannt werden, generiert der Native Client ODBC-Treiber den entsprechenden SQLSTATE.  
  
 Weitere Informationen über Statusfehlercodes finden Sie unter folgenden Themen:  
  
-   [Anhang A: ODBC-Fehlercodes](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [SQLSTATE-Zuordnungen](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
