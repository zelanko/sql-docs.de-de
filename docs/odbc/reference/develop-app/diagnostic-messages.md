---
title: Diagnosemeldungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305831"
---
# <a name="diagnostic-messages"></a>Diagnosemeldungen
Mit jedem SQLSTATE wird eine Diagnosemeldung zurückgegeben. Derselbe SQLSTATE wird häufig mit einer Reihe unterschiedlicher Nachrichten zurückgegeben. SqlSTATE 42000 (Syntaxfehler oder Zugriffsverletzung) wird z. B. für die meisten Fehler in der SQL-Syntax zurückgegeben. Jeder Syntaxfehler wird jedoch wahrscheinlich durch eine andere Meldung beschrieben.  
  
 Beispieldiagnosemeldungen werden in der Spalte Fehler in der Tabelle von SQLSTATEs in Anhang A und in jeder Funktion aufgeführt. Obwohl Treiber diese Nachrichten zurückgeben können, geben sie mit größerer Wahrscheinlichkeit jede Nachricht zurück, die von der Datenquelle an sie übergeben wird.  
  
 Anwendungen zeigen dem Benutzer in der Regel Diagnosemeldungen zusammen mit dem SQLSTATE- und systemeigenen Fehlercode an. Auf diese Weise können Benutzer und Supportmitarbeiter die Ursache von Problemen ermitteln. Die in die Nachricht eingebetteten Komponenteninformationen sind dabei besonders hilfreich.  
  
 Diagnosemeldungen stammen von Datenquellen und Komponenten in einer ODBC-Verbindung, z. B. Treiber, Gateways und dem Treiber-Manager. In der Regel unterstützen Datenquellen ODBC nicht direkt. Wenn eine Komponente in einer ODBC-Verbindung eine Nachricht von einer Datenquelle empfängt, muss sie daher die Datenquelle als Quelle der Nachricht identifizieren. Sie muss sich auch als die Komponente identifizieren, die die Nachricht empfangen hat.  
  
 Wenn die Ursache eines Fehlers oder einer Warnung eine Komponente selbst ist, muss dieDiagnosemeldung dies erklären. Daher hat der Text von Nachrichten zwei verschiedene Formate. Bei Fehlern und Warnungen, die nicht in einer Datenquelle auftreten, muss die Diagnosemeldung dieses Format verwenden:  
  
 **[** *Vendor-Identifier* **][** *ODBC-component-identifier* **]** *Komponenten-Liefertext*  
  
 Bei Fehlern und Warnungen, die in einer Datenquelle auftreten, muss die Diagnosemeldung dieses Format verwenden:  
  
 **[** *Vendor-Identifier* **][** *ODBC-component-identifier* **][** *data-source-identifier* **]** *data-source-supplied-text*  
  
 Die folgende Tabelle zeigt die Bedeutung der einzelnen Elemente.  
  
|Element|Bedeutung|  
|-------------|-------------|  
|*Vendor-Id*|Identifiziert den Anbieter der Komponente, in der der Fehler oder die Warnung aufgetreten ist oder die den Fehler oder die Warnung direkt aus der Datenquelle erhalten hat.|  
|*ODBC-Komponenten-Bezeichner*|Identifiziert die Komponente, in der der Fehler oder die Warnung aufgetreten ist oder die den Fehler oder die Warnung direkt von der Datenquelle empfangen hat.|  
|*Datenquellen-Bezeichner*|Identifiziert die Datenquelle. Bei dateibasierten Treibern ist dies in der Regel ein Dateiformat, z. B. Xbase[1] Für DBMS-basierte Treiber ist dies das DBMS-Produkt.|  
|*Von Komponenten gelieferter Text*|Generiert von der ODBC-Komponente.|  
|*Von der Datenquelle bereitgestellten Text*|Wird von der Datenquelle generiert.|  
  
 [1] In diesem Fall fungiert der Treiber sowohl als Treiber als auch als Datenquelle.  
  
 Klammern (**[ ]**) müssen in der Nachricht enthalten sein und keine optionalen Elemente anzeigen.
