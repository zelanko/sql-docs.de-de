---
title: Protokollierte und nicht protokollierte Änderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3635fee71c92196cbc9408db1487e95da2b489ea
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718768"
---
# <a name="logged-vs-unlogged-modifications"></a>Vergleich von protokollierten und nicht protokollierten Änderungen
  Eine Anwendung kann anfordern, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber keine **Text**-, **ntext**-und **Image** -Änderungen protokolliert. Diese Option sollte jedoch mit Vorsicht eingesetzt werden. Er sollte nur für Situationen verwendet werden, in denen die **Text**-, **ntext**-oder **Image** -Daten nicht von entscheidender Bedeutung sind und Daten Besitzer bereit sind, die Fähigkeit zum Wiederherstellen von Daten für eine höhere Leistung abzuwägen.  
  
 Die Protokollierung von **Text**-, **ntext**-und **Image** -Änderungen wird gesteuert, indem [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) aufgerufen wird, wobei der- *Attribut* Parameter auf SQL_SOPT_SS_ TEXTPTR_LOGGING und *ValuePtr* auf SQL_TL_ON oder SQL_TL_OFF festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Text und Imagespalten](managing-text-and-image-columns.md)  
  
  
