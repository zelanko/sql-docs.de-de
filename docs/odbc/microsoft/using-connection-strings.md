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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9083414503606720a40d372ed883a140953dc415
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307591"
---
# <a name="using-connection-strings"></a>Verwenden von Verbindungszeichenfolgen
Sie können eine Verbindungs Zeichenfolge verwenden, um eine Verbindung mit einer Visual FoxPro-Datenquelle herzustellen.  
  
 Wenn Sie z. b. eine Verbindung mit der Datenquelle Tastrade herstellen und die aktuelle Einstellung von exklusiv, die der Datenquelle zugeordnet ist, überschreiben möchten, verwenden Sie die folgende Zeichenfolge:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Eine Liste der Attribut Schlüsselwörter und-Werte, die Sie in die Verbindungs Zeichenfolge einschließen können, finden Sie unter [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Eine vollständige Erläuterung der Syntax der Verbindungs Zeichenfolge finden Sie unter [sqlbrowseconnetct](../../odbc/reference/syntax/sqlbrowseconnect-function.md) in der *ODBC Programmer es Reference*.
