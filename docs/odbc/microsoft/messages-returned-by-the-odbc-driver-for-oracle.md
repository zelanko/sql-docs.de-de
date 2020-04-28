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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8bdaf4238bd220987364a77aaa1af837885c6e6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298860"
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
