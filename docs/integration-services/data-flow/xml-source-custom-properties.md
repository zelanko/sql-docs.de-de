---
title: Benutzerdefinierte Eigenschaften der XML-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 32afa6d65929fda676f7eebb1bc78ab1d05cd789
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074018"
---
# <a name="xml-source-custom-properties"></a>Benutzerdefinierte Eigenschaften der XML-Quelle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die XML-Quelle verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der XML-Quelle beschrieben. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|und Beschreibung|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|Der zum Zugreifen auf die XML-Daten verwendete Modus.|  
|UseInlineSchema|Boolean|Ein Wert, der angibt, ob eine Inlineschemadefinition innerhalb der XML-Quelle verwendet werden soll. Der Standardwert dieser Eigenschaft ist **False**.|  
|XMLData|Zeichenfolge|Die Datei oder die Variablen, aus der bzw. denen die XML-Daten abgerufen werden sollen.<br /><br /> Der Wert dieser Eigenschaft kann mithilfe eines Eigenschaftsausdrucks angegeben werden.|  
|XMLSchemaDefinition|Zeichenfolge|Der Pfad und der Dateiname der Schemadefinitionsdatei (.xsd).<br /><br /> Der Wert dieser Eigenschaft kann mithilfe eines Eigenschaftsausdrucks angegeben werden.|  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften der Ausgabe der XML-Quelle. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|und Beschreibung|  
|-------------------|---------------|-----------------|  
|RowsetID|Zeichenfolge|Ein Wert, der das der Ausgabe zugeordnete Rowset identifiziert.|  
  
 Die Ausgabespalten der XML-Quelle verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
