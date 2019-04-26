---
title: Quellen-Editor für SAP BW (Seite „Spalten“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f0031b874b2477bff53f8f0855b557a3188c3719
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770896"
---
# <a name="sap-bw-source-editor-columns-page"></a>Quellen-Editor für SAP BW (Seite Spalten)
  Auf der Seite **Spalten** im **Quellen-Editor für SAP BW** können Sie jeder externen Spalte (Quellspalte) eine Ausgabespalte zuordnen.  
  
 Weitere Informationen zur SAP BW-Quellkomponente von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Quelle](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
 **So öffnen Sie die Seite "Spalten"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem die SAP BW-Quelle enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die SAP BW-Quelle.  
  
3.  Klicken Sie im **Quellen-Editor für SAP BW**auf **Spalten** , um die Seite **Spalten** des Editors zu öffnen.  
  
## <a name="options"></a>Optionen  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration der Quelle erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
 **Verfügbare externe Spalten**  
 Zeigen Sie die Liste der verfügbaren externen Spalten in der Datenquelle an, und wählen Sie dann die Spalten aus, die in den Datenfluss aufgenommen werden sollen.  
  
 Um eine Spalte in den Datenfluss einzuschließen, aktivieren Sie das Kontrollkästchen, das dieser Spalte entspricht. Die Spalten werden in der Reihenfolge ausgegeben, in der Sie die Kontrollkästchen aktivieren. Das heißt, das erste aktivierte Kontrollkästchen entspricht der ersten Ausgabespalte, das zweite Kontrollkästchen der zweiten Ausgabespalte usw.  
  
 **Externe Spalte**  
 Zeigt die ausgewählten externen Spalten (Quellspalten) an. Die ausgewählten Spalten werden in der Reihenfolge angezeigt, in der beim Konfigurieren von Downstreamkomponenten auch die entsprechenden Ausgabespalten angezeigt werden, die Daten aus dieser Quelle verwenden.  
  
 Um die Reihenfolge der Spalten in der Liste **Verfügbare externe Spalten** zu ändern, deaktivieren Sie die Kontrollkästchen für alle Spalten. Wählen Sie anschließend Spalten in der Reihenfolge aus, in der sie angezeigt werden sollen.  
  
 **Ausgabespalte**  
 Geben Sie für jede Ausgabespalte einen eindeutigen Namen an. Der Standardname ist der Name der ausgewählten externen Spalte (Quellspalte). Sie können jedoch einen eindeutigen, beschreibenden Namen eingeben. [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer die **Ausgabespalte** -Namen für die Spalten an.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für SAP BW &#40;Seite „Verbindungs-Manager“&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Quellen-Editor für SAP BW &#40;Seite „Fehlerausgabe“&#41;](sap-bw-source-editor-error-output-page.md)   
 [Quellen-Editor für SAP BW &#40;Seite „Erweitert“&#41;](sap-bw-source-editor-advanced-page.md)   
 [F1-Hilfe zu Microsoft Connector 1.1 für SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
