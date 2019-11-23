---
title: Auf den WMI-Anbieter für Reporting Services zugreifen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efbe03a4aab65f792b352eeb5b6c5130c4c32335
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783204"
---
# <a name="access-the-reporting-services-wmi-provider"></a>Zugreifen auf den Reporting Services-WMI-Anbieter
  Der Reporting Services-WMI-Anbieter macht zwei WMI-Klassen für die Verwaltung von Berichtsserverinstanzen im einheitlichen Modus durch Skripterstellung verfügbar:  
  
> [!IMPORTANT]  
>  Ab der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version wird der WMI-Anbieter nur für Berichtsserver im einheitlichen Modus unterstützt. Berichtsserver im SharePoint-Modus können über Seiten der SharePoint-Zentraladministration und PowerShell-Skripts verwaltet werden.  
  
|Klasse|Namespace|und Beschreibung|  
|-----------|---------------|-----------------|  
|MSReportServer_Instance|root\microsoft\sqlserver\reportserver\ RS_ *\<encoddinstancename >* \v11|Stellt grundlegende Informationen bereit, die ein Client benötigt, um eine Verbindung mit einem installierten Berichtsserver herzustellen.|  
|MSReportServer_ConfigurationSetting|root\microsoft\sqlserver\reportserver\ RS_ *\<encoddinstancename >* \v11\admin|Stellt die Installationsparameter und die Laufzeitparameter einer Berichtsserverinstanz dar. Diese Parameter werden in der Konfigurationsdatei für den Berichtsserver gespeichert.<br /><br /> **\*\* Wichtig \*\*** Für den Zugriffe auf diese Klasse sind Administratorrechte erforderlich.|  
  
 Für jede Berichtsserverinstanz wird eine Instanz von jeder der oben erwähnten Klassen erstellt. Sie können mit jedem Microsoft- oder Drittanbietertool auf die WMI-Objekte zugreifen, die vom Berichtsserver verfügbar gemacht werden, einschließlich WMI-Programmierungsschnittstellen, die von .NET Framework verfügbar gemacht werden. In diesem Thema wird die Verwendung von und der Zugriff auf WMI-Klasseninstanzen mit dem PowerShell-Befehl [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx)beschrieben.  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a>Bestimmen des Instanznamens in der Namespacezeichenfolge  
 Der Instanzname im Namespacepfad für Reporting Services-WMI-Klassen stellt eine Codierung des Instanznamens dar, den Sie angeben, wenn Sie die benannten Reporting Services-Instanzen installieren. Und zwar werden die Sonderzeichen in den Instanznamen codiert. Ein Unterstrich (_) wird z.B. als „_5f“ codiert, d.h., der Instanzname „My_Instance“ wird im WMI-Namespacepfad als „My_5fInstance“ codiert.  
  
 Um die codierten Instanznamen der Berichtsserverinstanzen im WMI-Namespacepfad aufzulisten, verwenden Sie den folgenden PowerShell-Befehl:  
  
```powershell
Get-WmiObject -Namespace root\Microsoft\SqlServer\ReportServer -Class __Namespace -ComputerName hostname | Select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a>Zugreifen auf die WMI-Klassen mit PowerShell  
 Führen Sie den folgenden Befehl aus, um auf die WMI-Klassen zuzugreifen:  
  
```powershell
Get-WmiObject -Namespace <namespacename> -Class <classname> -ComputerName <hostname>  
```  
  
 Um z. B. auf die MSReportServer_ConfigurationSetting-Klasse der Standardberichtsserverinstanz des Host "myrshost" zuzugreifen, führen Sie den folgenden Befehl aus. Für eine erfolgreiche Ausführungs dieses Befehls muss die Standardberichtsserverinstanz auf myrshost installiert sein.  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 Mit dieser Befehlssyntax werden alle Klasseneigenschaftsnamen und -werte ausgegeben. Hinweis: Alle Instanzen der Klasse "MSReportServer_ConfigurationSetting" werden zurückgegeben, auch wenn der Zugriff auf die Klasse im Namespace der Standardberichtsserverinstanz (RS_MSSQLSERVER) erfolgt. Wenn myrshost z. B. mit der Standardberichtsserverinstanz und einer benannten Berichtsserverinstanz mit dem Namen SHAREPOINT installiert ist, werden mit diesem Befehl zwei WMI-Objekte zurückgegeben und die Eigenschaftsnamen und Werte für beide Berichtsserverinstanzen ausgegeben.  
  
 Um eine bestimmte Klasseninstanz zurückzugeben, wenn mehrere Instanzen zurückgegeben werden, verwenden Sie den Parameter „-Filter“, um die Ergebnisse basierend auf den Eigenschaften mit eindeutigen Werten, z.B. InstanceName, zu filtern. Wenn Sie z. B. nur das WMI-Objekt für die Standardberichtsserverinstanz zurückgeben möchten, verwenden Sie den folgenden Befehl:  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a>Abfragen der verfügbaren Methoden und Eigenschaften  
 Um die in einer der Reporting Services-WMI-Klassen verfügbaren Methoden und Eigenschaften anzuzeigen, reichen Sie die Ergebnisse von Get-WmiObject an den Get-Member-Befehl weiter. Zum Beispiel:  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
 Dokumentation zu den Eigenschaften und Methoden der Reporting Services WMI-Klassen finden Sie unter....  
  
## <a name="use-a-wmi-method-or-property"></a>Verwenden einer WMI-Methode oder -Eigenschaft  
 Wenn Sie die WMI-Objekte der Reporting Services-Klassen abgerufen haben und die verfügbaren Methoden und Eigenschaften kennen, können Sie diese Methoden und Eigenschaften verwenden. Wenn z. B. eine Berichtsserverinstanz mit dem Namen SHAREPOINT im integrierten SharePoint-Modus vorhanden ist, rufen Sie die URL für die Website der SharePoint-Zentraladministration mithilfe der folgenden Befehlssequenz ab:  
  
```powershell
$rsconfig = Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='SHAREPOINT'"  
$rsconfig.GetAdminSiteUrl()  
```  
  
## <a name="see-also"></a>Siehe auch
 [Reporting Services-WMI-Anbieterbibliotheksreferenz &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md)   
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md)  
