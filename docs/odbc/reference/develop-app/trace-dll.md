---
title: Ablaufverfolgungs-DLL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace DLLs [ODBC]
- tracing options [ODBC], trace DLLs
ms.assetid: 5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7a99f6c2960600d62a789471f68c1f5da89ae8c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63148871"
---
# <a name="trace-dll"></a>Ablaufverfolgungs-DLL
Die DLL, die Ablaufverfolgung ist eine ODBC-Kernkomponenten. Die Ablaufverfolgung, die DLL derzeit bereitgestellt wird, wie eine DLL-Beispiel in der ODBC-Komponente des Windows SDK und wurde, enthalten früher Microsoft Data Access Components (MDAC) SDK. Aus diesem Grund sind die Registrierungseintrag, Benutzeroberfläche und Beispielcode für die Ablaufverfolgung DLL verfügbar. Diese DLL-Datei kann von einer Ablaufverfolgung erzeugten entweder eine ODBC-Benutzer oder ein Drittanbieter-DLL ersetzt werden. Eine benutzerdefinierte DLL-Ablaufverfolgung sollte einen anderen Namen als die ursprüngliche Beispiel Ablaufverfolgung DLL angegeben werden. Trace-DLLs im Verzeichnis Systems installiert werden, oder sie können nicht geladen. Die Verbindungszeichenfolgen werden nicht in die Ablaufverfolgung DLL vom Treiber-Manager übergeben.  
  
 Die DLL-Ablaufverfolgung verfolgt input-Argumente, Ausgabeargumente, verzögerte Argumente, Rückgabecodes und SQLSTATEs. Wenn die Ablaufverfolgung aktiviert ist, ruft der Treiber-Manager die Ablaufverfolgungs-DLL an zwei Punkten: einmal beim Funktionseinstieg (vor der argumentüberprüfung) und noch vor der Rückgabe der Funktion.  
  
 Wenn eine Anwendung eine Funktion aufruft, ruft der Treiber-Manager eine Ablaufverfolgungsfunktion in der Ablaufverfolgung DLL vor dem Aufrufen der Funktion im Treiber oder den Aufruf selbst verarbeiten. Jede ODBC-Funktion hat keine entsprechende Ablaufverfolgungsfunktion (mit dem Präfix *Ablaufverfolgung*), die an die ODBC-Funktion, mit Ausnahme von den Namen identisch ist. Wenn die Ablaufverfolgungsfunktion aufgerufen wird, wird die Ablaufverfolgung DLL erfasst die Eingabeargumente und einen Rückgabecode gibt. Da die Ablaufverfolgung DLL aufgerufen wird, bevor der Treiber-Manager Argumente überprüft, werden ungültige Funktionsaufrufe nachverfolgt, damit "Übergang Error" und "wurden ungültige Argumente protokolliert werden.  
  
 Nach dem Aufruf der Ablaufverfolgungsfunktion in der Ablaufverfolgung DLL, ruft der Treiber-Manager die ODBC-Funktion im Treiber. Es ruft dann **TraceReturn** in der Ablaufverfolgung DLL. Diese Funktion akzeptiert zwei Argumente: den Rückgabewert von der DLL-Ablaufverfolgung für die Ablaufverfolgungsfunktion, und den Rückgabecode, der vom Treiber zurückgegebene, um die Treiber-Managers für die ODBC-Funktion (oder der Wert, der vom Treiber-Manager selbst zurückgegeben, wenn er die Funktion verarbeitet). Die Funktion verwendet den für die Ablaufverfolgungsfunktion zurückgegebenen Wert um erfassten Eingabeargument Werte zu bearbeiten. Schreibt den Code für die ODBC-Funktion zurückgegeben wird, in die Protokolldatei (oder es zeigt dynamisch an, wenn, aktiviert ist). Es hebt den Verweis auf die argumentzeiger Ausgabe und die ausgabeargumentwerte protokolliert.
