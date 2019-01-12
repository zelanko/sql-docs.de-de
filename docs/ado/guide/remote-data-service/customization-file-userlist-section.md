---
title: UserList-Abschnitt der Anpassungsdatei | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- UserList section in rds [ADO]
- customization file in RDS [ADO]
ms.assetid: 42e8ec20-eaac-4a95-8cb8-4bba93a75bcb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5feb29337ccd0ee79cd1b6f98187cc6fdb52a942
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54130670"
---
# <a name="customization-file-userlist-section"></a>UserList-Abschnitt der Anpassungsdatei
Die **Userlist** Abschnitt bezieht sich auf die **verbinden** Abschnitt mit dem gleichen *Bezeichner* Parameter.  
  
 Kann in diesem Abschnitt enthalten eine *Eintrag des Benutzers Zugriff*, Rechte für den angegebenen Benutzer und überschreibt die gibt an, den Zugriff der *Standard* *greifen Sie auf Eintrag* in der entsprechenden **verbinden** Abschnitt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
 Ein Eintrag des Benutzers Zugriff hat das Format:  
  
 _Benutzername_ **=**   
 **_accessRights_**  
  
|Teil|Description|  
|----------|-----------------|  
|*userName*|Die *Benutzernamen* der Person, die diese Verbindung. Gültige Benutzernamen sind mit IIS hergestellt **Service Manager** Dialogfeld.|  
|**_accessRights_**|Eine der folgenden Zugriffsrechte:<br /><br /> -   **NoAccess** -Benutzer kann nicht auf die Datenquelle zugreifen.<br />-   **ReadOnly** -Benutzer kann die Datenquelle lesen.<br />-   **"ReadWrite"** -Benutzer Lese- oder Schreibzugriff auf Daten in die Datenquelle.|  
  
## <a name="see-also"></a>Siehe auch  
 [Connect-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Logs-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Clienteinstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zu der Anpassungsdatei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


