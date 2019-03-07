---
title: nodes()-Methode (XML-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nodes() method
- nodes method
ms.assetid: 7267fe1b-2e34-4213-8bbf-1c953822446c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c80985d6c69cc1f62e82ae26cbf4bc841501e9d
ms.sourcegitcommit: 71913f80be0cb6f8d3af00c644ee53e3aafdcc44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56590385"
---
# <a name="nodes-method-xml-data-type"></a>nodes()-Methode (xml-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Die **nodes()**-Methode ist nützlich, wenn Sie eine Instanz des **XML**-Datentyps in relationale Daten aufteilen möchten. Damit können Sie Knoten identifizieren, die einer neuen Zeile zugeordnet werden.  
  
Jede Instanz des **XML**-Datentyps verfügt über einen implizit bereitgestellten Kontextknoten. Für die in einer Spalte oder Variablen gespeicherte XML-Instanz ist dieser Knoten der Dokumentknoten. Der Dokumentknoten ist der implizite Knoten auf der obersten Ebene jeder Instanz des **XML**-Datentyps.  
  
Das Ergebnis der **nodes()**-Methode ist ein Rowset, das logische Kopien der ursprünglichen XML-Instanzen enthält. In diesen logischen Kopien ist der Kontextknoten jeder Zeileninstanz auf einen der Knoten festgelegt, der mit dem Abfrageausdruck identifiziert wird, sodass nachfolgende Abfragen relativ zu diesen Kontextknoten navigieren können. This way, later queries can navigate relative to these context nodes.  
  
Sie können mehrere Werte aus dem Rowset abrufen. Sie können die **value()**-Methode beispielsweise auf das Rowset anwenden, das von **nodes()** zurückgegeben wurde, und mehrere Werte aus der ursprünglichen XML-Instanz abrufen. Die **value()**-Methode gibt nur einen Wert zurück, wenn sie auf die XML-Instanz angewendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```sql
  
nodes (XQuery) as Table(Column)  
```  
  
## <a name="arguments"></a>Argumente  
*XQuery*  
Ist ein Zeichenfolgenliteral, ein XQuery-Ausdruck. Wenn der Abfrageausdruck Knoten konstruiert, werden diese konstruierten Knoten im resultierenden Rowset verfügbar gemacht. Wenn der Abfrageausdruck eine leere Sequenz ergibt, ist auch das Rowset leer. Wenn der Abfrageausdruck statisch eine Sequenz ergibt, die anstelle von Knoten atomare Werte enthält, wird ein statischer Fehler ausgelöst.  
  
*Tabelle*(*Spalte*)  
Ist der Tabellenname und der Spaltenname für das resultierende Rowset.  
  
## <a name="remarks"></a>Remarks  
Nehmen Sie beispielsweise an, es ist die folgende Tabelle vorhanden:  
  
```sql
T (ProductModelID int, Instructions xml)  
```  
  
In der Tabelle ist das folgende Produktionsanweisungsdokument gespeichert. Es ist nur ein Fragment dargestellt. Beachten Sie, dass es im Dokument drei Produktionsstandorte gibt.  
  
```sql
<root>  
  <Location LocationID="10"...>  
     <step>...</step>  
     <step>...</step>  
      ...  
  </Location>  
  <Location LocationID="20" ...>  
       ...  
  </Location>  
  <Location LocationID="30" ...>  
       ...  
  </Location>  
</root>  
```  
  
Ein Aufruf der `nodes()`-Methode mit dem Abfrageausdruck `/root/Location` würde ein Rowset mit drei Zeilen zurückgeben, die jeweils eine logische Kopie des ursprünglichen XML-Dokuments enthalten, und bei dem das Kontextelement auf einen der `<Location>`-Knoten festgelegt ist:  
  
```sql
Product  
ModelID      Instructions  
----------------------------------  
1       <root>  
             <Location LocationID="20" ... />  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
             <Location LocationID="20" ... />  
             </root>  
```  
  
Anschließend können Sie dieses Rowset mithilfe von **XML**-Datentypmethoden abfragen. Die folgende Abfrage extrahiert die Teilstruktur des Kontextelements für jede generierte Zeile:  
  
```sql
SELECT T2.Loc.query('.')  
FROM   T  
CROSS APPLY Instructions.nodes('/root/Location') as T2(Loc)   
```  
  
Hier ist das Ergebnis:  
  
```sql
ProductModelID  Instructions  
----------------------------------  
1        <Location LocationID="10" ... />  
1        <Location LocationID="20" ... />  
1        <Location LocationID="30" .../>  
```  
  
Das zurückgegebene Rowset hat die Typinformationen beibehalten. Sie können **XML**-Datentypmethoden wie z.B. **query()**, **value()**, **exist()** und **nodes()** auf das Ergebnis einer **nodes()**-Methode anwenden. Allerdings ist es nicht möglich, die **modify()**-Methode zum Ändern der XML-Instanz anzuwenden.  
  
Außerdem kann der Kontextknoten im Rowset nicht materialisiert werden. Das bedeutet, dass Sie ihn nicht in einer SELECT-Anweisung verwenden können. Allerdings können Sie ihn in IS NULL und COUNT(*) verwenden.  
  
Die Szenarien für die Verwendung der **nodes()**-Methode sind die gleichen wie für die Verwendung von [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md), womit eine Rowsetsicht der XML bereitgestellt wird. Allerdings müssen Sie keine Cursor verwenden, wenn Sie die **nodes()**-Methode für eine Tabelle verwenden, die mehrere Zeilen mit XML-Dokumenten enthält.  
  
Das von der **nodes()**-Methode zurückgegebene Rowset ist unbenannt. Deshalb muss es per Alias explizit benannt werden.  
  
Die **nodes()**-Funktion kann nicht direkt auf die Ergebnisse einer benutzerdefinierten Funktion angewendet werden. Zum Verwenden der **nodes()**-Funktion mit dem Ergebnis einer skalaren benutzerdefinierten Funktion haben Sie folgende Möglichkeiten:
 
- Zuweisen des Ergebnisses der benutzerdefinierten Funktion zu einer Variablen
- Verwenden Sie eine abgeleitete Tabelle, um dem Rückgabewert der benutzerdefinierten Funktion einen Spaltenalias zuzuweisen, und verwenden Sie dann `CROSS APPLY`, um im Alias eine Wahl zu treffen.  
  
Im folgenden Beispiel wird eine Methode gezeigt, um mithilfe von `CROSS APPLY` eine Auswahl aus dem Ergebnis einer benutzerdefinierten Funktion zu treffen.  
  
```sql
USE AdventureWorks;  
GO  
  
CREATE FUNCTION XTest()  
RETURNS xml  
AS  
BEGIN  
RETURN '<document/>';  
END;  
GO  
  
SELECT A2.B.query('.')  
FROM  
(SELECT dbo.XTest()) AS A1(X)   
CROSS APPLY X.nodes('.') A2(B);  
GO  
  
DROP FUNCTION XTest;  
GO  
```  
  
## <a name="examples"></a>Beispiele  
  
### <a name="using-nodes-method-against-a-variable-of-xml-type"></a>Verwenden der nodes()-Methode für eine Variable des xml-Typs  
Im folgenden Beispiel gibt es ein XML-Dokument, das ein <`Root`>-Element der obersten Ebene und drei untergeordnete <`row`>-Elemente enthält. Die Abfrage verwendet die `nodes()`-Methode, um für jedes <`row`>-Element einen eigenen Kontextknoten festzulegen. Die `nodes()`-Methode gibt ein Rowset mit drei Zeilen zurück. Jede Zeile enthält eine logische Kopie des XML-Originaldokuments, wobei jeder Kontextknoten ein anderes <`row`>-Element im Originaldokument identifiziert.  
  
Die Abfrage gibt dann den Kontextknoten aus jeder Zeile zurück:  
  
```sql
DECLARE @x xml   
SET @x='<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>'  
SELECT T.c.query('.') AS result  
FROM   @x.nodes('/Root/row') T(c)  
GO  
```  
  
Im folgenden Beispielergebnis gibt die Abfragemethode das Kontextelement und dessen Inhalt zurück:  
  
```sql
<row id="1"><name>Larry</name><oflw>some text</oflw></row>  
<row id="2"><name>moe</name></row>  
<row id="3"/>  
```  
  
Durch das Anwenden des übergeordneten Accessors auf den Kontextknoten wird das <`Root`>-Element für alle drei untergeordneten Elemente zurückgegeben:  
  
```sql
SELECT T.c.query('..') AS result  
FROM   @x.nodes('/Root/row') T(c)  
go  
```  
  
Hier ist das Ergebnis:  
  
```sql
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
```  
  
### <a name="specifying-the-nodes-method-against-a-column-of-xml-type"></a>Angeben der nodes()-Methode für eine Spalte des xml-Typs  
In diesem Beispiel werden die Produktionsanweisungen für Fahrräder verwendet und in der Instructions-Spalte vom Typ **XML** der **ProductModel**-Tabelle gespeichert.  
  
Im folgenden Beispiel wird die `nodes()`-Methode für die `Instructions`-Spalte vom Typ **XML** in der `ProductModel`-Tabelle angegeben.  
  
Die `nodes()`-Methode legt die <`Location`>-Elemente als Kontextknoten fest, indem sie den `/MI:root/MI:Location`-Pfad angibt. Das resultierende Rowset enthält logische Kopien des Originaldokuments, und zwar für jeden <`Location`>-Knoten im Dokument eine Kopie. Dabei ist der Kontextknoten auf das <`Location`>-Element festgelegt. Als Ergebnis gibt die `nodes()`-Funktion eine Gruppe von <`Location`>-Kontextknoten zurück.  
  
Die `query()`-Methode für dieses Rowset fordert `self::node` an und gibt das `<Location>`-Element in jeder Zeile zurück.  
  
In diesem Beispiel legt die Abfrage jedes <`Location`>-Element als Kontextknoten im Produktionsanweisungsdokument eines bestimmten Produktmodells fest. Sie können diese Kontextknoten verwenden, um Werte wie z.B. die folgenden abzurufen:  
  
- Suchen von Positions-IDs in jeder <`Location`>  
  
- Abrufen von Herstellungsschritten (untergeordnete <`step`> -Elemente) in jeder <`Location`>  
  
Diese Abfrage gibt in der `'.'`-Methode das Kontextelement zurück, in dem die abgekürzte Syntax `self::node()` für `query()` angegeben ist.  
  
Beachten Sie Folgendes:
  
- Die `nodes()`-Methode wird auf die Instructions-Spalte angewendet und gibt das Rowset `T (C)` zurück. Dieses Rowset enthält logische Kopien des ursprünglichen Produktionsanweisungsdokuments mit `/root/Location` als Kontextelement.  
  
- CROSS APPLY wendet `nodes()` auf jede Zeile in der `Instructions`-Tabelle an und gibt nur die Zeilen zurück, die ein Resultset erzeugen.  
  
    ```sql  
    SELECT C.query('.') as result  
    FROM Production.ProductModel  
    CROSS APPLY Instructions.nodes('  
    declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /MI:root/MI:Location') as T(C)  
    WHERE ProductModelID=7  
    ```  
  
  Hier ist das Teilergebnis:  
  
    ```sql
    <MI:Location LocationID="10"  ...>  
       <MI:step ... />  
          ...  
    </MI:Location>  
    <MI:Location LocationID="20"  ... >  
        <MI:step ... />  
          ...  
    </MI:Location>  
    ...  
    ```  
  
### <a name="applying-nodes-to-the-rowset-returned-by-another-nodes-method"></a>Anwenden von nodes() auf das Rowset, das von einer anderen nodes()-Methode zurückgegeben wurde  
Mit dem folgenden Code werden aus den XML-Dokumenten die Produktionsanweisungen in der `Instructions`-Spalte der `ProductModel`-Tabelle abgefragt. Die Abfrage gibt ein Rowset zurück, das die Produktmodell-ID, die Produktionsstandorte und die Fertigungsschritte enthält.  
  
Beachten Sie Folgendes:  
  
- Die `nodes()`-Methode wird auf die `Instructions`-Spalte angewendet und gibt das Rowset `T1 (Locations)` zurück. Dieses Rowset enthält logische Kopien des Originaldokuments für Produktionsanweisungen, wobei das `/root/Location`-Element als Elementkontext verwendet wird.  
  
- `nodes()` wird auf das `T1 (Locations)`-Rowset angewendet und gibt das Rowset `T2 (steps)` zurück. Dieses Rowset enthält logische Kopien des Originaldokuments für Produktionsanweisungen, wobei das `/root/Location/step`-Element als Elementkontext verwendet wird.  
  
```sql
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO         
```  
  
Hier ist das Ergebnis:  
  
```sql
ProductModelID LocID Step         
----------------------------         
7      10   <step ... />         
7      10   <step ... />         
...         
7      20   <step ... />         
7      20   <step ... />         
7      20   <step ... />         
...         
```  
  
Die Abfrage deklariert das `MI`-Präfix zweimal. Sie können stattdessen `WITH XMLNAMESPACES` verwenden, um das Präfix einmal zu deklarieren und es dann in der Abfrage zu verwenden:  
  
```sql
WITH XMLNAMESPACES (  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions'  AS MI)  
  
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO    
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Hinzufügen von Namespaces zu Abfragen mit WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
[Erstellen von Instanzen der XML-Daten](../../relational-databases/xml/create-instances-of-xml-data.md)   
[xml Data Type Methods (xml-Datentypmethoden)](../../t-sql/xml/xml-data-type-methods.md)  
  
  
