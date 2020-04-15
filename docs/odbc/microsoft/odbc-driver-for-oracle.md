---
title: ODBC-Treiber für Oracle | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 093cb7352a7f509b0afcc061e2691311bb183169
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298130"
---
# <a name="odbc-driver-for-oracle"></a>ODBC-Treiber für Oracle
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Mit dem Microsoft® ODBC-Treiber für Oracle können Sie Ihre ODBC-kompatible Anwendung mit einer Oracle-Datenbank verbinden. Der ODBC-Treiber für Oracle entspricht der ODBC-Spezifikation (Open Database Connectivity), die in der *ODBC-Programmiererreferenz*beschrieben ist. Es ermöglicht den Zugriff auf PL/SQL-Pakete, XA/DTC-Integration und Oracle-Zugriff über Internet Information Services (IIS).  
  
 Oracle RDBMS ist ein relationales Datenbankmanagementsystem für mehrere Benutzer, das mit verschiedenen Workstation- und Minicomputer-Betriebssystemen ausgeführt wird. IBM-kompatible Computer mit Microsoft Windows können über ein Netzwerk mit Oracle-Datenbankservern kommunizieren. Zu den unterstützten Netzwerken gehören Microsoft LAN Manager, NetWare, VINES, DECnet und jedes Netzwerk, das TCP/IP unterstützt.  
  
 Der ODBC-Treiber für Oracle ermöglicht einer Anwendung den Zugriff auf Daten in einer Oracle-Datenbank über die ODBC-Schnittstelle. Der Treiber kann auf lokale Oracle-Datenbanken zugreifen oder über SQL*Net mit dem Netzwerk kommunizieren. Das folgende Diagramm beschreibt diese Anwendung und Treiberarchitektur.  
  
 ![ODBC Driver für Oracle-&#47;Treiberarchitektur](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Der ODBC-Treiber für Oracle entspricht API-Konformitätsstufe 1 und SQL-Konformitäts-Level Core. Es unterstützt auch einige Funktionen in API-Konformitätsstufe 2 und die meisten Der Grammatik in der Core- und Extended SQL-Konformitätsebene. Der Treiber ist ODBC 2.5-kompatibel und unterstützt 32-Bit-Systeme. Oracle 7.3x wird vollständig unterstützt. Oracle8 bietet nur eingeschränkten Support. Der ODBC-Treiber für Oracle unterstützt weder die neuen Oracle8-Datentypen - Unicode-Datentypen, BLOBs, CLOBs usw. - noch das neue relationale Objektmodell von Oracle. Weitere Informationen zu unterstützten Datentypen finden Sie unter [Unterstützte Datentypen](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) in diesem Handbuch.  
  
 Für den Zugriff auf Oracle-Daten sind die folgenden Komponenten erforderlich:  
  
-   Der ODBC-Treiber für Oracle  
  
-   Eine Oracle RDBMS-Datenbank  
  
-   Oracle Client-Software  
  
 Zusätzlich für Remote-Verbindungen:  
  
-   Ein Netzwerk, das die Computer, auf denen der Treiber ausgeführt wird, mit der Datenbank verbindet. Das Netzwerk muss SQL*Net-Verbindungen unterstützen.  
  
## <a name="component-documentation"></a>Komponentendokumentation  
 Dieses Handbuch enthält detaillierte Informationen zum Einrichten und Konfigurieren des Microsoft ODBC-Treibers für Oracle und zum Hinzufügen programmgesteuerter Funktionen. Es enthält auch technisches Referenzmaterial.  
  
 Informationen zum spezifischen Oracle-Produktverhalten finden Sie in der Dokumentation zum Oracle-Produkt.  
  
 Informationen zum Einrichten oder Konfigurieren des Microsoft ODBC-Treibers für Oracle mithilfe des ODBC-Datenquellenadministrators finden Sie in der Dokumentation [zum ODBC-Datenquellenadministrator.](../../odbc/admin/odbc-data-source-administrator.md)  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [ODBC-Treiber für Oracle-Benutzerhandbuch](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [ODBC-Treiber für Oracle-Programmierreferenz](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
