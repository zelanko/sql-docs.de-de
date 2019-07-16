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
ms.openlocfilehash: 1079fbb02026e2043767082d5def7fac37322ef2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077730"
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
 Eine Datenquelle, die in der Datenbank von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] vorhanden ist.  
  
 *Abfragesyntax*  
 Eine Abfragesyntax, die ein Rowset zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 **OPENQUERY** bietet eine sicherere Möglichkeit für das Zugreifen auf externe Daten, weil es Datenquellenberechtigungen unterstützt. Da die Verbindungszeichenfolge direkt in der Datenquelle gespeichert wird, können Administratoren die Eigenschaften der Datenquelle dazu verwenden, den Zugriff auf die Daten zu verwalten. Weitere Informationen zu Datenquellen finden Sie unter [unterstützte Datenquellen &#40;SSAS – mehrdimensional&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 Durch Abfragen des **MDSCHEMA_INPUT_DATASOURCES** -Schemarowsets können Sie eine Liste der Datenquellen abrufen, die auf einem Server verfügbar sind. Weitere Informationen zur Verwendung von **MDSCHEMA_INPUT_DATASOURCES**, finden Sie unter [MDSCHEMA_INPUT_DATASOURCES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset).  
  
 Sie können auch eine Liste mit Datenquellen in der aktuellen Analysis Services-Datenbank zurückgeben, indem Sie folgende DMX-Abfrage verwenden:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die bereits in der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank definierte MyDS-Datenquelle verwendet, um eine Verbindung mit der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank herzustellen und die Sicht **vTargetMail** abzufragen.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Siehe auch  
 [&#60;quelldatenabfrage&#62;](../dmx/source-data-query.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
