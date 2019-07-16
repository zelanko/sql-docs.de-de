---
title: Objektbenennungsregeln (Analysis Services) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7267097b1a06cb44c801ed20cbfd206c330328ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165458"
---
# <a name="object-naming-rules-analysis-services"></a>Objektbenennungsregeln (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  In diesem Thema werden Benennungskonventionen für Objekte sowie reservierte Wörter und Zeichen beschrieben, die in Objektnamen, in Code oder Skripts in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht verwendet werden können.  
  
##  <a name="bkmk_Names"></a> Benennungskonventionen  
 Jedes Objekt verfügt über eine **Namen** und **ID** -Eigenschaft, die innerhalb des Bereichs der übergeordneten Auflistung eindeutig sein muss. Beispielsweise können zwei Dimensionen denselben Namen haben, solange sich beide in unterschiedlichen Datenbanken befinden.  
  
 Obwohl Sie es manuell angeben können die **ID** ist in der Regel automatisch generiert, wenn das Objekt erstellt wird. Sie sollten keine Änderung der **ID** Nachdem Sie begonnen haben, Erstellen eines Modells. Alle Objektverweise innerhalb eines Modells basieren auf der **ID**. Daher kann das Ändern einer **ID** sehr schnell zu Fehlern im Modell führen.  
  
 **DataSource** und **DataSourceView** Objekte gelten einige wichtige Ausnahmen Benennungskonventionen. **DataSource** ID kann ein einzelner Punkt (.), handelt es sich nicht eindeutig ist, als Verweis auf die aktuelle Datenbank festgelegt werden. Eine zweite Ausnahme ist **DataSourceView**, die entspricht der Benennungskonventionen für **DataSet** Objekte in .NET Framework, in dem die **Namen** dient als die Bezeichner.  
  
 Die folgenden Regeln gelten für **Namen** und **ID** Eigenschaften.  
  
-   Bei den Namen wird die Groß-/Kleinschreibung nicht berücksichtigt. Sie können einen Cube mit dem Namen "Sales" keine und eine andere mit dem Namen "Sales" in der gleichen Datenbank.  
  
-   Führende oder nachfolgende Leerzeichen sind in Objektnamen nicht zulässig. Innerhalb des Namens können Leerzeichen verwendet werden. Führende und nachstehende Leerzeichen werden implizit abgeschnitten. Dies gilt für die **Namen** und **ID** eines Objekts.  
  
-   Es können maximal 100 Zeichen eingegeben werden.  
  
-   Es gibt keine besondere Anforderung für das erste Zeichen eines Bezeichners. Das erste Zeichen kann ein beliebiges gültiges Zeichen sein.  
  
##  <a name="bkmk_reserved"></a> Reservierte Wörter und Zeichen  
 Reservierte Wörter sind auf Englisch und gelten für Objektnamen, nicht für Beschriftungen. Falls Sie ein reserviertes Wort versehentlich in einem Objektnamen verwenden, tritt ein Überprüfungsfehler auf. Die unten aufgeführten reservierten Wörter dürfen in keinem Fall in Objektnamen für mehrdimensionale Modelle und Data Mining-Modelle verwendet werden.  
  
 Bei tabellarischen Modellen mit dem Datenbank-Kompatibilitätsgrad 1103 wurden die Überprüfungsregeln für bestimmte Objekte gelockert, um zu gewährleisten, dass sie mit den Anforderungen an erweiterte Zeichen und Benennungskonventionen bestimmter Clientanwendungen kompatibel sind. Datenbanken, die diese Kriterien erfüllen, unterliegen weniger strengen Überprüfungsregeln. In diesem Fall kann ein Objekt die Überprüfung bestehen, obwohl es ein eingeschränktes Zeichen enthält.  
  
 **Reservierte Wörter**  
  
-   AUX  
  
-   CLOCK$  
  
-   COM1 bis COM9 (COM1, COM2, COM3 usw.)  
  
-   CON  
  
-   LPT1 bis LPT9 (LPT1, LPT2, LPT3 usw.)  
  
-   NUL  
  
-   PRN  
  
-   NULL ist in XML in keiner Zeichenfolge als Zeichen zulässig.  
  
 **Reservierte Zeichen**  
  
 In der folgenden Tabelle werden die ungültigen Zeichen für bestimmte Objekte aufgeführt.  
  
|Objekt|Ungültige Zeichen|  
|------------|------------------------|  
|**Server**|Befolgen Sie beim Benennen von Serverobjekten die Benennungskonventionen für Windows-Server. Finden Sie unter [Benennungskonventionen (Windows)](/windows/desktop/DNS/naming-conventions) Details.|  
|**DataSource**|: / \ * &#124; ? "() [] {} <>|  
|**Ebene** oder **Attribut**|. , ; ' ` : / \ * &#124; ? "& % $! + = [] {} < >|  
|**Dimension** oder **Hierarchie**|. , ; ' ` : / \ * &#124; ? "& % $! + () [] = {} \<, >|  
|Alle anderen Objekte|. , ; ' ` : / \ * &#124; ? "& % $! + () [] = {} < >|  
  
 **Ausnahmen: Wenn reservierte Zeichen zulässig sind**  
  
 Wie bereits erwähnt, können Datenbanken mit einem bestimmten Modalitäts- und Kompatibilitätsgrad Objektnamen enthalten, die reservierte Zeichen aufweisen. Dimensionsattribut-, Hierarchie-, Ebenen-, Measure- und KPI-Objektnamen für tabellarische Datenbanken (1103 oder höher) können reservierte Zeichen enthalten, wenn diese Datenbanken die Verwendung erweiterter Zeichen zulassen:  
  
|Servermodus und Datenbank-Kompatibilitätsgrad|Reservierte Zeichen zulässig?|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (alle Versionen)|Nein|  
|Tabellarischer Modus - 1050|Nein|  
|Tabellarischer Modus - 1100|Nein|  
|Tabellarischer Modus – 1130 und höher|Ja|  
  
 ModelType kann für Datenbanken auf default festgelegt sein. Da default mit multidimensional identisch ist, werden reservierte Zeichen in Spaltennamen folglich nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Reservierte Wörter in MDX](../../../mdx/mdx-reserved-words.md)   
 [Unterstützung für Übersetzungen in Analysis Services](../../../analysis-services/translation-support-in-analysis-services.md)   
 [XML for Analysis-Kompatibilität &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
