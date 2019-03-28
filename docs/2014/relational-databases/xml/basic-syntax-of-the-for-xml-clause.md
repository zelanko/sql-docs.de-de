---
title: Basissyntax der FOR XML-Klausel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- BINARY BASE64 directive
- ROOT directive
- FOR XML clause, BINARY BASE64 directive
- FOR XML clause, syntax
- FOR XML clause, ROOT directive
ms.assetid: df19ecbf-d28e-4e9c-aaa3-700f8bbd3be4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bb04374ede05406fdf6d273a76a246bb35f5dac
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537742"
---
# <a name="basic-syntax-of-the-for-xml-clause"></a>Basissyntax der FOR XML-Klausel
  Der FOR XML-Modus kann RAW, AUTO, EXPLICIT oder PATH lauten. Er bestimmt die Form des erhaltenen XML.  
  
> [!IMPORTANT]  
>  Die XMLDATA-Direktive zur FOR XML-Option ist veraltet. Verwenden Sie XSD-Generierung für RAW- und AUTO-Modus. Es gibt keinen Ersatz für die XMLDATA-Direktive im EXPLICIT-Modus. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Im Folgenden wird die Basissyntax der [FOR-Klausel (Transact-SQL) beschrieben](/sql/t-sql/queries/select-for-clause-transact-sql):  
  
```  
[ FOR { BROWSE | <XML> } ]  
<XML> ::=  
XML   
    {   
      { RAW [ ('ElementName') ] | AUTO }   
        [   
           <CommonDirectives>   
           [ , { XMLDATA | XMLSCHEMA [ ('TargetNameSpaceURI') ]} ]   
           [ , ELEMENTS [ XSINIL | ABSENT ]   
        ]  
      | EXPLICIT   
        [   
           <CommonDirectives>   
           [ , XMLDATA ]   
        ]  
      | PATH [ ('ElementName') ]   
        [   
           <CommonDirectives>   
           [ , ELEMENTS [ XSINIL | ABSENT ] ]  
        ]  
     }   
  
 <CommonDirectives> ::=   
   [ , BINARY BASE64 ]  
   [ , TYPE ]  
   [ , ROOT [ ('RootName') ] ]  
```  
  
## <a name="arguments"></a>Argumente  
 RAW[('*ElementName*')]  
 Verwendet das Abfrageergebnis und wandelt jede Zeile im Resultset in ein XML-Element mit einem generischen Bezeichner (\<row />) als Elementtag um. Sie können optional einen Namen für das Zeilenelement angeben, wenn Sie diese Direktive verwenden. Das sich ergebende XML verwendet den angegebenen *ElementName* als das für jede Zeile generierte Zeilenelement. Weitere Informationen finden Sie unter [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md).  
  
 AUTO  
 Gibt Abfrageergebnisse in einer einfachen, geschachtelten XML-Struktur zurück. Jede Tabelle in der FROM-Klausel, aus der mindestens eine Spalte in der SELECT-Klausel aufgeführt ist, wird als ein XML-Element dargestellt. Die in der SELECT-Klausel aufgelisteten Spalten werden den entsprechenden Elementattributen zugeordnet. Weitere Informationen finden Sie unter [Verwenden des AUTO-Modus mit FOR XML](use-auto-mode-with-for-xml.md).  
  
 EXPLICIT  
 Gibt an, dass die Form der sich ergebenden XML-Struktur explizit definiert wird. In diesem Modus müssen die Abfragen jedoch auf eine bestimmte Weise geschrieben werden, sodass zusätzliche Informationen über die gewünschte Schachtelung explizit angegeben werden. Weitere Informationen finden Sie unter [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md).  
  
 PATH  
 Stellt ein einfacheres Verfahren zum Mischen von Elementen und Attributen bereit und führt zusätzliche Schachtelung für die Darstellung komplexer Eigenschaften ein. Sie können Abfragen im FOR XML EXPLICIT-Modus zum Erstellen dieser Art von XML aus einem Rowset verwenden, der PATH-Modus stellt jedoch eine einfachere Alternative zu den möglicherweise aufwendigen Abfragen im EXPLICIT-Modus bereit. Der PATH-Modus ermöglicht in Kombination mit der Möglichkeit, verschachtelte FOR XML-Abfragen zu schreiben und die TYPE-Direktive zum Zurückgeben von Instanzen des Typs **xml** zu verwenden, das Schreiben von Abfragen mit geringerer Komplexität. Er bietet eine Alternative zum Schreiben der meisten Abfragen im EXPLICIT-Modus. Standardmäßig generiert der PATH-Modus einen \<row>-Elementwrapper für jede Zeile im Resultset. Optional können Sie einen Elementnamen angeben. Wenn Sie einen Elementnamen angeben, wird der angegebene Name als Wrapperelementname verwendet. Bei einer leeren Zeichenfolge (FOR XML PATH ('')) wird kein Wrapperelement generiert. Weitere Informationen finden Sie unter [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md).  
  
 XMLDATA  
 Gibt an, dass ein XML XDR-Inlineschema zurückgegeben werden soll. Das Schema wird dem Dokument als Inlineschema vorangestellt. Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md).  
  
 XMLSCHEMA  
 Gibt ein W3C XML-Inlineschema (XSD) zurück. Optional können Sie einen Zielnamespace-URI angeben, wenn Sie diese Direktive angeben. Auf diese Weise wird der angegebene Namespace im Schema zurückgegeben. Weitere Informationen finden Sie unter [Generieren eines XSD-Inlineschemas](generate-an-inline-xsd-schema.md). Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md).  
  
 ELEMENTS  
 Wenn die Option ELEMENTS angegeben ist, werden die Spalten als Teilelemente zurückgegeben. Andernfalls werden sie XML-Attributen zugeordnet. Diese Option wird nur in den Modi RAW, AUTO und PATH unterstützt. Optional können Sie XSINIL oder ABSENT angeben, wenn Sie diese Direktive angeben. XSINIL gibt an, dass ein Element, dessen **xsi:nil** -Attribut auf True festgelegt ist, für NULL-Spaltenwerte erstellt wird. Standardmäßig werden keine Elemente für NULL-Werte erstellt. Dies gilt auch, wenn ABSENT zusammen mit ELEMENTS angegeben wird. Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md) und unter [Verwenden des AUTO-Modus mit FOR XML](use-auto-mode-with-for-xml.md).  
  
 BINARY BASE64  
 Wenn die Option BINARY Base64 angegeben ist, werden alle von der Abfrage zurückgegebenen Binärdaten im Base64-codierten Format dargestellt. Zum Abrufen von Binärdaten mithilfe des Modus RAW oder EXPLICIT muss diese Option angegeben werden. Standardmäßig werden Binärdaten im AUTO-Modus als Verweis zurückgegeben. Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md).  
  
 TYPE  
 Gibt an, dass die Abfrage die Ergebnisse als **xml** -Typ zurückgibt. Weitere Informationen finden Sie unter [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md).  
  
 ROOT [('*RootName*')]  
 Gibt an, dass ein einzelnes Element der obersten Ebene dem als Ergebnis zurückgegebenen XML-Dokument hinzugefügt wird. Optional können Sie den zu generierenden Stammelementnamen angeben. Der Standardwert lautet "root".  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)   
 [Verwenden des AUTO-Modus mit FOR XML](use-auto-mode-with-for-xml.md)   
 [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md)   
 [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)  
  
  
