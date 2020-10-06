---
description: ALTER MINING STRUCTURE (DMX)
title: Alter Mining Structure (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6169d898479637d8f8c0a74aececd56cf1f62eb7
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727811"
---
# <a name="alter-mining-structure-dmx"></a>ALTER MINING STRUCTURE (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Erstellt ein neues Miningmodell, das auf einer vorhandenen Miningstruktur basiert.  Wenn Sie die **ALTER MINING STRUCTURE** -Anweisung verwenden, um ein neues Mining Modell zu erstellen, muss die Struktur bereits vorhanden sein. Wenn Sie im Gegensatz dazu die-Anweisung [erstellen, Mining Modell &#40;DMX-&#41;erstellen ](../dmx/create-mining-model-dmx.md), erstellen Sie ein Modell und generieren die zugrunde liegende Mining Struktur automatisch gleichzeitig.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ALTER MINING STRUCTURE <structure>  
ADD MINING MODEL <model>  
(  
    <column definition list>  
  [(<nested column definition list>) [WITH FILTER (<nested filter criteria>)]]  
)  
USING <algorithm> [(<parameter list>)]   
[WITH DRILLTHROUGH]  
[,FILTER(<filter criteria>)]  
```  
  
## <a name="arguments"></a>Argumente  
 *Werks*  
 Der Name der Miningstruktur, der das Miningmodell hinzugefügt wird.  
  
 *model*  
 Ein eindeutiger Name für das Miningmodell.  
  
 *Spalten Definitionsliste*  
 Eine durch Trennzeichen getrennte Liste mit Spaltendefinitionen.  
  
 *Definition der Liste der Spalten in der Liste*  
 Eine durch Trennzeichen getrennte Liste der Spalten einer geschachtelten Tabelle, falls zutreffend.  
  
 *Filterkriterien für Filter*  
 Ein Filterausdruck, der für die Spalten in einer geschachtelten Tabelle übernommen wird.  
  
 *projiziert*  
 Der Name eines Data Mining-Algorithmus, der vom Anbieter definiert wurde.  
  
> [!NOTE]  
>  Eine Liste der Algorithmen, die vom aktuellen Anbieter unterstützt werden, kann mithilfe [DMSCHEMA_MINING_SERVICES Rowsets](/previous-versions/sql/sql-server-2012/ms126251(v=sql.110))abgerufen werden. Informationen zum Anzeigen der in der aktuellen Instanz von unterstützten Algorithmen finden Sie unter [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [Data Mining-Eigenschaften](/analysis-services/server-properties/data-mining-properties).  
  
 *Parameterliste*  
 Optional. Eine durch Trennzeichen getrennte Liste mit anbieterdefinierten Parametern für den Algorithmus.  
  
 *Filterkriterien*  
 Ein Filterausdruck, der für die Spalten in der Falltabelle übernommen wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die Miningstruktur zusammengesetzte Schlüssel enthält, muss das Miningmodell alle Schlüsselspalten einschließen, die in der Struktur definiert sind.  
  
 Wenn für das Modell keine vorhersagbare Spalte erforderlich ist (z. B. bei Modellen, die mit dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering- oder dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus erstellt wurden), müssen Sie in der Anweisung keine Spaltendefinition einschließen. Alle Attribute in dem sich ergebenden Modell werden als Eingaben behandelt.  
  
 In der **with** -Klausel, die auf die Fall Tabelle angewendet wird, können Sie Optionen sowohl für das Filtern als auch für den Drillthrough angeben:  
  
-   Fügen Sie das **Filter** Schlüsselwort und eine Filterbedingung hinzu. Der Filter wird auf die Fälle im Miningmodell angewendet.  
  
-   Fügen Sie das Schlüsselwort Drillthrough hinzu, damit Benutzer des Mining Modells einen **Drilldown** von den Modellergebnissen zu den Falldaten ausführen können. In Data Mining-Erweiterungen (DMX) kann Drillthrough nur aktiviert werden, wenn Sie das Modell erstellen.  
  
 Um die Case-Filterung und den Drillthrough zu verwenden, kombinieren Sie die Schlüsselwörter in einer einzelnen **with** -Klausel, indem Sie die im folgenden Beispiel gezeigte Syntax verwenden:  
  
 `WITH DRILLTHROUGH, FILTER(Gender = 'Male')`  
  
## <a name="column-definition-list"></a>Spaltendefinitionsliste (Column Definition List)  
 Sie definieren die Struktur eines Modells, indem Sie eine Spaltendefinitionsliste angeben, die die folgenden Informationen für jede Spalte enthält:  
  
-   Name (obligatorisch)  
  
-   Alias (optional)  
  
-   Modellierungsflags  
  
-   Vorhersage Anforderung, die dem Algorithmus angibt, ob die Spalte einen vorhersagbaren Wert enthält, der durch die **Vorhersage** -oder **PREDICT_ONLY** -Klausel angegeben wird.  
  
 Verwenden Sie die folgende Syntax für die Spaltendefinitionsliste, wenn Sie eine einzelne Spalte definieren möchten:  
  
```  
<structure column name>  [AS <model column name>]  [<modeling flags>]    [<prediction>]  
```  
  
### <a name="column-name-and-alias"></a>Spaltenname und Alias  
 Der Spaltenname, den Sie in der Spaltendefinitionsliste verwenden, muss mit dem in der Miningstruktur verwendeten Spaltennamen identisch sein. Sie können jedoch optional einen Alias definieren, um die Strukturspalte im Miningmodell darzustellen. Außerdem können Sie mehrere Spaltendefinitionen für dieselbe Strukturspalte erstellen und jeder Kopie der Spalte einen anderen Alias und eine andere Vorhersageverwendung zuweisen. Standardmäßig wird der Name der Strukturspalte verwendet, falls Sie keinen Alias definieren. Weitere Informationen finden Sie unter [Erstellen eines Alias für eine Modell Spalte](/analysis-services/data-mining/create-an-alias-for-a-model-column).  
  
 Für geschachtelte Tabellen Spalten geben Sie den Namen der geschachtelten Tabelle an, geben den Datentyp als **Tabelle**an und stellen dann die Liste der geschachtelten Spalten bereit, die in Klammern eingeschlossen werden sollen.  
  
 Sie können einen Filterausdruck definieren, der auf die geschachtelte Tabelle angewendet wird, indem Sie nach der Definition für die Spalte der geschachtelten Tabelle einen Filterkriterienausdruck anhängen.  
  
### <a name="modeling-flags"></a>Modellierungsflags  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt die folgenden Modellierungsflags zur Verwendung in Miningmodellspalten:  
  
> [!NOTE]  
>  Das NOT NULL-Modellierungsflag gilt für die Miningstrukturspalte. Weitere Informationen finden Sie unter [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
|Begriff|Definition|  
|-|-|  
|**Regressor**|Zeigt an, dass der Algorithmus die angegebene Spalte in der Regressionsformel von Regressionsalgorithmen verwenden kann.|  
|**MODEL_EXISTENCE_ONLY**|Gibt an, dass die Werte für die Attributspalte weniger wichtig sind als das Vorhandensein der Attribute.|  
  
 Sie können mehrere Modellierungsflags für eine Spalte definieren. Weitere Informationen zum Verwenden von Modellierungsflags finden Sie unter [Modellierungsflags &#40;DMX-&#41;](../dmx/modeling-flags-dmx.md).  
  
### <a name="prediction-clause"></a>Vorhersageklausel  
 Die Vorhersageklausel beschreibt, wie die Vorhersagespalte verwendet wird. In der folgenden Tabelle sind die möglichen Klauseln aufgelistet.  
  
|Klausel|BESCHREIBUNG|  
|-|-|  
|**PREDICT**|Diese Spalte kann vom Modell vorhergesagt werden, und ihre Werte können als Eingabe verwendet werden, um den Wert anderer vorhersagbarer Spalten vorherzusagen.|  
|**PREDICT_ONLY**|Diese Spalte kann vom Modell vorhergesagt werden, aber ihre Werte können in Eingabefällen nicht dazu verwendet werden, den Wert anderer vorhersagbarer Spalten vorherzusagen.|  
  
## <a name="filter-criteria-expressions"></a>Filterkriterienausdrücke  
 Sie können einen Filter definieren, der die im Miningmodell verwendeten Fälle einschränkt. Der Filter kann auf die Spalten der Falltabelle, auf die Zeilen der geschachtelten Tabelle oder auf beides angewendet werden.  
  
 Filterkriterienausdrücke sind vereinfachte DMX-Prädikate und ähneln einer WHERE-Klausel. Filterausdrücke werden auf Formeln reduziert, die grundlegende mathematische Operatoren, Skalare und Spaltennamen verwenden. Eine Ausnahme bildet der EXISTS-Operator. Seine Auswertung ergibt TRUE, wenn mindestens eine Zeile für die Unterabfrage zurückgegeben wird. Prädikate können mit den allgemeinen logischen Operatoren kombiniert werden: AND, OR und NOT.  
  
 Weitere Informationen zu filtern, die mit Mining Modellen verwendet werden, finden Sie unter [Filter für Mining Modelle &#40;Analysis Services Data Mining-&#41;](/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
> [!NOTE]  
>  Spalten in einem Filter müssen Miningstrukturspalten sein. Sie können keinen Filter für eine Modellspalte oder eine Spalte mit einem Alias erstellen.  
  
 Weitere Informationen zu DMX-Operatoren und-Syntax finden Sie unter [Mining Modell Spalten](/analysis-services/data-mining/mining-model-columns).  
  
## <a name="parameter-definition-list"></a>Parameterdefinitionsliste (Parameter Definition List)  
 Durch Hinzufügen von Algorithmusparametern zur Parameterliste können Sie die Leistung und die Funktionsweise eines Modells anpassen. Die Parameter, die Sie verwenden können, hängen vom Algorithmus ab, den Sie in der USING-Klausel angeben. Eine Liste der Parameter, die den einzelnen Algorithmen zugeordnet sind, finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).  
  
 Die Syntax der Parameterliste sieht wie folgt aus:  
  
```  
[<parameter> = <value>, <parameter> = <value>,...]  
```  
  
## <a name="example-1-add-a-model-to-a-structure"></a>Beispiel 1: Hinzufügen eines Modells zu einer Struktur  
 Im folgenden Beispiel wird der **neuen Mailing** -Mining Struktur ein Naive Bayes-Mining Modell hinzugefügt, und die maximale Anzahl von Attribut Zuständen wird auf 50 beschränkt.  
  
```  
ALTER MINING STRUCTURE [New Mailing]  
ADD MINING MODEL [Naive Bayes]  
(  
    CustomerKey,   
    Gender,  
    [Number Cars Owned],  
    [Bike Buyer] PREDICT  
)  
USING Microsoft_Naive_Bayes (MAXIMUM_STATES = 50)  
```  
  
## <a name="example-2-add-a-filtered-model-to-a-structure"></a>Beispiel 2: Hinzufügen eines gefilterten Modells zu einer Struktur  
 Im folgenden Beispiel wird `Naive Bayes Women` der **neuen Mailing** -Mining Struktur ein Mining Modell hinzugefügt. Das neue Modell verfügt über dieselbe grundlegende Struktur wie das Miningmodell, das in Beispiel 1 hinzugefügt wurde. Dieses Modell beschränkt die Fälle aus der Miningstruktur allerdings auf weibliche Kunden über 50 Jahre.  
  
```  
ALTER MINING STRUCTURE [New Mailing]  
ADD MINING MODEL [Naive Bayes Women]  
(  
    CustomerKey,   
    Gender,  
    [Number Cars Owned],  
    [Bike Buyer] PREDICT  
)  
USING Microsoft_Naive_Bayes  
WITH FILTER([Gender] = 'F' AND [Age] >50)  
```  
  
## <a name="example-3-add-a-filtered-model-to-a-structure-with-a-nested-table"></a>Beispiel 3: Hinzufügen eines gefilterten Modells zu einer Struktur mit einer geschachtelten Tabelle  
 Im folgenden Beispiel wird ein Miningmodell einer geänderten Version der Warenkorbminingstruktur hinzugefügt. Die im Beispiel verwendete Mining Struktur wurde so geändert, dass Sie eine **Regions** Spalte, die Attribute für den Kundenbereich enthält, und eine Spalte mit **Einkommensgruppen** enthält, die das Kunden Einkommen mithilfe der **High**Werte hoch **, Mittel**oder **niedrig**kategorisiert.  
  
 Die Miningstruktur schließt auch eine geschachtelte Tabelle ein, in der die Elemente, die der Kunde gekauft hat, aufgelistet werden.  
  
 Da die Miningstruktur eine geschachtelte Tabelle enthält, können Sie einen Filter auf die Falltabelle, die geschachtelte Tabelle oder beides anwenden. In diesem Beispiel werden ein Fallfilter und ein geschachtelter Zeilenfilter kombiniert, um die Fälle auf wohlhabende europäische Kunden zu beschränken, die eines der "Road"-Reifenmodelle gekauft haben.  
  
```  
ALTER MINING STRUCTURE [Market Basket with Region and Income]  
ADD MINING MODEL [Decision Trees]  
(  
    CustomerKey,   
    Region,  
    [Income Group],  
    [Product] PREDICT (Model)   
WITH FILTER (EXISTS (SELECT * FROM [v Assoc Seq Line Items] WHERE   
 [Model] = 'HL Road Tire' OR  
 [Model] = 'LL Road Tire' OR  
 [Model] = 'ML Road Tire' )  
)  
) WITH FILTER ([Income Group] = 'High' AND [Region] = 'Europe')  
USING Microsoft_Decision Trees  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
