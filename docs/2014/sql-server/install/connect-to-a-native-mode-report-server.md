---
title: Verbinden mit einem Berichtsserver im einheitlichen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6fd7ff677fdbbfa91b616fd6a561d3eb48c2de57
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66096061"
---
# <a name="connect-to-a-native-mode-report-server"></a>Herstellen einer Verbindung mit einem Berichtsserver im einheitlichen Modus
  Verwenden Sie dieses Dialogfeld, um eine Verbindung mit einer lokalen oder Remote-Berichtsserverinstanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder einer späteren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Version herzustellen. Dieses Tool kann nicht verwendet werden, um eine Verbindung mit früheren Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsservern herzustellen. Sie können nur jeweils eine Verbindung zu einer Instanz herstellen.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager wird nicht zum Konfigurieren und Verwalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet. Verwenden Sie die SharePoint-Zentraladministration und PowerShell-Skripts zum Konfigurieren eines Berichtsservers im SharePoint-Modus. Weitere Informationen finden Sie unter [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
> [!TIP]  
>  Die[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) ist mit "HighestAvailable" Privilegstufe installiert. Dieses Verhalten ist beabsichtigt. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager erfordert Kommunikation mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-APIs. Ein Teil der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Kommunikation erfordert eine höhere Stufe oder Administratorprivilegien.  
  
-   Um eine Verbindung zu einer lokalen Berichtsserverinstanz herzustellen, verwenden Sie die Standardwerte, und klicken Sie auf **Verbinden**. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager gibt den Namen des lokalen Servers vor und erkennt die Standardinstanz. In den meisten Fällen können Sie auf **Verbinden** klicken, ohne die Werte ändern zu müssen. Wenn Sie mehr als eine Instanz installiert haben, müssen Sie diejenige auswählen, die Sie verwenden möchten.  
  
-   Um eine Verbindung zu einer Remote-Berichtsserverinstanz herzustellen, geben Sie den Servernamen ein, klicken Sie auf **Suchen**, wählen Sie die Instanz aus, und klicken Sie dann auf **Verbinden**.  
  
 Um dieses Dialogfeld zu öffnen, starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager. Dieses Dialogfeld wird sofort angezeigt, wenn Sie das Tool starten. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Optionen  
 **Servername**  
 Geben Sie den Netzwerknamen des Computers ein, auf dem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder eine spätere Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert ist. Geben Sie nur den Computernamen ein, kein Präfix oder Schrägstriche.  
  
 **Find**  
 Suchen Sie den unter **Servername**angegebenen Computer.  
  
 **Berichtsserver-Instanz**  
 Wählen Sie aus, zu welcher Instanz Sie eine Verbindung herstellen möchten, wenn mehrere Berichtsserverinstanzen installiert sind. Es stehen nur gültige Instanzen zur Auswahl zur Verfügung. Wenn Sie ältere Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] gleichzeitig mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz ausführen, werden diese Instanzen nicht in der Liste angezeigt.  
  
 **Verbinden**  
 Stellen Sie die Verbindung zum Server und zur Instanz, die Sie angegeben haben, her.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
