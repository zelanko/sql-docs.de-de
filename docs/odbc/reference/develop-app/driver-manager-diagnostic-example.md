---
title: Beispiel für Treiber-Manager-Diagnose | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305811"
---
# <a name="driver-manager-diagnostic-example"></a>Beispiel für die Diagnose des Treiber-Managers
Der Treiber-Manager kann auch Diagnosemeldungen generieren. Wenn eine Anwendung z. b. eine ungültige Richtungs Option an **SQLDataSources**übergeben hat, kann der Treiber-Manager die folgenden Werte von **SQLGetDiagRec**formatieren und zurückgeben:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Da der Fehler im Treiber-Manager aufgetreten ist, wurden der Diagnose Meldung für den Hersteller ([Microsoft]) und dessen Bezeichner ([ODBC Driver Manager]) Präfixe hinzugefügt.
