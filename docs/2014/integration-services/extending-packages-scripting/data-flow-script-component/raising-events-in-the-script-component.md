---
title: Auslösen von Ereignissen in der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 67d0e1263fdf2173f04bf52fb4644250212af14a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046945"
---
# <a name="raising-events-in-the-script-component"></a>Auslösen von Ereignissen in der Skriptkomponente
  Ereignisse bieten eine Möglichkeit, Fehler, Warnungen und andere Informationen, wie z. B. den Fortschritt oder Status eines Tasks, an das entsprechende Paket zu melden. Das Paket stellt Ereignishandler zum Verwalten von Ereignisbenachrichtigungen bereit. Die Skriptkomponente kann Ereignisse durch Aufrufen der Methoden in der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>-Eigenschaft der `ScriptMain`-Klasse auslösen. Weitere Informationen zum Umgang von [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Paketen mit Ereignissen finden Sie unter [Integration Services-Ereignishandler &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md).  
  
 Ereignisse können in jedem Protokollanbieter protokolliert werden, der im Paket aktiviert wird. Protokollanbieter speichern Informationen über Ereignisse in einem Datenspeicher. Die Skriptkomponente kann ebenfalls die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>-Methode verwenden, um Informationen in einem Protokollanbieter zu protokollieren, ohne ein Ereignis auszulösen. Weitere Informationen zur Verwendung der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>-Methode finden Sie im folgenden Abschnitt.  
  
 Um ein Ereignis auszulösen, ruft der Skripttask eine der folgenden Methoden der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle auf, die von der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>-Eigenschaft verfügbar gemacht wird:  
  
|Ereignis|Description|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|Löst ein benutzerdefiniertes Ereignis im Paket aus.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|Informiert das Paket über eine Fehlerbedingung.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|Stellt Informationen für den Benutzer bereit.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|Informiert das Paket über den Fortschritt der Komponente.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|Informiert das Paket darüber, dass die Komponente einen Status aufweist, der eine Benutzerbenachrichtigung erfordert, bei dem es sich aber nicht um eine Fehlerbedingung handelt.|  
  
 Nachfolgend finden Sie ein einfaches Beispiel zur Auslösung eines Error-Ereignisses:  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben Sie mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Ereignishandler &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md)   
 [Hinzufügen eines Ereignishandlers zu einem Paket](../../add-an-event-handler-to-a-package.md)  
  
  