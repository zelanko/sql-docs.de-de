---
description: Dynamische SQL-Anweisungen
title: Dynamisches SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/03/2020
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
ms.openlocfilehash: de711543748a91015a9aa0d4cb8aadb011744306
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494581"
---
# <a name="dynamic-sql"></a>Dynamische SQL-Anweisungen
Obwohl statisches SQL in vielen Situationen gut funktioniert, gibt es eine Klasse von Anwendungen, in denen der Datenzugriff nicht im Voraus bestimmt werden kann. Angenommen, eine Kalkulations Tabelle ermöglicht einem Benutzer die Eingabe einer Abfrage, die von der Tabelle dann an das DBMS gesendet wird, um Daten abzurufen. Der Inhalt dieser Abfrage kann dem Programmierer offensichtlich nicht bekannt sein, wenn das Tabellen Kalkulations Programm geschrieben wird.  
  
 Um dieses Problem zu beheben, verwendet die Kalkulations Tabelle eine Form des eingebetteten SQL-namens Dynamic SQL. Im Unterschied zu statischen SQL-Anweisungen, die im Programm hart codiert sind, können dynamische SQL-Anweisungen zur Laufzeit erstellt und in eine Zeichen folgen-Host Variable eingefügt werden. Sie werden dann zur Verarbeitung an das DBMS gesendet. Da das DBMS zur Laufzeit für dynamische SQL-Anweisungen einen Zugriffs Plan generieren muss, ist Dynamic SQL in der Regel langsamer als die statische SQL-Anweisung. Wenn ein Programm, das dynamische SQL-Anweisungen enthält, kompiliert wird, werden die dynamischen SQL-Anweisungen nicht aus dem Programm entfernt, wie in statischem SQL. Stattdessen werden Sie durch einen Funktions Aufrufer ersetzt, der die Anweisung an das DBMS übergibt. statische SQL-Anweisungen im selben Programm werden normal behandelt.  
  
 Die einfachste Möglichkeit, eine dynamische SQL-Anweisung auszuführen, ist mit einer EXECUTE IMMEDIATE-Anweisung. Diese Anweisung übergibt die SQL-Anweisung für die Kompilierung und Ausführung an das DBMS.  
  
 Ein Nachteil der EXECUTE IMMEDIATE-Anweisung besteht darin, dass das DBMS jeden der fünf Schritte zum Verarbeiten einer SQL-Anweisung jedes Mal durchlaufen muss, wenn die Anweisung ausgeführt wird. Der Aufwand für diesen Prozess kann signifikant sein, wenn viele-Anweisungen dynamisch ausgeführt werden, und es ist verschwenderisch, wenn diese Anweisungen ähnlich sind. Um diese Situation zu beheben, bietet dynamisches SQL eine optimierte Form der Ausführung mit der Bezeichnung vorbereitete Ausführung, die die folgenden Schritte verwendet:  
  
1.  Das Programm erstellt eine SQL-Anweisung in einem Puffer, genau wie bei der EXECUTE IMMEDIATE-Anweisung. Anstelle von Host Variablen kann ein Fragezeichen (?) an beliebiger Stelle im Anweisungs Text eine Konstante ersetzen, um anzugeben, dass ein Wert für die Konstante später bereitgestellt wird. Das Fragezeichen wird als Parameter Markierung bezeichnet.  
  
2.  Das Programm übergibt die SQL-Anweisung mit einer PREPARE-Anweisung an das DBMS, die anfordert, dass das DBMS die Anweisung analysiert, validiert und optimiert und einen Ausführungsplan für Sie generiert. Das Programm verwendet dann eine EXECUTE-Anweisung (keine EXECUTE IMMEDIATE-Anweisung), um die Prepare-Anweisung zu einem späteren Zeitpunkt auszuführen. Sie übergibt Parameterwerte für die-Anweisung über eine spezielle Datenstruktur, die als SQL-Datenbereich oder SQLDA bezeichnet wird.  
  
3.  Das Programm kann die EXECUTE-Anweisung wiederholt verwenden und dabei jedes Mal, wenn die dynamische Anweisung ausgeführt wird, unterschiedliche Parameterwerte bereitstellen.  
  
 Die vorbereitete Ausführung ist immer noch nicht mit der statischen SQL-Ausführung identisch. In statischem SQL erfolgen die ersten vier Schritte zur Verarbeitung einer SQL-Anweisung zur Kompilierzeit. Bei der vorbereiteten Ausführung erfolgen diese Schritte immer noch zur Laufzeit, werden jedoch nur einmal ausgeführt. die Ausführung des Plans findet nur statt, wenn Execute aufgerufen wird. Dadurch können einige der Leistungs Nachteile vermieden werden, die in der Architektur dynamischer SQL-Daten enthalten sind.
