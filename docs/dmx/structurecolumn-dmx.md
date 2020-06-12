---
title: Structurecolren (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 82317f4a4e5f4c4fddd4ffaf45c5897dfd4d0df5
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669979"
---
# <a name="structurecolumn-dmx"></a>StructureColumn (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt den Wert der Strukturspalte zurück, der dem angegebenen Fall entspricht, oder den Tabellenwert für eine geschachtelte Tabelle im angegebenen Fall.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StructureColumn('structure column name')  
```  
  
## <a name="arguments"></a>Argumente  
 Name der Strukturspalte.  
 Der Name einer Fallspalte oder der Spalte einer geschachtelten Miningstrukturtabelle.  
  
## <a name="result-type"></a>Ergebnistyp  
 Der Typ, der zurückgegeben wird, hängt vom Typ der Spalte ab, auf die in der \< Struktur Spaltenname>-Parameters verwiesen wird. Wenn beispielsweise auf eine Miningstrukturspalte verwiesen wird, die einen Skalarwert enthält, gibt die Funktion ebenfalls einen Skalarwert zurück.  
  
 Wenn die referenzierte Miningstrukturspalte eine geschachtelte Tabelle ist, gibt auch die Funktion einen Tabellenwert zurück. Der zurückgegebene Tabellenwert kann in der FROM-Klausel einer untergeordneten SELECT-Anweisung verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion ist polymorph und kann an beliebiger Stelle in Anweisungen verwendet werden, die Ausdrücke wie z B. die SELECT-Ausdrucksliste, den WHERE-Bedingungsausdruck und den ORDER BY-Ausdruck zulassen.  
  
 Der Name der Spalte in der Mining Struktur ist ein Zeichen folgen Wert, der in einfache Anführungszeichen eingeschlossen werden muss, z. b. `StructureColumn('` **Spalte 1** `')` . Wenn mehrere Spalten den gleichen Namen haben, wird der Name entsprechend dem Kontext der einschließenden SELECT-Anweisung aufgelöst.  
  
 Die Ergebnisse, die von einer Abfrage mithilfe der **structurecolren** -Funktion zurückgegeben werden, sind durch das vorhanden sein von Filtern im Modell betroffen. Das heißt, der Modellfilter kontrolliert die Fälle, die im Miningmodell enthalten sind. Daher gibt eine Abfrage auf der Strukturspalte nur die Fälle zurück, die im Miningmodell verwendet wurden. Im Abschnitt "Beispiele" zu diesem Thema finden Sie Codebeispiele, die die Auswirkung von Miningmodellfiltern auf Falltabellen und geschachtelte Tabellen zeigen.  
  
 Weitere Informationen zur Verwendung dieser Funktion in einer DMX-SELECT-Anweisung finden Sie unter [Select from &#60;Model&#62;. Fälle &#40;DMX-&#41;](../dmx/select-from-model-cases-dmx.md) oder [aus &#60;Struktur&#62; auswählen. Fälle](../dmx/select-from-structure-cases.md).  
  
## <a name="error-messages"></a>Fehlermeldungen  
 Der folgende Sicherheitsfehler wird ausgegeben, wenn der Benutzer keine Drillthroughberechtigungen für die übergeordnete Miningstruktur hat.  
  
 Der Benutzer "% {User/}" verfügt nicht über die Berechtigung, einen Drillthrough zur übergeordneten Mining Struktur des% {Model/}-Mining Modells auszuführen.  
  
 Die folgende Fehlermeldung wird ausgegeben, wenn ein ungültiger Strukturspaltenname angegeben wird:  
  
 Die% {Structure-Column-Name/}-Mining Struktur Spalte wurde in der übergeordneten Mining Struktur '% {Structure/} ' im aktuellen Kontext (Zeile% {Line/}, Spalte% {Column/}) nicht gefunden.  
  
## <a name="examples"></a>Beispiele  
 Für diese Beispiele wird die folgende Miningstruktur verwendet. Beachten Sie, dass die Miningstruktur zwei geschachtelte Tabellenspalten, `Products` und `Hobbies` enthält. Die geschachtelte Tabelle in der `Hobbies`-Spalte enthält eine einzige Spalte, die als Schlüssel für die geschachtelte Tabelle verwendet wird. Die geschachtelte Tabelle in der `Products`-Spalte ist eine komplex geschachtelte Tabelle mit einer Schlüsselspalte und weiteren Spalten, die für die Eingabe verwendet werden. Die folgenden Beispiele zeigen, wie eine Data Mining-Struktur so entworfen werden kann, dass sie viele unterschiedliche Spalten enthält, auch wenn nicht jedes Modell jede Spalte verwenden darf. Einige dieser Spalten sind auf der Modellebene zum Generalisieren von Mustern möglicherweise nicht von Nutzen, können jedoch sehr hilfreich für den Drillthrough sein.  
  
```  
CREATE MINING STRUCTURE [MyStructure]   
(  
CustomerName TEXT KEY,  
Occupation TEXT DISCRETE,  
Age LONG CONTINUOUS,  
MaritalStatus TEXT DISCRETE,  
Income LONG CONTINUOUS,  
Products  TABLE  
 (  
    ProductNameTEXT KEY,  
    Quantity LONG CONTINUOUS,  
    OnSale BOOLEAN  DISCRETE  
)  
 Hobbies  TABLE  
 (  
    Hobby KEY  
 ))  
```  
  
 Erstellen Sie anschließend mit folgendem Beispielcode ein Miningmodell, das auf der soeben erstellten Struktur basiert:  
  
```  
ALTER MINING STRUCTURE [MyStructure] ADD MINING MODEL [MyModel] (  
CustomerName,  
Age,  
MaritalStatus,  
Income PREDICT,  
Products   
(  
ProductName  
) WITH FILTER(NOT OnSale)  
) USING Microsoft_Decision_Trees   
WITH FILTER(EXISTS (Products))  
```  
  
### <a name="sample-query-1-returning-a-column-from-the-mining-structure"></a>Beispielabfrage 1: Zurückgeben einer Spalte der Miningstruktur  
 Die folgende Beispielabfrage gibt die Spalten `CustomerName` und `Age` zurück, die als Teil des Miningmodells definiert sind. Die Abfrage gibt außerdem die Spalte `Age` zurück, die zwar Teil der Struktur, nicht aber Teil des Miningmodells ist.  
  
```  
SELECT CustomerName, Age, StructureColumn('Occupation') FROM MyModel.CASES   
WHERE Age > 30  
```  
  
 Beachten Sie, dass das Filtern von Zeilen zum Einschränken der Fälle auf Kunden, die älter als 30 Jahre sind, auf Modellebene stattfindet. Daher gibt dieser Ausdruck keine Fälle zurück, die in den Strukturdaten enthalten sind, nicht aber vom Modell verwendet werden. Da die Filterbedingung zum Erstellen des Modells (`EXISTS (Products)`) die Fälle auf die Kunden beschränkt, die Produkte erworben haben, werden möglicherweise einige der in der Struktur enthaltenen Fälle durch diese Abfrage nicht zurückgegeben.  
  
### <a name="sample-query-2-applying-a-filter-to-the-structure-column"></a>Beispielabfrage 2: Anwenden eines Filters auf die Strukturspalte  
 Die folgende Beispielabfrage gibt nicht nur die Modellspalten `CustomerName` und `Age` sowie die geschachtelte Tabelle `Products` zurück, sondern auch den Wert der Spalte `Quantity` in der geschachtelten Tabelle, die nicht Teil des Modells ist.  
  
```  
SELECT CustomerName, Age,  
(SELECT ProductName, StructureColumn('Quantity') FROM Products) FROM MA.CASES   
WHERE StructureColumn('Occupation') = 'Architect'  
```  
  
 Beachten Sie, dass in diesem Beispiel ein Filter auf die Struktur Spalte angewendet wird, um die Fälle auf Kunden zu beschränken, deren Beruf "Architect" ist ( `WHERE StructureColumn('Occupation') = 'Architect'` ). Da das Anwenden der Modellfilterbedingung auf Fälle immer während der Erstellung des Modells stattfindet, werden nur die Fälle in die Modellfälle aufgenommen, die in der `Products`-Tabelle mindestens eine qualifizierende Zeile enthalten. Aus diesem Grund werden sowohl der Filter für die geschachtelte `Products`-Tabelle als auch der Filter für den `('Occupation')`-Fall angewendet.  
  
### <a name="sample-query-3-selecting-columns-from-a-nested-table"></a>Beispielabfrage 3: Auswählen von Spalten einer geschachtelten Tabelle  
 Die folgende Beispielabfrage gibt die Namen der Kunden zurück, die als Trainingsfälle des Modells verwendet wurden. Für jeden Kunden gibt die Abfrage auch eine geschachtelte Tabelle zurück, die die Kaufdetails enthält. Obwohl das Modell die `ProductName` Spalte enthält, verwendet das Modell nicht den Wert der `ProductName` Spalte. Das Modell überprüft nur, ob das Produkt zu einem regulären ( `NOT``OnSale` ) Preis gekauft wurde. Diese Abfrage gibt nicht nur den Produktnamen zurück, sondern auch die erworbene Menge, die nicht im Modell enthalten ist.  
  
```  
SELECT CustomerName,    
(SELECT ProductName, StructureColumn('Quantity')FROM Products)   
FROM MyModel.CASES  
```  
  
 Beachten Sie, dass sowohl die `ProductName`-Spalte als auch die `Quantity`-Spalte nur dann zurückgegeben werden, wenn Drillthrough für das Miningmodell aktiviert ist.  
  
### <a name="sample-query-4-filtering-on-and-returning-nested-table-columns"></a>Beispielabfrage 4: Filtern auf und Zurückgeben von geschachtelten Tabellenspalten  
 Die folgende Beispielabfrage gibt die Fallspalten und die Spalten der geschachtelten Tabelle zurück, die zwar in der Miningstruktur, nicht aber im Modell enthalten sind. Das Modell wurde durch Filtern bereits auf `OnSale`-Produkte beschränkt. Die folgende Abfrage wendet zusätzlich noch einen Filter auf die `Quantity`-Spalte der Miningstruktur an:  
  
```  
SELECT CustomerName, Age, StructureColumn('Occupation'),   
(SELECT ProductName, StructureColumn('Quantity') FROM Products)   
FROM MyModel.CASES   
WHERE EXISTS (SELECT * FROM Products WHERE StructureColumn('Quantity')>1)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
