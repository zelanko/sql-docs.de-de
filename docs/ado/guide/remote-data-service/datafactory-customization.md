---
title: DataFactory-Anpassung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1054596c74c00169f9a043acc3fdf47269c5b4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825208"
---
# <a name="datafactory-customization"></a>DataFactory-Anpassung
Remote Data Service (RDS) bietet eine Möglichkeit zum Zugriff auf Daten ganz einfach in eine dreistufige Client/Server-System durchführen. Ein Client-Steuerelement gibt Verbindungs- und Parameter zum Ausführen einer Abfrage auf einem remote-Datenquelle oder eine Verbindungszeichenfolge und [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt-Parameter, um ein Update durchzuführen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Die Parameter werden an ein Serverprogramm übergeben, die den Datenzugriff-Vorgang für die remote-Datenquelle ausführt. RDS bietet ein Standardserverprogramm wird aufgerufen, die [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt. Die **RDSServer.DataFactory** Objekt zurückgibt, eine **Recordset** Objekt erzeugt, die von einer Abfrage an den Client.  
  
 Allerdings die **RDSServer.DataFactory** ist mit dem Durchführen von Abfragen und Aktualisierungen beschränkt. Es kann keine Validierung oder Verarbeitung der Verbindung oder eines Befehl Zeichenfolgen ausführen.  
  
 Bei ADO können Sie angeben, die **DataFactory** funktionieren in Verbindung mit einem anderen Typ von Serverprogramm Namens eine *Handler*. Der Handler kann Clientverbindung und Befehlszeichenfolgen ändern, bevor sie den Zugriff auf die Datenquelle verwendet werden. Darüber hinaus kann der Handler Zugriffsrechte, erzwingen, die steuern die Fähigkeit eines Clients zu lesen und Schreiben von Daten in der Datenquelle.  
  
 Der Parameter, mit denen der Handler ändern Sie die Clientparameter und Zugriffsrechten sind in Abschnitte der Anpassung an angegeben.  
  
 Die folgenden Themen enthalten weitere Informationen zum Anpassen der **DataFactory** Objekt.  
  
-   [Grundlegendes zu der Anpassungsdatei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [Connect-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [SQL-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [UserList-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [Logs-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [Erforderliche Clienteinstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


