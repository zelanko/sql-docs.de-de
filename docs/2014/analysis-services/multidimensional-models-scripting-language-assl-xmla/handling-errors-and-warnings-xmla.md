---
title: Behandeln von Fehlern und Warnungen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc4d145d9f64c7a8b0761b6006aab9ede1184aa1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226350"
---
# <a name="handling-errors-and-warnings-xmla"></a>Behandeln von Fehlern und Warnungen (XMLA)
  Fehlerbehandlung ist notwendig, wenn ein XML for Analysis (XMLA) [Discover](../xmla/xml-elements-methods-discover.md) oder [Execute](../xmla/xml-elements-methods-execute.md) Methodenaufruf wird nicht ausgeführt, erfolgreich ausgeführt wird, aber Fehler oder Warnungen generiert oder erfolgreich ausgeführt wurde aber Ergebnisse zurückgibt die Fehler enthalten.  
  
|Fehler|Bericht|  
|-----------|---------------|  
|Der XMLA-Methodenaufruf wird nicht ausgeführt|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt einen SOAP-Fehlernachricht mit den Details des Fehlers zurück.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von SOAP-Fehlern](#handling_soap_faults).|  
|Fehler oder Warnungen bei erfolgreichem Methodenaufruf|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält eine [Fehler](../xmla/xml-elements-properties/error-element-xmla.md) oder [Warnung](../xmla/xml-elements-properties/warning-element-xmla.md) -Element für jeden Fehler oder Warnung aus, in der [Nachrichten](../xmla/xml-elements-properties/messages-element-xmla.md) Eigenschaft der [Stamm](../xmla/xml-elements-properties/root-element-xmla.md) Element die Ergebnisse des Methodenaufrufs enthält.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von Fehlern und Warnungen](#handling_errors_and_warnings).|  
|Fehler im Ergebnis bei erfolgreichem Methodenaufruf|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält ein Inline- `error` oder `warning` -Element für den Fehler oder die Warnung bzw. in die entsprechende [Zelle](../xmla/xml-elements-properties/cell-element-xmla.md) oder [Zeile](../xmla/xml-elements-properties/row-element-xmla.md) Element der Ergebnisse des Methodenaufrufs.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von Inlinefehlern und -warnungen](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling_soap_faults"></a> Behandlung von SOAP-Fehler  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt einen SOAP-Fehler zurück, wenn die folgenden Situationen auftreten:  
  
-   Die SOAP-Nachricht, die die XMLA-Methode enthält, ist nicht wohlgeformt oder konnte nicht überprüft werden, indem die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz.  
  
-   Eine Kommunikations- oder anderer Fehler ist in Bezug auf die SOAP-Nachricht, die die XMLA-Methode enthält, aufgetreten.  
  
-   Die XMLA-Methode wurde nicht auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz ausgeführt.  
  
 Die SOAP-Fehlercodes für XMLstartA beginnen mit „XMLForAnalysis“ gefolgt von einem Punkt und dem hexadezimalen HRESULT-Ergebniscode. Beispielsweise wird ein Fehlercode von „`0x80000005`“ formatiert als „`XMLForAnalysis.0x80000005`“. Weitere Informationen über das SOAP-Fehlerformat finden Sie unter „Soap Fault in the W3C Simple Object Access Protocol (SOAP) 1.1“.  
  
### <a name="fault-code-information"></a>Fehlercodeinformationen  
 Die folgende Tabelle zeigt die XMLA-Fehlercodeinformationen, die im Detailabschnitt der SOAP-Antwort enthalten sind. Die Spalten sind die Attribute eines Fehlers im Detailabschnitt eines SOAP-Fehlers.  
  
|Spaltenname|Typ|Description|Null zulässig<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|Rückgabecode, der den Erfolg oder das Scheitern der Methode angibt. Der Hexadezimalwert muss in konvertiert werden ein `UnsignedInt` Wert.|nein|  
|`WarningCode`|`UnsignedInt`|Rückgabecode, der eine Warnbedingung angibt. Der Hexadezimalwert muss in konvertiert werden ein `UnsignedInt` Wert.|ja|  
|`Description`|`String`|Fehler- oder Warnungstext und Beschreibung, die durch die Komponente zurückgegeben werden, die den Fehler erzeugt hat.|ja|  
|`Source`|`String`|Name der Komponente, die den Fehler oder die Warnung generiert hat.|ja|  
|`HelpFile`|`String`|Pfad oder URL zur Hilfedatei oder dem Thema, das den Fehler oder die Warnung beschreibt.|ja|  
  
 <sup>1</sup> angibt, ob die Daten erforderlich sind und zurückgegeben werden müssen, oder gibt an, ob die Daten optional sind und eine null-Zeichenfolge ist zulässig, wenn die Spalte nicht anwendbar ist.  
  
 Im Folgenden finden Sie ein Beispiel für einen SOAP-Fehler, der auftrat, als ein Methodenaufruf fehlschlug:  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling_errors_and_warnings"></a> Behandeln von Fehlern und Warnungen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt die `Messages` -Eigenschaft in der `root` -Element für einen Befehl aus, wenn nach Ausführung des Befehls die folgenden Situationen auftreten:  
  
-   Die Methode selbst keine Fehler aufgetreten, aber ein Fehler aufgetreten ist, auf die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz nach der Methodenaufruf erfolgreich war.  
  
-   Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz gibt eine Warnung zurück, wenn der Befehl erfolgreich ist.  
  
 Die `Messages` -Eigenschaft folgt allen Eigenschaften, die enthalten sind die `root` -Element, und kann eine oder mehrere enthalten `Message` Elemente. Jedes `Message`-Element kann entweder ein einzelnes `error`- oder ein `warning`-Element enthalten, das entweder Fehler oder Warnungen beschreibt, die beim angegebenen Befehl aufgetreten sind.  
  
 Weitere Informationen zu Fehlern und Warnungen, die in befinden die `Messages` -Eigenschaft finden Sie unter [Messages-Element &#40;XMLA&#41;](../xmla/xml-elements-properties/messages-element-xmla.md).  
  
### <a name="handling-errors-during-serialization"></a>Behandeln von Fehlern während der Serialisierung  
 Wenn ein Fehler auftritt, nachdem die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz wurde bereits gestartet Serialisierung der Ausgabe eines erfolgreich ausgeführten Befehls [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gibt ein [Ausnahme](../xmla/xml-elements-properties/exception-element-xmla.md) Element in einem anderen Namespace zum Zeitpunkt des Fehlers. Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz schließt dann alle geöffneten Elemente, damit die an den Client gesendete XML-Dokument gültig ist. Die Instanz gibt darüber hinaus ein `Messages`-Element zurück, das eine Beschreibung des Fehlers enthält.  
  
##  <a name="handling_inline_errors_and_warnings"></a> Behandeln von Inlinefehlern und-Warnungen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gibt einen Inline-`error` oder eine Inline-`warning` für einen Befehl zurück, wenn die XMLA-Methode selbst nicht fehlgeschlagen ist, aber nach einem erfolgreichen XMLA-Methodenaufruf ein Fehler, der spezifisch für ein Datenelement in den von der Methoden zurückgegebenen Ergebnissen ist, auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz aufgetreten ist.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt Inline- `error` und `warning` Elementen, wenn Sie Probleme im Zusammenhang mit einer Zelle oder anderen Daten, die sich innerhalb einer `root` Element mit der [MDDataSet](../xmla/xml-data-types/mddataset-data-type-xmla.md) Datentyp auftreten, z. B. einen Fehler oder die Formatierung Fehler für eine Zelle. In diesen Fällen gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ein `error`- oder ein `warning`-Element in der `Cell` oder im `row`-Element aus, das den Fehler oder die Warnung enthält.  
  
 Das folgende Beispiel veranschaulicht ein Resultset, das einen Fehler im aus zurückgegebenen Rowset enthält eine `Execute` Methode mithilfe der [Anweisung](../xmla/xml-elements-commands/statement-element-xmla.md) Befehl.  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
