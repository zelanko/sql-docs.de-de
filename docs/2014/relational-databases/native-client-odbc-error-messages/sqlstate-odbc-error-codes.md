---
title: SQLSTATE (ODBC-Fehler Codes) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ff3ec0a5cdc8f24f34e42849f7c8f6d1d9d41478
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019911"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC-Fehlercodes)
  SQLSTATE stellt ausführliche Informationen über die Ursache einer Warnung oder eines Fehlers bereit. Bei Fehlern, die in der von der Datenquelle erkannten und von zurückgegebenen Datenquelle auftreten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber die zurückgegebene systemeigene Fehlernummer dem entsprechenden SQLSTATE zu. Wenn eine systemeigene Fehlernummer keinen ODBC-Fehlercode aufweist, der zugeordnet werden kann, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der Native Client-ODBC-Treiber SQLSTATE 42000 ("Syntax Fehler oder Zugriffsverletzung") zurück. Für Fehler, die vom Treiber erkannt werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert der Native Client-ODBC-Treiber den entsprechenden SQLSTATE.  
  
 Weitere Informationen über Statusfehlercodes finden Sie unter folgenden Themen:  
  
-   [Anhang A: ODBC-Fehlercodes](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [SQLSTATE-Zuordnungen](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](handling-errors-and-messages.md)  
  
  
