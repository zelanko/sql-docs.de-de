---
title: Column-Element für Index (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.openlocfilehash: 008cba36af33c465c3a126dc3e101b8ebca28e36
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307885"
---
# <a name="column-element-for-index-dta"></a>Column-Element für Index (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Gibt die Spalten an, für die der Index für eine benutzerspezifische Konfiguration erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
 **Type**: Optional. Gibt den Indexspaltentyp an. Mit einem **string** -Datentyp können Sie dieses Attribut mit einem der folgenden zulässigen Werte angeben:  
  
-   **KeyColumn**  
  
     Gibt an, dass durch einen Indexschlüssel auf die Spalte verwiesen wird. Verwenden Sie die folgende Syntax, um dieses Attribut festzulegen:  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Weitere Informationen zu Schlüsselspalten finden Sie unter [Beschreibung von gruppierten und nicht gruppierten Indizes](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Gibt an, dass die Spalte eine eingeschlossene Spalte ist (statt einer Schlüsselspalte). Verwenden Sie die folgende Syntax, um dieses Attribut festzulegen:  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Weitere Informationen zu eingeschlossenen Spalten finden Sie unter [Erstellen von Indizes mit eingeschlossenen Spalten](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: Optional. Gibt die Sortierreihenfolge der Spalte an. Mit einem **string** -Datentyp können Sie die Sortierreihenfolge wie folgt als **Aufsteigend** oder **Absteigend** angeben:  
  
```  
<Column SortOrder="Ascending">  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Angabe von bis zu 1024 Spalten für das **Index** -Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Index-Element &#40;DTA&#41;](../../tools/dta/index-element-dta.md)|  
|**Untergeordnete Elemente**|[Name-Element für Spalte &#40;DTA&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
