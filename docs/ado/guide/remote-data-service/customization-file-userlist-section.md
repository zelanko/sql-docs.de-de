---
description: UserList-Abschnitt der Anpassungsdatei
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 14308aeda28311b73dc34a323a9a9bf662770e8b
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759814"
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
|*userName*|Der *Benutzername* der Person, die diese Verbindung verwendet. Gültige Benutzernamen werden mit dem Dialogfeld IIS **Service Manager** erstellt.|  
|**_accessRights_**|Eine der folgenden Zugriffsrechte:<br /><br /> -   **NoAccess** : der Benutzer kann nicht auf die Datenquelle zugreifen.<br />-   Schreib **geschützt: der** Benutzer kann die Datenquelle lesen.<br />-   " **Lesewrite** ": der Benutzer kann die Datenquelle lesen oder in diese schreiben.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](./customization-file-connect-section.md)   
 [Abschnitt "Anpassungs Datei Protokolle"](./customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](./customization-file-sql-section.md)   
 [DataFactory-Anpassung](./datafactory-customization.md)   
 [Erforderliche Client Einstellungen](./required-client-settings.md)   
 [Grundlegendes zur Anpassungs Datei](./understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](./writing-your-own-customized-handler.md)