---
title: Aktivieren einer DLL zur Ausführung unter DCOM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95bfd4d5f5c5dac4f5ee4a74369e68bd40f8f698
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788848"
---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Aktivieren einer DLL zur Ausführung unter DCOM
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Die folgenden Schritte beschreiben, wie Sie eine Business-Objekt-DLL für die Verwendung DCOM und Microsoft Internet Informationen Services (HTTP) über Komponentendienste zu aktivieren.  
  
1.  Erstellen Sie ein neues, leeres Paket, das Komponentendienste-MMC-Snap-in.  
  
     Sie können das Komponentendienste-MMC-Snap-in zum Erstellen eines Pakets aus, und fügen die DLL in dieses Paket. Dadurch kann die DLL-Datei zugegriffen werden, über DCOM, sondern über IIS entfernt. (Wenn Sie in der Registrierung für die DLL-Datei, überprüfen Sie die **Inproc** Schlüssel jetzt leer ist; das Festlegen der Activation-Attribut, das erklärt weiter unten in diesem Thema Fügt einen Wert in der **Inproc** Schlüssel.)  
  
2.  Installieren Sie ein Geschäftsobjekt, in dem Paket.  
  
     -oder-  
  
     Importieren der [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt in das Paket.  
  
3.  Legen Sie das Attribut "Aktivierung" das Paket **im Prozess des Erstellers** (Library-Anwendung).  
  
     Damit wird die DLL-Datei über DCOM und IIS auf dem gleichen Computer zugegriffen werden kann, müssen Sie die Komponentendienste-MMC-Snap-in-Aktivierung-Attribut der Komponente festlegen. Nachdem Sie das Attribut, um festgelegt **im Prozess des Erstellers**, werden Sie feststellen, dass ein **Inproc** , Ersatz-DLL der verweist auf eine Komponente Services Serverschlüssel in der Registrierung hinzugefügt wurde.  
  
 Weitere Informationen zu den Komponentendiensten (oder Microsoft Transaction-Dienst, bei Verwendung von Windows NT) und wie Sie diese Schritte ausführen, finden Sie auf der Website von Microsoft Transaction Server.


