---
title: SELECT verschieden vom &lt;Modell &gt; (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 67ed5236aad0549fa6850114280ee15d8cebcaeb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892531"
---
# <a name="select-distinct-from-ltmodel-gt-dmx"></a>SELECT-FROM &lt;- &gt; Modell (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt alle möglichen Status für die ausgewählte Spalte im Modell zurück. Die zurückgegebenen Werte variieren, je nachdem, ob die angegebene Spalte diskrete Werte, diskretisierte numerische Werte oder fortlaufende numerische Werte enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] DISTINCT [TOP <n>] <expression list> FROM <model>   
[WHERE <condition list>][ORDER BY <expression>]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die die Anzahl der zurück zugebende Zeilen angibt.  
  
 *Ausdrucks Liste*  
 Eine durch Trennzeichen getrennte Liste mit Bezeichnern verbundener Spalten (abgeleitet aus dem Modell) oder mit Ausdrücken.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Bedingungs Liste*  
 Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *Begriff*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die SELECT-Anweisung unter **schiedlicher from** -Anweisung kann nur mit einer einzelnen Spalte oder mit einem Satz verwandter Spalten verwendet werden. Für eine Gruppe nicht verbundener Spalten kann diese Klausel nicht verwendet werden.  
  
 Mit der **SELECT SELECT** -Anweisung können Sie direkt auf eine Spalte in einer geschachtelten Tabelle verweisen. Beispiel:  
  
```  
<model>.<table column reference>.<column reference>  
```  
  
 Die Ergebnisse der SELECT-Anweisung **vom \<Typ "Select verschieden from Model>** " variieren je nach Spaltentyp. In der folgenden Tabelle sind die unterstützten Spaltentypen sowie die Ausgabe beschrieben, die von der Anweisung erstellt wird.  
  
|Spaltentyp|Output|  
|-----------------|------------|  
|Discrete|Die eindeutigen Werte in der Spalte.|  
|Discretized|Der Mittelpunkt für jeden diskretisierten Bucket in der Spalte.|  
|Fortlaufend|Der Mittelpunkt für die Werte in der Spalte.|  
  
## <a name="discrete-column-example"></a>Beispiel zu einer diskreten Spalte  
 Das folgende Codebeispiel basiert auf dem `[TM Decision Tree]` Modell, das Sie im Lernprogramm zu [Data Mining-Grundlagen](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)erstellt haben. Die Abfrage gibt die eindeutigen Werte zurück, die in der diskreten Spalte `Gender` vorhanden sind.  
  
```  
SELECT DISTINCT [Gender]  
FROM [TM Decision Tree]  
```  
  
 Beispielergebnisse:  
  
|Geschlecht|  
|------------|  
||  
|F|  
|M|  
  
 In Spalten, die diskrete Werte enthalten, enthalten die Ergebnisse auch immer den fehlenden Status, der als Nullwert angezeigt wird.  
  
## <a name="continuous-column-example"></a>Beispiel für eine kontinuierliche Spalte  
 Im folgenden Codebeispiel wird das Mittelpunktalter, minimale und maximale Alter für alle Werte in der Spalte zurückgegeben.  
  
```  
SELECT DISTINCT [Age] AS [Midpoint Age],   
    RangeMin([Age]) AS [Minimum Age],   
    RangeMax([Age]) AS [Maximum Age]  
FROM [TM Decision Tree]  
```  
  
 Beispielergebnisse:  
  
|Mittelpunktalter|Mindestalter|Maximales Alter|  
|------------------|-----------------|-----------------|  
||||  
|62|26|97|  
  
 Die Abfrage gibt auch eine einzelne Zeile mit Nullwerten zurück, um die fehlenden Werte darzustellen.  
  
## <a name="discretized-column-example"></a>Beispiel zu einer diskretisierten Spalte  
 Im folgenden Codebeispiel werden der Mittelpunkt sowie der maximale und minimale Wert für jeden Bucket zurückgegeben, der von dem Algorithmus für die Spalte [`Yearly Income]` erstellt wurde. Um die Ergebnisse für dieses Beispiel zu reproduzieren, müssen Sie eine neue Miningstruktur erstellen, die der von `[Targeted Mailing]` entspricht. Ändern Sie im Assistenten den Inhaltstyp der `Yearly Income` Spalte von **fortlaufend** in **diskretisiert**.  
  
> [!NOTE]  
>  Sie können das im Lernprogramm zu Data Mining-Grundlagen erstellte Miningmodell auch so ändern, dass die Miningstrukturspalte [`Yearly Income]` diskretisiert wird. Weitere Informationen hierzu finden Sie unter [Ändern der Diskretisierung einer Spalte in einem Mining Modell](https://docs.microsoft.com/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model). Wenn Sie jedoch die Diskretisierung der Spalte ändern, wird die Miningstruktur neu verarbeitet, wodurch die Ergebnisse anderer Modelle, die mithilfe dieser Struktur erstellt wurden, geändert werden.  
  
```  
SELECT DISTINCT [Yearly Income] AS [Bucket Average],   
    RangeMin([Yearly Income]) AS [Bucket Minimum],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
 Beispielergebnisse:  
  
|Bucketdurchschnitt|Bucketminimum|Bucketmaximum|  
|--------------------|--------------------|--------------------|  
||||  
|24610,7|10000|39221,41|  
|55115,73|39221,41|71010,05|  
|84821,54|71010,05|98633,04|  
|111633,9|98633,04|124634,7|  
|147317,4|124634,7|170000|  
  
 Sie können feststellen, dass die Werte der Spalte [Yearly Income] in fünf Buckets diskretisiert wurden, zuzüglich einer weiteren Zeile von Nullwerten, die fehlende Daten darstellen.  
  
 Die Anzahl der Dezimalstellen in den Ergebnissen ist von dem für die Abfrage verwendeten Client abhängig. Hier wurde zur Vereinfachung und zur Wiedergabe der in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] angezeigten Werte auf zwei Dezimalstellen gerundet.  
  
 Wenn Sie das Modell beispielsweise mithilfe des Entscheidungsstruktur-Viewers durchsuchen und auf einen Knoten klicken, der Kunden gruppiert nach Einkommen enthält, werden in der Quickinfo folgende Knoteneigenschaften angezeigt:  
  
 Alter >= 69 und Jahreseinkommen < 39221,41  
  
> [!NOTE]  
>  Der Minimalwert des Minimalbuckets und der Maximalwert des Maximalbuckets sind lediglich die höchsten und niedrigsten ermittelten Werte. Von allen Werten, die außerhalb dieses ermittelten Bereichs liegen, wird angenommen, dass sie zu den Minimal- und Maximalbuckets gehören.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wählen Sie &#40;DMX-&#41;](../dmx/select-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
