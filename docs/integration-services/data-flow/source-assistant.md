---
title: Quellen-Assistenten | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sourceassistant.f1
- sql13.dts.designer.addNewSource.f1
ms.assetid: 5ca9d821-7d61-4727-9133-5f9cb485c7f3
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 96b9c897ddb8cb508d4ce95ee133a8060ec818e0
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411102"
---
# <a name="source-assistant"></a>Quellen-Assistent
  Mithilfe der Quellen-Assistenten-Komponente können Sie eine Quellkomponente und einen Verbindungs-Manager erstellen. Die Komponente befindet sich im Abschnitt **Favoriten** der SSIS-Toolbox.  
  
> [!NOTE]  
>  Der Quellen-Assistent ersetzt das Integration Services-Verbindungsprojekt und den entsprechenden Assistenten.  
  
## <a name="add-a-source-with-source-assistant"></a>Hinzufügen einer Quelle mit dem Quellen-Assistenten
In diesem Abschnitt werden Schritte vorgestellt, um eine neue Quelle mithilfe des Quellen-Assistenten hinzuzufügen, und die im Dialogfeld **Neue Quelle hinzufügen** verfügbaren Optionen aufgeführt, die angezeigt werden, wenn Sie den Quellen-Assistent per Drag &amp; Drop in den SSIS-Designer ziehen.  

1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, dem eine neue Quellkomponente hinzugefügt werden soll.  
  
2.  Ziehen Sie die **Quellen-Assistenten** -Komponente von der SSIS-Toolbox auf die Registerkarte **Datenfluss** . Sie sollten das Dialogfeld **Neue Quelle hinzufügen** sehen. Der nächste Abschnitt enthält Details zu den im Dialogfeld verfügbaren Optionen.  
  
3.  Wählen Sie den Zieltyp in der Liste **Typ** aus.  
  
4.  Wählen Sie in der Liste **Verbindungs-Manager** einen vorhandenen Verbindungs-Manager aus. Wählen Sie alternativ **\<Neu>** aus, um einen neuen Verbindungs-Manager zu erstellen.  
  
5.  Wenn Sie einen vorhandenen Verbindungs-Manager auswählen, klicken Sie auf **OK** , um das Dialogfeld **Neues Ziel hinzufügen** zu schließen. Sie sollten nun das Ziel und die Verbindungs-Manager sehen, die dem Datenfluss hinzugefügt wurden.  
  
6.  Wenn Sie auf **\<Neu>** klicken, um einen neuen Verbindungs-Manager zu erstellen, sollten Sie ein **Verbindungs-Manager**-Dialogfeld sehen, in dem Sie Parameter für die Verbindung angeben können. Nachdem Sie einen neuen Verbindungs-Managers erstellt haben, werden das Ziel und der Verbindungs-Manager in SSIS-Designer angezeigt.  

## <a name="add-new-source-dialog-box"></a>Neue Quelle hinzufügen (Dialogfeld)
In der folgenden Tabelle sind die Optionen im Dialogfeld **Neue Quelle hinzufügen** aufgeführt.  
  
|Option|und Beschreibung|  
|------------|-----------------|  
|Typen|Wählen Sie den Quelltyp aus, mit dem Sie eine Verbindung herstellen möchten.|  
|Verbindungs-Manager|Wählen Sie einen vorhandenen Verbindungs-Manager aus, oder klicken Sie auf **\<Neu>**, um einen neuen Verbindungs-Manager zu erstellen.|  
|Nur installierte anzeigen|Geben Sie an, ob nur installierte Quellen angezeigt werden sollen.|  
|OK|Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern, und öffnen Sie die entsprechenden nachfolgenden Dialogfelder, um zusätzliche Optionen zu konfigurieren.| 
  
