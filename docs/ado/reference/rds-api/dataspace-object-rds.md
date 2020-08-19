---
description: DataSpace-Objekt (RDS)
title: DataSpace-Objekt (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace object [RDS]
ms.assetid: 9194bffa-5bdf-4dff-af86-f7158c23bfa7
author: rothja
ms.author: jroth
ms.openlocfilehash: bb24cdf6acbe58891177dfc84d6c1e341699b129
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439062"
---
# <a name="dataspace-object-rds"></a>DataSpace-Objekt (RDS)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Erstellt Client seitige Proxys für benutzerdefinierte Geschäftsobjekte auf der mittleren Ebene.  
  
 Der Remote Datendienst benötigt Geschäftsobjekt Proxys, damit Client seitige Komponenten mit Geschäftsobjekten kommunizieren können, die sich auf der mittleren Ebene befinden. Proxys vereinfachen das Verpacken, das Entpacken und transportieren (Mars Hallen) der [Recordsetdaten](../../../ado/reference/ado-api/recordset-object-ado.md) der Anwendung über Prozess-oder Computer Grenzen hinweg.  
  
 Der Remote Datendienst verwendet **RDS. ** Die Methode " [kreateobject](../../../ado/reference/rds-api/createobject-method-rds.md) " des DataSpace-Objekts zum Erstellen von Geschäftsobjekt Proxys. Der Geschäftsobjekt Proxy wird dynamisch erstellt, wenn eine Instanz des Objekts der mittleren Ebene des Geschäftsobjekts erstellt wird. Der Remote Datendienst unterstützt die folgenden Protokolle: http, HTTPS (http Secure Sockets), DCOM und in-Process (Client Komponenten und das Geschäftsobjekt befinden sich auf demselben Computer).  
  
> [!NOTE]
>  RDS verhält sich bei **RDS. Das DataSpace** -Objekt verwendet die http-oder HTTPS-Protokolle. Das heißt, dass alle internen Informationen über eine Client Anforderung verworfen werden, nachdem der Server eine Antwort zurückgegeben hat.  
  
> [!NOTE]
>  Obwohl das Geschäftsobjekt für die Lebensdauer des Geschäftsobjekt Proxys vorhanden ist, ist das Geschäftsobjekt tatsächlich nur so lange vorhanden, bis eine Antwort an eine Anforderung gesendet wird. Wenn eine Anforderung ausgegeben wird (d. h., eine Methode wird für das Geschäftsobjekt aufgerufen), öffnet der Proxy eine neue Verbindung mit dem Server, und der Server erstellt eine neue Instanz des Geschäftsobjekts. Nachdem das Geschäftsobjekt auf die Anforderung reagiert hat, zerstört der Server das Geschäftsobjekt und schließt die Verbindung.  
  
> [!NOTE]
>  Dieses Verhalten bedeutet, dass Sie keine Daten von einer Anforderung an eine andere mithilfe einer Geschäftsobjekt Eigenschaft oder-Variablen übergeben können. Sie müssen einen anderen Mechanismus, z. b. eine Datei oder ein Methoden Argument, zum Speichern von Zustandsdaten verwenden.  
  
 Die Klassen-ID für das **RDS. Das DataSpace** -Objekt ist BD96C556-65A3-11D0-983A-00C04FC29E36.  
  
 Das **DataSpace** -Objekt ist für die Skripterstellung sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [DataSpace-Objekt (RDS) – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/rds-api/dataspace-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataSpace-Objekt und CreateObject-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)


