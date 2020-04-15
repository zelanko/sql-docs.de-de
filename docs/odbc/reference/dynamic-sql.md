---
title: Dynamischesql | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56419723540114f122be2582f0de7c7e7d0c54f3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306688"
---
# <a name="dynamic-sql"></a>Dynamische SQL-Anweisungen
Obwohl statischesql in vielen Situationen gut funktioniert, gibt es eine Klasse von Anwendungen, in der der Datenzugriff nicht im Voraus bestimmt werden kann. Angenommen, eine Kalkulationstabelle ermöglicht es einem Benutzer, eine Abfrage einzugeben, die die Kalkulationstabelle dann an das DBMS sendet, um Daten abzurufen. Der Inhalt dieser Abfrage kann dem Programmierer offensichtlich nicht bekannt sein, wenn das Tabellenkalkulationsprogramm geschrieben wird.  
  
 Um dieses Problem zu lösen, verwendet die Kalkulationstabelle eine Form von eingebettetem SQL namens Dynamic SQL. Im Gegensatz zu statischen SQL-Anweisungen, die im Programm hartcodiert sind, können dynamische SQL-Anweisungen zur Laufzeit erstellt und in einer Zeichenfolgenhostvariablen platziert werden. Sie werden dann zur Verarbeitung an das DBMS gesendet. Da das DBMS zur Laufzeit einen Zugriffsplan für dynamische SQL-Anweisungen generieren muss, ist dynamic SQL im Allgemeinen langsamer als statischesql. Wenn ein Programm kompiliert wird, das dynamische SQL-Anweisungen enthält, werden die dynamischen SQL-Anweisungen nicht aus dem Programm entfernt, wie in statischem SQL. Stattdessen werden sie durch einen Funktionsaufruf ersetzt, der die Anweisung an das DBMS übergibt. statische SQL-Anweisungen im selben Programm werden normal behandelt.  
  
 Die einfachste Möglichkeit zum Ausführen einer dynamischen SQL-Anweisung ist eine EXECUTE IMMEDIATE-Anweisung. Diese Anweisung übergibt die SQL-Anweisung zur Kompilierung und Ausführung an das DBMS.  
  
 Ein Nachteil der EXECUTE IMMEDIATE-Anweisung besteht darin, dass das DBMS jedes Mal, wenn die Anweisung ausgeführt wird, jeden der fünf Schritte der Verarbeitung einer SQL-Anweisung durchlaufen muss. Der in diesem Prozess verbundene Overhead kann erheblich sein, wenn viele Anweisungen dynamisch ausgeführt werden, und es ist verschwenderisch, wenn diese Anweisungen ähnlich sind. Um dieser Situation zu begegnen, bietet dynamic SQL eine optimierte Ausführungsform namens Vorbereitete Ausführung, die die folgenden Schritte verwendet:  
  
1.  Das Programm erstellt eine SQL-Anweisung in einem Puffer, genau wie für die EXECUTE IMMEDIATE-Anweisung. Anstelle von Hostvariablen kann ein Fragezeichen (?) durch eine Konstante an einer beliebigen Stelle im Anweisungstext ersetzt werden, um anzugeben, dass später ein Wert für die Konstante angegeben wird. Das Fragezeichen wird als Parametermarkierung aufgerufen.  
  
2.  Das Programm übergibt die SQL-Anweisung an das DBMS mit einer PREPARE-Anweisung, die anfordert, dass das DBMS die Anweisung analysiert, überprüft und optimiert und einen Ausführungsplan dafür generiert. Das Programm verwendet dann eine EXECUTE-Anweisung (keine EXECUTE IMMEDIATE-Anweisung), um die PREPARE-Anweisung zu einem späteren Zeitpunkt auszuführen. Es übergibt Parameterwerte für die Anweisung durch eine spezielle Datenstruktur, die SQL Data Area oder SQLDA genannt wird.  
  
3.  Das Programm kann die EXECUTE-Anweisung wiederholt verwenden und bei jeder Ausführung der dynamischen Anweisung unterschiedliche Parameterwerte angeben.  
  
 Die vorbereitete Ausführung ist immer noch nicht identisch mit statischem SQL. In static SQL finden die ersten vier Schritte zur Verarbeitung einer SQL-Anweisung zur Kompilierungszeit statt. In vorbereiteter Ausführung finden diese Schritte immer noch zur Laufzeit statt, werden jedoch nur einmal ausgeführt. Die Ausführung des Plans erfolgt nur, wenn EXECUTE aufgerufen wird. Dadurch werden einige der Leistungsnachteile beseitigt, die der Architektur von dynamic SQL innewohnen. Die nächste Abbildung zeigt die Unterschiede zwischen statischem SQL, dynamischem SQL mit sofortiger Ausführung und dynamischem SQL mit vorbereiteter Ausführung.
