---
title: ODBC-Treiber für Oracle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4685d209d768bd3ff41c1c7367ef6cb6dcd45bcf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043860"
---
# <a name="odbc-driver-for-oracle"></a>ODBC-Treiber für Oracle
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Microsoft® ODBC-Treiber für Oracle können Sie die ODBC-kompatiblen Anwendung mit einer Oracle-Datenbank verbinden. Der ODBC-Treiber für Oracle entspricht der Open Database Connectivity (ODBC)-Spezifikation beschrieben, die der *ODBC Programmer's Reference*. Sie können den Zugriff auf PL/SQL-Pakete, XA/DTC-Integration und Oracle-Zugriff auf in IIS (Internetinformationsdienste).  
  
 Oracle RDBMS ist ein relationaler Mehrbenutzer-Datenbank, die mit verschiedenen Betriebssystemen für die Arbeitsstation und Minicomputer ausgeführt wird. IBM-kompatiblen Computern unter Microsoft Windows können mit Oracle-Datenbank-Server über ein Netzwerk kommunizieren. Unterstützte Netzwerke umfasst Microsoft LAN Manager, NetWare, VINES, DECnet und einem Netzwerk, die TCP/IP unterstützt.  
  
 Der ODBC-Treiber für Oracle ermöglicht eine Anwendung Zugriff auf Daten in einer Oracle-Datenbank über ODBC-Schnittstelle. Der Treiber kann lokale Oracle-Datenbanken zuzugreifen oder sie können kommunizieren, mit dem Netzwerk über SQL * Net. Im folgende Diagramm werden diese Architektur von Anwendungen und Treiber.  
  
 ![ODBC-Treiber für Oracle-app&#47;Treiberarchitektur](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Der ODBC-Treiber für Oracle ist mit API-Standards Level 1 und SQL-Standards Level Core. Es unterstützt auch einige Funktionen in Übereinstimmung mit Standards Ebene 2 und die meisten der Grammatik in der Core und SQL erweitert Übereinstimmungsebenen. Der Treiber ist ODBC 2.5-kompatibel und unterstützt 32-Bit-Systeme. Oracle 7.3 x wird vollständig; unterstützt 8 bietet eine eingeschränkte Unterstützung. Der ODBC-Treiber für Oracle unterstützt keine der neuen Datentypen "8" - Unicode-Datentypen, BLOBs, CLOBs und So weiter – und unterstützt sie neue relationale Objektmodell von Oracle. Weitere Informationen zu unterstützten Datentypen finden Sie unter [Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) in diesem Handbuch.  
  
 Um die Oracle-Daten zugreifen zu können, sind die folgenden Komponenten erforderlich:  
  
-   Der ODBC-Treiber für Oracle  
  
-   Ein Oracle-RDBMS-Datenbank  
  
-   Oracle-Clientsoftware  
  
 Darüber hinaus für Remoteverbindungen einrichten:  
  
-   Ein Netzwerk, das die Computer eine Verbindung herstellt, die der Treiber und der Datenbank ausgeführt. Das Netzwerk muss unterstützen SQL * Net-Verbindungen.  
  
## <a name="component-documentation"></a>Komponente-Dokumentation  
 Dieses Handbuch enthält ausführliche Informationen über das Einrichten und Konfigurieren von Microsoft ODBC-Treiber für Oracle und Hinzufügen von programmgesteuerten Funktionen. Darüber hinaus enthält Technisches Referenzmaterial.  
  
 Informationen zu spezifischen Oracle Produktverhalten beobachten finden Sie in der Dokumentation, die dem Oracle-Produkt beigefügt ist.  
  
 Weitere Informationen zum Einrichten oder konfigurieren den Microsoft ODBC-Treiber für Oracle mit ODBC-Datenquellen-Administrator, finden Sie unter den [ODBC-Datenquellenadministrator](../../odbc/admin/odbc-data-source-administrator.md) Dokumentation.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [ODBC-Treiber für Oracle-Benutzerhandbuch](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [ODBC-Treiber für Oracle-Programmierreferenz](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
