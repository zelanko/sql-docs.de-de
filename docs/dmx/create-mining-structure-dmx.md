---
description: CREATE MINING STRUCTURE (DMX)
title: Mining Struktur erstellen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 06f013ccb5c33dfbaba2fe0a0e102a448c17e036
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414026"
---
# <a name="create-mining-structure-dmx"></a>CREATE MINING STRUCTURE (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Erstellt in einer Datenbank eine neue Miningstruktur und definiert optional Trainings- und Testpartitionen. Nachdem Sie die Mining Struktur erstellt haben, können Sie die [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md) -Anweisung verwenden, um der Mining Strukturmodelle hinzuzufügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE [SESSION] MINING STRUCTURE <structure>  
(  
    [(<column definition list>)]  
)  
[WITH HOLDOUT (<holdout-specifier> [OR <holdout-specifier>])]  
[REPEATABLE(<holdout seed>)]  
<holdout-specifier>::=  <holdout-maxpercent> PERCENT | <holdout-maxcases> CASES  
```  
  
## <a name="arguments"></a>Argumente  
 *Werks*  
 Ein eindeutiger Name für die Struktur.  
  
 *Spalten Definitionsliste*  
 Eine durch Trennzeichen getrennte Liste mit Spaltendefinitionen.  
  
 *zurück gehaltene Daten (maxprozent)*  
 Eine ganze Zahl zwischen 1 und 100, die den Prozentsatz der für Tests vorgesehenen Daten angibt.  
  
 *zurück gehaltene Daten (MaxCases)*  
 Eine ganze Zahl, die die maximale Anzahl von Fällen angibt, die für Tests verwendet werden sollen.  
  
 Wenn der für die maximale Anzahl von Fällen angegebene Wert größer ist als die Anzahl der Eingabefälle, werden alle Eingabefälle für Tests verwendet, und eine Warnung wird ausgegeben.  
  
> [!NOTE]  
>  Wenn sowohl der Prozentsatz als auch die maximale Anzahl von Fällen angegeben ist, wird der kleinere der beiden Grenzwerte verwendet.  
  
 *Ausgangs Ausgangs-Seed*  
 Eine ganze Zahl, die als Ausgangswert für das Partitionieren von Daten verwendet wird.  
  
 Wenn die Zahl auf 0 festgelegt ist, wird der Hash der Miningstruktur-ID als Ausgangswert verwendet.  
  
> [!NOTE]  
>  Sie sollten einen Ausgangswert angeben, wenn Sie sicherstellen müssen, dass eine Partition reproduziert werden kann.  
  
 Standardwert: REPEATABLE(0)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie definieren eine Miningstruktur, indem Sie eine Liste mit Spalten und optional hierarchische Beziehungen zwischen den Spalten angeben und dann wahlweise die Miningstruktur in Trainings- und Testdatasets partitionieren.  
  
 Das optionale SESSION-Schlüsselwort gibt an, dass die Struktur eine temporäre Struktur ist, die Sie nur für die Dauer der aktuellen Sitzung verwenden können. Wenn die Sitzung beendet wird, werden die Struktur und alle Modelle auf Grundlage der Struktur gelöscht. Um temporäre Mining Strukturen und-Modelle zu erstellen, müssen Sie zuerst die Daten Bank Eigenschaft AllowSessionMiningModels festlegen. Weitere Informationen finden Sie unter [Data Mining Properties](https://docs.microsoft.com/analysis-services/server-properties/data-mining-properties).  
  
## <a name="column-definition-list"></a>Spaltendefinitionsliste (Column Definition List)  
 Sie definieren eine Miningstruktur, indem Sie in der Spaltendefinitionsliste für jede Spalte folgende Informationen angeben:  
  
-   Name (obligatorisch)  
  
-   Datentyp (obligatorisch)  
  
-   Distribution  
  
-   Liste der Modellierungsflags  
  
-   Inhaltstyp (obligatorisch)  
  
-   Beziehung zu einer Attributspalte (nur obligatorisch, wenn zutreffend), angegeben durch die RELATED TO-Klausel  
  
 Verwenden Sie die folgende Syntax für die Spaltendefinitionsliste, wenn Sie eine einzelne Spalte definieren möchten:  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<column relationship>]  
```  
  
 Verwenden Sie die folgende Syntax für die Spaltendefinitionsliste, wenn Sie eine Spalte einer geschachtelten Tabelle definieren möchten:  
  
