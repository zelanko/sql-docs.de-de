---
title: Verbindungs-Manager erstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.connectionmanager.f1
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- packages [Integration Services], connections
- connection managers [Integration Services], creating
- SQL Server Integration Services packages, connections
ms.assetid: 6ca317b8-0061-4d9d-b830-ee8c21268345
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ef2ea7fa43556f0c4f12ee41101aedf396a23382
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374088"
---
# <a name="create-connection-managers"></a>Erstellen von Verbindungs-Managern
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthält eine Reihe von Verbindungs-Managern für Tasks, mit denen eine Verbindung mit verschiedenen Server- und Datenquellentypen hergestellt wird. Verbindungs-Manager werden von den Datenflusskomponenten verwendet, die Daten in verschiedenen Arten von Datenspeichern extrahieren und laden, und von den Protokollanbietern, die Protokolle auf einen Server, in eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Tabelle oder eine Datei schreiben. Beispielsweise verwendet ein Paket mit einem Task Mail senden einen SMTP-Verbindungs-Manager, um eine Verbindung mit einem SMTP-Server (Simple Mail Transfer Protocol) herzustellen. Ein Paket mit einem Task SQL ausführen kann einen OLE DB-Verbindungs-Manager zum Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank verwenden. Weitere Informationen finden Sie unter [Integration Services-Verbindungen &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md).  
  
 Um die Verbindungs-Manager beim Erstellen eines Pakets automatisch zu erstellen und zu konfigurieren, können Sie den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Import/Export-Assistenten verwenden. Dieser Assistent hilft Ihnen auch, die Quellen und Ziele zu erstellen und zu konfigurieren, die die Verbindungs-Manager verwenden. Weitere Informationen finden Sie unter [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).  
  
 Um manuell einen neuen Verbindungs-Manager zu erstellen und ihn einem vorhandenen Paket hinzuzufügen, verwenden Sie den Bereich **Verbindungs-Manager** auf den Registerkarten **Ablaufsteuerung**, **Datenfluss**und **Ereignishandler** des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers. Im Bereich **Verbindungs-Manager** wählen Sie in einem Dialogfeld des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers den Typ des Verbindungs-Managers zum Erstellen und dann zum Festlegen der Eigenschaften des Verbindungs-Managers aus. Weitere Informationen finden Sie im Abschnitt "Verwenden des Verbindungs-Manager-Bereichs" weiter unten in diesem Thema.  
  
 Nachdem der Verbindungs-Manager einem Paket hinzugefügt wurde, können Sie ihn in Tasks, Foreach-Schleifencontainern, Quellen, Transformationen und Zielen verwenden. Weitere Informationen finden Sie unter [Integration Services-Tasks](control-flow/integration-services-tasks.md), [Foreach-Schleifencontainer](control-flow/foreach-loop-container.md), und [Datenfluss](data-flow/data-flow.md).  
  
## <a name="using-the-connection-managers-area"></a>Verwenden des Verbindungs-Manager-Bereichs  
 Sie können Verbindungs-Manager erstellen, während die Registerkarte **Ablaufsteuerung**, **Datenfluss**oder **Ereignishandler** des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers aktiviert ist.  
  
 Im folgenden Diagramm wird der Bereich **Verbindungs-Manager** auf der Registerkarte **Ablaufsteuerung** des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers angezeigt.  
  
 ![Screenshot des Ablaufsteuerungs-Designers mit Paket](media/samplecontrolflow.gif "Screenshot des Ablaufsteuerungs-Designers mit Paket")  
  
#### <a name="to-add-configure-or-delete-a-connection-manager-in-ssis-designer"></a>So erstellen, konfigurieren oder löschen Sie einen Verbindungs-Manager im SSIS-Designer  
  
-   [Hinzufügen, Löschen oder Freigeben eines Verbindungs-Managers in einem Paket](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
-   [Festlegen der Eigenschaften eines Verbindungs-Managers](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)  
  
## <a name="32-bit-and-64-bit-providers-for-connection-managers"></a>32-Bit- und 64-Bit-Anbieter für Verbindungs-Manager  
 Viele der von Verbindungs-Managern verwendeten Anbieter sind in der 32-Bit- und 64-Bit-Version verfügbar. Die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Entwurfsumgebung ist eine 32-Bit-Umgebung, sodass beim Entwerfen eines Pakets nur 32-Bit-Anbieter angezeigt werden. Daher können Sie einen Verbindungs-Manager nur dann zum Verwenden eines bestimmten 64-Bit-Anbieters konfigurieren, wenn die 32-Bit-Version desselben Anbieters ebenfalls installiert ist.  
  
 Zur Laufzeit wird stets die richtige Version verwendet, unabhängig davon, ob Sie zur Entwurfszeit die 32-Bit-Version des Anbieters angegeben haben. Die 64-Bit-Version des Anbieters kann auch dann ausgeführt werden, wenn das Paket in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ausgeführt wird.  
  
 Beide Versionen des Anbieters verfügen über die gleiche ID. Um anzugeben, ob die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Laufzeit eine verfügbare 64-Bit-Version des Anbieters verwenden soll, müssen Sie die Run64BitRuntime-Eigenschaft des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekts festlegen. Wenn die Run64BitRuntime-Eigenschaft, um festgelegt ist `true`, die Laufzeit gefunden und verwendet Sie die 64-Bit-Anbieter aus, wenn Run64BitRuntime ist `false`, die Laufzeit gefunden und verwendet den 32-Bit-Anbieter. Weitere Informationen zu Eigenschaften, die Sie in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekten festlegen können, finden Sie unter [Integration Services- und Studio-Umgebungen &#40;SSIS&#41;](integration-services-ssis-development-and-management-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ablaufsteuerung](control-flow/control-flow.md)   
 [Datenfluss](data-flow/data-flow.md)   
 [Integration Services-Ereignishandler &#40;SSIS&#41;](integration-services-ssis-event-handlers.md)  
  
  
