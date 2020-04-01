---
title: sp_rxPredict | Microsoft Docs
ms.date: 03/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>= sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 86b9cd8a9327eb8afaf9945ca09629362062011f
ms.sourcegitcommit: 2426a5e1abf6ecf35b1e0c062dc1e1225494cbb0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80517452"
---
# <a name="sp_rxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Generiert einen vorhergesagten Wert für eine bestimmte Eingabe, die aus einem Machine Learning-Modell besteht, das in einem binären Format in einer SQL Server-Datenbank gespeichert ist.

Bietet die Bewertung von R- und Python-Machine Learning-Modellen in nahezu Echtzeit. `sp_rxPredict`ist eine gespeicherte Prozedur, die `rxPredict` als Wrapper für die [R-Funktion in RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) und [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)und die [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) Python-Funktion in [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)bereitgestellt wird. Es ist in C++ geschrieben und speziell für Scoring-Operationen optimiert.

Obwohl das Modell mit R oder Python erstellt werden muss, kann es, sobald es serialisiert und in einem binären Format auf einer Zieldatenbankmodulinstanz gespeichert ist, von dieser Datenbankmodulinstanz verbraucht werden, selbst wenn die R- oder Python-Integration nicht installiert ist. Weitere Informationen finden Sie unter [Echtzeitbewertung mit sp_rxPredict](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="syntax"></a>Syntax

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Argumente

**Modell**

Ein vortrainiertes Modell in einem unterstützten Format. 

**input**

Eine gültige SQL-Abfrage

### <a name="return-values"></a>Rückgabewerte

Es wird eine Score-Spalte sowie alle Pass-Through-Spalten aus der Eingabedatenquelle zurückgegeben.
Zusätzliche Score-Spalten, z. B. Konfidenzintervall, können zurückgegeben werden, wenn der Algorithmus die Generierung solcher Werte unterstützt.

## <a name="remarks"></a>Bemerkungen

Um die Verwendung der gespeicherten Prozedur zu aktivieren, muss SQLCLR auf der Instance aktiviert sein.

> [!NOTE]
> Es gibt Sicherheitsauswirkungen, um diese Option zu enabing. Verwenden Sie eine alternative Implementierung, z. B. die [Funktion Transact-SQL PREDICT,](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017) wenn SQLCLR auf Ihrem Server nicht aktiviert werden kann.

Der Benutzer `EXECUTE` benötigt die Berechtigung für die Datenbank.

### <a name="supported-algorithms"></a>Unterstützte Algorithmen

Verwenden Sie zum Erstellen und Trainieren eines Modells einen der unterstützten Algorithmen für R oder Python, der von [SQL Server 2Machine Learning Services (R oder Python),](https://docs.microsoft.com/sql/advanced-analytics/what-is-sql-server-machine-learning) [SQL Server 2016 R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services), SQL Server Machine Learning Server [(Standalone) (R oder Python)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone)oder [SQL Server 2016 R Server (Standalone)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2016)bereitgestellt wird.

#### <a name="r-revoscaler-models"></a>R: RevoScaleR-Modelle

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R: MicrosoftML-Modelle

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R: Von MicrosoftML bereitgestellte Transformationen

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python: revoscalepy Modelle

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)


#### <a name="python-microsoftml-models"></a>Python: microsoftml-Modelle

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python: Transformationen von microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>Nicht unterstützte Modelltypen

Die folgenden Modelltypen werden nicht unterstützt:

+ Modelle, `rxGlm` die `rxNaiveBayes` die oder Algorithmen in RevoScaleR verwenden
+ PMML-Modelle in R
+ Modelle, die mit anderen Bibliotheken von Drittanbietern erstellt wurden 

## <a name="examples"></a>Beispiele

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Die Eingabedaten in * \@inputData* müssen nicht nur eine gültige SQL-Abfrage sein, sondern auch Spalten enthalten, die mit den Spalten im gespeicherten Modell kompatibel sind.

`sp_rxPredict`unterstützt nur die folgenden .NET-Spaltentypen: double, float, short, ushort, long, ulong und string. Möglicherweise müssen Sie nicht unterstützte Typen in Ihren Eingabedaten herausfiltern, bevor Sie sie für die Echtzeitbewertung verwenden. 

  Informationen zu entsprechenden SQL-Typen finden Sie unter [SQL-CLR-Typzuordnung](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oder [Zuordnen von CLR-Parameterdaten](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