```  
<column name>    TABLE    ( <column definition list> )  
```  
  
 Eine Liste der Datentypen, Inhaltstypen, Spaltendistributionen und Modellierungsflags, mit denen Sie eine Strukturspalte definieren können, finden Sie in den folgenden Themen:  
  
-   [Datentypen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-types-data-mining)  
  
-   [Inhaltstypen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)  
  
-   [Spaltenverteilungen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining)  
  
-   [Modellierungsflags &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/modeling-flags-data-mining)  
  
 Sie können mehrere Modellierungsflagwerte für eine Spalte definieren. Für eine Spalte können jedoch nur jeweils ein Inhaltstyp und ein Datentyp gelten.  
  
### <a name="column-relationships"></a>Spaltenbeziehungen  
 Sie können jeder Spaltendefinitionsanweisung eine Klausel hinzufügen, um die Beziehung zwischen zwei Spalten zu beschreiben. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt die Verwendung der folgenden- \<column relationship> Klausel.  
  
 **verknüpft mit**  
 Gibt eine Wertehierarchie an. Das Ziel einer RELATED TO-Spalte kann eine Schlüsselspalte einer geschachtelten Tabelle, eine Spalte mit diskreten Werten in der Fallzeile oder eine andere Spalte mit einer RELATED TO-Klausel sein, wodurch eine tiefere Hierarchie gekennzeichnet ist.  
  
## <a name="holdout-parameters"></a>Zurückhaltungsparameter  
 Wenn Sie Zurückhaltungsparameter angeben, erstellen Sie eine Partition der Strukturdaten. Der Wert, den Sie für die Zurückhaltung angeben, wird für Tests reserviert. Die übrigen Daten werden zum Training verwendet. Wenn Sie mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine Miningstruktur aufbauen, wird eine Zurückhaltungspartition mit 30 Prozent Testdaten und 70 Prozent Trainingsdaten erstellt. Weitere Informationen finden Sie unter [Training and Testing Data Sets](https://docs.microsoft.com/analysis-services/data-mining/training-and-testing-data-sets).  
  
 Wenn Sie eine Miningstruktur mit Data Mining-Erweiterungen (DMX) aufbauen, müssen Sie manuell angeben, dass eine Zurückhaltungspartition erstellt werden soll.  
  
> [!NOTE]  
>  Die **ALTER MINING STRUCTURE** -Anweisung unterstützt keine zurückgehaltenen Daten.  
  
 Sie können bis zu drei Zurückhaltungsparameter angeben. Wenn Sie sowohl eine maximale Anzahl an Zurückhaltungsfällen als auch einen Zurückhaltungsprozentsatz angeben, wird ein Prozentsatz an Fällen reserviert, bis die Höchstgrenze der Fälle erreicht wird. Geben Sie den Prozentsatz der zurückgehaltenen Daten als Ganzzahl an, gefolgt vom Schlüsselwort " **Prozent** ", und geben Sie die maximale Anzahl von Fällen als Ganzzahl an, gefolgt vom Schlüsselwort " **Cases** ". Sie können die Bedingungen in beliebiger Reihenfolge kombinieren, wie in den folgenden Beispielen veranschaulicht:  
  
```  
WITH HOLDOUT (20 PERCENT)   
WITH HOLDOUT (2000 CASES)   
WITH HOLDOUT (20 PERCENT OR 2000 CASES)   
WITH HOLDOUT (2000 CASES OR 20 PERCENT)  
```  
  
 Der Zurückhaltungsausgangswert steuert den Anfangspunkt des Prozesses, mit dem Fälle nach dem Zufallsprinzip Trainings- oder Testdatasets zugewiesen werden. Sie können sicherstellen, dass die Partition wiederholt werden kann, indem Sie einen Zurückhaltungsausgangswert festlegen. Wenn dieser Wert nicht definiert ist, verwendet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] den Namen der Miningstruktur, um einen Ausgangswert zu erstellen. Wenn Sie die Struktur umbenennen, ändert sich der Ausgangswert. Der Parameter für den Zurückhaltungsausgangswert kann mit einem oder beiden anderen Zurückhaltungsparametern verwendet werden.  
  
