---
title: LookupSet-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f24c78e82d437ab7e2147122c5065f0b7274d5e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105229"
---
# <a name="lookupset-function-report-builder-and-ssrs"></a>LookupSet-Funktion (Berichts-Generator und SSRS)
  Gibt den Satz der übereinstimmenden Werte für den angegebenen Namen aus einem Dataset mit Name-Wert-Paaren zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a>Parameter  
 *source_expression*  
 (`Variant`) Ein Ausdruck, der im aktuellen Bereich ausgewertet wird und der den zu suchenden Namen oder Schlüssel angibt. Beispiel: `=Fields!ID.Value`.  
  
 *destination_expression*  
 (`Variant`) Ein Ausdruck, der für jede Zeile in einem Dataset ausgewertet wird und der den Namen oder den Schlüssel für die Übereinstimmung angibt. Beispiel: `=Fields!CustomerID.Value`.  
  
 *result_expression*  
 (`Variant`) Ein Ausdruck, der für die Zeile im Dataset ausgewertet wird, in der *source_expression* = *destination_expression*, und der den abzurufenden Wert angibt. Beispiel: `=Fields!PhoneNumber.Value`.  
  
 *Dataset (dataset)*  
 Eine Konstante, die den Namen eines Datasets im Bericht angibt. Beispiel: "ContactInformation".  
  
## <a name="return"></a>Rückgabewert  
 Gibt einen Wert vom Typ `VariantArray` zurück; gibt `Nothing` zurück, wenn keine Übereinstimmung vorhanden ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie für ein Name-Wert-Paar, für das eine 1:n-Beziehung vorhanden ist, einen Satz von Werten mithilfe von `LookupSet` aus dem angegebenen Dataset ab. Beispiel: Für einen Kundenbezeichner in einer Tabelle können Sie alle zugeordneten Telefonnummern dieses Kunden aus einem Dataset, das nicht an den Datenbereich gebunden ist, mithilfe von `LookupSet` abrufen.  
  
 Mit `LookupSet` wird Folgendes ausgeführt:  
  
-   Der Quellausdruck wird im aktuellen Bereich ausgewertet.  
  
-   Der Zielausdruck wird für jede Zeile des angegebenen Datasets ausgewertet, nachdem Filter angewendet wurden, und zwar anhand der Sortierung des angegebenen Datasets.  
  
-   Für jede Übereinstimmung von Quellausdruck und Zielausdruck wird der Ergebnisausdruck für diese Zeile im Dataset ausgewertet.  
  
-   Der Satz von Ergebnisausdruckswerten wird zurückgegeben.  
  
 Verwenden Sie die [Lookup-Funktion (Berichts-Generator und SSRS)](report-builder-functions-lookup-function.md), um einen einzelnen Wert aus einem Dataset mit Name-Wert-Paaren für einen angegebenen Namen abzurufen, wenn eine 1:1-Beziehung besteht. Um einen `Lookup` Satz von Werten aufzurufen, verwenden Sie die [Multilookup-Funktion &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-multilookup-function.md).  
  
 Es gelten folgende Einschränkungen:  
  
-   `LookupSet`wird ausgewertet, nachdem alle Filter Ausdrücke angewendet wurden.  
  
-   Nur eine Suchebene wird unterstützt. Ein Quell-, Ziel- oder Ergebnisausdruck kann keinen Verweis auf eine Suchfunktion einschließen.  
  
-   Quell- und Zielausdrücke müssen den gleichen Datentyp ergeben.  
  
-   Quell-, Ziel- und Ergebnisausdrücke können keine Verweise auf Berichts- oder Gruppenvariablen einschließen.  
  
-   `LookupSet` kann nicht als Ausdruck für die folgenden Berichtselemente verwendet werden:  
  
    -   Dynamische Verbindungszeichenfolgen für eine Datenquelle.  
  
    -   Berechnete Felder in einem Dataset.  
  
    -   Abfrageparameter in einem Dataset.  
  
    -   Filter in einem Dataset.  
  
    -   Berichtsparameter.  
  
    -   Die Eigenschaft „Report.Language“.  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Beispiel  
 Nehmen Sie im folgenden Beispiel an, dass die Tabelle an ein Dataset gebunden ist, das einen Vertriebsgebietbezeichner "TerritoryGroupID" enthält. Ein separates Dataset mit dem Namen "Stores" enthält die Liste aller Läden in einem Gebiet und schließt den Gebietsbezeichner "ID" sowie den Namen des Ladens "StoreName" ein.  
  
 Im folgenden Ausdruck vergleicht `LookupSet` für jede Zeile im Dataset "Stores" den Wert "TerritoryGroupID" mit "ID". Für jede Übereinstimmung wird dem Resultset der Wert des Felds "StoreName" für diese Zeile hinzugefügt.  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## <a name="example"></a>Beispiel  
 Da `LookupSet` eine Sammlung von Objekten zurückgibt, können Sie den Ergebnisausdruck nicht direkt in einem Textfeld anzeigen. Sie können die Werte der Objekte in der Sammlung als Zeichenfolge verketten.  
  
 Verwenden Sie die [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Funktion `Join`, um aus einem Satz von Objekten eine Zeichenfolge mit Trennzeichen zu erstellen. Verwenden Sie ein Komma als Trennzeichen, um die Objekte an einer einzelnen Zeile zu kombinieren. In einigen Renderern könnten Sie einen [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Zeilenvorschub (`vbCrLF`) als Trennzeichen verwenden, um jeden Wert auf einer neuen Zeile aufzulisten.  
  
 Der folgende Ausdruck verwendet `Join` , wenn er als Value-Eigenschaft für ein Textfeld verwendet wird, um eine Liste zu erstellen.  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## <a name="example"></a>Beispiel  
 Für Textfelder, die nur wenige Male gerendert werden, könnten Sie wahlweise benutzerdefinierten Code hinzufügen, um HTML-Code zum Anzeigen von Werten in einem Textfeld zu generieren. HTML-Code in einem Textfeld erfordert zusätzliche Verarbeitung, deshalb ist dies nicht empfehlenswert für ein Textfeld, das Tausende Male gerendert wird.  
  
 Kopieren Sie die folgenden [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Funktionen in einen Codeblock in einer Berichtsdefinition. **MakeList** erstellt aus dem Objektarray, das in *result_expression* zurückgegeben wird, mithilfe von HTML-Tags eine ungeordnete Liste. **Length** gibt die Anzahl der Elemente im Objektarray zurück.  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## <a name="example"></a>Beispiel  
 Um den HTML-Code zu generieren, müssen Sie die Funktion aufrufen. Fügen Sie den folgenden Ausdruck in die Value-Eigenschaft für das Textfeld ein, und legen Sie den Markuptyp für den Text auf HTML fest. Weitere Informationen finden Sie unter [Hinzufügen von HTML in einem Bericht (Berichts-Generator und SSRS)](add-html-into-a-report-report-builder-and-ssrs.md).  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
