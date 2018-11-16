---
title: Systemanforderungen für die Adresse buchen Anwendung | Microsoft-Dokumentation
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
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10a7097292562acd60e8b83af9a48bd61aeb8557
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558057"
---
# <a name="system-requirements-for-the-address-book-application"></a>Systemanforderungen für die Adress Book-Anwendung
Um die beispielanwendung Adressbuch einzurichten, müssen Sie die folgenden Software- und Datenbank-Anforderungen erfüllen:  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="software-requirements"></a>Softwareanforderungen  
 Die Server Computer Software-Anforderungen für die Ausführung dieser Webanwendung umfassen:  
  
-   Microsoft Windows NT® Server 4.0 mit Service Pack 3 oder höher oder Microsoft Windows® 2000 Server.  
  
-   Microsoft Internet Informationen Services (IIS) Version 3.0 oder höher, mit Active Server Pages.  
  
 Die softwareanforderungen für den Client Computer für die Ausführung dieser Webanwendung gehören:  
  
-   Microsoft InternetExplorer 4.0 oder höher.  
  
-   Microsoft Windows NT 4.0 Workstation oder Server, Windows 2000 oder Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Datenbankanforderungen  
 Um dieses Beispiel verwenden zu können, benötigen Sie Folgendes:  
  
-   Ein betriebsbereiter Microsoft® SQL Server Version 6.5 oder höher Datenbank-Server.  
  
-   Berechtigungen zum Erstellen der Datenbank, und füllen diese mit den Beispieldaten.  
  
-   Überprüfung der aufgefüllten Daten über das Enterprise Manager oder die ISQL-Dienstprogramme (aufgerufene Query Analyzer in SQL Server 7.0).  
  
 Wenn Sie nicht über Berechtigungen verfügen, müssen möglicherweise der Datenbankadministrator richten Sie die System- und gewähren Sie Zugriff auf die Berechtigung für die Datenbank, oder richten Sie die Datenbank für Sie.  
  
## <a name="see-also"></a>Siehe auch  
 [Die Adresse Book-SQL-Skript ausführen](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Ausführen der Adress Book-Beispielanwendung](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


