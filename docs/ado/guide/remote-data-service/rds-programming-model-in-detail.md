---
title: RDS-Programmiermodell im Detail | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO], details
ms.assetid: 3e57af8d-519b-4467-a0bd-af468534cefd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b511f5d241216c2586870adadeb3c8586ee803be
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560457"
---
# <a name="rds-programming-model-in-detail"></a>RDS-Programmiermodell im Detail
Im folgenden finden wichtige Elemente der RDS-Programmiermodell:  
  
-   RDS.DataSpace  
  
-   RDSServer.DataFactory  
  
-   RDS.DataControl  
  
-   Ereignis  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="rdsdataspace"></a>RDS.DataSpace  
 Ihre Clientanwendung muss den Server und zum Aufrufen des Programms angeben. Ihre Anwendung wird im Gegenzug erhält einen Verweis auf das Server-Programm und kann den Verweis behandeln, als handele es sich um die Server-Anwendung selbst.  
  
 Die RDS-Objektmodell stellt diese Funktionalität durch die [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) Objekt.  
  
 Das Server-Programm mit einer Programm-ID angegeben ist oder *ProgID*. Der Server verwendet die *ProgID* und des Servercomputers finden Sie Informationen über das tatsächliche Programm zu initiieren.  
  
 RDS wird unterschieden intern je nachdem, ob das Server-Programm auf einem Remoteserver über das Internet oder Intranet; einem Server auf einem lokalen Netzwerk oder nicht auf einem Server, sondern auf einen lokalen Dynamic Link Library (DLL). Dieser Unterschied wird bestimmt, wie Informationen zwischen dem Client und Server ausgetauscht, und einen realen Unterschied in den Typ des Verweises an die Clientanwendung zurückgegeben wird. Aus Ihrer Sicht hat dieser Unterschied jedoch keine besondere Bedeutung. Wichtig ist, dass Sie einen Programmverweis verwendet erhalten.  
  
## <a name="rdsserverdatafactory"></a>RDSServer.DataFactory  
 RDS bietet ein Standardserverprogramm, die entweder eine SQL-Abfrage für die Datenquelle und Rückgabe ausführen kann einen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt, oder übernehmen eine **Recordset** Objekt aus, und Aktualisieren der Datenquelle.  
  
 Die RDS-Objektmodell stellt diese Funktionalität durch die [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt.  
  
 Darüber hinaus ist dieses Objekt eine Methode zum Erstellen einer leeres **Recordset** -Objekt, das Sie programmgesteuert gefüllt werden können ([CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)), und eine andere Methode zum Konvertieren einer **Recordset**  Objekt in eine Textzeichenfolge, die eine Webseite ([ConvertToString](../../../ado/reference/rds-api/converttostring-method-rds.md)).  
  
 Bei ADO können Sie überschreiben einiger der standardverbindung und das Befehlsverhalten von der **RDSServer.DataFactory** mit einem **DataFactory** Handler und eine Anpassungsdatei, die Verbindung enthält-Befehl, und Security-Parameter.  
  
 Die Server-Anwendung bezeichnet ein *Geschäftsobjekt*. Sie können eigene benutzerdefinierte Business-Objekt erstellen, das komplexe Daten zugreifen, gültigkeitsüberprüfungen und So weiter ausführen können. Sogar, wenn Sie ein benutzerdefiniertes Geschäftsobjekt zu schreiben, können Sie erstellen eine Instanz von einem **RDSServer.DataFactory** Objekt, und einige ihrer Methoden eigene Aufgaben verwenden.  
  
## <a name="rdsdatacontrol"></a>RDS.DataControl  
 RDS bietet die Möglichkeit, die die Funktionalität kombinieren die **RDS. DataSpace** und **RDSServer.DataFactory**, und aktivieren Sie visuelle Steuerelemente auf einfache Weise verwendet auch die **Recordset** Objekt, das von einer Abfrage aus einer Datenquelle zurückgegeben. RDS versucht der häufigste Fall ist, Sie so weit wie möglich, automatisch Zugriff auf Informationen auf einem Server und in ein visuelles Steuerelement anzeigt.  
  
 Die RDS-Objektmodell stellt diese Funktionalität durch die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 Die **RDS. DataControl** hat zwei Aspekte. Ein Aspekt bezieht sich auf die Datenquelle. Setzen Sie den Befehl und die Verbindung mit der **Connect** und **SQL** Eigenschaften der **RDS. DataControl**, er verwendet automatisch die **RDS. DataSpace** , erstellen Sie einen Verweis auf den Standardwert **RDSServer.DataFactory** Objekt. Die **RDSServer.DataFactory** verwenden die **verbinden** Eigenschaftswert, der eine Verbindung mit der Datenquelle herstellen, verwenden Sie die **SQL** Eigenschaftswert abrufen eine  **Recordset** aus der Datenquelle, und die Rückgabe der **Recordset** -Objekt an die **RDS. DataControl**.  
  
 Der zweite Aspekt bezieht sich auf die Anzeige der zurückgegebenen **Recordset** Informationen in einem visual-Steuerelement. Sie können ein visuelles Steuerelement mit Zuordnen der **RDS. DataControl** (in einem Prozess, der als Bindung bezeichnet wird) und den Zugriff auf die Informationen in der zugeordneten **Recordset** -Objekt, das Anzeigen von Abfrageergebnissen auf einer Webseite in Microsoft® Internet Explorer. Jede **RDS. DataControl** Objekts bindet einen **Recordset** Objekt, das die Ergebnisse einer einzelnen Abfrage, um eine oder mehrere visuelle Steuerelemente (z. B. ein Textfeld, Kombinationsfeld, Grid-Steuerelement, usw.) darstellt. Gibt es möglicherweise mehrere **RDS. DataControl** Objekt auf jeder Seite. Jede **RDS. DataControl** Objekt kann mit einer anderen Datenquelle verbunden werden und die Ergebnisse einer separaten Abfrage enthalten.  
  
 Die **RDS. DataControl** -Objekt verfügt auch über eigene Methoden zum Navigieren, Sortieren und Filtern der Zeilen des zugeordneten **Recordset** Objekt. Diese Methoden ähneln, aber nicht dasselbe wie die Methoden für das ADO **Recordset** Objekt.  
  
## <a name="events"></a>Ereignisse  
 RDS unterstützt zwei seine eigenen Ereignisse, die das ADO-Ereignismodell unabhängig sind. Die ["onreadystatechange"](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) -Ereignis wird aufgerufen, wenn die **RDS. DataControl** [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) eigenschaftsänderungen, also benachrichtigt, wenn ein asynchroner Vorgang erfolgreich abgeschlossen wurde, beendet, oder es ist ein Fehler aufgetreten. Die [OnError](../../../ado/reference/rds-api/onerror-event-rds.md) Ereignis wird aufgerufen, wenn ein Fehler auftritt, selbst wenn der Fehler während eines asynchronen Vorgangs auftritt.  
  
> [!NOTE]
>  Microsoft Internet Explorer werden zwei zusätzliche Ereignisse zu RDS: **OnDataSetChanged**, die angibt, dass die **Recordset** ist voll funktionsfähiges und zugleich noch Abrufen von Zeilen und  **OnDataSetComplete**, die angibt, dass die **Recordset** wurde das Abrufen von Zeilen.  
  
## <a name="see-also"></a>Siehe auch  
 [RDS-Programmiermodell mit Objekten](../../../ado/guide/remote-data-service/rds-programming-model-with-objects.md)   
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [RDS-Architektur](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)



