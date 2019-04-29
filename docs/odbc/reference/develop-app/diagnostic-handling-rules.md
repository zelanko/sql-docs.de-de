---
title: Diagnose behandeln Regeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f59953dee77453bb8b453a40a36d17e865a1fe5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63034927"
---
# <a name="diagnostic-handling-rules"></a>Regeln der Diagnosebehandlung
Die folgenden Regeln bestimmen die diagnosebehandlung in **SQLGetDiagRec** und **SQLGetDiagField**.  
  
 Für alle ODBC-Komponenten:  
  
-   Muss nicht ersetzen, ändern oder maskieren, Fehler oder Warnungen, die von einer anderen ODBC-Komponente empfangen.  
  
-   Können einen zusätzlichen Status-Eintrag hinzufügen, beim Erhalt einer einer diagnosemeldung aus einer anderen ODBC-Komponente. Der ursprünglichen Nachricht muss der hinzugefügten Datensatz echten Wert hinzufügen.  
  
 Für den ODBC-Datenquelle Komponente, die direkt Schnittstellen:  
  
-   Müssen das Präfix der Hersteller-ID, die Komponenten­ID und der Datenquelle-Bezeichner, der die diagnosemeldung aus der Datenquelle empfangenen.  
  
-   Systemeigene Fehlercode für die Datenquelle muss beibehalten werden.  
  
-   Diagnosemeldung für die Datenquelle muss beibehalten werden.  
  
 Für jede ODBC-Komponente, die einen Fehler oder die Warnung unabhängig von der Datenquelle generiert:  
  
-   Müssen die richtigen SQLSTATE für den Fehler oder Warnung angeben.  
  
-   Muss den Text der diagnosemeldung zu generieren.  
  
-   Müssen die Anbieter-ID und die Komponentenbezeichner, der die diagnosemeldung Präfix voranstellen.  
  
-   Muss einen systemeigener Fehlercode, zurückgeben, wenn eine sinnvolle und verfügbar ist.  
  
 Für die ODBC-Komponente, die mit dem Treiber-Manager-Schnittstellen:  
  
-   Die Ausgabeargumente des muss initialisiert werden **SQLGetDiagRec** und **SQLGetDiagField**.  
  
-   Formatieren und die Diagnoseinformationen als Ausgabeargumente zurückgeben muss **SQLGetDiagRec** und **SQLGetDiagField** Wenn diese Funktion aufgerufen wird.  
  
 Für eine ODBC-Komponente als der Treiber-Manager:  
  
-   Basierend auf der systemeigene Fehler SQLSTATE muss festgelegt werden. Dateibasierte Treiber und DBMS-basierten Treibern, die einen Gateway nicht verwenden, muss der Treiber SQLSTATE festgelegt. Für DBMS-basierten Treibern, die einen Gateway verwenden, kann entweder der Treiber oder ein Gateway, die ODBC unterstützt den SQLSTATE festgelegt.
