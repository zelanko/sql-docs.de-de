---
title: Verwenden von Verbindungszeichenfolgen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307591"
---
# <a name="using-connection-strings"></a>Verwenden von Verbindungszeichenfolgen
Sie können eine Verbindungszeichenfolge verwenden, um eine Verbindung mit einer Visual FoxPro-Datenquelle herzustellen.  
  
 Um beispielsweise eine Verbindung mit der TasTrade-Datenquelle herzustellen und die aktuelle Einstellung exklusiv zu überschreiben, die der Datenquelle zugeordnet ist, verwenden Sie die Zeichenfolge:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Eine Liste der Attributschlüsselwörter und -werte, die Sie in die Verbindungszeichenfolge aufnehmen können, finden Sie unter [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Eine vollständige Erläuterung der Verbindungszeichenfolgensyntax finden Sie unter [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) in der *ODBC-Programmiererreferenz*.
