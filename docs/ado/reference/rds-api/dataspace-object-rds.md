---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 069e8d2bbc85027c0c0deab6bf05c9da7b0d1f17
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707725"
---
# <a name="dataspace-object-rds"></a>DataSpace-Objekt (RDS)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Erstellt die clientbasierten Proxys an benutzerdefinierte Geschäftsobjekte, die sich auf der mittleren Ebene befinden.  
  
 Remote Data Service benötigt Proxys für Geschäftsobjekte, damit der clientseitigen Komponenten mit Geschäftsobjekten befindet sich auf der mittleren Ebene kommunizieren können. Proxys ermöglichen das Packen, entpacken und (Marshallen) der Anwendung des Transports [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Daten über Prozess- oder Computergrenzen hinweg.  
  
 Remote Data Service verwendet die **RDS. DataSpace** des Objekts [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) Methode, um Proxys für Geschäftsobjekte zu erstellen. Business-Proxy-Objekt wird dynamisch erstellt, wenn eine Instanz des entsprechenden Objekts mittleren Ebene erstellt wird. Remote Data Service unterstützt die folgenden Protokolle: HTTP, HTTPS (HTTP Secure Sockets), DCOM, und in-Process (Client-Komponenten und das Geschäftsobjekt, das auf dem gleichen Computer befinden).  
  
> [!NOTE]
>  RDS in dem "zustandslosen" Weise verhält sich bei der **RDS. DataSpace** Objekt wird das Protokoll HTTP oder HTTPS verwendet. Alle internen Informationen über eine Clientanforderung wird, also verworfen, nachdem der Server eine Antwort zurückgibt.  
  
> [!NOTE]
>  Obwohl das Geschäftsobjekt, das angezeigt wird, für die Lebensdauer des Proxys, Business-Objekt vorhanden ist, ist das Geschäftsobjekt, das tatsächlich vorhanden, nur solange, bis eine Antwort auf eine Anforderung gesendet wird. Wenn eine Anforderung ausgegeben wird (d. h. eine Methode für ein Geschäftsobjekt aufgerufen wird), den Proxy öffnet eine neue Verbindung mit dem Server und der Server erstellt eine neue Instanz des Geschäftsobjekts. Nachdem das Geschäftsobjekt, das auf die Anforderung reagiert, wird der Server das Geschäftsobjekt, das zerstört, und schließt die Verbindung.  
  
> [!NOTE]
>  Dieses Verhalten bedeutet, dass Sie Daten von einer Anforderung in eine andere mithilfe einer Business-Objekteigenschaft oder eine Variable übergeben können. Sie müssen einen anderen Mechanismus, wie z. B. eine Datei oder ein Methodenargument Statusdaten beibehalten nutzen.  
  
 Die Klassen-ID für die **RDS. DataSpace** Objekt ist BD96C556 65A3 - 11-d 0-983A-00C04FC29E36.  
  
 Die **DataSpace** Objekt für die Skripterstellung sicher ist.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [DataSpace-Objekt (RDS) – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/rds-api/dataspace-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [DataSpace-Objekt und CreateObject-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)


