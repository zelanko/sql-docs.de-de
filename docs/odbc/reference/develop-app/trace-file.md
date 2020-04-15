---
title: Ablaufverfolgungsdatei | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddd0ee24649592cf4a1a296a51404334145a3bab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298057"
---
# <a name="trace-file"></a>Ablaufverfolgungsdatei
Eine Anwendung gibt die Ablaufverfolgungsdatei an, indem sie entweder das **TraceFile-Schlüsselwort** im Registrierungseintrag Odbc.ini festlegt oder **SQLSetConnectAttr** mit dem SQL_ATTR_TRACEFILE-Verbindungsattribut aufruft. Wenn die Datei nicht vorhanden ist, wenn die Ablaufverfolgung aktiviert ist, erstellt der Treiber-Manager die Datei. Jede Anwendung sollte über eine eigene dedizierte Ablaufverfolgungsdatei verfügen, um Konflikte zu vermeiden. Eine Anwendung kann mehr als eine Ablaufverfolgungsdatei verwenden. Das Setupprogramm einer Anwendung kann dem Benutzer eine Auswahl an Ablaufverfolgungsdateien bieten. Wenn die Ablaufverfolgung dynamisch aktiviert ist, kann eine Anwendung auch Ablaufverfolgungsergebnisse anzeigen, anstatt sich in der Ablaufverfolgungsdatei zu protokollieren.  
  
 Die Ablaufverfolgungsdatei stellt ein Protokoll jedes ODBC-Funktionsaufrufs mit den Datentypen und Werten aller Argumente bereit. Es protokolliert alle Eingabefunktionen und alle zurückgegebenen Funktionen mit Rückgabecodes und Fehlerzuständen.  
  
 In ODBC *3.x*werden der Ablaufverfolgungs-DLL keine Parameter für Verbindungsfunktionen bereitgestellt.
