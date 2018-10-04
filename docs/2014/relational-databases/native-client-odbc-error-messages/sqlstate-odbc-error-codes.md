---
title: SQLSTATE (ODBC-Fehlercodes) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6dbffb716887ed3ad7f5a34d12e806dedd713a30
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089820"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC-Fehlercodes)
  SQLSTATE stellt ausführliche Informationen über die Ursache einer Warnung oder eines Fehlers bereit. Für Fehler, die in der Datenquelle auftreten erkannt und zurückgegeben werden, indem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber die zurückgegebene systemeigene Fehlernummer dem entsprechenden SQLSTATE zugeordnet. Wenn eine systemeigene Fehlernummer kein ODBC-Fehlercodes an, ordnen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt SQLSTATE 42000 ("Syntaxfehler oder zugriffsverletzung"). Für Fehler, die vom Treiber erkannt werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber wird den entsprechenden SQLSTATE generiert.  
  
 Weitere Informationen über Statusfehlercodes finden Sie unter folgenden Themen:  
  
-   [Anhang A: ODBC-Fehlercodes](http://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [SQLSTATE-Zuordnungen](http://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Siehe auch  
 [Behandlung von Fehlern und Meldungen](handling-errors-and-messages.md)  
  
  
