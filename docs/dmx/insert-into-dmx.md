---
title: FÜGEN SIE IN (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 16732c1d889f7125d71d01bd0804b4202daceb7e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62505166"
---
# <a name="insert-into-dmx"></a>INSERT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Verarbeitet das angegebene Data Mining-Objekt. Weitere Informationen zum Verarbeiten von Miningmodellen und Miningstrukturen finden Sie unter [Verarbeitung von Anforderungen und Überlegungen &#40;Data Mining&#41;](../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Wenn eine Miningstruktur angegeben ist, verarbeitet die Anweisung die Miningstruktur sowie alle Miningmodelle, die der Struktur zugeordnet sind. Ist ein Miningmodell angegeben, verarbeitet die Anweisung nur das Miningmodell.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure> (<mapped model columns>) <source data query>  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure>.COLUMN_VALUES (<mapped model columns>) <source data query>  
```  
  
## <a name="arguments"></a>Argumente  
 *model*  
 Ein Modellbezeichner.  
  
 *structure*  
 Ein Strukturbezeichner.  
  
 *zugeordnete modellspalten*  
 Eine durch Trennzeichen getrennte Liste mit Spaltenbezeichnern und geschachtelten Bezeichnern.  
  
 *quelldatenabfrage*  
 Die Quellabfrage im anbieterdefinierten Format.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie keinen angeben **MININGMODELL** oder **MININGSTRUKTUR**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sucht nach den Objekttyp, der anhand des Namens, und verarbeitet das richtige Objekt. Wenn der Server eine Miningstruktur und ein Miningmodell enthält, die denselben Namen haben, wird ein Fehler zurückgegeben.  
  
 Durch die zweite Syntaxform, INSERT INTO *\<Objekt >* . COLUMN_VALUES können Sie Daten direkt in die modellspalten einfügen, ohne zu trainieren des Modells. Bei dieser Methode werden dem Modell Spaltendaten in einer übersichtlichen, geordneten Weise bereitgestellt, die sich anbietet, wenn Sie mit Datasets arbeiten, die Hierarchien oder geordnete Spalten enthalten.  
  
 Bei Verwendung von **INSERT INTO** mit einem Miningmodell oder eine Miningstruktur und nicht mehr die \<zugeordneten modellspalten > und \<quelldatenabfrage > Argumente, die Anweisung verhält sich wie  **ProcessDefault**, mit Bindungen, die bereits vorhanden. Wenn keine Bindungen vorhanden sind, gibt die Anweisung einen Fehler zurück. Weitere Informationen zu **ProcessDefault**, finden Sie unter [Verarbeitungsoptionen und-Einstellungen &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md). Das folgende Beispiel zeigt die Syntax:  
  
```  
INSERT INTO [MINING MODEL] <model>  
```  
  
 Bei Angabe von **MININGMODELL** und geben Sie zugeordneter Spalten und eine quelldatenabfrage, das Modell und die zugeordnete Struktur verarbeitet wird.  
  
 In der folgenden Tabelle sind die vom Status der Objekte abhängigen Ergebnisse der unterschiedlichen Formen der Anweisung beschrieben.  
  
|-Anweisung.|Status der Objekte|Ergebnis|  
|---------------|----------------------|------------|  
|INSERT INTO MINING MODEL *\<Modell >*|Miningstruktur wird verarbeitet.|Miningmodell wird verarbeitet.|  
||Miningstruktur wird nicht verarbeitet.|Miningmodell und Miningstruktur werden verarbeitet.|  
||Miningstruktur enthält weitere Miningmodelle.|Fehler bei der Verarbeitung. Sie müssen die Struktur und die zugeordneten Miningmodelle erneut verarbeiten.|  
|INSERT INTO MINING STRUCTURE *\<Struktur >*|Miningstruktur wird verarbeitet oder nicht verarbeitet.|Miningstruktur und zugeordnete Miningmodelle werden verarbeitet.|  
|INSERT INTO MINING MODEL *\<Modell >* , das eine Quellabfrage enthält<br /><br /> oder<br /><br /> INSERT INTO MINING STRUCTURE *\<Struktur >* , das eine Quellabfrage enthält|Entweder die Struktur oder das Modell enthält bereits Inhalt.|Fehler bei der Verarbeitung. Müssen Sie die Objekte löschen, bevor Sie mit diesen Vorgang ausführen [löschen &#40;DMX&#41;](../dmx/delete-dmx.md).|  
  
## <a name="mapped-model-columns"></a>Zugeordnete Modellspalten (Mapped Model Columns)  
 Mithilfe der \<zugeordnet modellspalten >-Element können Sie die Spalten aus der Datenquelle den Spalten in Ihrem Miningmodell zuordnen. Die \<zugeordneten modellspalten >-Element weist folgende Form:  
  
```  
<column identifier> | SKIP | <table identifier> (<column identifier> | SKIP), ...  
```  
  
 Mithilfe von **überspringen**, können Sie bestimmte Spalten, die muss in der Quellabfrage vorhanden sein, aber, nicht im Miningmodell vorhanden sind, ausschließen. SKIP ist hilfreich, wenn Sie keine Kontrolle über die Spalten haben, die in einem Eingaberowset enthalten sind. Wenn Sie Ihre eigene OPENQUERY schreiben, wird anstelle der Verwendung von SKIP empfohlen, die Spalte in der SELECT-Spaltenliste auszulassen.  
  
 SKIP ist auch nützlich, wenn eine Spalte aus dem Eingaberowset benötigt wird, um einen Join durchzuführen, die Spalte jedoch nicht von der Miningstruktur verwendet wird. Ein typisches Beispiel dafür sind eine Miningstruktur und ein Miningmodell, die eine geschachtelte Tabelle enthalten. Das Eingaberowset für diese Struktur umfasst eine Fremdschlüsselspalte, mit der ein hierarchisches Rowset mithilfe der SHAPE-Klausel erstellt wird. Die Fremdschlüsselspalte wird jedoch kaum im Modell verwendet.  
  
 Die Syntax für SKIP erfordert, dass Sie SKIP an der Position der einzelnen Spalte im Eingaberowset einfügen, das über keine entsprechende Miningstrukturspalte verfügt. Die geschachtelte Tabelle beispielsweise folgende muss z. B. OrderNumber in der APPEND-Klausel ausgewählt werden, damit Sie den Join angeben, es in der RELATE-Klausel verwendet werden kann; Allerdings möchten nicht Sie die OrderNumber-Daten in der geschachtelten Tabelle in der Miningstruktur einfügen. Aus diesem Grund verwendet das Beispiel das SKIP-Schlüsselwort anstelle von OrderNumber in INSERT INTO-Argument.  
  
## <a name="source-data-query"></a>Quelldatenabfrage (Source Data Query)  
 Die \<quelldatenabfrage >-Element kann die folgenden Datenquellentypen enthalten:  
  
-   **OPENQUERY**  
  
-   **OPENROWSET**  
  
-   **FORM "**  
  
-   Jede [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Abfrage, die ein Rowset zurückgibt  
  
 Weitere Informationen zu Datenquellentypen finden Sie unter [ &#60;quelldatenabfrage&#62;](../dmx/source-data-query.md).  
  
## <a name="basic-example"></a>Elementares Beispiel  
 Im folgenden Beispiel wird **OPENQUERY** zum Trainieren eines Naive Bayes-Modells, basierend auf der targeted mailing-Daten in die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenbank.  
  
```  
INSERT INTO NBSample (CustomerKey, Gender, [Number Cars Owned],  
    [Bike Buyer])  
OPENQUERY([AdventureWorksDW2012],'Select CustomerKey, Gender, [NumberCarsOwned], [BikeBuyer]   
FROM [vTargetMail]')  
```  
  
## <a name="nested-table-example"></a>Beispiel für eine geschachtelte Tabelle  
 Im folgenden Beispiel wird **Form** , ein zuordnungsminingmodell zu trainieren, das eine geschachtelte Tabelle enthält. Beachten Sie, die die erste Zeile enthält **überspringen** stattdessen OrderNumber, die erforderlich ist, in der **SHAPE_APPEND** Anweisung ist jedoch nicht im Miningmodell verwendet.  
  
```  
INSERT INTO MyAssociationModel  
    ([OrderNumber],[Models] (SKIP, [Model])  
    )  
SHAPE {  
    OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
AS [Models]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
