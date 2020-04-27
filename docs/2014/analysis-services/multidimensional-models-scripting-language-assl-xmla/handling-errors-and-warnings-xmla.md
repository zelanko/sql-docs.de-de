---
title: Behandeln von Fehlern und Warnungen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 856886a5edfa5dcae604b44f5c2dca356ba0addb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62702133"
---
# <a name="handling-errors-and-warnings-xmla"></a>Behandeln von Fehlern und Warnungen (XMLA)
  Eine Fehlerbehandlung ist notwendig, wenn ein XMLA-Aufruf (XML for Analysis) der Methoden [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) oder [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) nicht ausgeführt wird, erfolgreich ausgeführt wird, aber Fehler oder Warnungen generiert oder erfolgreich ausgeführt wird, aber fehlerhafte Ergebnisse zurückgibt.  
  
|Fehler|Berichterstellung|  
|-----------|---------------|  
|Der XMLA-Methodenaufruf wird nicht ausgeführt|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt eine SOAP-Fehlermeldung zurück, die die Details des Fehlers [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von SOAP-Fehlern](#handling_soap_faults).|  
|Fehler oder Warnungen bei erfolgreichem Methodenaufruf|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]enthält ein [Error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) -oder [Warning](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) -Element für jeden Fehler bzw. jede Warnung in der [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) -Eigenschaft des [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) -Elements, das die Ergebnisse des Methoden Aufrufes enthält.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von Fehlern und Warnungen](#handling_errors_and_warnings).|  
|Fehler im Ergebnis bei erfolgreichem Methodenaufruf|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]schließt ein Inline `error` - `warning` oder-Element für den Fehler bzw. die Warnung in das entsprechende [Zellen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) -oder [Zeilen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) Element der Ergebnisse des Methoden Aufrufes ein.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von Inlinefehlern und -warnungen](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling-soap-faults"></a><a name="handling_soap_faults"></a>Behandeln von SOAP-Fehlern  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gibt einen SOAP-Fehler zurück, wenn die folgenden Situationen auftreten:  
  
-   Die SOAP-Nachricht, die die XMLA-Methode enthält, ist nicht wohlgeformt oder konnte von der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz nicht überprüft werden.  
  
-   Eine Kommunikations- oder anderer Fehler ist in Bezug auf die SOAP-Nachricht, die die XMLA-Methode enthält, aufgetreten.  
  
-   Die XMLA-Methode wurde nicht auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ausgeführt.  
  
 Die SOAP-Fehlercodes für XMLstartA beginnen mit „XMLForAnalysis“ gefolgt von einem Punkt und dem hexadezimalen HRESULT-Ergebniscode. Beispielsweise wird ein Fehlercode von „`0x80000005`“ formatiert als „`XMLForAnalysis.0x80000005`“. Weitere Informationen über das SOAP-Fehlerformat finden Sie unter „Soap Fault in the W3C Simple Object Access Protocol (SOAP) 1.1“.  
  
### <a name="fault-code-information"></a>Fehlercodeinformationen  
 Die folgende Tabelle zeigt die XMLA-Fehlercodeinformationen, die im Detailabschnitt der SOAP-Antwort enthalten sind. Die Spalten sind die Attribute eines Fehlers im Detailabschnitt eines SOAP-Fehlers.  
  
|Spaltenname|type|Beschreibung|NULL zulässig<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|Rückgabecode, der den Erfolg oder das Scheitern der Methode angibt. Der Hexadezimalwert muss in einen `UnsignedInt`-Wert konvertiert werden.|Nein|  
|`WarningCode`|`UnsignedInt`|Rückgabecode, der eine Warnbedingung angibt. Der Hexadezimalwert muss in einen `UnsignedInt`-Wert konvertiert werden.|Ja|  
|`Description`|`String`|Fehler- oder Warnungstext und Beschreibung, die durch die Komponente zurückgegeben werden, die den Fehler erzeugt hat.|Ja|  
|`Source`|`String`|Name der Komponente, die den Fehler oder die Warnung generiert hat.|Ja|  
|`HelpFile`|`String`|Pfad oder URL zur Hilfedatei oder dem Thema, das den Fehler oder die Warnung beschreibt.|Ja|  
  
 <sup>1</sup> gibt an, ob die Daten erforderlich sind und zurückgegeben werden müssen oder ob die Daten optional sind und eine NULL-Zeichenfolge zulässig ist, wenn die Spalte nicht anwendbar ist.  
  
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
  
##  <a name="handling-errors-and-warnings"></a><a name="handling_errors_and_warnings"></a>Behandeln von Fehlern und Warnungen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gibt die `Messages`-Eigenschaft im `root`-Element für einen Befehl zurück, wenn nach Ausführung des Befehls die folgenden Situationen auftreten:  
  
-   Die Methode selber schlug nicht fehl, aber nach erfolgreicher Ausführung des Methodenaufrufs trat ein Fehler auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ein.  
  
-   Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz gibt eine Warnung zurück, wenn der Befehl erfolgreich ist.  
  
 Die `Messages`-Eigenschaft folgt allen Eigenschaften, die im `root`-Element enthalten sind, und kann ein oder mehr `Message`-Elemente enthalten. Jedes `Message`-Element kann entweder ein einzelnes `error`- oder ein `warning`-Element enthalten, das entweder Fehler oder Warnungen beschreibt, die beim angegebenen Befehl aufgetreten sind.  
  
 Weitere Informationen zu Fehlern und Warnungen, die in der `Messages` -Eigenschaft enthalten sind, finden Sie unter Messages- [Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).  
  
### <a name="handling-errors-during-serialization"></a>Behandeln von Fehlern während der Serialisierung  
 Wenn ein Fehler auftritt, nachdem die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz bereits mit der Serialisierung der Ausgabe eines erfolgreich ausgeführten Befehls begonnen hat, gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ein [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) -Element an einem anderen Namespace als dem Punkt des Fehlers zurück. Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz schließt dann alle geöffneten Elemente, sodass das an den Client gesendete XML-Dokument gültig ist. Die Instanz gibt darüber hinaus ein `Messages`-Element zurück, das eine Beschreibung des Fehlers enthält.  
  
##  <a name="handling-inline-errors-and-warnings"></a><a name="handling_inline_errors_and_warnings"></a>Behandeln von Inline Fehlern und-Warnungen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gibt einen Inline-`error` oder eine Inline-`warning` für einen Befehl zurück, wenn die XMLA-Methode selbst nicht fehlgeschlagen ist, aber nach einem erfolgreichen XMLA-Methodenaufruf ein Fehler, der spezifisch für ein Datenelement in den von der Methoden zurückgegebenen Ergebnissen ist, auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz aufgetreten ist.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]stellt Inline `error` - `warning` und-Elemente bereit, wenn Probleme auftreten, die für eine Zelle oder andere Daten `root` in einem-Element mit dem [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) -Datentyp spezifisch sind, z. b. ein Sicherheitsfehler oder ein Formatierungs Fehler für eine Zelle. In diesen Fällen gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ein `error`- oder ein `warning`-Element in der `Cell` oder im `row`-Element aus, das den Fehler oder die Warnung enthält.  
  
 Das folgende Beispiel veranschaulicht ein Resultset, das einen Fehler in dem Rowset enthält, `Execute` das von einer-Methode mit dem- [Anweisungs](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) Befehl zurückgegeben wird.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
