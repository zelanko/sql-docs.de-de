---
title: OPENQUERY (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f7b4744c3f521ed4c51e461f2b01a748b9b6496
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989758"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;quelldatenabfrage&gt; -OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ersetzt die Quelldatenabfrage durch eine Abfrage an eine vorhandene Datenquelle. Die Anweisungen INSERT, SELECT FROM PREDICTION JOIN und SELECT FROM NATURAL PREDICTION JOIN unterstützen **OPENQUERY**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Argumente  
 *benannte datasource*  
 Eine Datenquelle auf die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank.  
  
 *Abfragesyntax*  
 Eine Abfragesyntax, die ein Rowset zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 **OPENQUERY** bietet eine sicherere Möglichkeit für das Zugreifen auf externe Daten, weil es Datenquellenberechtigungen unterstützt. Da die Verbindungszeichenfolge direkt in der Datenquelle gespeichert wird, können Administratoren die Eigenschaften der Datenquelle dazu verwenden, den Zugriff auf die Daten zu verwalten. Weitere Informationen zu Datenquellen finden Sie unter [unterstützte Datenquellen &#40;SSAS – mehrdimensional&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 Durch Abfragen des **MDSCHEMA_INPUT_DATASOURCES** -Schemarowsets können Sie eine Liste der Datenquellen abrufen, die auf einem Server verfügbar sind. Weitere Informationen zur Verwendung von **MDSCHEMA_INPUT_DATASOURCES**, finden Sie unter [MDSCHEMA_INPUT_DATASOURCES-Rowset](../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md).  
  
 Sie können auch eine Liste mit Datenquellen in der aktuellen Analysis Services-Datenbank zurückgeben, indem Sie folgende DMX-Abfrage verwenden:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die MyDS-Datenquelle, die bereits in definiert die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank, um eine Verbindung zum Erstellen der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenbank- und der **vTargetMail** anzeigen.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Siehe auch  
 [&#60;quelldatenabfrage&#62;](../dmx/source-data-query.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
