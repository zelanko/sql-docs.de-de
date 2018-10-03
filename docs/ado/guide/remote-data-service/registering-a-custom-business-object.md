---
title: Registrieren ein benutzerdefiniertes Geschäftsobjekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- custom business object in RDS [ADO]
- registering custom business objects in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: e9032ad8-d14c-42e3-ba13-cb5f00084a79
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d5122b7484e35f16a357b590a843a4a6dd81d13
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655458"
---
# <a name="registering-a-custom-business-object"></a>Registrieren eines benutzerdefinierten Geschäftsobjekts
Um ein benutzerdefiniertes Geschäftsobjekt (.dll oder .exe) wurde erfolgreich über den Webserver zu starten, muss das Geschäftsobjekt, das die ProgID in der Registrierung eingegeben werden, wie in diesem Verfahren beschrieben. Dieses Feature von RDS schützt die Sicherheit Ihres Webservers durch nur zulässige ausführbare Dateien ausführen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!NOTE]
>  Für MDAC 2.0 und höher und Windows DAC, die Business-Standardobjekts, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), ist nicht standardmäßig während der Installation von MDAC/Windows DAC registriert. Aber wenn **RDSServer.DataFactory** registriert wurde, als für die Ausführung auf dem Computer vor der Installation sicher, wird der Registrierungseintrag für die neue Installation beibehalten.  
  
### <a name="to-register-a-custom-business-object"></a>So registrieren Sie ein benutzerdefiniertes Geschäftsobjekt:  
  
1.  Klicken Sie auf **starten** , und klicken Sie dann auf **ausführen**.  
  
2.  Typ **"regedit"** , und klicken Sie auf **OK**.  
  
3.  Navigieren Sie im Registrierungs-Editor zu den **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch** Registrierungsschlüssel.  
  
4.  Wählen Sie die **ADCLaunch** Schlüssel, und klicken Sie dann die **bearbeiten**, zeigen Sie auf **neu** , und klicken Sie auf **Schlüssel**.  
  
5.  Geben Sie die ProgID des benutzerdefinierten Objekts, und klicken Sie auf **EINGABETASTE**. Lassen Sie die **Wert** Eintrag leer.


