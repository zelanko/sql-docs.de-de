---
title: Beispiel für die Diagnose von dateibasierten Treibern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f09e4f4758b6276836b08f02b24fb31dd1fadc7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305638"
---
# <a name="file-based-driver-diagnostic-example"></a>Beispiel für die Diagnose des dateibasierten Treibers
Ein Datei basierter Treiber fungiert sowohl als ODBC-Treiber als auch als Datenquelle. Daher können Fehler und Warnungen sowohl als Komponente in einer ODBC-Verbindung als auch als Datenquelle generiert werden. Da es sich auch um die Komponente handelt, die eine Schnittstelle mit dem Treiber-Manager hat, werden Argumente für **SQLGetDiagRec**formatiert und zurückgegeben.  
  
 Wenn beispielsweise ein Microsoft®-Treiber für dBASE nicht genügend Arbeitsspeicher zuordnen konnte, werden möglicherweise die folgenden Werte von **SQLGetDiagRec**zurückgegeben:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Da dieser Fehler nicht mit der Datenquelle zusammenhängt, hat der Treiber der Diagnose Meldung für den Hersteller ([Microsoft]) und den Treiber ([ODBC-dBase-Treiber]) nur Präfixe hinzugefügt.  
  
 Wenn der Treiber die Datei Employee. dbf nicht finden konnte, werden möglicherweise die folgenden Werte von **SQLGetDiagRec**zurückgegeben:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Da dieser Fehler mit der Datenquelle verknüpft war, hat der Treiber der Diagnose Meldung das Dateiformat der Datenquelle ([dBASE]) als Präfix hinzugefügt. Da der Treiber auch die Komponente war, die mit der Datenquelle interstand, wurden dem Hersteller ([Microsoft]) und dem Treiber ([ODBC-dBase-Treiber]) Präfixe hinzugefügt.
