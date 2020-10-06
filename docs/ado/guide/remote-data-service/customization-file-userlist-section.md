---
description: UserList-Abschnitt der Anpassungsdatei
title: Abschnitt "Anpassungs Datei (userlist)" | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: b09e5f9356ad196e03c970623369d4918a6f5506
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724751"
---
# <a name="customization-file-userlist-section"></a>UserList-Abschnitt der Anpassungsdatei
Der Abschnitt " **userlist** " bezieht sich auf den **Connect** -Abschnitt mit dem gleichen Abschnitts *bezeichnerparameter* .  
  
 Dieser Abschnitt kann einen *Benutzer Zugriffs Eintrag*enthalten, der die Zugriffsrechte für den angegebenen Benutzer angibt und den *Standard* *Zugriffs Eintrag* im entsprechenden **Connect** -Abschnitt überschreibt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
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