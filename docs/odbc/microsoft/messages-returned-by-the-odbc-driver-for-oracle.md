---
title: Vom ODBC-Treiber für Oracle zurückgegebene Nachrichten | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298860"
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Fehlermeldungen, die vom ODBC-Treiber für Oracle zurückgegeben wurden
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Wenn eine Oracle-Fehlermeldung verfügbar ist, wird sie zurückgegeben, denen die Tags [Microsoft], [ODBC Driver for Oracle] und [Oracle] vorangestellt werden. Andernfalls wird die Nachricht ohne das [Oracle]-Tag zurückgegeben, wie in den folgenden Beispielen:  
  
## <a name="oracle-error-message"></a>Oracle-Fehlermeldung:  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>ODBC-Treiber für Oracle-Fehlermeldung:  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
