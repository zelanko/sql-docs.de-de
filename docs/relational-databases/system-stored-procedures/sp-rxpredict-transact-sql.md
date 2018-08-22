---
title: Sp_rxPredict | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/20/2018
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
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8f46403afef0e2f6cf967561a8fd24ec6409fe93
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434860"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Generiert einen vorhergesagten Wert für eine angegebene Eingabe, die basierend auf ein Machine learning-Modell in einem binären Format in einer SQL Server-Datenbank gespeichert.

Stellt die Bewertung auf R und Python Machine Learning-Modelle in nahezu in Echtzeit. `sp_rxPredict` ist eine gespeicherte Prozedur bereitgestellt, die als Wrapper für die `rxPredict` R-Funktion im [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) und [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package), und die [Rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) Python-Funktion in [Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und [Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Es ist in C++ geschrieben und ist speziell für die Bewertung der Vorgänge optimiert wird.

**Dieser Artikel gilt für**:  
- SQL Server 2017  
- SQL Server 2016 R Services mit [aktualisiert R-Komponenten](https://docs.microsoft.com/sql/advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server)

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
 
- SQL Server 2017 Machine Learning Services (einschließlich R Server 9.2)  
- SQL Server 2017-Machine-Learning-Server (eigenständig) 
- SQL Server R Services 2016 ein Upgrade der R-Services-Instanz mit R Server 9.1.0 oder höher  

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

  Weitere Informationen zu den entsprechenden SQL-Datentypen, finden Sie unter [SQL-CLR-Typzuordnung](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oder [Zuordnen von CLR-Parameterdaten](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

