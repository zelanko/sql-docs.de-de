---
title: Verwenden von Verbindungszeichenfolgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77bc54f857e04f31ccb982ca40b3ed6334664870
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633205"
---
# <a name="using-connection-strings"></a>Verwenden von Verbindungszeichenfolgen
Sie können eine Verbindungszeichenfolge für die Verbindung mit einer Visual FoxPro-Datenquelle verwenden.  
  
 Um eine Verbindung herzustellen, auf die Datenquelle TasTrade und außer Kraft setzen, die die aktuelle Einstellung der exklusiv mit der Datenquelle verknüpft ist, würden Sie z. B. die Zeichenfolge verwenden:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Eine Liste der Attribut-Schlüsselwörter und der Werte, die Sie in der Verbindungszeichenfolge enthalten können, finden Sie unter [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Eine vollständige Erläuterung der Syntax für Verbindungszeichenfolgen finden Sie unter [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) in die *ODBC Programmer's Reference*.
