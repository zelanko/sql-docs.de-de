---
title: Call-Level-Schnittstellen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6c37084ad91a931c4479ecf826c5cb554765412
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135666"
---
# <a name="call-level-interfaces"></a>Call-Level-Interface
Das letzte Verfahren für das Senden von SQL-Anweisungen für das DBMS ist mit einer Call-Level-Interface (CLI). Eine Call-Level-Interface bietet es sich um eine Bibliothek mit DBMS-Funktionen, die von der Anwendung aufgerufen werden kann. Folglich ähnelt anstatt zu versuchen, die eine andere Programmiersprache SQL überblendet, einer Call-Level-Interface routinemäßigen Bibliotheken, die meisten Programmierer vertraut sind, zu verwenden, z. B. die Zeichenfolge, die e/a- oder die mathematische Bibliotheken im c-Hinweis, DBMS-Systeme, die eingebettete SQL unterstützen verfügen Sie bereits eine Aufrufebene-Schnittstelle, die Aufrufe an die von der vorkompilierten generiert werden. Allerdings sind diese Aufrufe nicht dokumentierte und können ohne vorherige Ankündigung geändert.  
  
 Call-Level-Interface werden häufig in Client/Server-Architekturen verwendet, in der die Anwendung (Client) auf einem Computer befindet, und das DBMS (Server) auf einem anderen Computer befindet. Die Anwendung ruft die CLI-Funktionen auf dem lokalen System aus, und diese Aufrufe werden für das DBMS für die Verarbeitung über das Netzwerk gesendet.  
  
 Eine Call-Level-Interface ähnelt dynamisches SQL, SQL-Anweisungen für das DBMS zur Verarbeitung zur Laufzeit übergeben werden, aber es unterscheidet sich von embedded SQL als Ganzes, da keine eingebettete SQL-Anweisungen vorhanden sind und keine vorkompilierten ist erforderlich.  
  
 Verwenden in der Regel eine Call-Level-Interface umfasst die folgenden Schritte aus:  
  
1.  Die Anwendung ruft eine CLI-Funktion für die Verbindung für das DBMS an.  
  
2.  Die Anwendung eine SQL-Anweisung erstellt und in einem Puffer platziert. Es ruft dann eine oder mehrere CLI-Funktionen, um die Anweisung für das DBMS an, für die Vorbereitung und Ausführung zu senden.  
  
3.  Wenn die Anweisung eine SELECT-Anweisung ist, ruft die Anwendung eine CLI-Funktion, um die Ergebnisse im Anwendungspuffer zurückzugeben. Diese Funktion gibt eine Zeile oder einer Spalte mit Daten in der Regel zu einem Zeitpunkt.  
  
4.  Die Anwendung ruft eine CLI-Funktion, die aus dem DBMS zu trennen.
