---
title: Wählen Sie die Dimensionsattribute (Dimensions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7abb4560696dba21512066a7ff0ba3153ae2319a
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52508014"
---
# <a name="select-dimension-attributes-dimension-wizard"></a>Dimensionsattribute auswählen (Dimensions-Assistent)
  Auf der Seite **Dimensionsattribute auswählen** können Sie die Attribute für die zu erstellende Dimension auswählen und ändern.  
  
> [!NOTE]  
>  Wenn die Werte einer Spalte nicht vollständig angezeigt werden, können Sie das Assistentenfenster maximieren und die Breite jeder Spaltenüberschrift ändern, bis Sie die Werte lesen können.  
  
 **Um den Dimensions-Assistenten zu öffnen.**  
  
-   Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im **Projektmappen-Explorer**mit der rechten Maustaste auf den Ordner **Dimensionen** eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekts, und klicken Sie anschließend auf **Neue Dimension**.  
  
## <a name="options"></a>Optionen  
 (Spalte mit Kontrollkästchen)  
 Wählen Sie diese Option aus, um ein Attribut in die Dimension einzuschließen.  
  
 Wenn Sie ein spezielles Attribut einschließen möchten, aktivieren Sie das Kontrollkästchen für dieses Attribut.  
  
 Wenn Sie alle Attribute einschließen möchten, aktivieren Sie das Kontrollkästchen im Spaltenheader.  
  
> [!NOTE]  
>  Das Kontrollkästchen für das Schlüsselattribut kann nicht deaktiviert werden.  
  
 **Attributname**  
 Listet die verfügbaren Attribute auf.  
  
 Wenn Sie den Namen eines Attributs ändern möchten, klicken Sie auf den Attributnamen, und geben Sie einen neuen Namen ein.  
  
 **Durchsuchen aktivieren**  
 Wählen Sie diese Option aus, damit der Endbenutzer das Attribut durchsuchen und filtern kann. Die Option**Durchsuchen aktivieren** muss für das Schlüsselattribut aktiviert werden. In der Standardeinstellung ist die Option **Durchsuchen aktivieren** bei Attributen, die keine Schlüsselattribut sind, nicht aktiviert, sodass diese nur als Elementeigenschaften dargestellt werden.  
  
 In den meisten Fällen wird das Durchsuchen eines Attributs ermöglicht oder unterbunden, indem die `AttributeHierarchyEnabled`-Eigenschaft auf `True` bzw. `False` festgelegt wird. In den folgenden drei Fällen verwendet der Assistent jedoch andere Einstellungen.  
  
|Fall|Einstellungen|  
|----------|--------------|  
|Eine Dimension enthält eine Über-/Unterordnungshierarchie, und die Option **Durchsuchen aktivieren** ist nicht aktiviert.|Der Assistent behält für die `AttributeHierarchyEnabled`-Eigenschaft die Einstellung `True` bei und legt das `AttributeHierarchyVisible`-Attribut für das Schlüsselattribut auf `False` fest.|  
|Eine Tabelle in einer Dimension enthält einen Fremdschlüssel für eine Tabelle, die nicht in der Dimension enthalten ist.|Der Assistent wählt den Fremdschlüssel als aufzunehmendes Attribut aus, aktiviert die Option **Durchsuchen aktivieren**aber nicht. Wenn Sie diese Einstellungen beibehalten, dann ist die `AttributeHiearchyEnabled`-Eigenschaft des Attributs auf `True` festgelegt, und die `AttributeHieararchyVisible`Eigenschaft ist auf `False` festgelegt.|  
|Eine Dimension enthält Schneeflockentabellen, die durch auf NULL festlegbare Fremdschlüsselspalten erreicht werden<br /><br /> – und –<br /><br /> Die Option Durchsuchen aktivieren wird für das Attribut, das auf dem Schlüssel der Schneeflockentabelle basiert, nicht aktiviert.|Der Assistent erstellt das neue Attribut, dessen `AttributeHiearchyEnabled`-Eigenschaft auf `True` und dessen `AttributeHieararchyVisible`-Eigenschaft auf `False` festgelegt ist.|  
  
 **Attributtyp**  
 (Optional) Legen Sie den Typ des Attributs fest. Der Standardwert ist **Regulär**. Der Attributtyp stellt Clientanwendungen Hinweise dazu bereit, welche Informationen das Attribut enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensions-Assistent F1-Hilfe](dimension-wizard-f1-help.md)   
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
