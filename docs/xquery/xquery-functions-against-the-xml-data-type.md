---
title: XQuery-Funktionen für den Xml-Datentyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6a7527fe3fb4e250e0cf884e17ee6e53eeba7b8b
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56042951"
---
# <a name="xquery-functions-against-the-xml-data-type"></a>XQuery-Funktionen für den xml-Datentyp
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In diesem Thema und seine Unterthemen beschreiben die Funktionen Sie beim Angeben der XQuery-Abfrage für können die **Xml** -Datentyp. Die W3C-Spezifikationen finden Sie unter [ http://www.w3.org/TR/2004/WD-xpath-functions-20040723 ](https://go.microsoft.com/fwlink/?LinkId=4873).  
  
 Die XQuery-Funktionen gehören zu den http://www.w3.org/2004/07/xpath-functions Namespace. Die W3C-Spezifikationen verwenden das "fn:"-Namespacepräfix, um diese Funktionen zu beschreiben. Sie brauchen das "fn:"-Namespacepräfix nicht explizit anzugeben, wenn Sie die Funktionen verwenden. Daher, sowie auch zur besseren Lesbarkeit, werden die Namespacepräfixe in dieser Dokumentation im Allgemeinen weggelassen.  
  
 Die folgende Tabelle enthält die XQuery-Funktionen, die für unterstützt werden die **Xml**-Datentyp.  
  
|Kategorie|Funktionsname|  
|--------------|-------------------|  
|[Funktionen für numerische Werte](https://msdn.microsoft.com/library/d5740a32-b174-43b9-b64d-1cc6edc50cff)|[ceiling](../xquery/numeric-values-functions-ceiling.md)|  
||[floor](../xquery/numeric-values-functions-floor.md)|  
||[round](../xquery/numeric-values-functions-round.md)|  
|[XQuery-Funktionen für Zeichenfolgenwerte](https://msdn.microsoft.com/library/2dccefef-5d90-4f56-bda7-4c1954d8a730)|[concat](../xquery/functions-on-string-values-concat.md)|  
||[Enthält](../xquery/functions-on-string-values-contains.md)|  
||[substring](../xquery/functions-on-string-values-substring.md)|  
||[lower-case-Funktion &#40;XQuery&#41;](../xquery/functions-on-string-values-lower-case.md)|  
||[string-length](../xquery/functions-on-string-values-string-length.md)|  
||[Upper-Case-Funktion &#40;XQuery&#41;](../xquery/functions-on-string-values-upper-case.md)|  
|Funktionen für boolesche Werte|[not](../xquery/functions-on-boolean-values-not-function.md)|  
|[Funktionen für Knoten](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)|[number](../xquery/functions-on-nodes-number.md)|  
||[Local-Name-Funktion (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[Namespace-Uri-Funktion (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[Kontextfunktionen](https://msdn.microsoft.com/library/f7d8af33-9de9-450c-a667-23dee3129b5f)|[last](../xquery/context-functions-last-xquery.md)|  
||[position](../xquery/context-functions-position-xquery.md)|  
|[Funktionen für Sequenzen](https://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)|[empty](../xquery/functions-on-sequences-empty.md)|  
||[distinct-values](../xquery/functions-on-sequences-distinct-values.md)|  
||[ID-Funktion (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[Aggregatfunktionen &#40;XQuery&#41;](https://msdn.microsoft.com/library/be647ef1-291e-4a5d-ab18-07c759efe176)|[count](../xquery/aggregate-functions-count.md)|  
||[avg](../xquery/aggregate-functions-avg.md)|  
||[min](../xquery/aggregate-functions-min.md)|  
||[max](../xquery/aggregate-functions-max.md)|  
||[sum](../xquery/aggregate-functions-sum.md)|  
|[Konstruktorfunktionen &#40;XQuery&#41;](../xquery/constructor-functions-xquery.md)|[Konstruktorfunktionen](../xquery/constructor-functions-xquery.md)|  
|[Data Accessor Functions (Data Accessor-Funktionen)](../xquery/data-accessor-functions.md)|[Zeichenfolge](../xquery/data-accessor-functions-string-xquery.md)|  
||[data](../xquery/data-accessor-functions-data-xquery.md)|  
|[Boolesche Konstruktorfunktionen &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)|[True-Funktion (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[false-Funktion (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Functions Related to QNames sich &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)|[expanded-QName (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[local-name-from-QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[namespace-uri-from-QName (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[XQuery-Erweiterung für SQL Server-Funktionen](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)|[SQL:Column()-Funktion (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[SQL:Variable()-Funktion (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Datentypmethoden](../t-sql/xml/xml-data-type-methods.md)   
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XML-Daten &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  
