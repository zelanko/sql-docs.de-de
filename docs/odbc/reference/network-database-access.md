---
title: Netzwerkdatenbankzugriff | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2237c725d6fe3696d1f28d80c09f22183f718de8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295583"
---
# <a name="network-database-access"></a>Datenbankzugriff über ein Netzwerk
Für den Zugriff auf eine Datenbank über ein Netzwerk sind eine Reihe von Komponenten erforderlich, die jeweils unabhängig von der Programmierschnittstelle sind und sich darunter befinden. Diese Komponenten werden in der folgenden Abbildung dargestellt.  
  
 ![Komponenten für den Zugriff auf eine Datenbank über ein Netzwerk](../../odbc/reference/media/pr04.gif "pr04")  
  
 Eine weitere Beschreibung der einzelnen Komponenten folgt:  
  
-   **Programmierschnittstelle** Wie weiter oben in diesem Abschnitt beschrieben, enthält die Programmierschnittstelle die Aufrufe der Anwendung. Diese Schnittstellen (eingebettete SQL-, SQL-Module und Schnittstellen auf Aufrufebene) sind im Allgemeinen für jedes DBMS spezifisch, obwohl sie in der Regel auf einem ANSI- oder ISO-Standard basieren.  
  
-   **Data Stream-Protokoll** Das Datenstromprotokoll beschreibt den Datenstrom, der zwischen dem DBMS und seinem Client übertragen wird. Das Protokoll erfordert z. B. das erste Byte, um zu beschreiben, was der Rest des Streams enthält: eine auszuführende SQL-Anweisung, ein zurückgegebener Fehlerwert oder zurückgegebene Daten. Das Format der restlichen Daten im Stream hängt dann von diesem Flag ab. Ein Fehlerstream kann z. B. das Flag, einen 2-Byte-Ganzzahlfehlercode, eine Länge der 2-Byte-Ganzzahlfehlermeldung und eine Fehlermeldung enthalten.  
  
     Das Datenstromprotokoll ist ein logisches Protokoll und unabhängig von den Protokollen, die vom zugrunde liegenden Netzwerk verwendet werden. So kann ein einzelnes Datenstromprotokoll in der Regel in einer Reihe von verschiedenen Netzwerken verwendet werden. Datenstromprotokolle sind in der Regel proprietär und wurden für die Arbeit mit einem bestimmten DBMS optimiert.  
  
-   **Interprozess-Kommunikationsmechanismus** Der Mechanismus der Interprozesskommunikation (IPC) ist der Prozess, durch den ein Prozess mit einem anderen kommuniziert. Beispiele hierfür sind Named Pipes, TCP/IP-Sockets und DECnet-Sockets. Die Wahl des IPC-Mechanismus wird durch das verwendete Betriebssystem und Netzwerk eingeschränkt.  
  
-   **Netzwerkprotokoll** Das Netzwerkprotokoll wird verwendet, um den Datenstrom über ein Netzwerk zu transportieren. Es kann als die Installation betrachtet werden, die die IPC-Mechanismen unterstützt, die zum Implementieren des Datenstromprotokolls verwendet werden, sowie grundlegende Netzwerkoperationen wie Dateiübertragungen und Druckfreigaben unterstützen. Netzwerkprotokolle umfassen NetBEUI, TCP/IP, DECnet und SPX/IPX und sind für jedes Netzwerk spezifisch.
