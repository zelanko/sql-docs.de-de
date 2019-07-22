---
title: Quellen-Editor für SAP BW (Seite „Fehlerausgabe“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sapbwsource.erroroutput.f1
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2d823b1155a07f7bb3dc44f84f852d747692ae58
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002370"
---
# <a name="sap-bw-source-editor-error-output-page"></a>Quellen-Editor für SAP BW (Seite Fehlerausgabe)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mithilfe der Seite **Fehlerausgabe** im **Quellen-Editor für SAP BW** können Sie Fehlerbehandlungsoptionen auswählen und Eigenschaften für Fehlerausgabespalten festlegen.  
  
 Weitere Informationen zur SAP BW-Quellkomponente von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Quelle](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
 **So öffnen Sie die Seite "Fehlerausgabe"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem die SAP BW-Quelle enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die SAP BW-Quelle.  
  
3.  Klicken Sie im **Quellen-Editor für SAP BW**auf **Fehlerausgabe** , um die Seite **Fehlerausgabe** des Editors zu öffnen.  
  
## <a name="options"></a>enthalten  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration der Quelle erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
 **Eingabe oder Ausgabe**  
 Zeigt den Namen der Datenquelle an.  
  
 **Spalte**  
 Zeigt die externen Spalten (Quellspalten) an, die im Dialogfeld **Quellen-Editor für SAP BW** auf der Seite **Spalten** ausgewählt wurden. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Quellen-Editor für SAP BW &#40;Seite „Spalten“&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md).  
  
 **Fehler**  
 Gibt an, wie die SAP BW-Quellkomponente bei einem Fehler vorgehen soll: den Fehler ignorieren, die Zeile umleiten oder die Komponente mit einem Fehler abbrechen.  
  
 **Abschneiden**  
 Gibt an, wie die SAP BW-Quellkomponente bei einer Kürzung vorgehen soll: den Fehler ignorieren, die Zeile umleiten oder die Komponente mit einem Fehler abbrechen.  
  
 **Beschreibung**  
 Zeigt die Beschreibung des Fehlers an.  
  
 **Diesen Wert für ausgewählte Zellen festlegen**  
 Gibt an, wie die SAP BW-Quellkomponente im Falle eines Fehlers oder einer Kürzung vorgehen soll: den Fehler ignorieren, die Zeile umleiten oder die Komponente mit einem Fehler abbrechen.  
  
 **Anwenden**  
 Wendet die Fehlerbehandlungsoption auf die ausgewählten Zellen an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellen-Editor für SAP BW &#40;Seite „Verbindungs-Manager“&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Quellen-Editor für SAP BW &#40;Seite „Spalten“&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [Quellen-Editor für SAP BW &#40;Seite „Erweitert“&#41;](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [F1-Hilfe zum Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
