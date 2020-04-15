---
title: Ablaufverfolgungs-DLL | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e1f9dc57415ad9865ca1b2ad02487b62a93f18f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298070"
---
# <a name="trace-dll"></a>Ablaufverfolgungs-DLL
Die DLL, die die Ablaufverfolgung durchführt, ist eine der ODBC-Kernkomponenten. Die Ablaufverfolgungs-DLL wird derzeit als Beispiel-DLL in der ODBC-Komponente des Windows SDK bereitgestellt und war zuvor im Microsoft Data Access Components (MDAC)-SDK enthalten. Daher sind der Registrierungseintrag, die Schnittstelle und der Beispielcode für die Ablaufverfolgungs-DLL verfügbar. Diese DLL kann durch eine Ablaufverfolgungs-DLL ersetzt werden, die entweder von einem ODBC-Benutzer oder einem Drittanbieter erstellt wird. Eine benutzerdefinierte Ablaufverfolgungs-DLL sollte einen anderen Namen als die ursprüngliche Beispielablaufverfolgungs-DLL erhalten. Ablaufverfolgungs-DLLs müssen im Systemverzeichnis installiert sein, oder sie können nicht geladen werden. Die Verbindungszeichenfolgen werden vom Treiber-Manager nicht an die Ablaufverfolgungs-DLL übergeben.  
  
 Die Ablaufverfolgungs-DLL verfolgt Eingabeargumente, Ausgabeargumente, verzögerte Argumente, Rückgabecodes und SQLSTATEs. Wenn die Ablaufverfolgung aktiviert ist, ruft der Treiber-Manager die Ablaufverfolgungs-DLL an zwei Punkten auf: einmal nach Funktionseingabe (vor der Argumentüberprüfung) und erneut kurz bevor die Funktion zurückkehrt.  
  
 Wenn eine Anwendung eine Funktion aufruft, ruft der Treiber-Manager eine Ablaufverfolgungsfunktion in der Ablaufverfolgungs-DLL auf, bevor die Funktion im Treiber aufgerufen wird oder der Aufruf selbst verarbeitet wird. Jede ODBC-Funktion verfügt über eine entsprechende Ablaufverfolgungsfunktion (voranpräfix *mit Trace*), die mit der ODBC-Funktion mit Ausnahme des Namens identisch ist. Wenn die Ablaufverfolgungsfunktion aufgerufen wird, erfasst die Ablaufverfolgungs-DLL die Eingabeargumente und gibt einen Rückgabecode zurück. Da die Ablaufverfolgungs-DLL aufgerufen wird, bevor der Treiber-Manager Argumente überprüft, werden ungültige Funktionsaufrufe nachverfolgt, sodass Statusübergangsfehler und ungültige Argumente protokolliert werden.  
  
 Nach dem Aufruf der Ablaufverfolgungsfunktion in der Ablaufverfolgungs-DLL ruft der Treiber-Manager die ODBC-Funktion im Treiber auf. Anschließend wird **TraceReturn** in der Ablaufverfolgungs-DLL auf. Diese Funktion verwendet zwei Argumente: den Von der Ablaufverfolgungs-DLL für die Ablaufverfolgungsfunktion zurückgegebenen Wert und den Rückgabecode, den der Treiber an den Treiber-Manager für die ODBC-Funktion zurückgibt (oder den Vom Treiber-Manager selbst zurückgegebenen Wert, wenn er die Funktion verarbeitet hat). Die Funktion verwendet den für die Ablaufverfolgungsfunktion zurückgegebenen Wert, um erfasste Eingabeargumentwerte zu bearbeiten. Es schreibt den für die ODBC-Funktion zurückgegebenen Code in die Protokolldatei (oder zeigt ihn dynamisch an, sofern dieser aktiviert ist). Es dereferenziert die Ausgabeargumentzeiger und protokolliert die Ausgabeargumentwerte.
