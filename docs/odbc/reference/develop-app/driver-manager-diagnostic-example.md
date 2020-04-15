---
title: Treiber-Manager-Diagnosebeispiel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 839095e5544cab73cdddd4f4b17a3d8d52136c9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305811"
---
# <a name="driver-manager-diagnostic-example"></a>Beispiel für die Diagnose des Treiber-Managers
Der Treiber-Manager kann auch Diagnosemeldungen generieren. Wenn z. B. eine Anwendung eine Option für ungültige Richtung an **SQLDataSources**übergeben hat, kann der Treiber-Manager die folgenden Werte aus **SQLGetDiagRec**formatieren und zurückgeben:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Da der Fehler im Treiber-Manager aufgetreten ist, wurden der Diagnosenachricht für den Hersteller ([Microsoft]) und dem Bezeichner ([ODBC Driver Manager]) Präfixe hinzugefügt.
