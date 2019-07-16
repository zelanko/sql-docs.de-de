---
title: Typen von Deskriptoren | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d9d4a7572131afeeb0017d3773b72d899052b32
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087793"
---
# <a name="types-of-descriptors"></a>Typen von Deskriptoren
Ein Deskriptor wird verwendet, um einen der folgenden zu beschreiben:  
  
-   Ein Satz von NULL oder mehr Parameter. Ein Parameterdeskriptor kann verwendet werden, um zu beschreiben:  
  
    -   Die *Anwendung Parameterpuffer* die entweder die Eingabeargumente dynamische als Satz enthält, von der Anwendung oder die dynamische Ausgabeargumente nach der Ausführung einer **Aufrufen** SQL-Anweisung.  
  
    -   Die *Implementierung Parameterpuffer*. Für dynamische Eingabeargumente enthält die gleichen Argumente wie der Anwendung Parameterpuffer nach der Datenkonvertierung, die die Anwendung angeben kann. Für dynamische Ausgabeargumente enthält die zurückgegebene Argumente, bevor jede Datenkonvertierung, die die Anwendung angeben kann.  
  
     Für dynamische Eingabeargumente muss die Anwendung auf einem anwendungsparameterdeskriptor ausgeführt, vor dem Ausführen einer SQL-Anweisung, die Marker dynamischer Parameter enthält. Für Eingabe- und dynamische Argumente kann die Anwendung unterschiedliche Datentypen aus den IPD zum Erreichen der Datenkonvertierung angeben.  
  
-   Eine einzelne Zeile von Datenbankdaten. Ein Deskriptor für die Zeile kann verwendet werden, um zu beschreiben:  
  
    -   Die *Implementierung Zeilenpuffer,* enthält die Zeile aus der Datenbank. (Diese Puffer vom Konzept her Daten enthalten, wie in geschrieben oder aus der Datenbank gelesen. Die gespeicherten Form von Datenbankdaten ist jedoch nicht angegeben. Eine Datenbank kann zusätzliche Konvertierung für die Daten von der Form in der Implementierung Puffer ausführen.)  
  
    -   Die *Anwendung Zeilenpuffer,* die die Datenzeile enthält, wie für die Anwendung, die nach der Datenkonvertierung, die die Anwendung angeben kann.  
  
     Die Anwendung arbeitet mit den Anwendungsdienst-Deskriptor Zeile in jedem Fall, in dem Spaltendaten aus der Datenbank in Anwendungsvariablen angezeigt werden müssen. Um die Datenkonvertierung von Spaltendaten zu erreichen, kann die Anwendung unterschiedliche Datentypen aus den Implementierungszeilendeskriptor angeben.  
  
 Der deskriptortypen werden in der folgenden Tabelle zusammengefasst.  
  
|Puffertyp|Zeilen|Dynamische Parameter|  
|-----------------|----------|------------------------|  
|**Anwendungspuffer**|Zeile anwendungsdeskriptor (ARD)|anwendungsparameterdeskriptor (APD)|  
|**Implementierung Puffer**|implementierungszeilendeskriptors (IRD)|IPD (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor)|  
  
 Für den Parameter oder den Zeilenpuffer Wenn die Anwendung unterschiedliche Datentypen in der entsprechenden Datensätze die Implementierung und Deskriptoren angibt führt der Treiber Datenkonvertierung, wenn er die Deskriptoren verwendet. Es kann z. B. numerische und Datetime-Werte in Zeichenfolgen--Format konvertieren. (Konvertierungen, die gültige finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Ein Deskriptor kann verschiedene Rollen ausführen. Verschiedene Anweisungen können beliebige Deskriptoren freigeben, die die Anwendung explizit zuweist. Ein Deskriptor Zeile in einer Anweisung kann als eine Parameterdeskriptor in einer anderen Anweisung dienen.  
  
 Es ist immer, ob ein angegebener Deskriptor einen Anwendungsdienst-Deskriptor einer oder mehrerer Implementierung, ist bekannt, auch wenn der Deskriptor noch nicht in einem Datenbankvorgang verwendet wurde. Für die Deskriptoren, die die Implementierung implizit zuweist, zeichnet die Implementierung der vordefinierten Zeile relativ zur das Anweisungshandle verwenden. Alle Deskriptor, der die Anwendung durch Aufrufen von zuordnet **SQLAllocHandle** ist ein Anwendungsdienst-Deskriptor.
