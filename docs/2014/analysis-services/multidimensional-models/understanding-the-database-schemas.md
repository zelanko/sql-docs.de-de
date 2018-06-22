---
title: Grundlegendes zu Datenbankschemas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Schema Generation Wizard, database schema
- database schema [Analysis Services]
- relational schema [Analysis Services], database schema
- subject area schema options [Analysis Services]
- staging area schema options [Analysis Services]
- denormalized schemas
ms.assetid: 51e411f9-ee3f-4b92-9833-c2bce8c6b752
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf611a2ae8e2c2275fc59d3abc124d8fa202d388
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059249"
---
# <a name="understanding-the-database-schemas"></a>Grundlegendes zu Datenbankschemas
  Der Schemagenerierungs-Assistent generiert ein nicht normalisiertes relationales Schema für die Datenbank des Themenbereichs auf Basis der Dimensionen und Measuregruppen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Der Assistent generiert für jede Dimension eine relationale Tabelle zum Speichern von Dimensionsdaten, die als Dimensionstabelle bezeichnet wird, und für jede Measuregruppe eine relationale Tabelle zum Speichern von Faktendaten, die als Faktentabelle bezeichnet wird. Beim Generieren dieser relationalen Tabellen ignoriert der Assistent verknüpfte Dimensionen, verknüpfte Measuregruppen und Serverzeitdimensionen.  
  
## <a name="validation"></a>Überprüfung  
 Bevor das zugrunde liegende relationale Schema generiert wird, überprüft der Schemagenerierungs-Assistent die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Cubes und -Dimensionen. Wenn der Assistent einen Fehler feststellt, wird der Assistent beendet, und die Fehler werden an das Fenster Aufgabenliste in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]berichtet. Im Folgenden finden Sie Beispiele für Fehler, die das Generieren verhindern:  
  
-   Dimensionen, die mehr als ein Schlüsselattribut enthalten.  
  
-   Übergeordnete Attribute, deren Datentypen sich von denen der Schlüsselattribute unterscheiden.  
  
-   Measuregruppen, in denen keine Measures enthalten sind.  
  
-   Degenerierte Dimensionen oder Measures, die fehlerhaft konfiguriert sind.  
  
-   Ersatzschlüssel, die fehlerhaft konfiguriert sind, wie z. B. mehrere Attribute, die den `ScdOriginalID`-Attributtyp verwenden, oder ein Attribut mit dem `ScdOriginalID`-Attributtyp, das nicht an eine Spalte des integer-Datentyps gebunden ist.  
  
## <a name="dimension-tables"></a>Dimensionstabellen  
 Der Schemagenerierungs-Assistent generiert für jede Dimension eine Dimensionstabelle, die in die Datenbank des Themenbereichs eingeschlossen werden soll. Die Struktur der Dimensionstabelle hängt von den Optionen ab, die Sie beim Entwerfen der Dimension, auf der die Dimensionstabelle basiert, ausgewählt haben.  
  
 Spalte  
 Der Assistent generiert eine Spalte für die Bindungen, die verknüpft sind, die jedem Attribut in der Dimension, auf denen die Dimensionstabelle, z. B. die Bindungen für basiert, die `KeyColumns`, `NameColumn`, `ValueColumn`, `CustomRollupColumn`, `CustomRollupPropertiesColumn`, und `UnaryOperatorColumn`Eigenschaften jedes Attributs.  
  
 Beziehungen  
 Der Assistent generiert eine Beziehung zwischen der Spalte jedes übergeordneten Attributs und dem Primärschlüssel der Dimensionstabelle.  
  
 Bei Bedarf generiert der Assistent ebenfalls eine Beziehung zum Primärschlüssel in jeder zusätzlichen Dimensionstabelle, die im Cube als referenzierte Dimension definiert wird.  
  
 Einschränkungen  
 Der Assistent generiert standardmäßig eine PRIMARY KEY-Einschränkung für jede Dimensionstabelle auf Basis des Schlüsselattributs der Dimension. Beim Generieren der PRIMARY KEY-Einschränkung wird standardmäßig eine separate Namensspalte generiert. Ein logischer Primärschlüssel wird in der Datenquellensicht erstellt, auch wenn Sie den Primärschlüssel in der Datenbank nicht erstellen möchten.  
  
