---
title: Netzwerkdaten Bank Zugriff | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81295583"
---
# <a name="network-database-access"></a>Datenbankzugriff über ein Netzwerk
Der Zugriff auf eine Datenbank über ein Netzwerk erfordert eine Reihe von Komponenten, von denen jede unabhängig von der Programmierschnittstelle ist und sich darunter befindet. Diese Komponenten sind in der folgenden Abbildung dargestellt.  
  
 ![Komponenten für den Zugriff auf eine Datenbank über ein Netzwerk](../../odbc/reference/media/pr04.gif "pr04")  
  
 Es folgt eine weitere Beschreibung der einzelnen Komponenten:  
  
-   **Programmierschnittstelle** Wie weiter oben in diesem Abschnitt beschrieben, enthält die Programmierschnittstelle die Aufrufe, die von der Anwendung durchgeführt werden. Diese Schnittstellen (eingebettete SQL-, SQL-Module und Schnittstellen auf Aufrufebene) sind in der Regel für jedes DBMS spezifisch, obwohl Sie in der Regel auf einem ANSI-oder ISO-Standard basieren.  
  
-   **Datenstrom Protokoll** Das Datenstrom Protokoll beschreibt den Datenstrom von Daten, die zwischen dem DBMS und dem Client übertragen werden. Beispielsweise kann das Protokoll das erste Byte erfordern, um zu beschreiben, was der restliche Stream enthält: eine auszuführende SQL-Anweisung, ein zurückgegebener Fehlerwert oder zurückgegebene Daten. Das Format der restlichen Daten im Stream hängt dann von diesem Flag ab. Ein Fehler Datenstrom kann z. b. das-Flag, einen ganzzahligen 2-Byte-Fehlercode, eine 2-Byte-ganz Zahl Fehlermeldungs Länge und eine Fehlermeldung enthalten.  
  
     Das Datenstrom Protokoll ist ein logisches Protokoll und ist unabhängig von den Protokollen, die vom zugrunde liegenden Netzwerk verwendet werden. Folglich kann ein einzelnes Datenstrom Protokoll in der Regel für eine Reihe von verschiedenen Netzwerken verwendet werden. Datenstrom Protokolle sind in der Regel proprietäre und wurden für die Arbeit mit einem bestimmten DBMS optimiert.  
  
-   **Prozessübergreifende Kommunikationsmechanismus** Der IPC-Mechanismus (prozessübergreifende Communication) ist der Prozess, mit dem ein Prozess mit einem anderen kommuniziert. Beispiele hierfür sind Named Pipes, TCP/IP-Sockets und DECnet-Sockets. Die Auswahl des IPC-Mechanismus wird durch das Betriebssystem und das verwendete Netzwerk eingeschränkt.  
  
-   **Netzwerkprotokoll** Das Netzwerkprotokoll wird verwendet, um den Datenstrom über ein Netzwerk zu transportieren. Sie kann als die Grundlagen betrachtet werden, die die IPC-Mechanismen unterstützen, die zum Implementieren des Datenstrom Protokolls verwendet werden, sowie die Unterstützung grundlegender Netzwerk Vorgänge wie Dateiübertragungen und Druckfreigabe. Netzwerkprotokolle umfassen NetBEUI, TCP/IP, DECnet und SPX/IPX und sind für jedes Netzwerk spezifisch.
