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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bf59580985a4c46fa163a00423bb7dd90ad9463
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747757"
---
# <a name="rds-programming-model-in-detail"></a>RDS-Programmiermodell im Detail
Im folgenden sind die wichtigsten Elemente des RDS-Programmiermodells aufgeführt:  
  
-   RDS. DataSpace  
  
-   RDSServer. DataFactory  
  
-   RDS. DataControl  
  
-   Ereignis  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="rdsdataspace"></a>RDS. DataSpace  
 Die Client Anwendung muss den Server und das aufzurufende Serverprogramm angeben. In der Rückgabe erhält die Anwendung einen Verweis auf das Serverprogramm und kann den Verweis so behandeln, als ob es sich um das Serverprogramm handelt.  
  
 Das RDS-Objektmodell verkörpert diese Funktionalität mit dem [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) -Objekt.  
  
 Das Serverprogramm wird mit einer Programm Kennung oder *ProgID*angegeben. Der Server verwendet die *ProgID* und die Registrierung des Server Computers, um Informationen zum eigentlichen Programm zu finden, das initiiert werden soll.  
  
 RDS unterscheidet sich intern, abhängig davon, ob sich das Serverprogramm auf einem Remote Server über das Internet oder ein Intranet befindet. ein Server in einem lokalen Netzwerk; oder nicht auf einem Server, sondern in einer lokalen Dynamic Link Library (dll). Dieser Unterschied bestimmt, wie Informationen zwischen dem Client und dem Server ausgetauscht werden, und macht einen konkreten Unterschied in der Art des Verweises, der an die Client Anwendung zurückgegeben wird. Allerdings hat diese Unterscheidung aus ihrer Sicht keine besondere Bedeutung. Alles, was wichtig ist, ist, dass Sie einen verwendbaren Programm Verweis erhalten.  
  
## <a name="rdsserverdatafactory"></a>RDSServer. DataFactory  
 RDS stellt ein Standard Serverprogramm bereit, das entweder eine SQL-Abfrage für die Datenquelle ausführen und ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt zurückgeben oder ein **Recordset** -Objekt erstellen und die Datenquelle aktualisieren kann.  
  
 Das RDS-Objektmodell verkörpert diese Funktion mit dem [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) -Objekt.  
  
 Außerdem verfügt dieses Objekt über eine Methode zum Erstellen eines leeren **Recordset** -Objekts, das Sie Programm gesteuert ausfüllen können ([CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)), und eine weitere Methode zum umrechnen eines Recordset-Objekts in eine Text **Zeichenfolge** zum Erstellen einer Webseite ([ConvertTo String](../../../ado/reference/rds-api/converttostring-method-rds.md)).  
  
 Mit ADO können Sie einige der standardmäßigen Verbindungs-und Befehls Verhalten von **RDSServer. DataFactory** mit einem **DataFactory** -Handler und einer Anpassungs Datei überschreiben, die Verbindungs-, Befehls-und Sicherheitsparameter enthält.  
  
 Das Serverprogramm wird manchmal als *Geschäftsobjekt*bezeichnet. Sie können Ihr eigenes benutzerdefiniertes Geschäftsobjekt schreiben, mit dem komplizierter Datenzugriff, Gültigkeits Prüfungen usw. durchgeführt werden können. Selbst beim Schreiben eines benutzerdefinierten Geschäftsobjekts können Sie eine Instanz eines **RDSServer. DataFactory** -Objekts erstellen und einige der zugehörigen Methoden verwenden, um Ihre eigenen Aufgaben auszuführen.  
  
