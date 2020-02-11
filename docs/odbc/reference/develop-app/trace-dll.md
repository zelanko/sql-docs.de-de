---
title: Trace-dll | Microsoft-Dokumentation
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
ms.openlocfilehash: 6fe910c93beac676e5fb0f663b740c03a826c326
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985222"
---
# <a name="trace-dll"></a>Ablaufverfolgungs-DLL
Die dll, die die Ablauf Verfolgung ausführt, ist eine der ODBC-Kernkomponenten. Die Trace-dll wird derzeit als Beispiel-dll in der ODBC-Komponente des Windows SDK bereitgestellt und war zuvor das Microsoft Data Access Components (MDAC) SDK enthalten. Daher sind der Registrierungs Eintrag, die Schnittstelle und der Beispielcode für die Trace-dll verfügbar. Diese DLL kann durch eine von einem ODBC-Benutzer oder von einem Drittanbieter erstellte Ablaufverfolgungs-DLL ersetzt werden. Eine benutzerdefinierte Ablauf Verfolgungs-dll sollte einen anderen Namen als die ursprüngliche Beispiel-Trace-dll erhalten. Ablauf Verfolgungs-DLLs müssen im System Verzeichnis installiert werden, oder Sie können nicht geladen werden. Die Verbindungs Zeichenfolgen werden vom Treiber-Manager nicht an die Trace-dll übermittelt.  
  
 Die Trace-dll verfolgt Eingabeargumente, Ausgabe Argumente, verzögerte Argumente, Rückgabecodes und Sqlstates. Wenn die Ablauf Verfolgung aktiviert ist, ruft der Treiber-Manager die Ablauf Verfolgungs-dll an zwei Punkten auf: einmal nach dem Funktions Eintrag (vor der Argument Validierung) und erneut, kurz bevor die Funktion zurückgegeben wird.  
  
 Wenn eine Anwendung eine Funktion aufruft, ruft der Treiber-Manager eine Ablauf Verfolgungs Funktion in der Trace-dll auf, bevor die Funktion im Treiber aufgerufen oder der Aufruf selbst verarbeitet wird. Jede ODBC-Funktion verfügt über eine entsprechende Ablauf Verfolgungs Funktion (mit dem Präfix *Trace*), die mit der ODBC-Funktion identisch ist, mit Ausnahme des Namens. Wenn die Ablauf Verfolgungs Funktion aufgerufen wird, erfasst die Trace-dll die Eingabeargumente und gibt einen Rückgabecode zurück. Da die Trace-dll aufgerufen wird, bevor der Treiber-Manager Argumente überprüft, werden ungültige Funktionsaufrufe verfolgt, sodass Zustands Übergangs Fehler und ungültige Argumente protokolliert werden.  
  
 Nachdem die Ablauf Verfolgungs Funktion in der Trace-dll aufgerufen wurde, ruft der Treiber-Manager die ODBC-Funktion im Treiber auf. Anschließend ruft es die **tracereturn** -dll in der Trace-dll auf. Diese Funktion nimmt zwei Argumente an: den von der Trace-dll für die Ablauf Verfolgungs Funktion zurückgegebenen Wert und den Rückgabecode, der vom Treiber an den Treiber-Manager für die ODBC-Funktion zurückgegeben wird (oder den Wert, der vom Treiber-Manager selbst bei der Verarbeitung der Funktion zurückgegeben wird). Die Funktion verwendet den Wert, der für die Funktion Trace zurückgegeben wurde, um erfasste Eingabe Argument Werte zu bearbeiten. Der Code, der für die ODBC-Funktion zurückgegeben wird, wird in die Protokolldatei geschrieben (oder bei Aktivierung dynamisch angezeigt). Dabei werden die Ausgabe Argument Zeiger dereferenziert und die Ausgabe Argument Werte protokolliert.
