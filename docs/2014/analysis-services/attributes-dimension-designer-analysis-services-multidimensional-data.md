---
title: Attribute (Registerkarte Dimensions Struktur, Dimensions-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.attributespane.f1
ms.assetid: 627eaa08-7638-4edd-bdfa-0d8175a7cde5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a9eab7de49abaf06446fbd03f7b80c381d102f20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66064399"
---
# <a name="attributes-dimension-structure-tab-dimension-designer-analysis-services---multidimensional-data"></a>Attribute (Registerkarte Dimensionsstruktur, Dimensions-Designer) (Analysis Services – Mehrdimensionale Daten)
  Verwalten Sie mithilfe dieses Bereichs die mit der ausgewählten Dimension verknüpften Attribute. Attribute können aus diesem Bereich in den Bereich **Hierarchien** gezogen werden, um so Hierarchien und Ebenen zu erstellen. Weitere Informationen finden Sie unter [Hierarchies &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md).  
  
 Zum Erstellen eines Attributs ziehen Sie eine Spalte aus dem Bereich **Datenquellensicht** in den Bereich **Attribute** , während Sie sich im Listen-, Struktur- oder Sichtmodus befinden. Zum Entfernen eines Attributs wählen Sie im Kontextmenü die Option **Löschen** .  
  
 **So zeigen Sie den Bereich Attribute an**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt, und öffnen Sie dann die gewünschte Dimension.  
  
2.  Wenn sie nicht ausgewählt ist, klicken Sie auf die Registerkarte **Dimensionsstruktur** .  
  
## <a name="options"></a>Tastatur  
 **Attribute**  
 Zeigt die für die ausgewählte Dimension verfügbaren Attribute an. Diese Option kann in den folgenden Modi angezeigt werden:  
  
-   Listenmodus  
  
     In diesem Modus können Sie Hierarchien erstellen und ändern. Zum Anzeigen der Attribute im Listenmodus wählen Sie aus dem Kontextmenü die Option **Attribute anzeigen in** , und klicken Sie dann auf **Liste**.  
  
-   Strukturmodus  
  
     In diesem Modus können Sie Hierarchien erstellen und ändern. Zum Anzeigen der Attribute im Strukturmodus wählen Sie aus dem Kontextmenü die Option **Attribute anzeigen in** , und klicken Sie dann auf **Struktur**.  
  
-   Rastermodus  
  
     In diesem Modus können Sie Dimensionen manuell erstellen und Attributeigenschaften ändern. Zum Anzeigen der Attribute im Strukturmodus wählen Sie aus dem Kontextmenü die Option **Attribute anzeigen in** , und klicken Sie dann auf **Raster**.  
  
## <a name="grid-mode-options"></a>Rastermodusoptionen  
 Beim Anzeigen von Attributen im Rastermodus haben Sie Zugriff auf die in der folgenden Tabelle aufgeführten Spalten.  
  
 **Name**  
 Zeigt den Namen des Attributs an.  
  
 **Verwendung**  
 Legt die Verwendung des ausgewählten Attributs fest. Klicken Sie auf den Pfeil nach unten, und wählen Sie eine der folgenden Optionen aus:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|Regulär |Identifiziert ein reguläres Attribut.|  
|Key|Identifiziert das Schlüsselattribut für die Dimension. Dies entspricht den Blattelementen der Dimension. Pro Dimension kann es nur ein Schlüsselattribut geben. Klicken Sie zum Ändern des Attributs auf die Schaltfläche mit den Auslassungspunkten (**...**) neben der Eigenschaft **KeyColumns** im Bereich **Eigenschaften** .|  
|Parent|Bezeichnet das übergeordnete Attribut einer Über-/Unterordnungsbeziehung. In dieser Beziehung muss das untergeordnete Attribut immer ein Schlüsselattribut sein.|  
|AccountType|Bezeichnet ein Kontotypattribut. Wird vom Server oder von der Engine verwendet, wenn die Aggregatfunktion für ein Measure auf Aggregieren nach Konto ("ByAccount") festgelegt wird.|  
  
 **Typ**  
 Legt den Attributtyp fest. Klicken Sie auf den Pfeil nach unten, um eine der verfügbaren Optionen auszuwählen.  
  
 **Schlüssel Spalte**  
 Zeigt den Datentyp der zugrunde liegenden Spalten an. Klicken Sie beim Erstellen eines neuen Attributs auf den Pfeil nach unten, um eine der verfügbaren Optionen auszuwählen.  
  
 **Namensspalte**  
 Zeigt den Speicherort der zugrunde liegenden Spalte an. Klicken Sie beim Erstellen eines neuen Attributs auf den Pfeil nach unten, um zwischen den Optionen **Wie Schlüssel** oder **Eigene Spalte**zu wählen. Wenn Sie die Option **Eigene Spalte** auswählen, legt die Eigenschaft **NameColumn** im Bereich **Eigenschaften** die Spalte fest, die den für das Attribut zu verwendenden Namen speichert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions Struktur &#40;Dimensions-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md)   
 [Hierarchien &#40;Registerkarte "Dimensions Struktur", Dimensions-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte "Dimensions Struktur", Dimensions-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md)  
  
  
