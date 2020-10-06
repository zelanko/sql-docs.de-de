---
description: Ausführen von Geschäftsobjekten in Komponentendiensten
title: Ausführen von Geschäftsobjekten in Komponenten Diensten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e4cafeaf590c07ec52153a2932de3e105e26950
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91723101"
---
# <a name="running-business-objects-in-component-services"></a>Ausführen von Geschäftsobjekten in Komponentendiensten
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 Geschäftsobjekte können ausführbare Dateien (. exe) oder Dynamic Link Libraries (dll) sein. Die Konfiguration, die Sie zum Ausführen des Geschäftsobjekts verwenden, hängt davon ab, ob es sich bei dem Objekt um eine DLL-oder exe-Datei handelt:  
  
-   Geschäftsobjekte, die als exe-Dateien erstellt werden, können über DCOM aufgerufen werden. Wenn diese Geschäftsobjekte über Internetinformationsdienste (IIS) verwendet werden, unterliegen Sie einem zusätzlichen Marshalling von Daten, wodurch die Client Leistung verlangsamt wird.  
  
-   Geschäftsobjekte, die als DLL-Dateien erstellt werden, können über IIS und somit auch über HTTP verwendet werden. Sie können auch über DCOM nur über Komponenten Dienste oder über den Microsoft-Transaktions Server verwendet werden, wenn Sie Windows NT verwenden. Geschäftsobjektdlls müssen auf dem IIS-Server Computer registriert werden, damit Sie über IIS darauf zugreifen können. Informationen dazu, wie Sie eine DLL für die DCOM-Konfiguration konfigurieren, finden Sie im Abschnitt Aktivieren der DLL-Datei für [DCOM](./enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Wenn Geschäftsobjekte auf der mittleren Ebene mithilfe von **GetObjectContext**, **SetComplete**und **SetAbort**als Komponenten Dienst Komponenten implementiert werden, können die Geschäftsobjekte Komponenten Dienste (oder MTS, wenn Sie Windows NT verwenden) verwenden, um ihren Zustand über mehrere Client Aufrufe hinweg beizubehalten. Dieses Szenario ist mit DCOM möglich, das normalerweise zwischen vertrauenswürdigen Clients und Servern in einem Intranet implementiert wird. In diesem Fall ist das [RDS. Das DataSpace](../../reference/rds-api/dataspace-object-rds.md) -Objekt und die Methode " [kreateobject](../../reference/rds-api/createobject-method-rds.md) " auf der Clientseite werden durch das Transaktionskontext Objekt und die Methode " **kreateinstance** " ersetzt, die von der **itransaktioncontext** -Schnittstelle bereitgestellt und von Komponenten Diensten implementiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](./rds-fundamentals.md)