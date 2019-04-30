---
title: Netzwerk-Datenbankzugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- network database access [ODBC]
- standardizing database access [ODBC], network
ms.assetid: f31dd938-e992-436b-b613-145c23973064
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ff13d2e46377b0d29c9bbc8e8ad1705dedc048b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63272885"
---
# <a name="network-database-access"></a>Datenbankzugriff über ein Netzwerk
Zugreifen auf eine Datenbank in einem Netzwerk erfordert eine Reihe von Komponenten, von die jedes ist unabhängig von, und befindet sich unterhalb der Programmierschnittstelle. Diese Komponenten werden in der folgenden Abbildung angezeigt.  
  
 ![Komponenten, die Zugriff auf eine Datenbank in einem Netzwerk](../../odbc/reference/media/pr04.gif "pr04")  
  
 Es folgt eine weitere Beschreibung der einzelnen Komponenten:  
  
-   **Programmierschnittstelle** wie weiter oben in diesem Abschnitt beschrieben wird, enthält die Programmierschnittstelle der Aufrufe von der Anwendung. Diese Schnittstellen (embedded SQL, SQL-Module und Schnittstellen von Aufrufebene) beziehen sich in der Regel mit dem jeweiligen Datenbankverwaltungssystem, obwohl sie in der Regel ein ANSI oder ISO-Standard basieren.  
  
-   **Data Stream-Protokoll** Datenprotokoll Stream beschreibt den Datenstrom zwischen dem DBMS und dem Client übertragen. Das Protokoll kann z. B. das erste Byte zu beschreiben, was der Rest des Datenstroms enthält benötigen: eine SQL-Anweisung ausgeführt, einen Wert gab den Fehlercode oder hat Daten zurückgegeben werden soll. Das Format der Rest der Daten in den Stream dann hängt dieses Kennzeichen ab. Ein fehlerdatenstrom kann z. B. das Flag, einen Fehlercode 2-Byte-Ganzzahl, die Nachrichtenlänge für eine 2-Byte-Ganzzahl-Fehler und eine Fehlermeldung enthalten.  
  
     Das Data Stream-Protokoll ist ein logisches Protokoll, und ist unabhängig vom zugrunde liegenden Netzwerk verwendete Protokolle. Daher kann ein einzelnes Data Stream-Protokoll in der Regel auf einer Reihe von verschiedenen Netzwerken verwendet werden. Data Stream-Protokolle sind in der Regel proprietär und wurden optimiert, um für ein bestimmtes DBMS zu arbeiten.  
  
-   **Prozessübergreifende Kommunikationsmechanismus** der Mechanismus der prozessübergreifenden Kommunikation (IPC) ist der Prozess, der mit dem ein Prozess mit einem anderen kommuniziert. Beispiele für sind benannte Pipes, TCP/IP-Sockets und DECnet-Sockets. Die Auswahl der IPC-Mechanismus wird durch das Betriebssystem und Netzwerk verwendet wird, eingeschränkt.  
  
-   **Netzwerkprotokoll** das Netzwerkprotokoll wird verwendet, um den Datenstrom über das Netzwerk übertragen. Sie können die Routinearbeiten betrachtet werden, unterstützt die IPC-Mechanismen verwendet, um die Daten zu implementieren stream-Protokoll als auch Standard-Vorgänge wie dateiübertragungen unterstützt und Druckerfreigabe. Netzwerkprotokolle sind NetBEUI, TCP/IP, DECnet und SPX/IPX und beziehen sich auf jedem Netzwerk.
