---
title: Deskriptortypen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304891"
---
# <a name="types-of-descriptors"></a>Typen von Deskriptoren
Ein Deskriptor wird verwendet, um einen der folgenden zu beschreiben:  
  
-   Ein Satz von 0 (null) oder mehr Parametern. Ein Parameter Deskriptor kann verwendet werden, um Folgendes zu beschreiben:  
  
    -   Der *Anwendungsparameter Puffer,* der die von der Anwendung festgelegten dynamischen Eingabeargumente oder die dynamischen Argumente der Ausgabe nach der Ausführung einer SQL- **Anweisung enthält** .  
  
    -   Der *Implementierungs Parameter Puffer*. Für dynamische Eingabeargumente enthält diese die gleichen Argumente wie der Anwendungsparameter Puffer, nachdem eine beliebige Datenkonvertierung von der Anwendung möglich ist. Für dynamische Ausgabe Argumente enthält diese die zurückgegebenen Argumente, bevor eine von der Anwendung angegebene Datenkonvertierung möglich ist.  
  
     Bei dynamischen Eingabe Argumenten muss die Anwendung mit einem Anwendungsparameter Deskriptor arbeiten, bevor eine SQL-Anweisung ausgeführt wird, die dynamische Parameter Markierungen enthält. Sowohl für Eingabe-als auch für Ausgabe dynamische Argumente kann die Anwendung unterschiedliche Datentypen aus den Implementierungs Parameter Deskriptoren angeben, um die Datenkonvertierung zu erzielen.  
  
-   Eine einzelne Zeile mit Datenbankdaten. Ein Zeilen Deskriptor kann verwendet werden, um Folgendes zu beschreiben:  
  
    -   Der *Implementierungs Zeilen Puffer,* der die Zeile aus der Datenbank enthält. (Diese Puffer enthalten konzeptionell Daten, die in die Datenbank geschrieben oder aus ihr gelesen werden. Die gespeicherte Form von Datenbankdaten ist jedoch nicht angegeben. Eine Datenbank kann eine zusätzliche Konvertierung der Daten aus Ihrem Formular im Implementierungs Puffer ausführen.)  
  
    -   Der *Anwendungs Zeilen Puffer,* der die Zeile der Daten enthält, die der Anwendung gemäß der von der Anwendung angegebenen Datenkonvertierung angezeigt werden.  
  
     Die Anwendung wird in jedem Fall mit dem Anwendungs Zeilen Deskriptor betrieben, wenn Spaltendaten aus der Datenbank in Anwendungsvariablen angezeigt werden müssen. Um die Datenkonvertierung von Spaltendaten zu erreichen, kann die Anwendung unterschiedliche Datentypen aus den Zeilen Deskriptoren der Implementierung angeben.  
  
 Die deskriptortypen sind in der folgenden Tabelle zusammengefasst.  
  
|Puffertyp|Zeilen|Dynamische Parameter|  
|-----------------|----------|------------------------|  
|**Anwendungs Puffer**|Anwendungs Zeilen Deskriptor (ARD)|Anwendungsparameter Deskriptor (APD)|  
|**Implementierungs Puffer**|Implementierungs Zeilen Deskriptor (IRD)|Implementierungs Parameter Deskriptor (IPD)|  
  
 Wenn die Anwendung unterschiedliche Datentypen in den entsprechenden Datensätzen der Implementierungs-und Anwendungs Deskriptoren angibt, führt der Treiber die Datenkonvertierung durch, wenn die Deskriptoren verwendet werden. Beispielsweise können numerische Werte und DateTime-Werte in das Zeichen folgen Format konvertiert werden. (Informationen zu gültigen Konvertierungen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Mit einem Deskriptor können unterschiedliche Rollen durchgeführt werden. Verschiedene-Anweisungen können alle Deskriptoren gemeinsam verwenden, die von der Anwendung explizit zugewiesen werden. Ein Zeilen Deskriptor in einer Anweisung kann als Parameter Deskriptor in einer anderen Anweisung dienen.  
  
 Es ist immer bekannt, ob es sich bei einem bestimmten Deskriptor um einen Anwendungs Deskriptor oder einen Implementierungs Deskriptor handelt, auch wenn der Deskriptor noch nicht in einem Daten Bank Vorgang verwendet wurde. Bei den Deskriptoren, die von der Implementierung implizit zugewiesen werden, zeichnet die-Implementierung die vordefinierte Zeile relativ zum Anweisungs Handle auf. Jeder Deskriptor, den die Anwendung durch Aufrufen von **sqlzugechandle** zugewiesen, ist ein Anwendungs Deskriptor.
