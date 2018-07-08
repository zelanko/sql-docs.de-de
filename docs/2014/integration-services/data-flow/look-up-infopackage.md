---
title: InfoPackage suchen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce2da77e51370960d433981e28c32c5e7c4e55cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151321"
---
# <a name="look-up-infopackage"></a>InfoPackage suchen
  Verwenden Sie das Dialogfeld **InfoPackage suchen** , um ein InfoPackage zu suchen, das im SAP NetWeaver BW-System definiert ist. Wenn die Liste der InfoPackages angezeigt wird, wählen Sie das gewünschte InfoPackage aus. Daraufhin werden die zugehörigen Optionen vom Ziel mit den erforderlichen Werten aufgefüllt.  
  
 Das SAP BW-Ziel von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW verwendet das Dialogfeld **Prozesskette suchen** . Weitere Informationen zum SAP BW-Ziel finden Sie unter [SAP BW Destination](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie das Dialogfeld "InfoPackage suchen"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem das SAP BW-Ziel enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das SAP BW-Ziel.  
  
3.  Klicken Sie im **Ziel-Editor für SAP BW**auf **Verbindungs-Manager** , um die Seite **Verbindungs-Manager** des Editors zu öffnen.  
  
4.  Klicken Sie auf der Seite **Verbindungs-Manager** im Gruppenfeld **InfoPackage/InfoSource** auf **Suchen** , um das Dialogfeld **InfoPackage suchen** anzuzeigen.  
  
## <a name="lookup-options"></a>Suchoptionen  
 In den Suchfeldern können Sie Ergebnisse filtern, indem Sie das Platzhalterzeichen (*) oder eine Teilzeichenfolge in Kombination mit dem Platzhalterzeichen (*) verwenden. Wenn Sie ein Suchfeld leer lassen, werden beim Suchvorgang jedoch nur leere Zeichenfolgen in diesem Feld abgeglichen.  
  
 **InfoPackage**  
 Geben Sie den Namen des InfoPackage ein, das Sie suchen möchten, oder geben Sie einen Teilnamen mit dem Platzhalterzeichen (*) ein. Alternativ können Sie das Platzhalterzeichen alleine verwenden, um alle InfoPackages einzuschließen.  
  
 **InfoSource**  
 Geben Sie den Namen der InfoSource oder einen Teilnamen mit dem Platzhalterzeichen (*) ein. Alternativ können Sie das Platzhalterzeichen (*) alleine verwenden, um alle InfoPackages unabhängig von InfoSource einzuschließen.  
  
 **Quellsystem**  
 Geben Sie den Namen des Quellsystems oder einen Teilnamen mit dem Platzhalterzeichen (*) ein. Alternativ können Sie das Platzhalterzeichen alleine verwenden, um alle InfoPackages unabhängig von Quellsystemen einzuschließen.  
  
 **Suchen**  
 Suchen Sie übereinstimmende InfoPackages, die im SAP NetWeaver BW-System definiert sind.  
  
## <a name="lookup-results"></a>Suchergebnisse  
 Nachdem Sie auf die Schaltfläche Suchen geklickt haben, wird eine Liste der im SAP NetWeaver BW-System enthaltenen InfoPackages in einer Tabelle angezeigt, die über die folgenden Spaltenüberschriften verfügt.  
  
 **InfoPackage**  
 Zeigt den Namen des InfoPackage an, das im SAP NetWeaver BW-System definiert ist.  
  
 **Typ**  
 Zeigt den Typ des InfoPackage an. In der folgenden Tabelle sind die möglichen Werte für den Typ aufgelistet.  
  
|value|Description|  
|-----------|-----------------|  
|Trans.|Transaktionsdaten.|  
|Attr.|Attributdaten.|  
|Texte|Texte.|  
  
 **Beschreibung**  
 Zeigt die Beschreibung des InfoPackage an.  
  
 **InfoSource**  
 Zeigt den Namen der InfoSource an, die dem InfoPackage ggf. zugeordnet ist.  
  
 **Source System**  
 Zeigt den Namen des Quellsystems an.  
  
 Wenn die Liste der InfoPackages angezeigt wird, wählen Sie das gewünschte InfoPackage aus. Daraufhin werden die zugehörigen Optionen vom Ziel mit den erforderlichen Werten aufgefüllt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ziel-Editor für SAP BW &#40;Seite Verbindungs-Manager&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [F1-Hilfe zu Microsoft Connector 1.1 für SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
