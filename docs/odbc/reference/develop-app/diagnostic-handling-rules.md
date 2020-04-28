---
title: Regeln für die Diagnose Behandlung | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305841"
---
# <a name="diagnostic-handling-rules"></a>Regeln der Diagnosebehandlung
Die folgenden Regeln steuern die Diagnose Behandlung in **SQLGetDiagRec** und **SQLGetDiagField**.  
  
 Für alle ODBC-Komponenten:  
  
-   Fehler oder Warnungen, die von einer anderen ODBC-Komponente empfangen wurden, dürfen nicht ersetzt, geändert oder maskiert werden.  
  
-   Kann einen zusätzlichen Statusdaten Satz hinzufügen, wenn Sie eine Diagnose Meldung von einer anderen ODBC-Komponente empfangen. Der hinzugefügte Datensatz muss der ursprünglichen Nachricht einen echten Informationswert hinzufügen.  
  
 Für die ODBC-Komponente, die eine Datenquelle direkt Durchschnitt stellen:  
  
-   Dem Hersteller Bezeichner, dessen Komponenten Bezeichner und dem Bezeichner der Datenquelle muss die von der Datenquelle empfangene Diagnose Nachricht vorangestellt werden.  
  
-   Der systemeigene Fehlercode der Datenquelle muss beibehalten werden.  
  
-   Die Diagnose Meldung der Datenquelle muss beibehalten werden.  
  
 Für jede ODBC-Komponente, die unabhängig von der Datenquelle einen Fehler oder eine Warnung generiert:  
  
-   Muss den korrekten SQLSTATE für den Fehler oder die Warnung angeben.  
  
-   Der Text der Diagnose Meldung muss generiert werden.  
  
-   Die Hersteller-ID und deren Komponenten Bezeichner müssen der Diagnose Meldung vorangestellt werden.  
  
-   Es muss ein nativer Fehlercode zurückgegeben werden, wenn ein solcher verfügbar und aussagekräftig ist.  
  
 Für die ODBC-Komponente, die eine Schnittstelle mit dem Treiber-Manager hat:  
  
-   Die Ausgabe Argumente von **SQLGetDiagRec** und **SQLGetDiagField**müssen initialisiert werden.  
  
-   Muss die Diagnoseinformationen formatieren und als Ausgabe Argumente von **SQLGetDiagRec** und **SQLGetDiagField** zurückgeben, wenn diese Funktion aufgerufen wird.  
  
 Für eine andere ODBC-Komponente als den Treiber-Manager:  
  
-   Der SQLSTATE muss basierend auf dem systemeigenen Fehler festgelegt werden. Bei dateibasierten Treibern und DBMS-basierten Treibern, von denen kein Gateway verwendet wird, muss der Treiber SQLSTATE festlegen. Bei DBMS-basierten Treibern, die ein Gateway verwenden, kann der Treiber oder ein Gateway, das ODBC unterstützt, den SQLSTATE-Wert festlegen.
