---
title: Index-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Index element (DTA)
ms.assetid: 447d3964-b387-40f6-9189-71386774c29e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 59650edbef55b7bb433c6003c9ddc0f203ca7c5e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63229004"
---
# <a name="index-element-dta"></a>Index-Element (DTA)
  Enthält Informationen zu einem Index, den Sie für eine benutzerspezifische Konfiguration erstellen oder löschen möchten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Recommendation>  
  <Create>  
    <Index [Clustered | Unique | Online | IndexSizeInMB | NumberOfRows             | QUOTED_IDENTIFIER | ARITHABORT | CONCAT_NULL_YIELDS_NULL             | ANSI_NULLS | ANSI_PADDING | ANSI_WARNINGS  
            | NUMERIC_ROUNDABORT]  
     ...code removed here...  
    </Index>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|Indexattribut|Datentyp|BESCHREIBUNG|  
|---------------------|---------------|-----------------|  
|`Clustered`|`boolean`|Optional. Gibt einen gruppierten Index an. Auf "true" oder "false" festgelegt, z. B.:<br /><br /> `<Index Clustered="true">`<br /><br /> Standardmäßig ist dieses Attribut auf "false" festgelegt.|  
|`Unique`|`boolean`|Optional. Gibt einen eindeutigen Index an. Auf "true" oder "false" festgelegt, z. B.:<br /><br /> `<Index Unique="true">`<br /><br /> Standardmäßig ist dieses Attribut auf "false" festgelegt.|  
|`Online`|`boolean`|Optional. Gibt einen Index an, der Vorgänge ausführen kann, wenn der Server online ist. Dadurch ist temporärer Speicherplatz erforderlich. Auf "true" oder "false" festgelegt, z. B.:<br /><br /> `<Index Online="true">`<br /><br /> Standardmäßig ist dieses Attribut auf "false" festgelegt.<br /><br /> Weitere Informationen finden Sie unter [Ausführen von Onlineindexvorgängen](../../relational-databases/indexes/perform-index-operations-online.md) .|  
|`IndexSizeInMB`|`double`|Optional. Gibt die maximale Indexgröße in Megabyte an, z. B.:<br /><br /> `<Index IndexSizeInMB="873.75">`<br /><br /> Keine Standardeinstellung.|  
|`NumberOfRows`|`integer`|Optional. Simuliert unterschiedliche Indexgrößen zur effektiven Simulation unterschiedlicher Tabellengrößen, z. B.:<br /><br /> `<Index NumberOfRows="3000">`<br /><br /> Keine Standardeinstellung.|  
|`QUOTED_IDENTIFIER`|`boolean`|Optional. Bewirkt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dass die ISO-Regeln für Anführungszeichen befolgt, die Bezeichner und Literalzeichenfolgen begrenzen. Dieses Attribut muss aktiviert sein, wenn der Index für eine berechnete Spalte oder eine Sicht gilt. So wird dieses Attribut beispielsweise durch die folgende Syntax aktiviert:<br /><br /> `<Index QUOTED_IDENTIFIER [...]>`<br /><br /> Standardmäßig ist dieses Attribut deaktiviert.<br /><br /> Weitere Informationen finden Sie unter [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).|  
|`ARITHABORT`|`boolean`|Optional. Bewirkt die Beendigung einer Abfrage, wenn beim Ausführen der Abfrage ein Überlauffehler oder ein Fehler aufgrund einer Division durch 0 auftritt. Dieses Attribut muss aktiviert sein, wenn der Index für eine berechnete Spalte oder eine Sicht gilt. So wird dieses Attribut beispielsweise durch die folgende Syntax aktiviert:<br /><br /> `<Index ARITHABORT [...]>`<br /><br /> Standardmäßig ist dieses Attribut deaktiviert.<br /><br /> Weitere Informationen finden Sie unter [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).|  
|`CONCAT_NULL_YIELDS_`<br /><br /> `NULL`|`boolean`|Optional. Steuert die Behandlung von Verkettungsergebnissen als NULL-Werte oder als leere Zeichenfolgenwerte. Dieses Attribut muss aktiviert sein, wenn der Index für eine berechnete Spalte oder eine Sicht gilt. So wird dieses Attribut beispielsweise durch die folgende Syntax aktiviert:<br /><br /> `<Index CONCAT_NULL_YIELDS_NULL [...]>`<br /><br /> Standardmäßig ist dieses Attribut deaktiviert.<br /><br /> Weitere Informationen finden Sie unter [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).|  
|`ANSI_NULLS`|`boolean`|Optional. Gibt an, dass sich die Vergleichsoperatoren "gleich" (=) und "ungleich" (<>) bei Verwendung mit NULL-Werten ISO-konform verhalten müssen. Dieses Attribut muss aktiviert sein, wenn der Index für eine berechnete Spalte oder eine Sicht gilt. So wird dieses Attribut beispielsweise durch die folgende Syntax aktiviert:<br /><br /> `<Index ANSI_NULLS [...]>`<br /><br /> Standardmäßig ist dieses Attribut deaktiviert.<br /><br /> Weitere Informationen finden Sie unter [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)|  
|`ANSI_PADDING`|`boolean`|Optional. Steuert das Speichern von Werten in der Spalte, wenn die Werte kürzer als die definierte Spaltengröße sind. Dieses Attribut muss aktiviert sein, wenn der Index für eine berechnete Spalte oder eine Sicht gilt. So wird dieses Attribut beispielsweise durch die folgende Syntax aktiviert:<br /><br /> `<Index ANSI_PADDING [...]>`<br /><br /> Standardmäßig ist dieses Attribut deaktiviert.<br /><br /> Weitere Informationen finden Sie unter [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).|  
|`ANSI_WARNINGS`|`boolean`|Optional. Gibt das ISO-Standardverhalten für verschiedene Fehlerbedingungen an. Dieses Attribut muss aktiviert sein, wenn der Index für eine berechnete Spalte oder eine Sicht gilt. So wird dieses Attribut beispielsweise durch die folgende Syntax aktiviert:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> Standardmäßig ist dieses Attribut deaktiviert.<br /><br /> Weitere Informationen finden Sie unter [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql).|  
|`NUMERIC_ROUNDABORT`|`boolean`|Optional. Gibt an, welche Fehlerberichtsstufe generiert wird, wenn beim Runden in einem Ausdruck Genauigkeitsverluste entstehen. Dieses Attribut muss deaktiviert sein, wenn der Index für eine berechnete Spalte oder eine Sicht gilt.<br /><br /> Dieses Attribut wird durch die folgende Syntax aktiviert:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> Standardmäßig ist dieses Attribut deaktiviert.<br /><br /> Weitere Informationen finden Sie unter [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich pro `Create`- oder `Drop`-Element, wenn keine andere physische Entwurfsstruktur anhand des `Statistics`- oder `Heap`-Elements angegeben ist.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Create Element &#40;DTA&#41;](create-element-dta.md)<br /><br /> `Drop`Gewisses. Weitere Informationen finden Sie im XML-Schema des Datenbankoptimierungsratgebers.|  
|**Untergeordnete Elemente**|[Name-Element für Index &#40;DTA&#41;](name-element-for-index-dta.md)<br /><br /> [Column-Element für Index &#40;DTA&#41;](column-element-for-index-dta.md)<br /><br /> `PartitionScheme`Gewisses. Weitere Informationen finden Sie im XML-Schema des Datenbankoptimierungsratgebers.<br /><br /> `PartitionColumn`Gewisses. Weitere Informationen finden Sie im XML-Schema des Datenbankoptimierungsratgebers.<br /><br /> [FILEGROUP-Element für Index &#40;DTA&#41;](filegroup-element-for-index-dta.md)<br /><br /> `NumberOfReferences`Gewisses. Weitere Informationen finden Sie im XML-Schema des Datenbankoptimierungsratgebers.<br /><br /> `PercentUsage`Gewisses. Weitere Informationen finden Sie im XML-Schema des Datenbankoptimierungsratgebers.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
