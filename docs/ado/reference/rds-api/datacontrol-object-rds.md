---
title: DataControl-Objekt (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl
- RDS.DataControl
helpviewer_keywords:
- DataControl object [ADO]
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa05b8b4be3c155c7ca59132892e0863dda60a5f
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600640"
---
# <a name="datacontrol-object-rds"></a>DataControl-Objekt (RDS)
Eine Datenabfrage bindet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) an einen oder mehrere Steuerelemente (z. B. ein Textfeld, ein Grid-Steuerelement oder ein Kombinationsfeld) zum Anzeigen der **Recordset** Daten auf einer Webseite.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
</OBJECT>  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Klassen-ID für die **RDS. DataControl** Objekt ist BD96C556 65A3 - 11-d 0-983A-00C04FC29E33.  
  
> [!NOTE]
>  Wenn Sie eine Fehlermeldung, die erhalten eine [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oder **RDS. DataControl** Objekt nicht geladen werden, stellen Sie sicher, dass Sie die richtige Klasse-ID verwenden Die Klasse haben-IDs für diese Objekte von Version 1.0 und 1.1 geändert. Achten Sie zudem auch auf NULL festlegbare Spalten müssen festgelegt sein, bei der Verwendung der **RDS DataControl** Objekt.  
  
 Bei grundlegenden Szenario müssen Sie nur Festlegen der **SQL**, **Connect**, und **Server** Eigenschaften der **RDS. DataControl** -Objekt, das das Geschäftsobjekt, das standardmäßig automatisch aufruft, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md).  
  
 Alle Eigenschaften in der **RDS. DataControl** sind optional, da benutzerdefinierte Geschäftsobjekte ihre Funktionalität ersetzen können.  
  
> [!NOTE]
>  Bei für mehrere Ergebnisse Abfragen, nur die ersten [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) zurückgegeben wird. Wenn mehrere Resultsets benötigt werden, weisen Sie jedes Element eine eigene **DataControl**. Ein Beispiel für eine Abfrage für mehrere Ergebnisse könnte folgendermaßen aussehen: `"Select * from Authors, Select * from Topics"`  
  
 Hinzufügen von "DFMode = 20;" zur Verbindungszeichenfolge bei Verwendung der **RDS. DataControl** Objekt kann die Leistung Ihres Servers verbessern, wenn es sich bei Daten zu aktualisieren. Mit dieser Einstellung die **RDSServer.DataFactory** Objekt auf dem Server einen weniger ressourcenintensiv-Modus verwendet. Die folgenden Funktionen sind jedoch nicht in dieser Konfiguration verfügbar:  
  
-   Verwenden von parametrisierten Abfragen.  
  
-   Abrufen von Informationen von Parameter oder eine Spalte vor dem Aufruf der **Execute** Methode.  
  
-   Festlegen von **Transact Updates** zu **"true"**.  
  
-   Abrufen des Zeilenstatus.  
  
-   Aufrufen der [Resync](../../../ado/reference/ado-api/resync-method.md) Methode.  
  
-   Aktualisieren (explizit oder automatisch) über die [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) Eigenschaft.  
  
-   Festlegen von **Befehl** oder [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) Eigenschaften.  
  
-   Mithilfe von **AdCmdTableDirect**.  
  
 Die **RDS. DataControl** Objekt standardmäßig im asynchronen Modus ausgeführt wird. Wenn Sie die synchrone Ausführung für Ihre Anwendung benötigen, legen Sie die [ExecuteOptions](../../../ado/reference/rds-api/executeoptions-property-rds.md) Parameter gleich **AdcExecSync** und [FetchOptions](../../../ado/reference/rds-api/fetchoptions-property-rds.md) Parameter gleich **AdcFetchUpFront**, wie im folgenden Beispiel gezeigt.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"   
    ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
   <PARAM NAME="ExecuteOptions" VALUE="1">   <PARAM NAME="FetchOptions" VALUE="1">  
</OBJECT>  
```  
  
 Verwenden Sie eine **RDS. DataControl** Objekt, das die Ergebnisse einer einzelnen Abfrage mit einem oder mehreren visuellen Steuerelementen verknüpft. Nehmen wir beispielsweise an Ihr Code eine Kundendaten Abfragen wie z. B. Name, Wohnort, Geburtsort, Alter und Prioritätsstatus der Kunden. Sie können ein einzelnes **RDS. DataControl** Objekt, um Name, Alter und Region eines Kunden in drei separaten Textfelder anzuzeigen Status für die Priorität-Kunden in einem Kontrollkästchen; und alle Daten in einem Datenraster-Steuerelement.  
  
 Andere **RDS. DataControl** Objekte, um die Ergebnisse von mehreren Abfragen mit verschiedenen visuellen Steuerelementen zu verknüpfen. Nehmen wir beispielsweise an, dass Sie mithilfe einer Abfrage zum Abrufen von Informationen zu einem Kunden und eine zweite Abfrage zum Abrufen von Informationen über waren, die der Kunde gekauft hat. Möchten die Ergebnisse der ersten Abfrage in drei Textfelder und ein Kontrollkästchen und die Ergebnisse der zweiten Abfrage in einem Datenraster-Steuerelement anzuzeigen. Wenn Sie das Geschäftsobjekt, das standardmäßig verwenden (**RDSServer.DataFactory**), müssen Sie Folgendes tun:  
  
-   Hinzufügen von zwei **RDS. DataControl** Objekte auf Ihrer Webseite.  
  
-   Schreiben Sie zwei Abfragen, eine für jede **SQL** Eigenschaft der beiden **RDS. DataControl** Objekte. Eine **RDS. DataControl** Objekt eine SQL-Abfrage, die Kundeninformationen enthält; das zweite enthält eine Abfrage, die eine Modellliste waren, die der Kunde gekauft hat.  
  
-   Geben Sie in den Objekt-Tags der einzelnen gebundene Steuerelemente den DATAFLD-Wert, um die Werte für die Daten festlegen, die in den einzelnen visuellen Steuerelementen angezeigt werden soll.  
  
 Es gibt keine Beschränkung für die Anzahl der **RDS. DataControl** Objekten, die Sie mithilfe von Objekt-Tags auf eine einzelne Webseite einbetten können.  
  
 Beim Definieren der **RDS. DataControl** Objekt auf einer Webseite, die ungleich null verwenden **Höhe** und **Breite** Werte wie z. B. 1 sein (um die Einbeziehung zusätzlicher Speicherplatz zu vermeiden).  
  
 Remote Data Service-Clientkomponenten sind bereits als Bestandteil von Internet Explorer 4.0. aus diesem Grund, Sie müssen nicht in einen CODEBASIS-Parameter enthalten Ihre **RDS. DataControl** object-Tag.  
  
 Mit Internet Explorer 4.0 oder höher, können Sie binden an Daten mithilfe von HTML-Steuerelemente und ActiveX® Steuerelemente nur dann, wenn sie als Apartment-Modell-Steuerelemente gekennzeichnet sind.  
  
> [!NOTE]
>  **Microsoft Visual Basic-Benutzer** der **RDS. DataControl** ist sicher für Skripting und wird nur in einer webbasierten Anwendung verwendet. Eine Visual Basic-Client-Anwendung ist nicht erforderlich.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [DataControl-Objekt (RDS) – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/rds-api/datacontrol-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [DataControl-Objekt – Beispiel (VBScript)](../../../ado/reference/rds-api/datacontrol-object-example-vbscript.md)






















