---
title: sp_rxPredict | Microsoft-Dokumentation
ms.date: 03/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning-services
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
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: b3f6ee7c1f0b1dc1ccbcd4db260621dc5bda3168
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750462"
---
# <a name="sp_rxpredict"></a>sp_rxPredict  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly.md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Generiert einen vorhergesagten Wert für eine angegebene Eingabe, bestehend aus einem Machine Learning-Modell, das in einem binären Format in einer SQL Server-Datenbank gespeichert ist.

Bietet eine Bewertung für R-und python Machine Learning-Modelle nahezu in Echtzeit. `sp_rxPredict`ist eine gespeicherte Prozedur `rxPredict` , die in [revoscaler](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) und [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)als Wrapper für die R-Funktion bereitgestellt wird, und die [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) python-Funktion in [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Sie wird in C++ geschrieben und ist speziell für Bewertungs Vorgänge optimiert.

Obwohl das Modell mit R oder python erstellt werden muss, kann es nach der Serialisierung und Speicherung in einem binären Format auf einer Instanz der Datenbank-Engine auch dann von dieser Datenbank-Engine-Instanz genutzt werden, wenn die R-oder python-Integration nicht installiert ist. Weitere Informationen finden Sie unter [Echtzeitbewertung mit sp_rxPredict](https://docs.microsoft.com/sql/machine-learning/real-time-scoring).

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

Es wird eine Score-Spalte sowie alle Pass-Through-Spalten aus der Eingabedaten Quelle zurückgegeben.
Weitere Bewertungs Spalten (z. b. das Konfidenzintervall) können zurückgegeben werden, wenn der Algorithmus die Generierung solcher Werte unterstützt.

## <a name="remarks"></a>Hinweise

Um die Verwendung der gespeicherten Prozedur zu aktivieren, muss SQLCLR für die-Instanz aktiviert werden.

> [!NOTE]
> Es gibt Sicherheits Implikationen, wenn diese Option aktiviert wird. Verwenden Sie eine alternative Implementierung, z. b. die [Transact-SQL-Vorhersage](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017) Funktion, wenn SQLCLR auf dem Server nicht aktiviert werden kann.

Der Benutzer benötigt die- `EXECUTE` Berechtigung für die Datenbank.

### <a name="supported-algorithms"></a>Unterstützte Algorithmen

Um das Modell zu erstellen und zu trainieren, verwenden Sie einen der unterstützten Algorithmen für R oder python, bereitgestellt von [SQL Server Machine Learning Services (r oder python)](https://docs.microsoft.com/sql/machine-learning/sql-server-machine-learning-services), [SQL Server 2016 R Services](https://docs.microsoft.com/sql/machine-learning/r/sql-server-r-services), [SQL Server Machine Learning Server (eigenständig) (r oder python)](https://docs.microsoft.com/sql/machine-learning/r/r-server-standalone)oder [SQL Server 2016 R Server (eigenständig)](https://docs.microsoft.com/sql/machine-learning/r/r-server-standalone?view=sql-server-2016).

#### <a name="r-revoscaler-models"></a>R: revoscaler-Modelle

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R: microsoftml-Modelle

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R: von microsoftml bereitgestellte Transformationen

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python: revoscalepy-Modelle

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

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python: von microsoftml bereitgestellte Transformationen

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>Nicht unterstützte Modelltypen

Die folgenden Modelltypen werden nicht unterstützt:

+ Modelle mit den `rxGlm` `rxNaiveBayes` Algorithmen oder in revoscaler
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

Zusätzlich zu einer gültigen SQL-Abfrage müssen die Eingabedaten in * \@ inputData* Spalten enthalten, die mit den Spalten im gespeicherten Modell kompatibel sind.

`sp_rxPredict`unterstützt nur die folgenden .net-Spaltentypen: Double, float, Short, ushort, Long, ULONG und String. Möglicherweise müssen Sie nicht unterstützte Typen in ihren Eingabedaten herausfiltern, bevor Sie Sie für die Echtzeitbewertung verwenden. 

  Informationen zu entsprechenden SQL-Typen finden Sie unter [SQL-CLR-Typzuordnung](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oder [Zuordnen von CLR-Parameterdaten](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

