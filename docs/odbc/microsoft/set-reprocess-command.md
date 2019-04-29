---
title: Befehl SET REPROCESS | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41877986d5d0e8afdfb30841860df360efd26da0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63159371"
---
# <a name="set-reprocess-command"></a>SET REPROCESS-Befehl
Gibt an, wie viele oder wie lange eine Datei oder einen Datensatz nach dem Versuch nicht erfolgreich Sperren zu sperren.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>Argumente  
 UM *nAttempts*[Sekunden]  
 Gibt die Häufigkeit oder die Anzahl der Sekunden, um zu versuchen, einen Datensatz oder eine Datei zu sperren, sobald Sie versuchen, ein nicht erfolgreichen anfänglichen. Der Standardwert ist 0. Der maximale Wert ist 32.000.  
  
 Sekunden gibt an, dass Visual FoxPro Sperren einer Datei oder der Datensatz für *nAttempts* Sekunden. Es ist nur verfügbar, wenn *nAttempts* ist größer als 0 (null).  
  
 Z. B. wenn *nAttempts* 30, Visual FoxPro versucht, einen Datensatz zu sperren oder die Datei bis zu 30 Mal. Wenn Sie sich auch um Sekunden (Legen Sie erneut zu VERARBEITEN und 30 Sekunden) angeben, versucht Visual FoxPro fortlaufend, einen Datensatz oder eine Datei für bis zu 30 Sekunden zu sperren.  
  
 Wenn eine ON ERROR-Routine eingerichtet wurde, und versuchen, einen Befehl aus, um den Datensatz bzw. die Datei zu Sperren nicht erfolgreich sind, wird die ON ERROR-Routine ausgeführt. Jedoch wenn eine Funktion, die Sperre versucht, eine ON ERROR-Routine wird nicht ausgeführt, und die Funktion gibt "false" zurück (. F.).  
  
 Wenn eine ON ERROR-Routine nicht aktiv, ein Befehl versucht, den Datensatz bzw. die Datei zu sperren, und die Sperre kann nicht platziert werden, wird ein Fehler generiert. Wenn eine Funktion versucht, die Sperre, die Warnung wird nicht angezeigt, und die Funktion gibt "false" zurück (. F.).  
  
 Wenn *nAttempts* ist 0 (Standardwert) und Sie geben Sie einen Befehl oder eine Funktion, die versucht, einen Datensatz oder eine Datei zu sperren, Visual FoxPro versucht, den Datensatz zu sperren oder die Datei auf unbestimmte Zeit. Wenn der Eintrag oder Datei verfügbar ist, während Sie warten, zu sperren, wird die Sperre und die die systemmeldung deaktiviert ist. Versucht, eine Funktion, die Sperre, die Funktion gibt "true" zurück (. "T".).  
  
 Die ON ERROR-Routine hat Vorrang vor allen weitere Versuche, den Datensatz bzw. die Datei zu sperren, wenn eine ON ERROR-Routine aktiviert ist, und versucht, ein Befehl, den Datensatz bzw. die Datei zu sperren, ist. Die ON ERROR-Routine wird sofort ausgeführt. Visual FoxPro wird nicht versucht, zusätzlichen Eintrag oder Datei gesperrt, und die systemmeldung nicht angezeigt.  
  
 Wenn *nAttempts* ist 1, Visual FoxPro versucht, den Datensatz zu sperren oder die Datei auf unbestimmte Zeit und eine ON ERROR-Routine wird nicht ausgeführt.  
  
 Wenn eine Sperre, von einem anderen Benutzer auf den Datensatz bzw. die Datei, die Sie sperren möchten erteilt wurden, müssen Sie warten, bis der Benutzer die Sperre aufhebt.  
  
 STARTTYP  
 Gibt an, dass Visual FoxPro den Datensatz zu sperren oder die Datei auf unbestimmte Zeit. (Gruppe für die Aktualisierung-2 ist einen gleichwertigen Befehl.)  
  
## <a name="remarks"></a>Hinweise  
 Beim erste Versuch, einen Datensatz oder eine Datei gesperrt ist, nicht immer erfolgreich. In vielen Fällen ist ein Datensatz oder eine Datei von einem anderen Benutzer im Netzwerk gesperrt. Legen Sie erneut VERARBEITEN, bestimmt, ob es sich bei Visual FoxPro stellt weitere Versuche, den Datensatz bzw. die Datei zu sperren, wenn es sich bei der erste Versuch nicht erfolgreich ist. Sie können entweder Häufigkeit angeben, weitere Versuche erfolgen, oder für wie lange die Versuche erfolgen. Eine ON ERROR-Routine wirkt sich auf wie nicht erfolgreich sperren, die Versuche behandelt werden.