> [!NOTE]  
>  Ein Fehler tritt auf, wenn mehr als ein Schlüsselattribut in der Dimension, auf der die Dimensionstabelle basiert, angegeben wird.  
  
 Translations  
 Der Assistent generiert eine separate Tabelle für die übersetzten Werte eines beliebigen Attributs, das eine Übersetzungsspalte erfordert. Des Weiteren erstellt der Assistent eine separate Spalte für jede erforderliche Sprache.  
  
## <a name="fact-tables"></a>Faktentabellen  
 Der Schemagenerierungs-Assistent generiert für jede Measuregruppe eines Cubes eine Faktentabelle, die in die Datenbank des Themenbereichs eingeschlossen werden soll. Die Struktur der Faktentabelle hängt von den Optionen ab, die Sie beim Entwerfen der Measuregruppe, auf der die Faktentabelle basiert, ausgewählt haben. Des Weiteren hängt die Struktur von den zwischen der Measuregruppe und den eingeschlossenen Dimensionen erstellten Beziehungen ab.  
  
 Spalte  
 Der Assistent generiert eine Spalte für jedes Measure, mit Ausnahme von Measures, mit denen die `Count` Aggregationsfunktion. Für diese Art von Measures ist in der Faktentabelle keine entsprechende Spalte erforderlich.  
  
 Der Assistent generiert ebenfalls eine Spalte pro Granularitätsattributspalte für jede reguläre Dimensionsbeziehung der Measuregruppe. Bei Bedarf generiert der Assistent mindestens eine Spalte für die Bindungen, die jedem Attribut einer Dimension mit einer Faktendimensionsbeziehung zur Measuregruppe, auf der die Tabelle basiert, zugeordnet sind.  
  
 Beziehungen  
 Der Assistent generiert eine Beziehung für jede reguläre Dimensionsbeziehung der Faktentabelle zum Granularitätsattribut der Dimensionstabelle. Wenn die Granularität auf dem Schlüsselattribut der Dimensionstabelle basiert, wird die Beziehung in der Datenbank und in der Datenquellensicht erstellt. Wenn die Granularität auf einem anderen Attribut basiert, wird die Beziehung nur in der Datenquellensicht erstellt.  
  
 Wenn Sie im Assistenten die Indizes generieren, wird ein nicht gruppierter Index für jede dieser Beziehungsspalten generiert.  
  
 Einschränkungen  
 Primärschlüssel werden nicht in Faktentabellen generiert.  
  
 Wenn Sie die referenzielle Integrität erzwingen möchten, werden bei Bedarf Einschränkungen für die referenzielle Integrität zwischen Dimensionstabellen und Faktentabellen generiert.  
  
 Translations  
 Der Assistent generiert eine separate Tabelle für die übersetzten Werte beliebiger Eigenschaften der Measuregruppe, die eine Übersetzungsspalte erfordert. Des Weiteren erstellt der Assistent eine separate Spalte für jede erforderliche Sprache.  
  
## <a name="data-type-conversion-and-default-lengths"></a>Datentypkonvertierung und Standardlängen  
 Im Schemagenerierungs-Assistent werden in allen Fällen Datentypen ignoriert. Ausgeschlossen sind hiervon Spalten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar`-Datentyps. Die `wchar` -Datengröße wird direkt an die `nvarchar` -Datentyp. Wenn die angegebene Länge einer Spalte, die die `wchar`-Größe verwendet, 4.000 Byte überschreitet, generiert der Schemagenerierungs-Assistent einen Fehler.  
  
 Wenn für ein Datenelement, wie z. B. die Bindung eines Attributs, keine Länge angegeben ist, wird für die Spalte die in der folgenden Tabelle aufgelistete Standardlänge verwendet.  
  
|Datenelement|Standardlänge (Byte)|  
|---------------|------------------------------|  
|KeyColumn|50|  
|NameColumn|50|  
|CustomRollupColumn|3000|  
|CustomRollupPropertiesColumn|500|  
|UnaryOperatorColumn|1|  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zur inkrementellen Generierung](understanding-incremental-generation.md)   
 [Verwalten von Änderungen an Datenquellensichten und Datenquellen](manage-changes-to-data-source-views-and-data-sources.md)  
  
  