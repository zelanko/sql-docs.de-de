---
title: Vom ODBC-Treiber für Oracle zurückgegebene Nachrichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bb2fc54692a77441bb2516ad72c0c44951152f56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68045182"
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Fehlermeldungen, die vom ODBC-Treiber für Oracle zurückgegeben wurden
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Wenn eine Oracle-Fehlermeldung verfügbar ist, wird Sie mit vorangestellten [Microsoft], [ODBC Driver for Oracle]-und [Oracle]-Tags zurückgegeben. Andernfalls wird die Nachricht ohne das [Oracle]-Tag zurückgegeben, wie in den folgenden Beispielen gezeigt:  
  
## <a name="oracle-error-message"></a>Oracle-Fehlermeldung:  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>ODBC-Treiber für Oracle-Fehlermeldung:  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
