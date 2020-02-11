---
title: Treiber-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC]
- ODBC architecture [ODBC], driver manager
- driver manager [ODBC], about driver manager
- ODBC driver manager [ODBC]
ms.assetid: 559e4de1-16c9-4998-94f5-6431122040cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 659678451c368df0b6a213e54cf7edaedfc29bd1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039330"
---
# <a name="the-driver-manager"></a>Der Treiber-Manager
Der *Treiber-Manager* ist eine Bibliothek, die die Kommunikation zwischen Anwendungen und Treibern verwaltet. Beispielsweise ist der Treiber-Manager auf Microsoft® Windows®-Plattformen eine Dynamic Link Library (dll), die von Microsoft geschrieben wird und von Benutzern des verteilbaren MDAC 2,8 SP1 SDK neu verteilt werden kann.  
  
 Der Treiber-Manager ist hauptsächlich für Anwendungs Schreiber und löst eine Reihe von Problemen aus, die allen Anwendungen gemeinsam sind. Dazu gehört die Bestimmung des zu ladenden Treibers basierend auf dem Namen der Datenquelle, das Laden und Entladen von Treibern und das Aufrufen von Funktionen in Treibern.  
  
 Um zu ermitteln, warum es sich um ein Problem handelt, sollten Sie Bedenken, was passiert, wenn die Anwendung direkt Funktionen im Treiber aufrief. Wenn die Anwendung nicht direkt mit einem bestimmten Treiber verknüpft ist, muss Sie eine Tabelle mit Zeigern auf die Funktionen in diesem Treiber erstellen und diese Funktionen per Zeiger aufzurufen. Wenn Sie denselben Code für mehr als einen Treiber gleichzeitig verwenden, wird eine andere Komplexitäts Ebene hinzugefügt. Die Anwendung muss zuerst einen Funktionszeiger festlegen, um auf die richtige Funktion im richtigen Treiber zu zeigen, und dann die Funktion über diesen Zeiger aufzurufen.  
  
 Der Treiber-Manager löst dieses Problem, indem er eine einzige Stelle zum Abrufen der einzelnen Funktionen bereitstellt. Die Anwendung ist mit dem Treiber-Manager verknüpft und ruft ODBC-Funktionen im Treiber-Manager und nicht den Treiber auf. Die Anwendung identifiziert den Ziel Treiber und die Datenquelle mit einem *Verbindungs Handle*. Beim Laden eines Treibers erstellt der Treiber-Manager eine Tabelle mit Zeigern auf die Funktionen in diesem Treiber. Er verwendet das Verbindungs Handle, das von der Anwendung zum Suchen der Adresse der Funktion im Ziel Treiber und das Aufrufen dieser Funktion nach Adresse verwendet wird.  
  
 Zum größten Teil übergibt der Treiber-Manager einfach Funktionsaufrufe von der Anwendung an den richtigen Treiber. Es implementiert jedoch auch einige Funktionen (**SQLDataSources**, **SQLDrivers**und **SQLGetFunctions**) und führt eine grundlegende Fehlerüberprüfung aus. Beispielsweise prüft der Treiber-Manager, ob Handles keine NULL-Zeiger sind, ob Funktionen in der richtigen Reihenfolge aufgerufen werden und ob bestimmte Funktionsargumente gültig sind. Eine umfassende Beschreibung der vom Treiber-Manager geprüften Fehler finden Sie im Abschnitt "Reference" für jede Funktion und [Anhang B: ODBC-Status Übergangs Tabellen](../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Die letzte Hauptrolle des Treiber-Managers ist das Laden und Entladen von Treibern. Die Anwendung lädt und entlädt nur den Treiber-Manager. Wenn ein bestimmter Treiber verwendet werden soll, wird eine Verbindungsfunktion (**SQLCONNECT**, **SQLDriverConnect**oder **sqlbrowseconnetct**) im Treiber-Manager aufgerufen und der Name einer bestimmten Datenquelle oder eines Treibers (z. b. "Accounting" oder "SQL Server") angegeben. Wenn Sie diesen Namen verwenden, durchsucht der Treiber-Manager die Datenquellen Informationen nach dem Dateinamen des Treibers, z. b. sqlsrvr. dll. Anschließend wird der Treiber geladen (vorausgesetzt, er ist nicht bereits geladen), die Adresse der einzelnen Funktionen im Treiber speichert und die Verbindungsfunktion im Treiber aufruft, die dann selbst initialisiert und eine Verbindung mit der Datenquelle herstellt.  
  
 Wenn die Anwendung mit dem Treiber ausgeführt wird, wird **SQLDisconnect** im Treiber-Manager aufgerufen. Der Treiber-Manager ruft diese Funktion im Treiber auf, der die Verbindung mit der Datenquelle trennt. Der Treiber-Manager behält den Treiber jedoch im Arbeitsspeicher bei, wenn die Anwendung erneut eine Verbindung mit der Anwendung herstellt. Der Treiber wird nur entladen, wenn die vom Treiber verwendete Verbindung von der Anwendung freigegeben wird oder die Verbindung für einen anderen Treiber verwendet wird und keine anderen Verbindungen den Treiber verwenden. Eine umfassende Beschreibung der Rolle des Treiber-Managers beim Laden und Entladen von Treibern finden Sie unter [Treiber-Manager-Rolle im Verbindungsprozess](../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).
