---
description: RDS-Szenario
title: RDS-Szenario | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f5a1058b23c92160b039d2cb439d429b46bfcb98
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452092"
---
# <a name="rds-scenario"></a>RDS-Szenario
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Die Adressbuch Anwendung ist ein Szenario, das zeigt, wie Sie Remote Data Service (RDS) verwenden, um eine einfache, Daten kompatible Webanwendung zu erstellen, ein Online-Unternehmens Adressbuch. Dieses Szenario eignet sich für Microsoft Visual Basic Scripting Edition (VBScript) und com-Programmierer, die erfahren möchten, wie Sie Daten kompatible ActiveX-Steuerelemente mit RDS verwenden, und für erfahrene Softwareentwickler, die datenzentrierte Webanwendungen erstellen möchten.  
  
 In diesem Szenario wird davon ausgegangen, dass Sie wissen, wie grundlegende HTML-Layouttags verwendet, DHTML-Daten Bindungs Techniken verwendet und mit ActiveX-Steuerelementen programmiert werden  
  
 Wenn Sie das SDK installiert haben, finden Sie den gesamten Quellcode für die Address Book-Beispielanwendung im SDK-Verzeichnis unter samples\dataaccess\rds\addressbook\addressbook.ASP. Geben Sie zum Anzeigen des Adressbuch Szenarios in Internet Explorer 4,0 oder höher **https://*Webserver*/RDS/addressbook/addressbook.ASP** ein, wobei *Webserver* der Name ist, der Ihrem Windows NT 4,0-oder Windows 2000-Webserver Computer zugewiesen ist, auf dem Internetinformationsdienste (IIS) und ASP ausgeführt wird.  
  
## <a name="introduction-to-address-book"></a>Einführung in das Adressbuch  
 Die Address Book-Beispielanwendung stellt ein einfaches Online Adressbuch bereit, mit dem Sie ein durchsuchbares Verzeichnis über ein Intranet veröffentlichen können. Das Adressbuch ist so konzipiert, dass ein Benutzer in einem oder mehreren Feldern eine Such Zeichenfolge eingeben kann, um Informationen zu Mitarbeitern anzufordern. Um Ihnen die grundlegenden Features von Remote Data Service anzuzeigen, wird die Beispielanwendung absichtlich klein gehalten, mit einer minimalen Anzahl von Objekten und Suchfeldern.  
  
 Die Anwendungs Schnittstelle besteht aus den folgenden Teilen:  
  
-   Ein nicht-Visual **RDS. DataControl** -Daten Bindungs Objekt, das vom Client verwendet wird, um eine Verbindung mit der Datenbank herzustellen.  
  
-   HTML-Textfelder, die als Eingabefelder für die Suchkriterien von Employee-Attributen fungieren.  
  
-   HTML-Befehls Schaltflächen zum Erstellen von Abfragen, Löschen von Suchfeldern, Aktualisieren der Datenbank mit Mitarbeiter Informationen, Abbrechen ausstehender Änderungen und Navigieren in den Daten Zeilen, die im Raster angezeigt werden.  
  
-   DHTML-Datenbindung zum Anzeigen von Daten, die von Abfragen an eine Back-End-Datenbank (über RDS) zurückgegeben werden **. DataControl** -Daten Bindungs Objekt) in einer Tabelle.  
  
-   VBScript-Routinen, die jedes der bereits erwähnten Elemente verbinden und die Interaktion ermöglichen. VBScript-Code wird auch verwendet, um RDS zu initialisieren **. DataControl** -Objekt und erstellen Sie die Spaltenüberschriften in der HTML-Tabelle dynamisch aus den Namen der **RDS. DataControl** -Recordsetfelder.  
  
 Befolgen Sie die Links Zwischenschritt-für-Schritt-Anleitung, um das Szenario einzurichten und auszuführen, und weitere Informationen zur Funktionsweise des Szenarios.  
  
 Dieses Szenario enthält die folgenden Themen.  
  
-   [Systemanforderungen für die Adress Book-Anwendung](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [Ausführen des Adress Book-SQL-Skripts](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [Ausführen der Adress Book-Beispielanwendung](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [Adress Book-Datenbindungsobjekt](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [Adress Book-Befehlsschaltflächen](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [Adress Book-Navigationsschaltflächen](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Anforderungen für die Adressbuch Anwendung](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [RDS-Grundlagen](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)


