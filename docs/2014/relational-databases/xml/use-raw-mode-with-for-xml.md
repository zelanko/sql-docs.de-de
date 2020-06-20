---
title: Verwenden des RAW-Modus mit FOR XML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: rothja
ms.author: jroth
ms.openlocfilehash: b2908a98336ec8a6e12029ad471f22a33d7a4dcf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061190"
---
# <a name="use-raw-mode-with-for-xml"></a>Verwenden des RAW-Modus mit FOR XML
  Der RAW-Modus wandelt jede Zeile im Resultset der Abfrage in ein XML-Element um, das über den generischen Bezeichner \<row> oder den optional bereitgestellten Elementnamen verfügt. Standardmäßig wird jeder Spaltenwert im Rowset, der nicht NULL ist, einem Attribut des-Elements zugeordnet \<row> . Wenn die Elements-Direktive der for XML-Klausel hinzugefügt wird, wird jeder Spaltenwert einem Unterelement des- \<row> Elements zugeordnet. Zusammen mit der ELEMENTS-Direktive können Sie optional die Option XSINIL angeben, um NULL-Spaltenwerte im Resultset einem Element zuzuordnen, das das Attribut xsi:nil=`"`true`"`besitzt.  
  
 Sie können ein Schema für das sich ergebende XML anfordern. Wenn Sie die Option XMLDATA angeben, wird ein Inline-XDR-Schema zurückgegeben. Wenn Sie die Option XMLSCHEMA angeben, wird ein Inline-XSD-Schema zurückgegeben. Das Schema wird zu Beginn der Daten angezeigt. Im Resultset wird der Verweis auf den Schemanamespace für jedes Element der obersten Ebene wiederholt.  
  
 Die Option BINARY BASE64 muss in der FOR XML-Klausel angegeben werden, um die Binärdaten im Base64-codierten Format zurückzugeben. Im RAW-Modus führt das Abrufen von Binärdaten ohne Angabe der Option BINARY BASE64 zu einem Fehler.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Dieser Abschnitt enthält folgende Beispiele:  
  
-   [Beispiel: Abrufen von Produktmodellinformationen als XML](example-retrieving-product-model-information-as-xml.md)  
  
-   [Beispiel: Angeben von XSINIL mit der ELEMENTS-Direktive](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [Beispiel: Anfordern von Schemas als Ergebnisse mithilfe der Optionen XMLDATA und XMLSCHEMA](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [Beispiel: Abrufen von Binärdaten](example-retrieving-binary-data.md)  
  
-   [Beispiel: Umbenennen des &#60;row&#62;-Elements](example-renaming-the-row-element.md)  
  
-   [Beispiel: Angeben eines Stammelements für das durch FOR XML generierte XML](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [Beispiel: Abfragen von Spalten des Typs XML](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Namespaces zu Abfragen mit WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Verwenden des AUTO-Modus mit FOR XML](use-auto-mode-with-for-xml.md)   
 [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md)   
 [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
