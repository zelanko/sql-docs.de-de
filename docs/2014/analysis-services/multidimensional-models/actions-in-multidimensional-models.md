---
title: Aktionen in mehrdimensionalen Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- actions [Analysis Services], creating
- report actions [Analysis Services]
- drillthrough actions [Analysis Services]
- cubes [Analysis Services], actions
ms.assetid: b9fee2b9-05a5-4077-848d-d8457326dc27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 19754c99e87c50121fc79b80649d7555b79ca59e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544874"
---
# <a name="actions-in-multidimensional-models"></a>Aktionen in mehrdimensionalen Modellen
  Eine Aktion ist ein vom Endbenutzer initiierter Vorgang, der auf einem ausgewählten Cube oder Teil eines Cubes ausgeführt wird. Der Vorgang kann eine Anwendung mit dem ausgewählten Element als Parameter starten, oder er kann Informationen zum ausgewählten Element abrufen. Weitere Informationen zu Aktionstypen finden Sie unter [Aktionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](actions-analysis-services-multidimensional-data.md).  
  
 Mithilfe der Registerkarte **Aktionen** des Cube-Designers können Sie Aktionen für einen Cube erstellen. Geben Sie Folgendes an:  
  
 **Name**  
 Wählen Sie einen Namen für die Aktion aus.  
  
 **Aktionsziel**  
 Wählen Sie das Objekt aus, dem die Aktion angefügt wird. In Clientanwendungen wird die Aktion grundsätzlich angezeigt, wenn der Endbenutzer das Zielobjekt ausgewählt hat; jedoch bestimmt die Clientanwendung, welcher Endbenutzervorgang Aktionen anzeigt. Wählen Sie für **Zieltyp**aus den folgenden Objekten aus:  
  
-   Attributelemente  
  
-   Zellen  
  
-   Cube  
  
-   Dimensionselemente  
  
-   Hierarchy  
  
-   Hierarchieelemente  
  
-   Ebene  
  
-   Ebenenelemente  
  
 Nachdem Sie den Zielobjekttyp ausgewählt haben, wählen Sie unter **Zielobjekt**das Cubeobjekt vom entsprechenden Typ aus.  
  
 **Bedingung (Optional)**  
 Geben Sie einen optionalen MDX-Ausdruck (Multidimensional Expressions) an, der zu einem Booleschen Wert aufgelöst wird. Beim Wert `True` wird die Aktion für das angegebene Ziel durchgeführt. Beim Wert `False` wird die Aktion nicht durchgeführt.  
  
 **Aktionsinhalt**  
 Wählen Sie den Typ der Aktion aus. In der folgenden Tabelle werden die verfügbaren Aktionstypen zusammengefasst.  
  
|type|Beschreibung|  
|----------|-----------------|  
|Dataset|Ruft ein Dataset ab.|  
|Proprietär|Führt einen Vorgang über eine Schnittstelle aus, die nicht in dieser Tabelle aufgelistet ist.|  
|Rowset|Ruft ein Rowset ab.|  
|-Anweisung.|Gibt einen OLE DB-Befehl zurück.|  
|URL|Zeigt eine veränderliche Seite in einem Internetbrowser an.|  
  
 Geben Sie für **Aktionsausdruck**die Parameter an, die beim Ausführen der Aktion übergeben werden. Die Syntax muss zu einer Zeichenfolge ausgewertet werden, und Sie müssen einen in MDX geschriebenen Ausdruck einschließen. Der MDX-Ausdruck kann z. B. einen Teil des Cubes anzeigen, der in die Syntax eingeschlossen ist. MDX-Ausdrücke werden ausgewertet, bevor die Parameter übergeben werden. Darüber hinaus steht Ihnen der MDX-Generator zur Verfügung, der Sie bei der Erstellung von MDX-Ausdrücken unterstützt.  
  
 **Zusätzliche Eigenschaften**  
 Wählen Sie die Eigenschaft aus. In der folgenden Tabelle werden die verfügbaren Eigenschaften zusammengefasst.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|**Aufruf**|Gibt an, wie die Aktion ausgeführt wird. Die Standardeinstellung Interaktiv gibt an, dass die Aktion ausgeführt wird, wenn ein Benutzer auf ein Objekt zugreift. Die möglichen Einstellungen sind:<br /><br /> Batch<br /><br /> Interactive<br /><br /> Beim Öffnen|  
|**Anwendung**|Beschreibt die Anwendung der Aktion.|  
|**Beschreibung**|Beschreibt die Aktion.|  
|**Caption**|Stellt eine Beschriftung bereit, die für die Aktion angezeigt wird. Wenn es sich bei der Beschriftung um MDX handelt, geben Sie `True` für **Beschriftung ist MDX**an.|  
|**Beschriftung ist MDX**|Geben Sie `True` an, wenn es sich bei der Beschriftung um MDX handelt; andernfalls geben Sie `False` an.|  
  
> [!NOTE]  
>  Sie müssen Analysis Services Scripting Language (ASSL) oder Analysis Management Objects (AMO) verwenden, um HTML- und Befehlszeilen-Aktionstypen zu definieren. Weitere Informationen finden Sie unter [Action-Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl), [Type-Element &#40;Action&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl) und [Programmieren von erweiterten AMO OLAP-Objekten](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects).  
  
## <a name="creating-a-reporting-action"></a>Erstellen einer Berichtsaktion  
 Der Berichtsserver antwortet auf URL-basierte Anforderungen nach Berichten. Klicken Sie zum Erstellen einer Berichtsaktion im Menü **Cube** auf **Neue Berichtsaktion**. Eine Berichtsaktion zeichnet sich durch die folgenden spezifischen Optionen aus.  
  
 **Berichts Server**  
 Die in der folgenden Tabelle beschriebenen Eigenschaften sind spezifisch für den Berichtsserver.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|**Servername**|Name des Computers, auf dem der Berichtsserver ausgeführt wird.|  
|**Serverpfad**|Der vom Berichtsserver verfügbar gemachte Pfad.|  
|**Berichtsformat**|HTML5, HTML3, Excel oder PDF.|  
  
 **Parameter (Optional)**  
 Die Parameter werden als Bestandteil der URL-Zeichenfolge an den Server gesendet, wenn die Aktion erstellt wird. Dazu gehören **Parametername** und **Parameterwert**, wobei es sich um einen MDX-Ausdruck handelt.  
  
 Die Berichtsserver-URL setzt sich wie folgt zusammen:  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 Zum Beispiel:  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a>Erstellen einer Drillthroughaktion  
 Eine Drillthroughaktion wird durch eine Rowsetaktion definiert, die als Drillthroughanweisung an die Clientanwendung zurückgegeben wird. Das Aktionsziel ist ein Mitglied einer Measuregruppe. Klicken Sie zum Erstellen einer neuen Drillthroughaktion im Menü **Cube** auf **Neue Drillthroughaktion**. Eine Drillthroughaktion zeichnet sich durch die folgenden spezifischen Optionen aus:  
  
 **Drillthroughspalten**  
 Wählen Sie eine oder mehrere Dimensionen aus und für jede Dimension die durch die Aktion an die Clientanwendung zurückgegebenen Drillthroughspalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cubes in mehrdimensionalen Modellen](cubes-in-multidimensional-models.md)  
  
  
