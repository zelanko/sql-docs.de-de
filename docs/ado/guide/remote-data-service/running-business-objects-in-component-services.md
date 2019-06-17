---
title: Ausführen von Geschäftsobjekten in Komponentendiensten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f64909f4f7db1f765d233878631eb90a4760531e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704210"
---
# <a name="running-business-objects-in-component-services"></a>Ausführen von Geschäftsobjekten in Komponentendiensten
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Geschäftsobjekten können es sich um ausführbare Dateien (.exe) oder Dynamic Link Libraries (DLL) sein. Die Konfiguration, die Sie verwenden, um das Geschäftsobjekt, das ausgeführt wird, hängt davon ab, gibt an, ob das Objekt eine .dll oder .exe-Datei ist:  
  
-   Business-Objekten, die als .exe-Dateien erstellt, können über DCOM aufgerufen werden. Wenn diese Geschäftsobjekte durch Internet Information Services (IIS) verwendet werden, unterliegen sie zusätzliche Marshalling von Daten, die Leistung des Clients verlangsamt werden.  
  
-   Business-Objekten, die erstellt werden, da DLL-Dateien, die über IIS verwendet werden können und somit auch von HTTP. Sie können auch über DCOM nur über Komponentendienste oder über Microsoft Transaction Server, verwendet werden, wenn Sie Windows NT verwenden. Das Geschäftsobjekt DLLs müssen auf dem IIS-Servercomputer für den Zugriff darauf über IIS registriert werden. Informationen zum Konfigurieren einer DLL zur Ausführung unter DCOM finden Sie im Abschnitt [Aktivieren einer DLL zur Ausführung unter DCOM](../../../ado/guide/remote-data-service/enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Bei Geschäftsobjekten auf der mittleren Ebene mithilfe von Component Services-Komponenten implementiert sind **GetObjectContext**, **SetComplete**, und **SetAbort**, das Unternehmen Objekte können Component Services (oder MTS, bei Verwendung von Windows NT) Kontextobjekte verwalten Sie ihren Status bei mehreren clientaufrufen. Dieses Szenario ist möglich, mit DCOM, die in der Regel zwischen vertrauenswürdigen Clients und Servern in einem Intranet implementiert wird. In diesem Fall die [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) Objekt und [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) Methode auf der Clientseite werden durch das Kontextobjekt für die Transaktion ersetzt und **CreateInstance** -Methode, die von der bereitgestellten**ITransactionContext** Schnittstelle, und von Component Services implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


