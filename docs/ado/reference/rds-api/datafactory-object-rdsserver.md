---
title: DataFactory-Objekt (RDSServer) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 189dc8604883d8d91a8bc223c54dd3cb5c14969e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63134362"
---
# <a name="datafactory-object-rdsserver"></a>DataFactory-Objekt (RDSServer)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Diese serverseitige Standardobjekt implementiert Methoden, die Lese-/Schreibzugriff Datenzugriff mit angegebenen Datenquellen für die clientseitige Anwendungen bereitstellen.  
  
 Die **RDSServer.DataFactory** Objekt dient als ein serverseitiges Automatisierungsobjekt, das Clientanforderungen empfängt. In einer Internet-Implementierung befindet sich auf einem Webserver, und es wird von der Komponente ADISAPI instanziiert. Die **RDSServer.DataFactory** Objekt bereitstellt, gelesen und Schreibzugriff auf die angegebenen Daten Datenquellen, enthält jedoch kein Validierung oder Regeln die Geschäftslogik.  
  
 Wenn Sie eine Methode verwenden, die sowohl in der **RDSServer.DataFactory** und [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekte aufweist, Remote Data Service verwendet die **RDS. DataControl** Version standardmäßig. Standardmäßig geht davon aus, eine grundlegende programmierungszenario, in dem die **RDSServer.DataFactory** dient als generische serverseitige-Objekt.  
  
 Wenn Sie Ihre Webanwendung aufgabenspezifische serverseitige Verarbeitung behandeln möchten, können Sie ersetzen die **RDSServer.DataFactory** mit einem benutzerdefinierten Objekt.  
  
 Können Sie serverseitige-Objekte, die aufgerufen werden erstellen die **RDSServer.DataFactory** Methoden, wie z. B. [Abfrage](../../../ado/reference/rds-api/query-method-rds.md) und [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md). Dies ist hilfreich, wenn Sie Ihre Geschäftsobjekte Funktionen hinzugefügt, aber vorhandene Remote Data Service-Technologien nutzen möchten.  
  
 Die **DataFactory** Objekt ist nicht sicher für Skripts, die auf dem Client ausgeführt.  
  
 Die Klassen-ID für die **RDSServer.DataFactory** Objekt ist 9381D8F5-0288-11-D 0-9501-00AA00B911A5.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [DataFactory-Objekt (RDSServer) – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [DataFactory-Objekt, Abfragemethode und CreateObject-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


