---
description: Verwenden von Verbindungszeichenfolgen
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
ms.openlocfilehash: 3ae8c3b1eda098a506d273f0d7baafec40985813
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471352"
---
# <a name="using-connection-strings"></a>Verwenden von Verbindungszeichenfolgen
Sie können eine Verbindungs Zeichenfolge verwenden, um eine Verbindung mit einer Visual FoxPro-Datenquelle herzustellen.  
  
 Wenn Sie z. b. eine Verbindung mit der Datenquelle Tastrade herstellen und die aktuelle Einstellung von exklusiv, die der Datenquelle zugeordnet ist, überschreiben möchten, verwenden Sie die folgende Zeichenfolge:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Eine Liste der Attribut Schlüsselwörter und-Werte, die Sie in die Verbindungs Zeichenfolge einschließen können, finden Sie unter [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Eine vollständige Erläuterung der Syntax der Verbindungs Zeichenfolge finden Sie unter [sqlbrowseconnetct](../../odbc/reference/syntax/sqlbrowseconnect-function.md) in der *ODBC Programmer es Reference*.
