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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be63e9d78960e40ac5e9ee016d2cfd868d99a922
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305831"
---
# <a name="diagnostic-messages"></a>Diagnosemeldungen
Eine Diagnose Meldung wird mit jedem SQLSTATE zurückgegeben. Der gleiche SQLSTATE wird häufig mit einer Reihe von unterschiedlichen Meldungen zurückgegeben. Beispielsweise wird SQLSTATE 42000 (Syntax Fehler oder Zugriffsverletzung) für die meisten Fehler in der SQL-Syntax zurückgegeben. Allerdings wird jeder Syntax Fehler wahrscheinlich durch eine andere Nachricht beschrieben.  
  
 Beispiel Diagnosemeldungen werden in der Spalte Fehler in der Tabelle SQLStates in Anhang A und in jeder Funktion aufgelistet. Obwohl Treiber diese Nachrichten zurückgeben können, werden Sie wahrscheinlich die von der Datenquelle an Sie weiter gegebene Nachricht zurückgeben.  
  
 Anwendungen zeigen in der Regel Diagnosemeldungen für den Benutzer an, zusammen mit dem SQLSTATE-Fehlercode und dem nativen Fehlercode. Dadurch können Benutzer und Supportmitarbeiter die Ursache von Problemen ermitteln. Die Komponenten Informationen, die in die Nachricht eingebettet sind, sind besonders hilfreich.  
  
 Diagnosemeldungen stammen aus Datenquellen und Komponenten in einer ODBC-Verbindung, wie z. b. Treibern, Gateways und Treiber-Manager. Datenquellen unterstützen ODBC in der Regel nicht direkt. Wenn eine Komponente in einer ODBC-Verbindung folglich eine Nachricht von einer Datenquelle empfängt, muss Sie die Datenquelle als Quelle der Nachricht identifizieren. Er muss sich auch als die Komponente identifizieren, die die Nachricht empfangen hat.  
  
 Wenn die Quelle eines Fehlers oder einer Warnung eine Komponente selbst ist, muss diese in der Diagnose Meldung erläutert werden. Daher weist der Text der Nachrichten zwei verschiedene Formate auf. Bei Fehlern und Warnungen, die nicht in einer Datenquelle auftreten, muss die Diagnose Meldung folgendes Format aufweisen:  
  
 **[** *Hersteller-* **ID] [** *ODBC-Component-Identifier* **]** von der *Komponente bereitgestellter Text*  
  
 Für Fehler und Warnungen, die in einer Datenquelle auftreten, muss die Diagnose Meldung dieses Format verwenden:  
  
 **[** *Hersteller-ID* **] [** *ODBC-Component-Identifier* **] [** *Datenquellen-* ID **]** von der *Datenquelle bereitgestellter Text*  
  
 Die folgende Tabelle zeigt die Bedeutung der einzelnen Elemente.  
  
|Element|Bedeutung|  
|-------------|-------------|  
|*Hersteller-ID*|Identifiziert den Anbieter der Komponente, in der der Fehler oder die Warnung aufgetreten ist oder der den Fehler bzw. die Warnung direkt von der Datenquelle erhalten hat.|  
|*ODBC-Component-Identifier*|Identifiziert die Komponente, in der der Fehler oder die Warnung aufgetreten ist oder die den Fehler bzw. die Warnung direkt von der Datenquelle empfangen hat.|  
|*Datenquellen-Bezeichner*|Identifiziert die Datenquelle. Bei dateibasierten Treibern ist dies in der Regel ein Dateiformat (z. b. xbase [1] für DBMS-basierte Treiber). Dies ist das DBMS-Produkt.|  
|*von der Komponente bereitgestellter Text*|Wird von der ODBC-Komponente generiert.|  
|*von der Datenquelle bereitgestellter Text*|Wird von der Datenquelle generiert.|  
  
 [1] in diesem Fall fungiert der Treiber sowohl als Treiber als auch als Datenquelle.  
  
 Eckige Klammern (**[]**) müssen in der Nachricht enthalten sein und dürfen keine optionalen Elemente angeben.