> [!NOTE]  
>  Da die Partitionsinformationen mit den Trainingsdaten zwischengespeichert werden, müssen Sie sicherstellen, dass die **CacheMode** -Eigenschaft der Mining Struktur auf **KeepTrainingData**festgelegt ist, um zurück gehaltene Daten verwenden zu können. Dies ist die Standardeinstellung in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] für neue Miningstrukturen. Das Ändern der **CacheMode** -Eigenschaft in **ClearTrainingCases** für eine vorhandene Mining Struktur, die eine zurück Haltungs Partition enthält, wirkt sich nicht auf Mining Modelle aus, die verarbeitet wurden. Wenn jedoch <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> nicht auf **KeepTrainingData**festgelegt ist, haben die zurück Haltungs Parameter keine Auswirkungen. Dies bedeutet, dass alle Quelldaten zum Training verwendet werden und kein Testdataset verfügbar ist. Die Definition der Partition wird zusammen mit der Struktur im Cache abgelegt. Wenn Sie die Trainingsfälle aus dem Cache entfernen, entfernen Sie auch die Testdaten und die Definition des Zurückhaltungsdatasets.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird veranschaulicht, wie mithilfe von DMX eine Miningstruktur mit Zurückhaltung erstellt wird.  
  
### <a name="example-1-adding-a-structure-with-no-training-set"></a>Beispiel 1: Hinzufügen einer Struktur ohne Trainingssatz  
 Im folgenden Beispiel wird eine neue Miningstruktur namens `New Mailing` erstellt, ohne dass zugeordnete Miningmodelle erstellt werden und Zurückhaltung verwendet wird. Weitere Informationen zum Hinzufügen eines Mining Modells zur Struktur finden Sie unter [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)  
```  
  
### <a name="example-2-specifying-holdout-percentage-and-seed"></a>Beispiel 2: Angeben des Zurückhaltungsprozentsatzes und des Ausgangswerts  
 Die folgende Klausel kann nach der Spaltendefinitionsliste hinzugefügt werden, um ein Dataset zu definieren, das zum Testen aller der Miningstruktur zugeordneten Miningmodelle verwendet werden kann. Mithilfe der folgenden Klausel wird ein Testsatz erstellt, der 25 Prozent der gesamten Eingabefälle umfasst, ohne die maximale Anzahl der Fälle einzuschränken. Der Wert 5.000 wird als Ausgangswert zum Erstellen der Partition verwendet. Wenn Sie einen Ausgangswert angeben, werden für den Testsatz bei jeder Verarbeitung der Miningstruktur die gleichen Fälle ausgewählt, so lange die zugrunde liegenden Daten nicht geändert werden.  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT) REPEATABLE(5000)  
```  
  
### <a name="example-3-specifying-holdout-percentage-and-max-cases"></a>Beispiel 3: Angeben des Zurückhaltungsprozentsatzes und der maximalen Anzahl der Fälle  
 Mit der folgenden Klausel wird ein Testsatz erstellt, der entweder 25 Prozent der gesamten Eingabefälle oder 2.000 Fälle umfasst, je nachdem, welche Zahl kleiner ist. Da 0 als Ausgangswert angegeben ist, wird anhand des Namens der Miningstruktur der Anfangswert erstellt, der für die Stichprobe von Eingabefällen verwendet wird.  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT OR 2000 CASES) REPEATABLE(0)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
