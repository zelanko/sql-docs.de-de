---
title: Befehl "neu verarbeiten" festlegen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300830"
---
# <a name="set-reprocess-command"></a>SET REPROCESS-Befehl
Gibt an, wie oft oder wie lange eine Datei oder ein Datensatz nach einem erfolglosen Sperrversuch gesperrt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>Argumente  
 Zu *nattempts*[Sekunden]  
 Gibt die Anzahl von Sekunden an, die versucht, einen Datensatz oder eine Datei nach einem anfänglichen erfolglosen Versuch zu sperren. Der Standardwert ist 0 (null). der Höchstwert ist 32.000.  
  
 Seconds gibt an, dass Visual FoxPro versucht, eine Datei oder einen Datensatz für *nattempts* Sekunden zu sperren. Sie ist nur verfügbar, wenn *nattempts* größer als 0 (null) ist.  
  
 Wenn *nattempts* z. b. 30 ist, versucht Visual FoxPro einen Datensatz oder eine Datei bis zu 30-Mal zu sperren. Wenn Sie auch Sekunden einschließen (Set Reprocess to 30 seconds), versucht Visual FoxPro fortlaufend, einen Datensatz oder eine Datei für bis zu 30 Sekunden zu sperren.  
  
 Wenn eine On-Error-Routine wirksam ist und wenn versucht wird, den Datensatz oder die Datei zu sperren, wird die On Error-Routine ausgeführt. Wenn jedoch eine Funktion die Sperre versucht, wird eine On Error-Routine nicht ausgeführt, und die Funktion gibt false zurück (. F.).  
  
 Wenn eine On-Error-Routine nicht wirksam ist, versucht ein Befehl, den Datensatz oder die Datei zu sperren, und die Sperre kann nicht platziert werden. es wird ein Fehler generiert. Wenn eine Funktion versucht, die Sperre zu platzieren, wird die Warnung nicht angezeigt, und die Funktion gibt false zurück. F.).  
  
 Wenn *nattempts* den Wert 0 (Standardwert) hat und Sie einen Befehl oder eine Funktion ausgeben, der versucht, einen Datensatz oder eine Datei zu sperren, versucht Visual FoxPro unbegrenzt, den Datensatz oder die Datei zu sperren. Wenn der Datensatz oder die Datei für das Sperren verfügbar ist, während Sie warten, wird die Sperre abgelegt und die Systemmeldung gelöscht. Wenn eine Funktion versucht hat, die Sperre zu platzieren, gibt die Funktion true zurück. T.).  
  
 Wenn eine On-Error-Routine wirksam ist und ein Befehl versucht, den Datensatz oder die Datei zu sperren, hat die On Error-Routine Vorrang vor zusätzlichen versuchen, den Datensatz oder die Datei zu sperren. Die On Error-Routine wird sofort ausgeführt. Visual FoxPro versucht nicht, zusätzliche Daten Satz-oder Dateisperren zu übernehmen, und die Systemmeldung wird nicht angezeigt.  
  
 Wenn *nattempts* den Wert 1 hat, versucht Visual FoxPro unbegrenzt, den Datensatz oder die Datei zu sperren, und eine On Error-Routine wird nicht ausgeführt.  
  
 Wenn eine Sperre von einem anderen Benutzer für den Daten Satz oder die Datei, die Sie sperren möchten, festgelegt wurde, müssen Sie warten, bis der Benutzer die Sperre freigibt.  
  
 in automatisch  
 Gibt an, dass Visual FoxPro unbegrenzt versucht, den Datensatz oder die Datei zu sperren. (Set Reprocess to-2 ist ein entsprechender Befehl.)  
  
## <a name="remarks"></a>Bemerkungen  
 Der erste Versuch, einen Datensatz oder eine Datei zu sperren, ist nicht immer erfolgreich. Häufig wird ein Datensatz oder eine Datei von einem anderen Benutzer im Netzwerk gesperrt. Set Reprocess bestimmt, ob Visual FoxPro zusätzliche Versuche zum Sperren des Datensatzes oder der Datei durchführt, wenn der anfängliche Versuch nicht erfolgreich war. Sie können entweder angeben, wie oft zusätzliche Versuche unternommen werden oder wie lange die Versuche unternommen werden. Eine On Error-Routine wirkt sich darauf aus, wie nicht erfolgreiche Sperr Versuche verarbeitet werden.
