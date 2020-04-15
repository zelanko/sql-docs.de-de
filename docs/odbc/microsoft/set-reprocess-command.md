---
title: SET REPROCESS Befehl | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET REPROCESS command [ODBC]
ms.assetid: b0708757-b1d7-42f3-8988-787f2a806b8b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5a7eb5fd19ca538c4f25077926567011ae133e54
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300830"
---
# <a name="set-reprocess-command"></a>SET REPROCESS-Befehl
Gibt an, wie oft oder für wie lange eine Datei oder ein Datensatz nach einem erfolglosen Sperrversuch gesperrt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>Argumente  
 TO *nAttempts*[SECONDS]  
 Gibt an, wie oft oder anzahl der Sekunden versucht werden soll, einen Datensatz oder eine Datei nach einem ersten erfolglosen Versuch zu sperren. Der Standardwert ist 0; der Maximalwert beträgt 32.000.  
  
 SECONDS gibt an, dass Visual FoxPro versucht, eine Datei oder einen Datensatz für *nAttempts* Sekunden zu sperren. Sie ist nur verfügbar, wenn *nAttempts* größer als Null ist.  
  
 Wenn *nAttempts* beispielsweise 30 Jahre alt ist, versucht Visual FoxPro, einen Datensatz oder eine Datei bis zu 30 Mal zu sperren. Wenn Sie auch SECONDS (SET REPROCESS TO 30 SECONDS) einschließen, versucht Visual FoxPro kontinuierlich, einen Datensatz oder eine Datei für bis zu 30 Sekunden zu sperren.  
  
 Wenn eine ON ERROR-Routine in Kraft ist und Versuche eines Befehls, den Datensatz oder die Datei zu sperren, fehlschlagen, wird die ON ERROR-Routine ausgeführt. Wenn jedoch eine Funktion die Sperre versucht, wird keine ON ERROR-Routine ausgeführt, und die Funktion gibt False (. F.).  
  
 Wenn eine ON ERROR-Routine nicht wirksam ist, ein Befehl versucht, den Datensatz oder die Datei zu sperren, und die Sperre nicht platziert werden kann, wird ein Fehler generiert. Wenn eine Funktion versucht, die Sperre zu platzieren, wird die Warnung nicht angezeigt, und die Funktion gibt False (. F.).  
  
 Wenn *nAttempts* 0 ist (der Standardwert) und Sie einen Befehl oder eine Funktion ausgeben, die versucht, einen Datensatz oder eine Datei zu sperren, versucht Visual FoxPro, den Datensatz oder die Datei auf unbestimmte Zeit zu sperren. Wenn der Datensatz oder die Datei während des Wartens zum Sperren verfügbar wird, wird die Sperre platziert, und die Systemnachricht wird gelöscht. Wenn eine Funktion versucht hat, die Sperre zu platzieren, gibt die Funktion True (zurück. T.).  
  
 Wenn eine ON ERROR-Routine wirksam ist und ein Befehl versucht, den Datensatz oder die Datei zu sperren, hat die ON ERROR-Routine Vorrang vor zusätzlichen Versuchen, den Datensatz oder die Datei zu sperren. Die ON ERROR-Routine wird sofort ausgeführt. Visual FoxPro versucht keine zusätzlichen Datensatz- oder Dateisperren und zeigt die Systemmeldung nicht an.  
  
 Wenn *nAttempts* 1 ist, versucht Visual FoxPro, den Datensatz oder die Datei auf unbestimmte Zeit zu sperren, und eine ON ERROR-Routine wird nicht ausgeführt.  
  
 Wenn eine Sperre von einem anderen Benutzer für den Datensatz oder die Datei, die Bzw. die Sie sperren möchten, platziert wurde, müssen Sie warten, bis der Benutzer die Sperre aufgehoben hat.  
  
 ZU AUTOMATISCH  
 Gibt an, dass Visual FoxPro versucht, den Datensatz oder die Datei auf unbestimmte Zeit zu sperren. (SET REPROCESS TO -2 ist ein gleichwertiger Befehl.)  
  
## <a name="remarks"></a>Bemerkungen  
 Der erste Versuch, einen Datensatz oder eine Datei zu sperren, ist nicht immer erfolgreich. Häufig wird ein Datensatz oder eine Datei von einem anderen Benutzer im Netzwerk gesperrt. SET REPROCESS bestimmt, ob Visual FoxPro zusätzliche Versuche unternimmt, den Datensatz oder die Datei zu sperren, wenn der erste Versuch fehlschlägt. Sie können angeben, wie oft zusätzliche Versuche unternommen werden oder wie lange die Versuche unternommen werden. Eine ON ERROR-Routine wirkt sich darauf aus, wie erfolglose Sperrversuche gehandhabt werden.
