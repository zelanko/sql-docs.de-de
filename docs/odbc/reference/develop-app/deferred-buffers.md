---
title: Verzögerte Puffer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], deferred
- deferred buffers [ODBC]
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b071494697d21a37f4420889a8f60cc35fe3d8b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797198"
---
# <a name="deferred-buffers"></a>Zurückgestellte Puffer
Ein *verzögerte Puffer* ist eine, deren Wert, zu einem Zeitpunkt verwendet wird *nach* in einem Funktionsaufruf angegeben ist. Z. B. **SQLBindParameter** wird verwendet, um zu verknüpfen, oder *zu binden,* einen Datenpuffer mit einem Parameter in einer SQL-Anweisung. Die Anwendung gibt die Anzahl der Parameter und übergibt die Adresse, Byte-Länge und Typ des Puffers. Der Treiber speichert diese Informationen aber untersucht nicht den Inhalt des Puffers. Später, wenn die Anwendung die Anweisung ausgeführt wird, der Treiber Ruft die Informationen ab und wird verwendet, die Parameterdaten abzurufen und an die Datenquelle zu senden. Aus diesem Grund wird die Eingabe von Daten in den Puffer verzögert. Da verzögerte Puffer sind eine Funktion nicht angegeben und in einem anderen verwendet, ist es ein anwendungsprogrammierungsfehler Fehler um eine verzögerte Puffer freizugeben, während der Treiber noch vorhanden sein, erwartet; Weitere Informationen finden Sie unter [zuweisen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)weiter unten in diesem Abschnitt.  
  
 Sowohl Eingabe- und Ausgabepuffer können verzögert werden. In der folgende Tabelle werden die Verwendungen der verzögerte Puffer zusammengefasst. Beachten Sie, dass verzögerte Puffer gebunden, die zu einer Gruppe von Spalten mit angegeben werden **SQLBindCol**, und verzögerte Puffer an SQL-Anweisungsparameter gebunden werden mit **SQLBindParameter**.  
  
|Puffer verwenden|Typ|Mit angegeben wird|Verwendet von|  
|----------------|----------|--------------------|-------------|  
|Senden von Daten für Eingabeparameter|Verzögerte Eingabe|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Sendende von Daten zu aktualisieren, oder fügen Sie eine Zeile in einem Resultset festlegen|Verzögerte Eingabe|**SQLBindCol**|**SQLSetPos**|  
|Zurückgeben von Daten für die Ausgabe und Eingabe/Ausgabe-Parameter|Verzögerte Ausgabe|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Ergebnis zurückgegeben festlegen Daten|Verzögerte Ausgabe|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll-SQLSetPos**|
