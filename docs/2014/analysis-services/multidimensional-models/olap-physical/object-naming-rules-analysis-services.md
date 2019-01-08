---
title: Objektbenennungsregeln (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c8bcf9fc52ef26837d32fa765472e0056469a2a
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52511322"
---
# <a name="object-naming-rules-analysis-services"></a>Objektbenennungsregeln (Analysis Services)
  In diesem Thema werden die Benennungskonventionen für Objekte sowie reservierte Wörter und Zeichen beschieben, die in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht in Objektnamen, Code oder Skripts verwendet werden können.  
  
##  <a name="bkmk_Names"></a> Benennungskonventionen  
 Jedes Objekt verfügt über eine `Name`-Eigenschaft und eine `ID`-Eigenschaft, die innerhalb des Bereichs der übergeordneten Auflistung eindeutig sein müssen. Beispielsweise können zwei Dimensionen denselben Namen haben, solange sich beide in unterschiedlichen Datenbanken befinden.  
  
 Sie können die `ID` manuell eingeben. In der Regel wird diese jedoch automatisch beim Erstellen des Objekts generiert. Ändern Sie die `ID` nicht, nachdem Sie mit dem Erstellen eines Modells begonnen haben. Alle Objektverweise innerhalb eines Modells basieren auf der `ID`. Daher kann das Ändern der `ID` sehr schnell zu Fehlern im Modell führen.  
  
 Bei den Benennungskonventionen für `DataSource`-Objekte und `DataSourceView`-Objekte gelten keine nennenswerten Ausnahmen. Die `DataSource`-ID kann auf einen einzelnen Punkt (.) festgelegt werden, der als Verweis auf die aktuelle Datenbank dient, aber nicht eindeutig ist. Eine zweite Ausnahme ist `DataSourceView`, das den Benennungskonventionen für `DataSet`-Objekte in .NET Framework folgt und `Name` als Bezeichner verwendet.  
  
 Für die `Name`-Eigenschaft und die `ID`-Eigenschaft gelten folgende Regeln.  
  
-   Bei den Namen wird die Groß-/Kleinschreibung nicht berücksichtigt. Sie können einen Cube mit dem Namen "Sales" keine und eine andere mit dem Namen "Sales" in der gleichen Datenbank.  
  
-   Führende oder nachfolgende Leerzeichen sind in Objektnamen nicht zulässig. Innerhalb des Namens können Leerzeichen verwendet werden. Führende und nachfolgende Leerzeichen werden implizit abgeschnitten. Dies gilt für die `Name`-Eigenschaft und die `ID`-Eigenschaft eines Objekts.  
  
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
|`Server`|Beachten Sie die Windows-Serverbenennungskonventionen, wenn Sie ein Serverobjekt benennen. Finden Sie unter [Benennungskonventionen (Windows)](/windows/desktop/DNS/naming-conventions) Details.|  
|`DataSource`|: / \ * &#124; ? "() [] {} <>|  
|`Level` oder `Attribute`|. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] {} \< >|  
|`Dimension` oder `Hierarchy`|. , ; ' ` : / \ * &#124; ? " & % $ ! + () [] = {} \<, >|  
|Alle anderen Objekte|. , ; ' ` : / \ * &#124; ? " & % $ ! + = () [] {} \< >|  
  
 **Ausnahmen: Wenn reservierte Zeichen zulässig sind**  
  
 Wie bereits erwähnt, können in Datenbanken mit einer bestimmten Modalität und einem bestimmten Kompatibilitätsgrad Objektnamen verwendet werden, die reservierte Zeichen enthalten. Dimensionsattribut-, Hierarchie-, Ebenen-, Measure- und KPI-Objektnamen für tabellarische Datenbanken (1103 oder höher) können reservierte Zeichen enthalten, wenn diese Datenbanken die Verwendung erweiterter Zeichen zulassen:  
  
|Servermodus und Datenbank-Kompatibilitätsgrad|Reservierte Zeichen zulässig?|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (alle Versionen)|Nein|  
|Tabellarischer Modus - 1050|Nein|  
|Tabellarischer Modus - 1100|Nein|  
|Tabellarischer Modus – 1130 und höher|Ja|  
  
 Für Datenbanken kann als ModelType Default angegeben sein. Default ist äquivalent zu Multidimensional, und die Verwendung von reservierten Zeichen in Spaltennamen wird in diesem Fall nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Reservierte Wörter in MDX](/sql/mdx/mdx-reserved-words)   
 [Übersetzungen &#40;Analysis Services&#41;](../../../analysis-services/translations-analysis-services.md)   
 [XML for Analysis-Kompatibilität &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
