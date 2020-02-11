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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 95392367b70af3eb820f0943af5dc668783a3fe5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046959"
---
# <a name="driver-manager-diagnostic-example"></a>Beispiel für die Diagnose des Treiber-Managers
Der Treiber-Manager kann auch Diagnosemeldungen generieren. Wenn eine Anwendung z. b. eine ungültige Richtungs Option an **SQLDataSources**übergeben hat, kann der Treiber-Manager die folgenden Werte von **SQLGetDiagRec**formatieren und zurückgeben:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Da der Fehler im Treiber-Manager aufgetreten ist, wurden der Diagnose Meldung für den Hersteller ([Microsoft]) und dessen Bezeichner ([ODBC Driver Manager]) Präfixe hinzugefügt.
