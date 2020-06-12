---
title: Create Mining Model (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c0355c8f0286fe894b7c723177c4146b1e460758
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669473"
---
# <a name="create-mining-model-dmx"></a>CREATE MINING MODEL (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Erstellt sowohl ein neues Miningmodell als auch eine Miningstruktur in der Datenbank. Sie können ein Modell erstellen, indem Sie entweder das neue Modell in der Anweisung definieren oder PMML (Predictive Model Markup Language) verwenden. Diese zweite Möglichkeit empfiehlt sich nur für fortgeschrittene Benutzer.  
  
 Der Name der Miningstruktur ergibt sich, indem "_structure" an den Modellnamen angefügt wird. Dadurch ist sichergestellt, dass sich der Strukturname vom Modellnamen unterscheidet.  
  
 Um ein Mining Modell für eine vorhandene Mining Struktur zu erstellen, verwenden Sie die Anweisung [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE [SESSION] MINING MODEL <model>  
(  
    [(<column definition list>)]  
)  
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH]  
CREATE MINING MODEL <model> FROM PMML <xml string>  
```  
  
## <a name="arguments"></a>Argumente  
 *model*  
 Ein eindeutiger Name für das Modell.  
  
 *Spalten Definitionsliste*  
 Eine durch Trennzeichen getrennte Liste mit Spaltendefinitionen.  
  
 *projiziert*  
 Der Name eines Data Mining-Algorithmus, der vom aktuellen Anbieter definiert wurde.  
  
> [!NOTE]  
>  Eine Liste der Algorithmen, die vom aktuellen Anbieter unterstützt werden, kann mithilfe [DMSCHEMA_MINING_SERVICES Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)abgerufen werden. Informationen zum Anzeigen der in der aktuellen Instanz von unterstützten Algorithmen finden Sie unter [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [Data Mining-Eigenschaften](https://docs.microsoft.com/analysis-services/server-properties/data-mining-properties).  
  
 *Parameterliste*  
 Optional. Eine durch Trennzeichen getrennte Liste mit anbieterdefinierten Parametern für den Algorithmus.  
  
 *XML-Zeichenfolge*  
 (Nur für Erweiterte Verwendung.) Ein XML-codiertes Modell (PMML). Die Zeichenfolge muss in einfache Anführungszeichen (') eingeschlossen werden.  
  
 Mit der **Session** -Klausel können Sie ein Mining Modell erstellen, das automatisch vom Server entfernt wird, wenn die Verbindung geschlossen wird oder ein Timeout der Sitzung auftritt. **Sitzungs** Mining Modelle sind nützlich, da Sie nicht erfordern, dass der Benutzer ein Datenbankadministrator ist, und Sie verwenden nur Speicherplatz, solange die Verbindung geöffnet ist.  
  
 Die **with Drillthrough** -Klausel ermöglicht einen Drillthrough für das neue Mining Modell. Drillthrough kann nur aktiviert werden, wenn das Modell erstellt wird. Bei einigen Modelltypen ist ein Drillthrough erforderlich, um das Modell im benutzerdefinierten Viewer zu durchsuchen. Ein Drillthrough ist nicht erforderlich für Vorhersagen oder das Durchsuchen des Modells mit dem Microsoft Generic Content Tree Viewer.  
  
 Die **Create Mining Model** -Anweisung erstellt ein neues Mining Modell, das auf der Spalten Definitionsliste, dem Algorithmus und der Algorithmusparameterliste basiert.  
  
### <a name="column-definition-list"></a>Spaltendefinitionsliste (Column Definition List)  
 Sie definieren die Struktur eines Modells, für das die Spaltendefinitionsliste verwendet wird, indem Sie für jede Spalte die folgenden Informationen einschließen:  
  
-   Name (obligatorisch)  
  
-   Datentyp (obligatorisch)  
  
-   Verteilung  
  
-   Liste der Modellierungsflags  
  
-   Inhaltstyp (obligatorisch)  
  
-   Vorhersage Anforderung, die dem Algorithmus anzeigt, dass diese Spalte vorhergesagt werden soll, angegeben durch die **Vorhersage** -oder **PREDICT_ONLY** -Klausel  
  
-   Beziehung zu einer Attribut Spalte (nur obligatorisch, wenn zutreffend), angegeben durch die **related to** -Klausel  
  
 Verwenden Sie die folgende Syntax für die Spalten Definitionsliste, um eine einzelne Spalte zu definieren:  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<prediction>]    [<column relationship>]   
```  
  
 Verwenden Sie die folgende Syntax für die Spalten Definitionsliste, um eine Spalte für eine Spalte in einer Spalte zu definieren:  
  
```  
<column name>    TABLE    [<prediction>] ( <non-table column definition list> )  
```  
  
 Zum Definieren einer Spalte können Sie jeweils nur eine Klausel aus einer bestimmten Gruppe verwenden. Die einzige Ausnahme bilden Modellierungsflags. Sie können mehrere Modellierungsflags für eine Spalte definieren.  
  
 Eine Liste der Datentypen, Inhaltstypen, Spaltendistributionen und Modellierungsflags, mit denen Sie eine Spalte definieren können, finden Sie in den folgenden Themen:  
  
-   [Datentypen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-types-data-mining)  
  
-   [Inhaltstypen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)  
  
-   [Spaltenverteilungen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining)  
  
-   [Modellierungsflags &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/modeling-flags-data-mining)  
  
 Sie können der Anweisung eine Klausel hinzufügen, um die Beziehung zwischen zwei Spalten zu beschreiben. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]unterstützt die Verwendung der folgenden \< Spalten Beziehung>-Klausel.  
  
 **verknüpft mit**  
 Diese Form kennzeichnet eine Wertehierarchie. Das Ziel einer RELATED TO-Spalte kann eine Schlüsselspalte einer geschachtelten Tabelle, eine Spalte mit diskreten Werten in der Fallzeile oder eine andere Spalte mit einer RELATED TO-Klausel sein, wodurch eine tiefere Hierarchie gekennzeichnet ist.  
  
 Mit einer Vorhersageklausel können Sie beschreiben, wie die Vorhersagespalte verwendet wird. In der folgenden Tabelle sind die beiden möglichen Klauseln beschrieben.  
  
