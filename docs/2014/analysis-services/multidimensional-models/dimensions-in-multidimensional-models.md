---
title: Dimensionen in mehrdimensionalen Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a25bcc56bdd0a0f07c0ebaa6e59de0b44979661d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165850"
---
# <a name="dimensions-in-multidimensional-models"></a>Dimensionen in mehrdimensionalen Modellen
  Eine Datenbankdimension ist eine Auflistung verknüpfter Objekte, Attribute genannt, mit deren Hilfe Informationen zu Faktendaten in einem oder mehreren Cubes zur Verfügung gestellt werden können. Typische Attribute in einer Produktdimension können z. B. Produktname, Produktkategorie, Produktlinie, Produktgröße und Produktpreis sein. Diese Objekte sind an eine oder mehrere Spalten in einer oder mehreren Tabellen in einer Datenquellensicht gebunden. Standardmäßig sind diese Attribute als Attributhierarchien sichtbar und dienen zum besseren Verständnis der Faktdaten in einem Cube. Attribute können in Form von benutzerdefinierten Hierarchien organisiert werden, die Navigationspfade bereitstellen, um Benutzer beim Durchsuchen der Daten in einem Cube zu unterstützen.  
  
 Cubes enthalten alle Dimensionen, auf die Benutzer ihre Analysen von Faktendaten stützen. Eine Instanz einer Datenbankdimension in einem Cube wird Cubedimension genannt. Sie bezieht sich auf eine oder mehrere Measuregruppen in einem Cube. Eine Datenbankdimension kann mehrere Male in einem Cube verwendet werden. Eine Faktentabelle kann z. B. mehrere zeitbezogene Fakten aufweisen, und es kann eine separate Cubedimension definiert werden, die die Analyse der einzelnen zeitbezogenen Fakten unterstützt. Es muss jedoch nur eine zeitbezogene Datenbankdimension vorhanden sein, was auch bedeutet, dass nur eine zeitbezogene relationale Datenbanktabelle vorhanden sein muss, um mehrere zeitbasierte Cubedimensionen zu unterstützen.  
  
> [!NOTE]  
>  Informationen zu Leistungsproblemen im Zusammenhang mit dem Dimensionsentwurf finden Sie im [Leistungsleitfaden zu SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=306717).  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a>Definieren von Dimensionen, Attributen und Hierarchien  
 Die einfachste Möglichkeit, Datenbank- und Cubedimensionen, Attribute und Hierarchien zu definieren, besteht darin, den Cube-Assistenten zu verwenden, um Dimensionen zur gleichen Zeit zu erstellen, zu der Sie den Cube definieren. Der Cube-Assistent erstellt Dimensionen auf der Basis der Dimensionstabellen in der Datenquellensicht, die der Assistent identifiziert, oder die Sie für die Verwendung in dem Cube angeben. Der Assistent erstellt daraufhin die Datenbankdimensionen und fügt sie dem neuen Cube hinzu, wodurch Cubedimensionen erstellt werden.  
  
 Wenn Sie einen Cube erstellen, können Sie dem neuen Cube zudem jede beliebige Dimension hinzufügen, die bereits in der Datenbank vorhanden ist. Diese wurde zuvor möglicherweise schon für einen anderen Cube oder vom Dimensions-Assistenten definiert. Nachdem eine Datenbankdimension definiert wurde, können Sie sie im Dimensions-Designer ändern und konfigurieren. Sie können auch mithilfe des Cube-Designers begrenzte benutzerdefinierte Einstellungen an der Cubedimension vornehmen.  
  
> [!NOTE]  
>  Mithilfe von XMLA oder Analysis Management Objects (AMO) können Sie Dimensionen, Attribute und Hierarchien auch programmgesteuert entwerfen und konfigurieren. Weitere Informationen finden Sie unter [Analysis Services Scripting Language &#40;ASSL&#41; Verweis](../scripting/analysis-services-scripting-language-assl-for-xmla.md) und [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In der folgenden Tabelle werden die Themen in diesem Abschnitt beschrieben.  
  
 [Definieren von Datenbankdimensionen](define-database-dimensions.md)  
 Beschreibt das Ändern und Konfigurieren einer Datenbankdimension mithilfe des Dimensions-Designers.  
  
 [Dimensionsattributeigenschaften-Verweis](dimension-attribute-properties-reference.md)  
 Beschreibt das Definieren, Ändern und Konfigurieren eines Datenbankdimensionsattributs mithilfe des Dimensions-Designers.  
  
 [Definieren von Attributbeziehungen](attribute-relationships-define.md)  
 Beschreibt das Definieren, Ändern und Konfigurieren einer Attributbeziehung mithilfe des Dimensions-Designers.  
  
 [Erstellen von benutzerdefinierten Hierarchien](user-defined-hierarchies-create.md)  
 Beschreibt das Definieren, Ändern und Konfigurieren einer aus Dimensionsattributen bestehenden benutzerdefinierten Hierarchie mithilfe des Dimensions-Designers.  
  
 [Verwenden des Business Intelligence-Assistenten zum Erweitern von Dimensionen](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 Beschreibt das Verbessern einer Datenbankdimension mithilfe des Business Intelligence-Assistenten.  
  
## <a name="see-also"></a>Siehe auch  
 [Cubes in mehrdimensionalen Modellen](cubes-in-multidimensional-models.md)  
  
  
