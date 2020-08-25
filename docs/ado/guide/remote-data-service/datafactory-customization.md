---
description: DataFactory-Anpassung
title: DataFactory-Anpassung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
author: rothja
ms.author: jroth
ms.openlocfilehash: c34ae14feda7c0a6847d638f35bf84c6b9cd0fd5
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759804"
---
# <a name="datafactory-customization"></a>DataFactory-Anpassung
Remote Data Service (RDS) bietet eine Möglichkeit, auf einfache Weise Datenzugriff in einem Client/Server-System mit drei Ebenen auszuführen. Ein Client Daten Steuerelement gibt Verbindungs-und Befehls Zeichenfolgen-Parameter an, um eine Abfrage für eine Remote Datenquelle oder Verbindungs [Zeichenfolgen-und Recordset](../../reference/ado-api/recordset-object-ado.md) -Objekt Parameter zum Ausführen eines Updates auszuführen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Die Parameter werden an ein Serverprogramm weitergeleitet, das den Datenzugriffs Vorgang für die Remote Datenquelle ausführt. RDS bietet ein Standardmäßiges Serverprogramm, das als [RDSServer. DataFactory](../../reference/rds-api/datafactory-object-rdsserver.md) -Objekt bezeichnet wird. Das **RDSServer. DataFactory** -Objekt gibt ein beliebiges **Recordset** -Objekt zurück, das von einer Abfrage an den Client erzeugt wurde.  
  
 **RDSServer. DataFactory** ist jedoch auf die Durchführung von Abfragen und Updates beschränkt. Es kann keine Validierung oder Verarbeitung der Verbindungs-oder Befehls Zeichenfolgen ausführen.  
  
 Mit ADO können Sie angeben, dass das **DataFactory** in Verbindung mit einem anderen Typ von Serverprogramm funktioniert, das als " *Handler*" bezeichnet wird. Der Handler kann die Client Verbindung und Befehls Zeichenfolgen ändern, bevor Sie für den Zugriff auf die Datenquelle verwendet werden. Außerdem kann der Handler Zugriffsrechte erzwingen, die die Fähigkeit des Clients steuern, Daten in der Datenquelle zu lesen und zu schreiben.  
  
 Die Parameter, die der Handler zum Ändern von Client Parametern und Zugriffsrechten verwendet, werden in Abschnitten einer Anpassungs Datei angegeben.  
  
 Die folgenden Themen enthalten weitere Informationen zum Anpassen des **DataFactory** -Objekts.  
  
-   [Grundlegendes zur Anpassungsdatei](./understanding-the-customization-file.md)  
  
-   [Connect-Abschnitt der Anpassungsdatei](./customization-file-connect-section.md)  
  
-   [SQL-Abschnitt der Anpassungsdatei](./customization-file-sql-section.md)  
  
-   [UserList-Abschnitt der Anpassungsdatei](./customization-file-userlist-section.md)  
  
-   [Logs-Abschnitt der Anpassungsdatei](./customization-file-logs-section.md)  
  
-   [Erforderliche Clienteinstellungen](./required-client-settings.md)  
  
-   [Schreiben Ihres eigenen benutzerdefinierten Handlers](./writing-your-own-customized-handler.md)