---
title: Objektbenennungsregeln (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 64e04754fd4bc4a404854eb5260daddf543e3c2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65979962"
---
# <a name="object-naming-rules-analysis-services"></a>Objektbenennungsregeln (Analysis Services)
  In diesem Thema werden Benennungskonventionen für Objekte sowie reservierte Wörter und Zeichen beschrieben, die in Objektnamen, in Code oder Skripts in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht verwendet werden können.  
  
##  <a name="bkmk_Names"></a> Benennungskonventionen  
 Jedes Objekt verfügt über eine `Name`-Eigenschaft und eine `ID`-Eigenschaft, die innerhalb des Bereichs der übergeordneten Auflistung eindeutig sein müssen. Beispielsweise können zwei Dimensionen denselben Namen haben, solange sich beide in unterschiedlichen Datenbanken befinden.  
  
 Sie können die `ID` manuell eingeben. In der Regel wird diese jedoch automatisch beim Erstellen des Objekts generiert. Die `ID` sollte nicht mehr geändert werden, nachdem Sie mit dem Erstellen eines Modells begonnen haben. Alle Objektverweise im gesamten Modell basieren auf der `ID`. Daher kann das Ändern der `ID` sehr schnell zu Fehlern im Modell führen.  
  
 Bei den Benennungskonventionen für `DataSource`-Objekte und `DataSourceView`-Objekte gelten keine nennenswerten Ausnahmen. Die `DataSource`-ID kann auf einen einzelnen Punkt (.) festgelegt werden, der als Verweis auf die aktuelle Datenbank dient, aber nicht eindeutig ist. Eine zweite Ausnahme bildet das `DataSourceView`-Objekt, das der für `DataSet`-Objekte in .NET Framework definierten Benennungskonvention folgt, bei der `Name` als Bezeichner verwendet wird.  
  
 Die folgenden Regeln gelten für `Name`-Eigenschaften und `ID`-Eigenschaften.  
  
-   Bei den Namen wird die Groß-/Kleinschreibung nicht berücksichtigt. Sie können einen Cube mit dem Namen "Sales" keine und eine andere mit dem Namen "Sales" in der gleichen Datenbank.  
  
-   Führende oder nachfolgende Leerzeichen sind in Objektnamen nicht zulässig. Innerhalb des Namens können Leerzeichen verwendet werden. Führende und nachstehende Leerzeichen werden implizit abgeschnitten. Dies gilt für die `Name`-Eigenschaft und die `ID`-Eigenschaft eines Objekts.  
  
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
|`Server`|Befolgen Sie beim Benennen von Serverobjekten die Benennungskonventionen für Windows-Server. Finden Sie unter [Benennungskonventionen (Windows)](/windows/desktop/DNS/naming-conventions) Details.|  
|`DataSource`|`: / \ * | ? " () [] {} <>`|  
|`Level` oder `Attribute`|````. , ; ' ` : / \ * &| ? " & % $ ! + = [] {} \< >````|  
|`Dimension` oder `Hierarchy`|````. , ; ' ` : / \ * | ? " & % $ ! + = () [] {} \<,>````|  
|Alle anderen Objekte|````. , ; ' ` : / \ * | ? " & % $ ! + = () [] {} \< >````|  
  
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
 [Reservierte Wörter in MDX](/sql/mdx/mdx-reserved-words)   
 [Übersetzungen &#40;Analysis Services&#41;](../../../analysis-services/translations-analysis-services.md)   
 [XML for Analysis-Kompatibilität &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
