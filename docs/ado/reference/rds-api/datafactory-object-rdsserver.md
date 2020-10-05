---
description: DataFactory-Objekt (RDSServer)
title: DataFactory-Objekt (RDSServer) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e31d39f0820a485d4954d789fe2dfb398d8490b
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91720981"
---
# <a name="datafactory-object-rdsserver"></a>DataFactory-Objekt (RDSServer)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 Dieses standardmäßige serverseitige Geschäftsobjekt implementiert Methoden, die Lese-/Schreibdaten Zugriff auf bestimmte Datenquellen für Client seitige Anwendungen bereitstellen.  
  
 Das **RDSServer. DataFactory** -Objekt ist als serverseitiges Automatisierungs Objekt konzipiert, das Client Anforderungen empfängt. In einer Internet Implementierung befindet er sich auf einem Webserver und wird von der ADISAPI-Komponente instanziiert. Das **RDSServer. DataFactory** -Objekt bietet Lese-und Schreibzugriff auf angegebene Datenquellen, enthält jedoch keine Validierungs-oder Geschäftsregel Logik.  
  
 Wenn Sie eine Methode verwenden, die sowohl in **RDSServer. DataFactory** als auch in [RDS verfügbar ist. DataControl](./datacontrol-object-rds.md) -Objekte, Remote Data Service verwendet **RDS. Standardmäßig DataControl** -Version. Standardmäßig wird von einem grundlegenden Programmier Szenario ausgegangen, bei dem **RDSServer. DataFactory** als allgemeines serverseitiges Geschäftsobjekt fungiert.  
  
 Wenn Sie möchten, dass die Webanwendung die Task spezifische serverseitige Verarbeitung behandelt, können Sie **RDSServer. DataFactory** durch ein benutzerdefiniertes Geschäftsobjekt ersetzen.  
  
 Sie können serverseitige Geschäftsobjekte erstellen, die die **RDSServer. DataFactory** -Methoden aufrufen, z. b. " [Query](./query-method-rds.md) " und " [kreaterecordset](./createrecordset-method-rds.md)". Dies ist hilfreich, wenn Sie Ihren Geschäftsobjekten Funktionen hinzufügen möchten, aber vorhandene Technologien für den Remote Datendienst nutzen möchten.  
  
 Das **DataFactory** -Objekt ist für Skripts, die auf der Clientseite ausgeführt werden, nicht sicher.  
  
 Die Klassen-ID für das **RDSServer. DataFactory** -Objekt lautet 9381d8s5-0288-11D0-9501-00aa00b911a5.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [DataFactory-Objekt (RDSServer) – Eigenschaften, Methoden und Ereignisse](./datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataFactory-Objekt, Abfragemethode und CreateObject-Methode – Beispiel (VBScript)](./datafactory-object-query-method-and-createobject-method-example-vbscript.md)