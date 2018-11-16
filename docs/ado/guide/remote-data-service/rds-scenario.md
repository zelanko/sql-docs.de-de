---
title: RDS-Architektur | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e936b6b68a67c1616a00d38f6d84776d44ef327
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559434"
---
# <a name="rds-scenario"></a>RDS-Szenario
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Das Adressbuch-App ist ein Szenario, das zeigt, wie Sie Remote Data Service (RDS) verwenden, um eine einfache, Daten-fähigen Webanwendung zu erstellen – ein online-Unternehmens-Adressbuch. Dieses Szenario eignet sich für Microsoft Visual Basic Scripting Edition (VBScript) COM-Programmierer, die möchten erfahren, wie Sie mithilfe von datenkompatible ActiveX-Steuerelemente mit RDS und für Software von erfahrenen Entwickler möchten datenorientierte Webanwendungen erstellen.  
  
 Dieses Szenario wird davon ausgegangen, dass Sie wissen, wie Sie grundlegende HTML-Layouttags, DHTML-Datenbindung mit Techniken und Programm mit ActiveX-Steuerelemente verwenden.  
  
 Wenn Sie das SDK installiert haben, kann der vollständigen Quellcode für die beispielanwendung Adressbuch im SDK-Verzeichnis am samples\dataaccess\rds\AddressBook\AddressBook.asp gefunden werden. In Internet Explorer 4.0 oder höher, geben Sie zum Anzeigen der Szenario-Adressbuch **https://*Webserver*/RDS/AddressBook/AddressBook.asp** , in denen *Webserver* ist der Name erhält auf Ihrer Windows NT 4.0 oder Windows 2000-Web-Server-Computer, auf denen Internet Information Services (IIS) und ASP ausgeführt wird.  
  
## <a name="introduction-to-address-book"></a>Einführung in das Buch zu beheben.  
 Die Address Book-beispielanwendung enthält ein einfachen online-Adressbuch, das Sie verwenden können, um einem durchsuchbaren Verzeichnis über ein Intranet zu veröffentlichen. Das Adressbuch ist so konzipiert, dass ein Benutzer eine Suchzeichenfolge in ein oder mehrere Felder zum Anfordern von Informationen zu Mitarbeitern eingeben kann. Damit die grundlegenden Funktionen von Remote Data Service angezeigt werden, wird die beispielanwendung absichtlich klein und verfügen über eine minimale Anzahl von Objekten und Suchfelder beibehalten.  
  
 Die Anwendungsschnittstelle besteht aus den folgenden Teilen:  
  
-   Eine nicht visuelle **RDS. DataControl** Datenbindung-Objekt, das vom Client für die Verbindung mit der Datenbank verwendet wird.  
  
-   HTML-Inhalt der Textfelder, die als Eingabefelder für die Suchkriterien für Mitarbeiter Attribute fungieren.  
  
-   HTML-Befehlsschaltflächen zum Erstellen von Abfragen, Suchfelder zu löschen, aktualisieren Sie die Datenbank mit Informationen zu Mitarbeitern, ausstehende Änderungen Abbrechen, und navigieren die Zeilen mit Daten, die im Raster angezeigt.  
  
-   DHTML-Datenbindung zum Anzeigen von Daten von Abfragen für ein Back-End-Datenbank zurückgegeben (über die **RDS. DataControl** Datenbindungsobjekt) in einer Tabelle.  
  
-   VBScript-Routinen, die verbinden Sie alle Elemente, die bereits erwähnten und Interaktion ermöglichen. VBScript-Code wird auch zum Initialisieren der **RDS. DataControl** Objekt, und erstellen Sie dynamisch die Spaltenüberschriften in der HTML-Tabelle aus den Namen der der **RDS. DataControl** Recordset-Feldern.  
  
 Führen Sie die Links aus Schritt zum Schritt zum Einrichten, und führen Sie das Szenario, und erfahren Sie, wie das Szenario funktioniert.  
  
 Dieses Szenario enthält die folgenden Themen.  
  
-   [Systemanforderungen für die Adress Book-Anwendung](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [Ausführen des Adress Book-SQL-Skripts](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [Ausführen der Adress Book-Beispielanwendung](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [Adress Book-Datenbindungsobjekt](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [Adress Book-Befehlsschaltflächen](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [Adress Book-Navigationsschaltflächen](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Systemanforderungen für die Adress Book-Anwendung](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)


