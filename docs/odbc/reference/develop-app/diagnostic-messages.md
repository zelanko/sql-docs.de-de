---
title: Diagnosemeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic messages messages
- error messages [ODBC], diagnostic messages
- diagnostic messages [ODBC]
ms.assetid: 98027871-9901-476e-a722-ee58b7723c1f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 39ebda5de5820cdfd7333ad1d0997593922e0a4f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039892"
---
# <a name="diagnostic-messages"></a>Diagnosemeldungen
Eine diagnosemeldung wird mit jeder SQLSTATE zurückgegeben. Die gleiche SQLSTATE wird häufig mit einer Anzahl von unterschiedlichen Nachrichten zurückgegeben. SQLSTATE 42000 (Syntaxfehler oder zugriffsverletzung) wird z. B. für die meisten Fehler im SQL-Syntax zurückgegeben. Jede Syntaxfehler ist jedoch wahrscheinlich durch eine andere Meldung beschrieben werden.  
  
 Beispiel-diagnosemeldungen werden in der Error-Spalte in der Tabelle der SQLSTATEs in Anhang A und in jeder Funktion aufgeführt. Obwohl Treiber diese Meldungen zurückgegeben werden können, sind sie eher zurückgeben, alle Nachrichten werden von der Datenquelle übergeben wird.  
  
 Anwendungen anzeigen diagnosemeldungen in der Regel dem Benutzer zusammen mit den SQLSTATE und systemeigener Fehlercode. Dies hilft dem Benutzer und Support in Verbindung bestimmen, die Ursache von Problemen. Die Komponenteninformationen in der Meldung eingebetteten ist dies besonders hilfreich.  
  
 Diagnosemeldungen stammen aus Datenquellen und -Komponenten in eine ODBC-Verbindung wie Treiber, Gateways und der Treiber-Manager. Datenquellen unterstützen nicht in der Regel direkt ODBC. Wenn eine Komponente in eine ODBC-Verbindung eine Nachricht aus einer Datenquelle empfängt, müssen sie daher die Datenquelle als Quelle der Nachricht identifizieren. Sie müssen auch selbst als die Komponente kennzeichnen, die die Nachricht zu empfangen.  
  
 Wenn die Quelle der Warnung oder ein Fehler einer Komponente selbst ist, muss die diagnosemeldung diese erläutern. Der Text der Nachrichten hat daher zwei verschiedene Formate. Für Fehler und Warnungen, die nicht in einer Datenquelle auftreten, muss die diagnosemeldung dieses Format verwenden:  
  
 **[** *Hersteller-ID* **] [** *ODBC-Komponenten-ID* **]** *Komponente bereitgestellten Text*  
  
 Für Fehler und Warnungen, die in einer Datenquelle auftreten, muss die diagnosemeldung dieses Format verwenden:  
  
 **[** *Hersteller-ID* **] [** *ODBC-Komponenten-ID* **] [** *datenquellenbezeichner*  **]** *Data-Source-bereitgestellten-Text*  
  
 Die folgende Tabelle zeigt die Bedeutung der einzelnen Elemente.  
  
|Element|Bedeutung|  
|-------------|-------------|  
|*vendor-identifier*|Gibt den Hersteller der Komponente in der der Fehler oder die Warnung aufgetreten ist, oder, der den Fehler oder Warnung direkt aus der Datenquelle empfangen.|  
|*ODBC-Komponenten-ID*|Identifiziert die Komponente in der der Fehler oder die Warnung aufgetreten ist, oder, der den Fehler oder Warnung direkt aus der Datenquelle empfangen.|  
|*data-source-identifier*|Identifiziert die Datenquelle an. Für dateibasierte Treiber, dies ist normalerweise ein Dateiformat, z. B. Xbase [1] für die DBMS-basierten Treibern, ist dies das DBMS-Produkt.|  
|*component-supplied-text*|Von der ODBC-Komponente generiert.|  
|*data-source-supplied-text*|Von der Datenquelle generiert.|  
  
 [1] In diesem Fall wird der Treiber als sowohl der Treiber und der Datenquelle verwendet.  
  
 Eckige Klammern ( **[]** ) in der Nachricht enthalten sein müssen, und zeigen optionale Elemente.
