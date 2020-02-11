---
title: Abschnitt "Anpassungs Datei (userlist)" | Microsoft-Dokumentation
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
ms.openlocfilehash: 558fd9c8379808e6c2f109a9c9584e8831cddd0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922764"
---
# <a name="customization-file-userlist-section"></a>UserList-Abschnitt der Anpassungsdatei
Der Abschnitt " **userlist** " bezieht sich auf den **Connect** -Abschnitt mit dem gleichen Abschnitts *bezeichnerparameter* .  
  
 Dieser Abschnitt kann einen *Benutzer Zugriffs Eintrag*enthalten, der die Zugriffsrechte für den angegebenen Benutzer angibt und den *Standard* *Zugriffs Eintrag* im entsprechenden **Connect** -Abschnitt überschreibt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
 Ein Benutzer Zugriffs Eintrag hat folgendes Format:  
  
 _Benutzername_**=**   
 **_accessRights_**  
  
|Teil|BESCHREIBUNG|  
|----------|-----------------|  
|*User*|Der *Benutzername* der Person, die diese Verbindung verwendet. Gültige Benutzernamen werden mit dem Dialogfeld IIS **Service Manager** erstellt.|  
|**_accessRights_**|Eine der folgenden Zugriffsrechte:<br /><br /> -   **NoAccess** : der Benutzer kann nicht auf die Datenquelle zugreifen.<br />-   Schreib **geschützt: der** Benutzer kann die Datenquelle lesen.<br />-   " **Lesewrite** ": der Benutzer kann die Datenquelle lesen oder in diese schreiben.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Abschnitt "Anpassungs Datei Protokolle"](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Client Einstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zur Anpassungs Datei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


