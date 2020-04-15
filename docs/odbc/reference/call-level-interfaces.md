---
title: Call-Level-Schnittstellen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4288a278f745d533c92d3d45892753ef1a74c2b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306541"
---
# <a name="call-level-interfaces"></a>Call-Level-Interface
Die letzte Technik zum Senden von SQL-Anweisungen an das DBMS erfolgt über eine Schnittstelle auf Aufrufebene (CLI). Eine Schnittstelle auf Aufrufebene stellt eine Bibliothek mit DBMS-Funktionen bereit, die vom Anwendungsprogramm aufgerufen werden können. Anstatt also zu versuchen, SQL mit einer anderen Programmiersprache zu verschmelzen, ähnelt eine Schnittstelle auf Aufrufebene den Routinebibliotheken, an die die meisten Programmierer gewöhnt sind, z. B. die Zeichenfolgen-, E/A- oder mathematischen Bibliotheken in C. Beachten Sie, dass DBMS, die Embedded SQL unterstützen, bereits über eine Schnittstelle auf Aufrufebene verfügen, deren Aufrufe vom Vorcompiler generiert werden. Diese Anrufe sind jedoch nicht dokumentiert und können ohne vorherige Ankündigung geändert werden.  
  
 Schnittstellen auf Aufrufebene werden häufig in Client-/Serverarchitekturen verwendet, in denen sich das Anwendungsprogramm (der Client) auf einem Computer und das DBMS (der Server) auf einem anderen Computer befindet. Die Anwendung ruft CLI-Funktionen auf dem lokalen System auf, und diese Aufrufe werden zur Verarbeitung über das Netzwerk an das DBMS gesendet.  
  
 Eine Schnittstelle auf Aufrufebene ähnelt dynamic SQL, da SQL-Anweisungen zur Verarbeitung zur Laufzeit an das DBMS übergeben werden, sich jedoch von Embedded SQL als Ganzes dadurch unterscheidet, dass keine eingebetteten SQL-Anweisungen vorhanden sind und kein Vorkompilierer erforderlich ist.  
  
 Die Verwendung einer Schnittstelle auf Aufrufebene umfasst in der Regel die folgenden Schritte:  
  
1.  Die Anwendung ruft eine CLI-Funktion auf, um eine Verbindung mit dem DBMS herzustellen.  
  
2.  Die Anwendung erstellt eine SQL-Anweisung und platziert sie in einem Puffer. Anschließend werden eine oder mehrere CLI-Funktionen aufgesendet, um die Anweisung zur Vorbereitung und Ausführung an das DBMS zu senden.  
  
3.  Wenn es sich bei der Anweisung um eine SELECT-Anweisung handelt, ruft die Anwendung eine CLI-Funktion auf, um die Ergebnisse in Anwendungspuffern zurückzugeben. In der Regel gibt diese Funktion jeweils eine Zeile oder eine Datenspalte zurück.  
  
4.  Die Anwendung ruft eine CLI-Funktion auf, um die Verbindung zum DBMS zu trennen.
