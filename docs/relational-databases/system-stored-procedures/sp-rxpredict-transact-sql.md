---
title: Sp_rxPredict | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: ede8232f36f42cc2b9758bdee8f50457ebd58dfe
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036048"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Generiert einen vorhergesagten Wert auf Grundlage eines gespeicherten Modells.

Stellt die Bewertung auf Machine Learning-Modelle in nahezu in Echtzeit. `sp_rxPredict` ist eine gespeicherte Prozedur bereitgestellt, die als Wrapper für die `rxPredict` -Funktion in [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) und [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package). Es ist in C++ geschrieben und ist speziell für die Bewertung der Vorgänge optimiert wird. Es unterstützt sowohl R oder Python-machine Learning-Modellen.

**Dieses Thema gilt für**:  
- SQL Server 2017  
- SQL Server 2016 R Services mit Upgrade auf Microsoft R Server  

## <a name="syntax"></a>Syntax

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Argumente

**model**

Ein vortrainiertes Modell in einem unterstützten Format. 

**input**

Eine gültige SQL-Abfrage

### <a name="return-values"></a>Rückgabewerte

Eine Bewertungsspalte wird zurückgegeben, sowie alle Pass-Through-Spalten aus der Eingabedatenquelle.
Zusätzliche Spalten, z. B. Konfidenzintervall zu bewerten, die zurückgegeben werden kann, wenn der Algorithmus die Generierung von solche Werte unterstützt.

## <a name="remarks"></a>Hinweise

Um die Verwendung der gespeicherten Prozedur zu aktivieren, muss die SQLCLR für die Instanz aktiviert sein.

> [!NOTE]
> Beachten Sie die Sicherheitsrisiken, bevor Sie diese Option aktivieren.

Die benutzeranforderungen `EXECUTE` Berechtigung für die Datenbank.

### <a name="supported-platforms"></a>Unterstützte Plattformen

Erfordert eine der folgenden Editionen:  
- SQL Server 2017 Machine Learning Services (einschließlich Microsoft R Server 9.1.0)  
- Microsoft Machine Learning-Server  
- SQL Server R Services 2016 ein Upgrade der R-Services-Instanz für Microsoft R Server 9.1.0 oder höher  

### <a name="supported-algorithms"></a>Unterstützte Algorithmen

Eine Liste der unterstützten Algorithmen, finden Sie unter [echtzeitbewertung](../../advanced-analytics/real-time-scoring.md).

Sind die folgenden Modelltypen **nicht** unterstützt:  
- Modelle, die mit anderen, nicht unterstützte Typen von R-Transformationen  
- Modelle mit den `rxGlm` oder `rxNaiveBayes` Algorithmen in RevoScaleR  
- PMML-Modelle  
- Mit anderen R-Bibliotheken über CRAN oder andere Repositorys erstellte Modelle  
- Modelle, die eine andere Art von R-Transformation, als die hier aufgeführten enthält.  

## <a name="examples"></a>Beispiele

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Abgesehen davon, dass eine gültige SQL-Abfrage, die Eingabedaten in *@inputData* müssen Sie die Spalten, die kompatibel mit den Spalten in das gespeicherte Modell einschließen.

`sp_rxPredict` unterstützt nur die folgenden .NET Spaltentypen: double, Float, Short, Ushort, long, Ulong und Zeichenfolge. Sie müssen möglicherweise nicht unterstützten Typen in Ihre Daten herausfiltern, bevor Sie ihn für die echtzeitbewertung verwenden. 

  Weitere Informationen zu den entsprechenden SQL-Datentypen, finden Sie unter [SQL-CLR-Typzuordnung](https://msdn.microsoft.com/library/bb386947.aspx) oder [Zuordnen von CLR-Parameterdaten](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

