---
title: Ablauf Verfolgung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], about tracing
- driver manager [ODBC], tracing
ms.assetid: 77ed4c6c-d976-4eb2-8526-a12697b0ef83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a08047409b203916fe5403cf28802d8570647cf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298047"
---
# <a name="tracing"></a>Ablaufverfolgung
Der ODBC-Treiber-Manager verfügt über eine Ablauf Verfolgungs Funktion, mit der die Abfolge von Funktionsaufrufen durch eine ODBC-Anwendung aufgezeichnet und in eine Protokolldatei umgewandelt werden kann. Die Ablauf Verfolgung wird von einer Trace-dll ausgeführt, die Aufrufe zwischen der Anwendung und dem Treiber-Manager sowie zwischen dem Treiber-Manager und dem Treiber erfasst. Diese Methode der Ablauf Verfolgung ersetzt die vom ODBC 2 *. x* -Treiber-Manager ausgeführte Ablauf Verfolgung und die in ODBC 2 *. x* durchgeführte Ablauf Verfolgung durch ODBC Spy.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Ablaufverfolgungs-DLL](../../../odbc/reference/develop-app/trace-dll.md)  
  
-   [Ablauf Verfolgungs Datei](../../../odbc/reference/develop-app/trace-file.md)  
  
-   [Aktivieren der Ablaufverfolgung](../../../odbc/reference/develop-app/enabling-tracing.md)  
  
-   [Dynamische Ablaufverfolgung](../../../odbc/reference/develop-app/dynamic-tracing.md)
