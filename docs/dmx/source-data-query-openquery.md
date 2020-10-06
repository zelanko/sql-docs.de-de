---
description: '&lt;Quelldaten Abfrage &gt; -OPENQUERY'
title: OPENQUERY (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 62d638b6b6028ffa861460e07f2283cb7380e129
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726106"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;Quelldaten Abfrage &gt; -OPENQUERY
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Ersetzt die Quelldatenabfrage durch eine Abfrage an eine vorhandene Datenquelle. Die Anweisungen INSERT, SELECT FROM PREDICTION JOIN und SELECT FROM NATURAL PREDICTION JOIN unterstützen **OPENQUERY**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Argumente  
 *benannte Datenquelle*  
 Eine Datenquelle, die in der Datenbank vorhanden ist [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 *Abfrage Syntax*  
 Eine Abfragesyntax, die ein Rowset zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 **OPENQUERY** bietet eine sicherere Möglichkeit für das Zugreifen auf externe Daten, weil es Datenquellenberechtigungen unterstützt. Da die Verbindungszeichenfolge direkt in der Datenquelle gespeichert wird, können Administratoren die Eigenschaften der Datenquelle dazu verwenden, den Zugriff auf die Daten zu verwalten. Weitere Informationen zu Datenquellen finden Sie [unter Unterstützte Datenquellen &#40;SSAS-Multidimensional&#41;](/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional).  
  
 Durch Abfragen des **MDSCHEMA_INPUT_DATASOURCES** -Schemarowsets können Sie eine Liste der Datenquellen abrufen, die auf einem Server verfügbar sind. Weitere Informationen zum Verwenden von **MDSCHEMA_INPUT_DATASOURCES**finden Sie unter [MDSCHEMA_INPUT_DATASOURCES Rowsets](/previous-versions/sql/sql-server-2012/ms126243(v=sql.110)).  
  
 Sie können auch eine Liste mit Datenquellen in der aktuellen Analysis Services-Datenbank zurückgeben, indem Sie folgende DMX-Abfrage verwenden:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die bereits in der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank definierte MyDS-Datenquelle verwendet, um eine Verbindung mit der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank herzustellen und die Sicht **vTargetMail** abzufragen.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#60;Quelldaten Abfrage&#62;](../dmx/source-data-query.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
