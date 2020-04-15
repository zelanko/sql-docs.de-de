---
title: Arten von Deskriptoren | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], types
ms.assetid: ec20e446-e540-41ad-8559-d9c0a5b8358f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a6c7b55194eb61c1a909ced2296e4ad2050b674
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304891"
---
# <a name="types-of-descriptors"></a>Typen von Deskriptoren
Ein Deskriptor wird verwendet, um eine der folgenden Beschreibungen zu beschreiben:  
  
-   Ein Satz von null oder mehr Parametern. Ein Parameterdeskriptor kann verwendet werden, um zu beschreiben:  
  
    -   Der *Anwendungsparameterpuffer,* der entweder die von der Anwendung festgelegten dynamischen Eingabeargumente oder die dynamischen Ausgabeargumente nach der Ausführung einer **CALL-Anweisung** von SQL enthält.  
  
    -   Der *Implementierungsparameterpuffer*. Bei dynamischen Eingabeargumenten enthält dies dieselben Argumente wie der Anwendungsparameterpuffer nach jeder Datenkonvertierung, die die Anwendung angeben kann. Bei dynamischen Ausgabeargumenten enthält dies die zurückgegebenen Argumente vor jeder Datenkonvertierung, die die Anwendung angeben kann.  
  
     Für dynamische Eingabeargumente muss die Anwendung mit einem Anwendungsparameterdeskriptor arbeiten, bevor eine SQL-Anweisung ausgeführt wird, die dynamische Parametermarkierungen enthält. Sowohl für Eingabe- als auch für Ausgabe-Dynamische Argumente kann die Anwendung verschiedene Datentypen als die im Implementierungsparameterdeskriptor angeben, um eine Datenkonvertierung zu erreichen.  
  
-   Eine einzelne Zeile mit Datenbankdaten. Ein Zeilendeskriptor kann verwendet werden, um zu beschreiben:  
  
    -   Der *Implementierungszeilenpuffer,* der die Zeile aus der Datenbank enthält. (Diese Puffer enthalten konzeptionell Daten, die in die Datenbank geschrieben oder aus der Datenbank gelesen werden. Die gespeicherte Form der Datenbankdaten ist jedoch nicht angegeben. Eine Datenbank kann eine zusätzliche Konvertierung für die Daten aus ihrem Formular im Implementierungspuffer durchführen.)  
  
    -   Der *Anwendungszeilenpuffer,* der die der Anwendung angezeigte Datenzeile nach jeder Datenkonvertierung enthält, die die Anwendung angeben kann.  
  
     Die Anwendung arbeitet auf dem Anwendungszeilendeskriptor in jedem Fall, in dem Spaltendaten aus der Datenbank in Anwendungsvariablen angezeigt werden müssen. Um die Datenkonvertierung von Spaltendaten zu erreichen, kann die Anwendung andere Datentypen als die im Implementierungszeilendeskriptor angeben.  
  
 Die Deskriptortypen sind in der folgenden Tabelle zusammengefasst.  
  
|Puffertyp|Zeilen|Dynamische Parameter|  
|-----------------|----------|------------------------|  
|**Anwendungspuffer**|Anwendungszeilendeskriptor (ARD)|Anwendungsparameterdeskriptor (APD)|  
|**Implementierungspuffer**|Implementierungszeilendeskriptor (IRD)|Implementierungsparameterdeskriptor (IPD)|  
  
 Wenn die Anwendung für den Parameter oder die Zeilenpuffer unterschiedliche Datentypen in entsprechenden Datensätzen der Implementierungs- und Anwendungsdeskriptoren angibt, führt der Treiber die Datenkonvertierung durch, wenn er die Deskriptoren verwendet. Beispielsweise können numerische und Datumszeitwerte in Zeichenzeichenfolgenformatkonvertierte konvertiert werden. (Für gültige Konvertierungen siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Ein Deskriptor kann verschiedene Rollen ausführen. Verschiedene Anweisungen können jeden Deskriptor gemeinsam verwenden, den die Anwendung explizit zuweist. Ein Zeilendeskriptor in einer Anweisung kann als Parameterdeskriptor in einer anderen Anweisung dienen.  
  
 Es ist immer bekannt, ob ein gegebener Deskriptor ein Anwendungsdeskriptor oder ein Implementierungsdeskriptor ist, auch wenn der Deskriptor noch nicht in einem Datenbankvorgang verwendet wurde. Für die Deskriptoren, die die Implementierung implizit zuweist, zeichnet die Implementierung die vordefinierte Zeile relativ zum Anweisungshandle auf. Jeder Deskriptor, den die Anwendung durch aufrufen von **SQLAllocHandle** zuweist, ist ein Anwendungsdeskriptor.