## <a name="rdsdatacontrol"></a>RDS. DataControl  
 RDS bietet die Möglichkeit, die Funktionalität des RDS zu kombinieren **. DataSpace** und **RDSServer. DataFactory.** Außerdem können visuelle Steuerelemente problemlos das **Recordset** -Objekt verwenden, das von einer Abfrage aus einer Datenquelle zurückgegeben wird. RDS-Versuche, für den häufigsten Fall, so weit wie möglich zu tun, um automatisch Zugriff auf Informationen auf einem Server zu erhalten und in einem visuellen Steuerelement anzuzeigen.  
  
 Das RDS-Objektmodell verkörpert diese Funktionalität mit dem [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
 Das **RDS. DataControl** hat zwei Aspekte. Ein Aspekt bezieht sich auf die Datenquelle. Wenn Sie den Befehl und die Verbindungsinformationen mithilfe der Eigenschaften " **Connect** " und " **SQL** " des **RDS festlegen. DataControl**, wird das RDS automatisch verwendet **. DataSpace** zum Erstellen eines Verweises auf das standardmäßige **RDSServer. DataFactory** -Objekt. Anschließend verwendet das **RDSServer. DataFactory** den **Connect** -Eigenschafts Wert, um eine Verbindung mit der Datenquelle herzustellen, den **SQL** -Eigenschafts Wert zum Abrufen eines **Recordsets** aus der Datenquelle zu verwenden und das **Recordset** -Objekt an das RDS-Objekt zurückzugeben **. DataControl**.  
  
 Der zweite Aspekt bezieht sich auf die Anzeige der zurückgegebenen **Recordsetinformationen** in einem visuellen Steuerelement. Sie können dem RDS ein visuelles Steuerelement zuordnen **. DataControl** (in einem Prozess, der als Bindung bezeichnet wird) und den Zugriff auf die Informationen im zugeordneten **Recordset** -Objekt erhalten, wobei die Abfrageergebnisse auf einer Webseite in Microsoft® Internet Explorer angezeigt werden. Jeder **RDS. Das DataControl** -Objekt bindet ein **Recordset** -Objekt, das die Ergebnisse einer einzelnen Abfrage darstellt, an ein oder mehrere visuelle Steuerelemente (z. b. ein Textfeld, ein Kombinations Feld, ein Raster Steuerelement usw.). Möglicherweise sind mehrere RDS vorhanden **. DataControl** -Objekt auf jeder Seite. Jeder **RDS. Das DataControl** -Objekt kann mit einer anderen Datenquelle verbunden werden und die Ergebnisse einer separaten Abfrage enthalten.  
  
 Das **RDS. Das DataControl** -Objekt verfügt auch über eigene Methoden zum Navigieren, Sortieren und Filtern der Zeilen des zugeordneten **Recordset** -Objekts. Diese Methoden sind ähnlich, aber nicht identisch mit den Methoden für das ADO- **Recordset** -Objekt.  
  
## <a name="events"></a>Ereignisse  
 RDS unterstützt zwei der eigenen Ereignisse, die vom ADO-Ereignis Modell unabhängig sind. Das [onleserystatechange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) -Ereignis wird immer dann aufgerufen, wenn **RDS. Die DataControl** -Eigenschaft " [leserystate](../../../ado/reference/rds-api/readystate-property-rds.md) " ändert sich, sodass Sie benachrichtigt werden, wenn ein asynchroner Vorgang erfolgreich abgeschlossen wurde, beendet wurde oder einen Fehler festgestellt hat. Das [OnError](../../../ado/reference/rds-api/onerror-event-rds.md) -Ereignis wird immer dann aufgerufen, wenn ein Fehler auftritt, auch wenn der Fehler während eines asynchronen Vorgangs auftritt.  
  
> [!NOTE]
>  Microsoft Internet Explorer stellt zwei weitere Ereignisse für RDS bereit: **ondatasetchanged**, das angibt, dass das **Recordset** funktionsfähig ist, aber trotzdem Zeilen abruft, und **ondatasetcomplete**, das angibt, dass das **Recordset** das Abrufen von Zeilen abgeschlossen hat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RDS-Programmiermodell mit Objekten](../../../ado/guide/remote-data-service/rds-programming-model-with-objects.md)   
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [RDS-Szenario](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)



