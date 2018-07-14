---
title: Objektbenennungsregeln (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c59c295c627c311aaec574ecd04b153004c3c926
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202080"
---
# <a name="object-naming-rules-analysis-services"></a>Objektbenennungsregeln (Analysis Services)
  In diesem Thema werden Benennungskonventionen für Objekte sowie reservierte Wörter und Zeichen beschrieben, die in Objektnamen, in Code oder Skripts in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht verwendet werden können.  
  
##  <a name="bkmk_Names"></a> Benennungskonventionen  
 Jedes Objekt verfügt über eine `Name`-Eigenschaft und eine `ID`-Eigenschaft, die innerhalb des Bereichs der übergeordneten Auflistung eindeutig sein müssen. Beispielsweise können zwei Dimensionen denselben Namen haben, solange sich beide in unterschiedlichen Datenbanken befinden.  
  
 Obwohl Sie die `ID` manuell angeben können, wird sie normalerweise bei der Objekterstellung automatisch generiert. Die `ID` sollte nicht mehr geändert werden, nachdem Sie mit dem Erstellen eines Modells begonnen haben. Alle Objektverweise im gesamten Modell basieren auf der `ID`. Daher kann die Änderung einer `ID` dazu führen, dass das Modell beschädigt wird.  
  
 Bei den Benennungskonventionen für `DataSource`-Objekte und `DataSourceView`-Objekte gelten keine nennenswerten Ausnahmen. Die `DataSource`-ID kann auf einen einzelnen Punkt (.) festgelegt werden, der als Verweis auf die aktuelle Datenbank dient, aber nicht eindeutig ist. Eine zweite Ausnahme bildet das `DataSourceView`-Objekt, das der für `DataSet`-Objekte in .NET Framework definierten Benennungskonvention folgt, bei der `Name` als Bezeichner verwendet wird.  
  
 Die folgenden Regeln gelten für `Name`-Eigenschaften und `ID`-Eigenschaften.  
  
-   Bei den Namen wird die Groß-/Kleinschreibung nicht berücksichtigt. Ein Cube mit dem Namen "sales" und ein anderer mit dem Namen "Sales" können nicht gleichzeitig in derselben Datenbank vorhanden sein.  
  
-   Führende oder nachfolgende Leerzeichen sind in Objektnamen nicht zulässig. Innerhalb des Namens können Leerzeichen verwendet werden. Führende und nachfolgende Leerzeichen werden implizit abgeschnitten. Davon betroffen sind der `Name` und die `ID` eines Objekts.  
  
-   Es können maximal 100 Zeichen eingegeben werden.  
  
-   Es gibt keine besondere Anforderung für das erste Zeichen eines Bezeichners. Das erste Zeichen kann jedes gültige Zeichen sein.  
  
##  <a name="bkmk_reserved"></a> Reservierte Wörter und Zeichen  
 Reservierte Wörter sind auf Englisch und gelten für Objektnamen, nicht für Beschriftungen. Wenn Sie versehentlich ein reserviertes Wort in einem Objektnamen verwenden, tritt ein Überprüfungsfehler auf. Bei mehrdimensionalen und Data Mining-Modellen können die unten beschriebenen reservierten Wörter in Objektnamen nicht verwendet werden.  
  
 Bei tabellarischen Modellen, deren Datenbankkompatibilität auf 1103 festgelegt ist, wurden die Überprüfungsregeln für bestimmte Objekte gelockert, um Kompatibilität mit den erweiterten Zeichenanforderungen und Benennungskonventionen bestimmter Clientanwendungen zu gewährleisten. Datenbanken, die diese Kriterien erfüllen, unterliegen weniger strengen Überprüfungsregeln. In diesem Fall ist die Überprüfung eines Objektnamens auch dann erfolgreich, wenn er reserviertes Zeichen enthält.  
  
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
|`Server`|Beachten Sie die Windows-Serverbenennungskonventionen, wenn Sie ein Serverobjekt benennen. Finden Sie unter [Benennungskonventionen (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682856\(v=vs.85\).aspx) Details.|  
|`DataSource`|: / \ * &#124; ? "() [] {} <>|  
|`Level` oder `Attribute`|zugreifen. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] {} \< >|  
|`Dimension` oder `Hierarchy`|zugreifen. , ; ' ` : / \ * &#124; ? " & % $ ! + () [] = {} \<, >|  
|Alle anderen Objekte|zugreifen. , ; ' ` : / \ * &#124; ? " & % $ ! + = () [] {} \< >|  
  
 **Ausnahmen: Wenn reservierte Zeichen zulässig sind**  
  
 Wie bereits erwähnt, können in Datenbanken mit einer bestimmten Modalität und einem bestimmten Kompatibilitätsgrad Objektnamen verwendet werden, die reservierte Zeichen enthalten. Dimensionsattribut-, Hierarchie-, Ebenen-, Measure- und KPI-Objektnamen für tabellarische Datenbanken (1103 oder höher) können reservierte Zeichen enthalten, wenn diese Datenbanken die Verwendung erweiterter Zeichen zulassen:  
  
|Servermodus und Datenbank-Kompatibilitätsgrad|Reservierte Zeichen zulässig?|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (alle Versionen)|nein|  
|Tabellarischer Modus - 1050|nein|  
|Tabellarischer Modus - 1100|nein|  
|Tabellarischer Modus – 1130 und höher|ja|  
  
 Für Datenbanken kann als ModelType Default angegeben sein. 
          Default ist äquivalent zu Multidimensional, und die Verwendung von reservierten Zeichen in Spaltennamen wird in diesem Fall nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Reservierte Wörter in MDX](/sql/mdx/mdx-reserved-words)   
 [Übersetzungen &#40;Analysis Services&#41;](../../../analysis-services/translations-analysis-services.md)   
 [XML for Analysis-Kompatibilität &#40;XMLA&#41;](../../xmla/xml-for-analysis-compliance-xmla.md)  
  
  
