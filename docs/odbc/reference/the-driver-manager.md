---
title: Der Treiber-Manager | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 0c1ae3f098aea3886d5cb84a0bfcb7553a8181fa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62719726"
---
# <a name="the-driver-manager"></a>Der Treiber-Manager
Die *-Treiber-Manager* ist eine Bibliothek, die Kommunikation zwischen Anwendungen und Treiber verwaltet. Beispielsweise ist der Treiber-Manager auf Microsoft® Windows®-Plattformen, eine Dynamic Link Library (DLL), die von Microsoft geschrieben und kann von den Benutzern das verteilbare MDAC 2.8 SP1 SDK verteilt werden.  
  
 Der Treiber-Manager vorhanden ist, hauptsächlich als Annehmlichkeit für Anwendungsentwickler und löst eine Reihe von Problemen, die für alle Anwendungen. Dazu gehören bestimmen, welcher Treiber für das Laden auf einen Datenquellennamen basieren, laden und Entladen von Treibern und Aufrufen von Funktionen in Treiber.  
  
 Um festzustellen, warum Letzteres ein Problem aufgetreten ist, erwägen Sie, was passieren würde, wenn die Anwendung Funktionen im Treiber direkt aufgerufen. Wenn die Anwendung direkt an einen bestimmten Treiber verknüpft wurde, müssten sie eine Tabelle von Zeigern auf Funktionen in diesen Treiber zu erstellen und diese Funktionen aufrufen, indem Zeiger. Verwenden den gleichen Code für mehr als einen Treiber zu einem Zeitpunkt würden noch eine weitere Ebene der Komplexität hinzufügen. Die Anwendung würde müssen zuerst einen Funktionszeiger, zeigen Sie auf die ordnungsgemäße Funktion in den richtigen Treiber festlegen und dann die Funktion über diesen Zeiger aufrufen.  
  
 Der Treiber-Manager löst dieses Problem durch die Bereitstellung einer zentralen Stelle jede Funktion aufgerufen. Die Anwendung ist für die Treiber-Manager und ruft ODBC-Funktionen im Treiber-Manager, nicht die Treiber verknüpft. Die Anwendung identifiziert den Ziel-Treiber und die Datenquelle mit einem *Verbindungshandle*. Wenn sie einen Treiber geladen wird, erstellt der Treiber-Manager eine Tabelle von Zeigern auf Funktionen in diesen Treiber. Der Verbindungshandles, die von der Anwendung übergebenen verwendet, um die Adresse der Funktion in der Zieltreiber finden und ruft diese Funktion über die Adresse.  
  
 Zum größten Teil, übergibt der Treiber-Manager nur Funktionsaufrufe von der Anwendung an den richtigen Treiber. Allerdings es implementiert auch einige Funktionen (**SQLDataSources**, **SQLDrivers**, und **SQLGetFunctions**) und führt grundlegende fehlerprüfung. Beispielsweise überprüft der Treiber-Manager, dass-Handles keine null-Zeiger sind, dass Funktionen in der richtigen Reihenfolge aufgerufen werden und dass bestimmte Argumente der Funktion gültig sind. Eine vollständige Beschreibung der Fehler vom Treiber-Manager überprüft werden soll, finden Sie im Referenzabschnitt "für jede Funktion und [Anhang B: ODBC-Übergang Statustabellen](../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Die letzte wichtige Rolle des Treiber-Managers ist laden und Entladen von Treibern. Die Anwendung lädt und entlädt nur die Treiber-Manager. Wenn es einen bestimmten Treiber zu verwenden möchte, ruft er eine Verbindungsfunktion (**SQLConnect**, **SQLDriverConnect**, oder **SQLBrowseConnect**) im Treiber-Manager und gibt an, der Name einer bestimmten Datenquelle oder ein Treiber, z. B. "Finanzwesen" oder "SqlServer." Mit diesem Namen, sucht der Treiber-Manager für Dateinamen des Treibers, z. B. SQLSRVR Informationen für die Datenquelle aus. Klicken Sie dann lädt den Treiber (vorausgesetzt, dass sie nicht bereits geladen wurde), speichert die Adresse für jede Funktion im Treiber und ruft die Verbindungsfunktion im Treiber, die dann initialisiert sich selbst und eine Verbindung mit der Datenquelle her.  
  
 Wenn die Anwendung erfolgt mit dem Treiber ruft **SQLDisconnect** im Treiber-Manager. Der Treiber-Manager ruft diese Funktion in den Treiber, der aus der Datenquelle wird getrennt. Der Treiber-Manager behält jedoch den Treiber im Speicher für den Fall, dass die Anwendung, erneut eine Verbindung herstellt. Den Treiber entladen nur, wenn die Anwendung gibt frei, die vom Treiber verwendete Verbindung oder die Verbindung für einen anderen Treiber verwendet und keine weiteren Verbindungen verwenden Sie den Treiber. Eine vollständige Beschreibung der Treiber-Manager-Rolle im Laden und Entladen von Treibern, finden Sie unter [Treiber-Manager-Rolle in der Verbindungsprozess](../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).
