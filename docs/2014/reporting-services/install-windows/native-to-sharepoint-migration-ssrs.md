---
title: Migration vom einheitlichen Modus zum SharePoint-Modus (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c5b15bec-6fde-4174-bcde-d043307244dd
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0667c3fc2154875d3f68e5eea22f9cd0a6600956
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264316"
---
# <a name="native-to-sharepoint-migration-ssrs"></a>Migration vom einheitlichen vom SharePoint-Modus (SSRS)
  Es ist nicht möglich, Upgrades oder Konvertierungen zwischen verschiedenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Servermodi auszuführen. Beispielsweise können Sie keinen Berichtsserver im einheitlichen Modus auf den SharePoint-Modus aktualisieren bzw. diesen konvertieren. Das Kopieren der Berichtsserver-Datenbanken zwischen verschiedenen Modi ist nicht möglich, weil die Modi verschiedene Datenbankschemas verwenden. Sie können Inhalte zwischen verschiedenen Berichtsservern migrieren. Welche Tools Sie verwenden, hängt vom Berichtsservermodus ab, der für den Quell- und den Zielserver konfiguriert wurde.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] | SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]   
  
##  <a name="bkmk_native_to_sharepoint"></a> Reporting Services-Migrationstool  
 Das Tool unterstützt die Migration von Inhalten von einer Bereitstellung im einheitlichen Modus zu einer Bereitstellung im SharePoint-Modus. Das Tool unterstützt keine Migration von SharePoint-Modus zu SharePoint-Modus oder vom SharePoint-Modus zum einheitlichen Modus.  
  
 Weitere Informationen finden Sie unter [Reporting Services-Migrationstool](http://www.microsoft.com/download/details.aspx?id=29560) (http://www.microsoft.com/download/details.aspx?id=29560).  
  
## <a name="use-script-to-migrate-content"></a>Migrieren von Inhalten mithilfe von Skripts  
 Wenn das Migrationstool Ihren Anforderungen nicht entspricht, können Sie die Berichtsserverdaten manuell migrieren. Im Folgenden sind die Schritte zusammengefasst, die Sie ausführen, um Berichtselemente von einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung zu einer anderen zu migrieren. Bei dieser Methode wird der einheitliche Modus oder der SharePoint-Modus als Quell- oder Zielserver unterstützt.  
  
1.  Sichern und stellen Sie die Verschlüsselungsschlüssel wieder her. Dies ist der Schlüssel, der zum Verschlüsseln von Daten verwendet wird. Der Verschlüsselungsschlüssel wird außerdem zur Verschlüsselung von Kennwörtern verwendet, z. B. die für Datenquellenverbindungen gespeicherten Kennwörter. Kennwörter selbst können jedoch nicht migriert werden und müssen in der Zielumgebung erneut eingegeben werden.  
  
2.  **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] RSS-Skripts:** Schreiben Sie ein Visual Basic-Skript, das SOAP-Methoden des Berichtsserver-Webdiensts aufruft, um Daten von einer Datenbank in eine andere Datenbank zu kopieren. Verwenden Sie das Hilfsprogramm **RS.exe** , um das Skript auszuführen. RS.exe wird mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installiert.  
  
    -   [Sample Reporting Services-Beispielskript rs.exe zum Migrieren von Inhalten zwischen Berichtsservern](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md). In den Themen wird erläutert, wie Sie das von CodePlex herunterladbare Beispielskript verwenden.  
  
    -   Das RSS-Beispielskript auf CodePlex finden Sie unter [Reporting Services-Skript "RS.exe" zum Migrieren von Inhalten von einem Berichtsserver zu einem anderen](http://azuresql.codeplex.com/releases/view/115207).  
  
    -   [Scripting and PowerShell with Reporting Services (Skripterstellung und PowerShell mit Reporting Services)](../tools/scripting-and-powershell-with-reporting-services.md)  
  
 In der folgenden Tabelle sind die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Objekte zusammengefasst, die Sie mithilfe von Skripts migrieren können:  
  
|Objekt|Skripterstellung möglich|Kommentare|  
|------------|---------------------|--------------|  
|Berichte|ja|Nach der Migration geben Sie die Kennwörter für Datenquellen erneut ein.|  
|Datenquellen|ja|Nach der Migration verknüpfen Sie Berichte erneut mit Datenquellen.|  
|Modelle|ja||  
|Datasets|ja||  
|Berichtsteile||Nach der Migration überprüfen oder aktualisieren Sie den Pfad zu den Berichtsteilen.|  
|Zeitpläne|ja|Finden Sie im Thema zur ListSchedules-Methode [Subscription and Delivery Methods](../report-server-web-service/methods/subscription-and-delivery-methods.md)|  
|Abonnements|ja|Finden Sie unter Listsubscriptions-Methode [Subscription and Delivery Methods](../report-server-web-service/methods/subscription-and-delivery-methods.md) und ChangeSubscriptionOwner-Methode <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>|  
|Momentaufnahmen|||  
||||  
  
  
