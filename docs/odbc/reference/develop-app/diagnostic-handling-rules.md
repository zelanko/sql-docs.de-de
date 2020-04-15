---
title: Diagnose-Handhabungsregeln | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f7f9d19a5a369e9da0efbc0d62f8e556b0597c1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305841"
---
# <a name="diagnostic-handling-rules"></a>Regeln der Diagnosebehandlung
Die folgenden Regeln regeln die Diagnosebehandlung in **SQLGetDiagRec** und **SQLGetDiagField**.  
  
 Für alle ODBC-Komponenten:  
  
-   Fehler oder Warnungen, die von einer anderen ODBC-Komponente empfangen wurden, dürfen nicht ersetzt, geändert oder maskiert werden.  
  
-   Kann einen zusätzlichen Statusdatensatz hinzufügen, wenn eine Diagnosemeldung von einer anderen ODBC-Komponente empfangen wird. Der hinzugefügte Datensatz muss der ursprünglichen Nachricht einen echten Informationswert hinzufügen.  
  
 Für die ODBC-Komponente, die direkt mit einer Datenquelle überdies steht:  
  
-   Muss dem Herstellerbezeichner, dem Komponentenbezeichner und dem Bezeichner der Datenquelle der Diagnosenachricht, die sie von der Datenquelle empfängt, vorangestellt werden.  
  
-   Muss den systemeigenen Fehlercode der Datenquelle beibehalten.  
  
-   Muss die Diagnosemeldung der Datenquelle beibehalten.  
  
 Für jede ODBC-Komponente, die unabhängig von der Datenquelle einen Fehler oder eine Warnung generiert:  
  
-   Muss die richtige SQLSTATE für den Fehler oder die Warnung angeben.  
  
-   Muss den Text der Diagnosenachricht generieren.  
  
-   Muss der Diagnosemeldung den Lieferantenbezeichner und den Komponentenbezeichner voranlegen.  
  
-   Muss einen systemeigenen Fehlercode zurückgeben, sofern ein systemeigener Fehlercode verfügbar und aussagekräftig ist.  
  
 Für die ODBC-Komponente, die mit dem Treiber-Manager in Verbindung ist:  
  
-   Muss die Ausgabeargumente von **SQLGetDiagRec** und **SQLGetDiagField**initialisieren.  
  
-   Die Diagnoseinformationen müssen als Ausgabeargumente von **SQLGetDiagRec** und **SQLGetDiagField** formatiert und zurückgegeben werden, wenn diese Funktion aufgerufen wird.  
  
 Für eine andere ODBC-Komponente als den Treiber-Manager:  
  
-   Muss SQLSTATE basierend auf dem systemeigenen Fehler festlegen. Für dateibasierte Treiber und DBMS-basierte Treiber, die kein Gateway verwenden, muss der Treiber SQLSTATE festlegen. Für DBMS-basierte Treiber, die ein Gateway verwenden, kann entweder der Treiber oder ein Gateway, das ODBC unterstützt, SQLSTATE festlegen.
