---
title: Verwenden von Verbindungs Zeichenfolgen | Microsoft-Dokumentation
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
ms.openlocfilehash: 496fe10fbf49f4d712127e2e4122c50fa20ba2be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68044581"
---
# <a name="using-connection-strings"></a>Verwenden von Verbindungszeichenfolgen
Sie können eine Verbindungs Zeichenfolge verwenden, um eine Verbindung mit einer Visual FoxPro-Datenquelle herzustellen.  
  
 Wenn Sie z. b. eine Verbindung mit der Datenquelle Tastrade herstellen und die aktuelle Einstellung von exklusiv, die der Datenquelle zugeordnet ist, überschreiben möchten, verwenden Sie die folgende Zeichenfolge:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Eine Liste der Attribut Schlüsselwörter und-Werte, die Sie in die Verbindungs Zeichenfolge einschließen können, finden Sie unter [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Eine vollständige Erläuterung der Syntax der Verbindungs Zeichenfolge finden Sie unter [sqlbrowseconnetct](../../odbc/reference/syntax/sqlbrowseconnect-function.md) in der *ODBC Programmer es Reference*.
