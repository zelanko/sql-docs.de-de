---
description: Aktivieren einer DLL zur Ausführung unter DCOM
title: Aktivieren einer DLL-Datei für die DCOM-Aktivierung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
author: rothja
ms.author: jroth
ms.openlocfilehash: 220f4a8abfe37a12a7f0699b9aec8a634691cabe
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91723221"
---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Aktivieren einer DLL zur Ausführung unter DCOM
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 In den folgenden Schritten wird beschrieben, wie Sie eine Geschäftsobjekt-DLL für die Verwendung von DCOM und Microsoft Internetinformationsdienste (http) über Komponenten Dienste aktivieren.  
  
1.  Erstellen Sie im MMC-Snap-in "Komponenten Dienste" ein neues leeres Paket.  
  
     Verwenden Sie das MMC-Snap-in "Komponenten Dienste", um ein Paket zu erstellen und die dll zu diesem Paket hinzuzufügen. Dadurch kann die DLL-Datei über DCOM zugänglich gemacht werden. die Barrierefreiheit wird jedoch über IIS entfernt. (Wenn Sie die Registrierung für die DLL-Datei einchecken, ist der **INPROC** -Schlüssel nun leer. durch das Festlegen des Aktivierungs Attributs, das weiter unten in diesem Thema erläutert wird, wird ein Wert im **INPROC** -Schlüssel hinzugefügt.)  
  
2.  Installieren Sie ein Geschäftsobjekt im Paket.  
  
     Oder  
  
     Importieren Sie das [RDSServer. DataFactory](../../reference/rds-api/datafactory-object-rdsserver.md) -Objekt in das Paket.  
  
3.  Legen Sie das Aktivierungs Attribut für das Paket **im Prozess des Erstellers** (Bibliotheks Anwendung) auf fest.  
  
     Um die DLL-Datei über DCOM und IIS auf demselben Computer zugänglich zu machen, müssen Sie das Aktivierungs Attribut der Komponente im MMC-Snap-in "Komponenten Dienste" festlegen. Nachdem Sie **im Prozess des Erstellers das-** Attribut auf festgelegt haben, werden Sie feststellen, dass in der Registrierung ein **INPROC** -Server Schlüssel hinzugefügt wurde, der auf die Komponente "Ersatz. dll" für Komponenten Dienste verweist.  
  
 Weitere Informationen zu den Komponenten Diensten (oder zum Microsoft Transaction Service, wenn Sie Windows NT verwenden) und zum Ausführen dieser Schritte finden Sie auf der Microsoft Transaction Server-Website.