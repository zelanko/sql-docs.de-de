---
title: Konvertieren von mit Anmerkungen in XDR-Schemas in gleichbedeutende XSD-Schemas (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce9e49aa31dea2a08283fdea1829f6565ad52fa4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63131537"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a>Konvertieren von XDR-Schemas mit Anmerkungen in gleichbedeutende XSD-Schemas (SQLXML 4.0)
  Die XSD-Sprache (XML Schema Definition) ist Nachfolger der XDR-Sprache (XML-Data Reduced) für Schemadefinitionen. Nachdem XSD ab [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 unterstützt wird, wird davon ausgegangen, dass neue Schemas mit Anmerkungen mit XSD erstellt werden. SQLXML 4.0 umfasst ein Konvertierungstool für die Umwandlung von XDR in XSD, das die Konvertierung vorhandener XDR-Schemas mit Anmerkungen in entsprechende XSD-Schemas erleichtern soll.  
  
> [!IMPORTANT]  
>  Verwenden Sie dieses Tool nur, wenn Sie XDR-Schemas mit Anmerkungen in mit SQLXML 4.0 zu verwendendes XSD konvertieren möchten. Dies ist kein universelles XDR-in-XSD-Konvertierungstool. Die konvertierten XSD-Schemas verhalten sich unter Umständen anders als die ursprünglichen XDR-Schemas, wenn sie in anderen Umgebungen verwendet werden.  
  
 Wenn in der XDR-Eingabedatei die Codierung innerhalb der XML-Deklaration angegeben wird, dann wird diese Codierung für die generierte XSD-Ausgabedatei verwendet.  
  
 Das Konvertierungstool (Cvtschema.exe) wird im Ordner Programme\SQLXML 4.0\bin installiert und an der Eingabeaufforderung ausgeführt.  
  
 Das ist die allgemeine Syntax:  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 Erläuterungen:  
  
 XDRFileName  
 Der Name der XDR-Datei, die in XSD konvertiert werden soll. Das Tool liest die XDR-Eingabedatei und erstellt im aktuellen Arbeitsverzeichnis eine XSD-Ausgabedatei. Wenn die Eingabedatei über die Namenerweiterung .XDR oder .XML verfügt, wird eine XSD-Ausgabedatei gleichen Namens mit der Erweiterung .XSD erstellt. Wenn die Eingabedatei eine andere Namenerweiterung als .XDR oder .XML hat (oder die Erweiterung fehlt), wird eine Ausgabedatei erstellt, die den gleichen Namen wie die Eingabedatei trägt, und dieser Dateiname wird zusätzlich mit der Erweiterung .XSD versehen. Wenn der Name der XDR-Eingabedatei beispielsweise SampleFile.abc lautet, wird das resultierende XSD unter dem Namen SampleFile.abc.xsd gespeichert.  
  
 -y  
 (Optional) Überschreibt die vorhandene XSD-Datei mit der XSD-Datei, die vom Konvertierungstool generiert wird. Wenn dieses Flag nicht angegeben wird, fordert Sie das Tool auf anzugeben, ob die vorhandene XSD-Datei überschrieben werden soll, und gibt Ihnen die Möglichkeit, den Namen der Ausgabedatei zu ändern.  
  
 -w  
 (Optional) Gibt im Konvertierungsprozess des Tools generierte Warnungen zurück, die nicht schwerwiegend sind. Standardmäßig zeigt das Tool nur Meldungen für schwerwiegende Fehler an.  
  
 -?  
 Gibt eine Liste der Optionen, die Sie für `cvtschema` angeben können, und Erläuterungen dieser Optionen zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnen von XSD-Datentypen zu XPath-Datentypen &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)   
 [XSD-Anmerkungen &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
