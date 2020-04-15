---
title: Der Treiber-Manager | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 686a2b9673fb392f969a42f4cc86dd95a95668a6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286794"
---
# <a name="the-driver-manager"></a>Der Treiber-Manager
Der *Treiber-Manager* ist eine Bibliothek, die die Kommunikation zwischen Anwendungen und Treibern verwaltet. Auf Microsoft® Windows®-Plattformen ist der Treiber-Manager beispielsweise eine Dynamic-Link-Bibliothek (DLL), die von Microsoft geschrieben wird und von Benutzern des verteilbaren MDAC 2.8 SP1 SDK weiterverteilt werden kann.  
  
 Der Treiber-Manager existiert hauptsächlich als Komfort für Anwendungsautoren und löst eine Reihe von Problemen, die allen Anwendungen gemeinsam sind. Dazu gehören das Bestimmen des zu ladenden Treibers basierend auf einem Datenquellennamen, das Laden und Entladen von Treibern und das Aufrufen von Funktionen in Treibern.  
  
 Um zu sehen, warum Letzteres ein Problem ist, überlegen Sie, was passieren würde, wenn die Anwendung Direktfunktionen im Treiber aufrief. Wenn die Anwendung nicht direkt mit einem bestimmten Treiber verknüpft ist, muss sie eine Tabelle mit Zeigern auf die Funktionen in diesem Treiber erstellen und diese Funktionen per Zeiger aufrufen. Die Verwendung desselben Codes für mehr als einen Treiber gleichzeitig würde eine weitere Komplexitätsstufe hinzufügen. Die Anwendung müsste zuerst einen Funktionszeiger so einstellen, dass er auf die richtige Funktion im richtigen Treiber hinweist, und dann die Funktion über diesen Zeiger aufrufen.  
  
 Der Treiber-Manager löst dieses Problem, indem er einen einzigen Ort zum Aufrufen jeder Funktion bereitstellt. Die Anwendung ist mit dem Treiber-Manager verknüpft und ruft ODBC-Funktionen im Treiber-Manager auf, nicht den Treiber. Die Anwendung identifiziert den Zieltreiber und die Datenquelle mit einem *Verbindungshandle*. Wenn ein Treiber geladen wird, erstellt der Treiber-Manager eine Tabelle mit Zeigern auf die Funktionen in diesem Treiber. Es verwendet das Verbindungshandle, das von der Anwendung übergeben wird, um die Adresse der Funktion im Zieltreiber zu finden, und ruft diese Funktion nach Adresse auf.  
  
 In den meisten Teilen übergibt der Treiber-Manager nur Funktionsaufrufe von der Anwendung an den richtigen Treiber. Es implementiert jedoch auch einige Funktionen (**SQLDataSources**, **SQLDrivers**und **SQLGetFunctions**) und führt grundlegende Fehlerüberprüfungen durch. Der Treiber-Manager überprüft beispielsweise, ob Handles keine NULL-Zeiger sind, dass Funktionen in der richtigen Reihenfolge aufgerufen werden und dass bestimmte Funktionsargumente gültig sind. Eine vollständige Beschreibung der vom Treiber-Manager überprüften Fehler finden Sie im Referenzabschnitt für jede Funktion und [in Anhang B: ODBC-Statusübergangstabellen](../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Die letzte wichtige Rolle des Driver Managers ist das Laden und Entladen von Treibern. Die Anwendung lädt und entlädt nur den Treiber-Manager. Wenn ein bestimmter Treiber verwendet werden soll, ruft er eine Verbindungsfunktion (**SQLConnect**, **SQLDriverConnect**oder **SQLBrowseConnect**) im Treiber-Manager auf und gibt den Namen einer bestimmten Datenquelle oder eines bestimmten Treibers an, z. B. "Accounting" oder "SQL Server". Unter diesem Namen durchsucht der Treiber-Manager die Datenquelleninformationen nach dem Dateinamen des Treibers, z. B. Sqlsrvr.dll. Anschließend wird der Treiber geladen (vorausgesetzt, er ist noch nicht geladen), speichert die Adresse jeder Funktion im Treiber und ruft die Verbindungsfunktion im Treiber auf, die sich dann selbst initialisiert und eine Verbindung mit der Datenquelle herstellt.  
  
 Wenn die Anwendung mit dem Treiber fertig ist, ruft sie **SQLDisconnect** im Treiber-Manager auf. Der Treiber-Manager ruft diese Funktion im Treiber auf, der die Verbindung zur Datenquelle trennt. Der Treiber-Manager behält den Treiber jedoch im Arbeitsspeicher, falls die Anwendung erneut eine Verbindung herstellt. Er entlädt den Treiber nur, wenn die Anwendung die vom Treiber verwendete Verbindung freigibt oder die Verbindung für einen anderen Treiber verwendet, und keine anderen Verbindungen den Treiber verwenden. Eine vollständige Beschreibung der Rolle des Treiber-Managers beim Laden und Entladen von Treibern finden Sie unter [Die Rolle des Treiber-Managers im Verbindungsprozess](../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).
