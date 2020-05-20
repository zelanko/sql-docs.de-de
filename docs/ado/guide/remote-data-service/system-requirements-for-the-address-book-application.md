---
title: System Anforderungen für die Adressbuch Anwendung | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8aec1ebbb5d83829431e1045e746c99f1569dc48
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764631"
---
# <a name="system-requirements-for-the-address-book-application"></a>Systemanforderungen für die Adress Book-Anwendung
Zum Einrichten der Address Book-Beispielanwendung müssen Sie die folgenden Software-und Datenbankanforderungen erfüllen:  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="software-requirements"></a>Softwareanforderungen  
 Die Softwareanforderungen für den Server Computer zum Ausführen dieser Webanwendung umfassen Folgendes:  
  
-   Microsoft Windows NT® Server 4,0, mit Service Pack 3 oder höher oder Microsoft Windows® 2000 Server.  
  
-   Microsoft Internetinformationsdienste (IIS), Version 3,0 oder höher, mit Active Server Seiten.  
  
 Die Softwareanforderungen für den Client Computer für die Ausführung dieser Webanwendung umfassen Folgendes:  
  
-   Microsoft Internet Explorer 4,0 oder höher.  
  
-   Microsoft Windows NT 4,0 Workstation oder Server, Windows 2000 oder Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Datenbankanforderungen  
 Um dieses Beispiel verwenden zu können, benötigen Sie Folgendes:  
  
-   Eine operative Microsoft® SQL Server Version 6,5 oder höher.  
  
-   Berechtigungen zum Erstellen der Datenbank und Auffüllen der Datenbank mit den Beispiel Daten.  
  
-   Überprüfung der gefüllten Daten über Enterprise Manager oder die isql-Hilfsprogramme (in SQL Server 7,0) als Query Analyzer bezeichnet.  
  
 Wenn Sie nicht über Berechtigungen verfügen, muss der Datenbankadministrator möglicherweise das System einrichten und ihnen Zugriffsberechtigungen für die Datenbank erteilen oder die Datenbank für Sie einrichten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen des Adressbuch-SQL-Skripts](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Ausführen der Adress Book-Beispielanwendung](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


