---
title: Dynamisches SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], dynamic SQL
- SQL statements [ODBC], embedded SQL
- dynamic SQL [ODBC]
- SQL [ODBC], dynamic SQL
- embedded SQL [ODBC]
ms.assetid: 0bfb9ab7-9c15-4433-93bc-bad8b6c9d287
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbecd1d6db1d5ed77082253f6a6a57a96ceec4d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628696"
---
# <a name="dynamic-sql"></a>Dynamische SQL-Anweisungen
Statische SQL-Anweisungen in vielen Situationen funktioniert, aber es ist eine Klasse von Anwendungen, die in denen der Datenzugriff im Voraus nicht bestimmt werden kann. Nehmen wir beispielsweise an, dass eine Tabelle ermöglicht dem Benutzer eine Abfrage aus, geben die klicken Sie dann das Arbeitsblatt für das DBMS sendet, um Daten abzurufen. Den Inhalt dieser Abfrage können nicht für den Programmierer natürlich bekannt sein, wenn das Arbeitsblatt-Programm geschrieben wird.  
  
 Um dieses Problem zu beheben, verwendet das Arbeitsblatt eine Form von embedded SQL dynamischen SQL-Code aufgerufen. Im Gegensatz zu SQL-Anweisungen, die im Programm hartcodiert sind, können dynamische SQL-Anweisungen zur Laufzeit erstellt und in einer Zeichenfolgenvariablen für den Host platziert werden. Sie werden dann an das DBMS zur Verarbeitung gesendet. Da das DBMS einen Zugriffsplan für dynamische SQL-Anweisungen zur Laufzeit generieren muss, ist dynamisches SQL in der Regel langsamer als statische SQL-Anweisungen. Wenn ein Programm mit der dynamischen SQL-Anweisungen kompiliert wird, werden die dynamischen SQL-Anweisungen nicht aus der Anwendung, wie statische SQL-Anweisungen entfernt. Stattdessen werden sie durch einen Funktionsaufruf ersetzt, die die Anweisung für das DBMS übergibt; statische SQL-Anweisungen im selben Programm werden normalerweise behandelt.  
  
 Die einfachste Möglichkeit zum Ausführen einer dynamischen SQL­Anweisung ist mit einer Anweisung sofort AUSZUFÜHREN. Diese Anweisung übergibt die SQL-Anweisung für das DBMS an, für die Kompilierung und Ausführung an.  
  
 Ein Nachteil der Anweisung sofort ausgeführt wird, dass das DBMS durchlaufen muss jede der fünf Schritte bei der Verarbeitung einer SQL-Anweisung jedes Mal, wenn die Anweisung ausgeführt wird. Der Aufwand bei diesem Vorgang kann erheblich sein, wenn mehrere-Anweisungen dynamisch ausgeführt werden und verschwenderisch, ist Wenn diese Anweisungen ähneln. Um diese Situation zu beheben, bietet dynamisches SQL für eine optimierte Form der Ausführung mit der Bezeichnung die vorbereitete Ausführung, verwendet die folgenden Schritte aus:  
  
1.  Das Programm erstellt eine SQL-Anweisung in einem Puffer, genau wie für die Anweisung sofort AUSZUFÜHREN. Anstelle von Hostvariablen kann ein Fragezeichen (?) ersetzt werden, für die eine Konstante an eine beliebige Stelle im Text Anweisung, um anzugeben, dass ein Wert für die Konstante später angegeben. Das Fragezeichen wird als eine parametermarkierung aufgerufen.  
  
2.  Die Anwendung übergibt die SQL-Anweisung für das DBMS wird mit einer PREPARE-Anweisung, welche Anforderungen an, dass das DBMS analysieren, zu überprüfen und optimieren die Anweisung und generieren eine Ausführung planen. Das Programm verwendet eine EXECUTE-Anweisung (keine EXECUTE IMMEDIATE-Anweisung) klicken Sie dann auf die PREPARE-Anweisung zu einem späteren Zeitpunkt ausführen. Sie übergibt die Parameterwerte für die Anweisung über eine spezielle Datenstruktur, die als SQL-Datenbereich oder SQLDA bezeichnet.  
  
3.  Das Programm können die EXECUTE-Anweisung wiederholt wird, Bereitstellung unterschiedliche Parameterwerte jedes Mal, wenn die dynamische-Anweisung ausgeführt wird.  
  
 Die vorbereitete Ausführung ist noch nicht mit statischem SQL identisch. In statische SQL-Anweisungen erfolgen die ersten vier Schritte der Verarbeitung einer SQL-Anweisung zum Zeitpunkt der Kompilierung. Bei der vorbereiteten Ausführung dieser Schritte finden weiterhin statt zur Laufzeit, aber sie werden nur einmal ausgeführt; Ausführung des Plans wird nur bei EXECUTE aufgerufen wird. Dadurch wird die Leistung in der Architektur von dynamischem SQL inhärenten Nachteile zu vermeiden. Die folgende Abbildung zeigt die Unterschiede zwischen statische SQL-Anweisungen, dynamische SQL mit sofortige Ausführung und dynamisches SQL bei der vorbereiteten Ausführung.