|\<Vorhersage>-Klausel|Beschreibung|  
|---------------------------|-----------------|  
|**PREDICT**|Diese Spalte kann vom Modell vorhergesagt werden, und sie kann in Eingabefällen bereitgestellt werden, um den Wert anderer vorhersagbarer Spalten vorherzusagen.|  
|**PREDICT_ONLY**|Diese Spalte kann vom Modell vorhergesagt werden, aber ihre Werte können in Eingabefällen nicht dazu verwendet werden, den Wert anderer vorhersagbarer Spalten vorherzusagen.|  
  
### <a name="parameter-definition-list"></a>Parameterdefinitionsliste (Parameter Definition List)  
 Mit der Parameterliste können Sie die Leistung und die Funktionsweise eines Miningmodells anpassen. Die Syntax der Parameterliste sieht wie folgt aus:  
  
```  
[<parameter> = <value>, <parameter> = <value>,...]  
```  
  
 Eine Liste der Parameter, die den einzelnen Algorithmen zugeordnet sind, finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie ein Modell mit einem integrierten Testdataset erstellen möchten, sollten Sie die Anweisung CREATE MINING STRUCTURE gefolgt von ALTER MINING STRUCTURE verwenden. Jedoch unterstützen nicht alle Modelltypen ein zurückgehaltenes Dataset. Weitere Informationen finden Sie unter [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
 Eine exemplarische Vorgehensweise zum Erstellen eines Mining Modells mit der Anweisung "-Anweisung" finden Sie unter [Zeitreihen vorhersagbares DMX-Tutorial](https://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2).  
  
## <a name="naive-bayes-example"></a>Beispiel für Naive Bayes-Algorithmus  
 Im folgenden Beispiel wird der [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Algorithmus verwendet, um ein neues Miningmodell zu erstellen. Die Bike Buyer-Spalte ist als das vorhersagbare Attribut definiert.  
  
```  
CREATE MINING MODEL [NBSample]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE PREDICT  
)  
USING Microsoft_Naive_Bayes  
```  
  
## <a name="association-model-example"></a>Beispiel für Association-Algorithmus  
 Im folgenden Beispiel wird der [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus verwendet, um ein neues Miningmodell zu erstellen. Für die Anweisung wird die Möglichkeit genutzt, eine Tabelle in einer Modelldefinition zu schachteln, indem eine Tabellenspalte verwendet wird. Das Modell wird mit den Parametern *MINIMUM_PROBABILITY* und *MINIMUM_SUPPORT* geändert.  
  
```  
CREATE MINING MODEL MyAssociationModel (  
    OrderNumber TEXT KEY,  
    [Products] TABLE PREDICT (  
        [Model] TEXT KEY  
    )  
)  
USING Microsoft_Association_Rules (Minimum_Probability = 0.1, MINIMUM_SUPPORT = 0.01)  
```  
  
## <a name="sequence-clustering-example"></a>Beispiel für den Sequence Clustering-Algorithmus  
 Im folgenden Beispiel wird der [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus verwendet, um ein neues Miningmodell zu erstellen. Das Modell wird mit zwei Schlüsseln definiert. Die OrderNumber-Spalte wird als Fall Schlüssel verwendet und gibt einzelne Aufträge an. Die Spalte "LineNumber" wird als Schlüssel der Schlüssel Tabelle verwendet und gibt die Reihenfolge an, in der Elemente einer Bestellung hinzugefügt wurden.  
  
```  
CREATE MINING MODEL BuyingSequence (  
    [Order Number] TEXT KEY,  
    [Products] TABLE   
     (  
        [Line Number] LONG KEY SEQUENCE,  
        [Model] TEXT DISCRETE PREDICT  
    )  
)  
USING Microsoft_Sequence_Clustering  
```  
  
## <a name="time-series-example"></a>Beispiel für den Time Series-Algorithmus  
 Im folgenden Beispiel wird der [!INCLUDE[msCoName](../includes/msconame-md.md)]-Zeitreihenalgorithmus verwendet, um mit dem ARTxp-Algorithmus ein neues Miningmodell zu erstellen. ReportingDate ist die Schlüssel Spalte für die Zeitreihen und ModelRegion ist die Schlüssel Spalte für die Datenreihe. In diesem Beispiel wird davon ausgegangen, dass die Periodizität der Daten alle 12 Monate ist. Daher wird der *PERIODICITY_HINT* -Parameter auf 12 festgelegt.  
  
> [!NOTE]  
>  Sie müssen den *PERIODICITY_HINT* -Parameter angeben, indem Sie Klammer Zeichen verwenden. Da der Wert eine Zeichenfolge ist, muss er außerdem in einfache Anführungszeichen eingeschlossen werden: "{ \< numeric Value>}".  
  
```  
CREATE MINING MODEL SalesForecast (  
        ReportingDate DATE KEY TIME,  
        ModelRegion TEXT KEY,  
        Amount LONG CONTINUOUS PREDICT,  
        Quantity LONG CONTINUOUS PREDICT  
)  
USING Microsoft_Time_Series (PERIODICITY_HINT = '{12}', FORECAST_METHOD = 'ARTXP')  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
