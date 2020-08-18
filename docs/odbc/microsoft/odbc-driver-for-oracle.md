---
description: ODBC-Treiber für Oracle
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a561539ff960dfa6691d26496b1b62d2ee8ae763
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449332"
---
# <a name="odbc-driver-for-oracle"></a>ODBC-Treiber für Oracle
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Mit dem Microsoft® ODBC-Treiber für Oracle können Sie Ihre ODBC-kompatible Anwendung mit einer Oracle-Datenbank verbinden. Der ODBC-Treiber für Oracle entspricht der Open Database Connectivity (ODBC)-Spezifikation, die in der *ODBC Programmer es Reference*beschrieben wird. Sie ermöglicht den Zugriff auf PL/SQL-Pakete, XA/DTC-Integration und Oracle-Zugriff aus Internetinformationsdienste (IIS).  
  
 Oracle RDBMS ist ein mehr Benutzer fähiges Verwaltungssystem für relationale Datenbanken, das mit verschiedenen Betriebssystemen für Arbeitsstationen und Minicomputer ausgeführt wird. IBM-kompatible Computer, auf denen Microsoft Windows ausgeführt wird, können mit Oracle-Datenbankservern über ein Netzwerk kommunizieren. Zu den unterstützten Netzwerken zählen Microsoft LAN Manager, NetWare, Vines, DECnet und jedes Netzwerk, das TCP/IP unterstützt.  
  
 Der ODBC-Treiber für Oracle ermöglicht einer Anwendung den Zugriff auf Daten in einer Oracle-Datenbank über die ODBC-Schnittstelle. Der Treiber kann auf lokale Oracle-Datenbanken zugreifen, oder er kann über SQL * Net mit dem Netzwerk kommunizieren. Im folgenden Diagramm werden diese Anwendungs-und Treiberarchitektur ausführlich erläutert.  
  
 ![ODBC-Treiber für Oracle App&#47;-Treiberarchitektur](../../odbc/microsoft/media/orcdrvsdkarch.gif "Orcdrvsdkarch")  
  
 Der ODBC-Treiber für Oracle entspricht der API-Konformitätsstufe 1 und der SQL-Konformitätsstufe Core. Es unterstützt außerdem einige Funktionen in API-Konformitätsstufe 2 und den meisten der Grammatik in den Konformitätsstufen "Core" und "Extended SQL". Der Treiber ist ODBC 2,5-kompatibel und unterstützt 32-Bit-Systeme. Oracle 7.3 x wird vollständig unterstützt. Oracle8 wird nur eingeschränkt unterstützt. Der ODBC-Treiber für Oracle unterstützt keinen der neuen Oracle8-Datentypen (Unicode-Datentypen, BLOB, CLOB usw.) und unterstützt auch das neue relationale Objektmodell von Oracle. Weitere Informationen zu unterstützten Datentypen finden Sie [unter Unterstützte Datentypen](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) in diesem Handbuch.  
  
 Für den Zugriff auf Oracle-Daten sind folgende Komponenten erforderlich:  
  
-   Der ODBC-Treiber für Oracle  
  
-   Eine Oracle-RDBMS-Datenbank  
  
-   Oracle-Client Software  
  
 Außerdem gilt für Remote Verbindungen Folgendes:  
  
-   Ein Netzwerk, das die Computer, auf denen der Treiber ausgeführt wird, und die-Datenbank verbindet. Das Netzwerk muss SQL * NET-Verbindungen unterstützen.  
  
## <a name="component-documentation"></a>Komponentendokumentation  
 Dieses Handbuch enthält ausführliche Informationen zum Einrichten und Konfigurieren des Microsoft ODBC-Treibers für Oracle und zum Hinzufügen von programmatischen Funktionen. Außerdem enthält es technische Referenzmaterial.  
  
 Informationen zu bestimmten Oracle-Produktverhalten finden Sie in der Dokumentation, die das Oracle-Produkt begleitet.  
  
 Informationen zum Einrichten oder Konfigurieren des Microsoft ODBC-Treibers für Oracle mit dem ODBC-Datenquellen-Administrator finden Sie in der Dokumentation zum [ODBC-Datenquellen-Administrator](../../odbc/admin/odbc-data-source-administrator.md) .  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [ODBC-Treiber für Oracle-Benutzerhandbuch](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [ODBC-Treiber für Oracle-Programmierreferenz](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
