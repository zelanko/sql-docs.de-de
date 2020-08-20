---
description: Ablaufverfolgung
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
ms.openlocfilehash: 25a7a08fb5c5d2fb203151fb014bdc0edfd25746
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487483"
---
# <a name="tracing"></a>Ablaufverfolgung
Der ODBC-Treiber-Manager verfügt über eine Ablauf Verfolgungs Funktion, mit der die Abfolge von Funktionsaufrufen durch eine ODBC-Anwendung aufgezeichnet und in eine Protokolldatei umgewandelt werden kann. Die Ablauf Verfolgung wird von einer Trace-dll ausgeführt, die Aufrufe zwischen der Anwendung und dem Treiber-Manager sowie zwischen dem Treiber-Manager und dem Treiber erfasst. Diese Methode der Ablauf Verfolgung ersetzt die vom ODBC 2 *. x* -Treiber-Manager ausgeführte Ablauf Verfolgung und die in ODBC 2 *. x* durchgeführte Ablauf Verfolgung durch ODBC Spy.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Ablaufverfolgungs-DLL](../../../odbc/reference/develop-app/trace-dll.md)  
  
-   [Ablauf Verfolgungs Datei](../../../odbc/reference/develop-app/trace-file.md)  
  
-   [Aktivieren der Ablaufverfolgung](../../../odbc/reference/develop-app/enabling-tracing.md)  
  
-   [Dynamische Ablaufverfolgung](../../../odbc/reference/develop-app/dynamic-tracing.md)
