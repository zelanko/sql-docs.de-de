---
title: Registrieren von Geschäftsobjekten auf dem Client für die Verwendung mit DCOM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 999eb43304150c9af8d61be591f3c4c0ab62566f
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559577"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Registrieren von Geschäftsobjekten auf dem Client für die Verwendung mit DCOM
Benutzerdefinierte Geschäftsobjekte müssen sicherstellen, dass es sich bei die Clientseite ihren Programmnamen (ProgId), eine ID (CLSID) zugeordnet werden kann, die über DCOM verwendet werden kann. Aus diesem Grund muss die ProgID des DCOM-Objekte werden in der Registrierung der clientseitigen und die Klassen-ID des Objekts serverseitige zugeordnet. Für die anderen unterstützten Protokolle (HTTP, HTTPS und in-Process) ist dies nicht erforderlich.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Stellen Sie z. B., wenn Sie eine serverseitige Objekt mit dem Namen MyBObj mit einer bestimmten Klasse-ID, z. B. "{00112233-4455-6677-8899-00AABBCCDDEE}", verfügbar machen Sie sicher, dass die folgenden Einträge in die Registrierung der clientseitigen hinzugefügt werden:  
  
```console
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


