---
title: Behandeln von Fehlern und Warnungen (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 884474398abc9f449e5f6bd82c9f4b981f9a3a43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261694"
---
# <a name="handling-errors-and-warnings-xmla"></a>Behandeln von Fehlern und Warnungen (XMLA)
  Eine Fehlerbehandlung ist notwendig, wenn ein XMLA-Aufruf (XML for Analysis) der Methoden [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) oder [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) nicht ausgeführt wird, erfolgreich ausgeführt wird, aber Fehler oder Warnungen generiert oder erfolgreich ausgeführt wird, aber fehlerhafte Ergebnisse zurückgibt.  
  
|Fehler|Bericht|  
|-----------|---------------|  
|Der XMLA-Methodenaufruf wird nicht ausgeführt|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt einen SOAP-Fehlernachricht mit den Details des Fehlers zurück.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von SOAP-Fehlern](#handling_soap_faults).|  
|Fehler oder Warnungen bei erfolgreichem Methodenaufruf|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält eine [Fehler](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) oder [Warnung](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) -Element für jeden Fehler oder Warnung aus, in der [Nachrichten](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) Eigenschaft der [Stamm](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) Element die Ergebnisse des Methodenaufrufs enthält.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von Fehlern und Warnungen](#handling_errors_and_warnings).|  
|Fehler im Ergebnis bei erfolgreichem Methodenaufruf|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält ein Inline- **Fehler** oder **Warnung** -Element für den Fehler oder die Warnung bzw. in die entsprechende [Zelle](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) oder [Zeile](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) Element der Ergebnisse des Methodenaufrufs.<br /><br /> Weitere Informationen finden Sie im Abschnitt [Behandeln von Inlinefehlern und -warnungen](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling_soap_faults"></a> Behandlung von SOAP-Fehler  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gibt einen SOAP-Fehler zurück, wenn die folgenden Situationen auftreten:  
  
-   Die SOAP-Nachricht, die die XMLA-Methode enthält, ist nicht wohlgeformt oder konnte von der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz nicht überprüft werden.  
  
-   Eine Kommunikations- oder anderer Fehler ist in Bezug auf die SOAP-Nachricht, die die XMLA-Methode enthält, aufgetreten.  
  
-   Die XMLA-Methode wurde nicht auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ausgeführt.  
  
 Die SOAP-Fehlercodes für XMLstartA beginnen mit „XMLForAnalysis“ gefolgt von einem Punkt und dem hexadezimalen HRESULT-Ergebniscode. Beispielsweise wird ein Fehlercode von „`0x80000005`“ formatiert als „`XMLForAnalysis.0x80000005`“. Weitere Informationen über das SOAP-Fehlerformat finden Sie unter „Soap Fault in the W3C Simple Object Access Protocol (SOAP) 1.1“.  
  
### <a name="fault-code-information"></a>Fehlercodeinformationen  
 Die folgende Tabelle zeigt die XMLA-Fehlercodeinformationen, die im Detailabschnitt der SOAP-Antwort enthalten sind. Die Spalten sind die Attribute eines Fehlers im Detailabschnitt eines SOAP-Fehlers.  
  
|Spaltenname|Typ|Description|Null zulässig<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|**ErrorCode**|**UnsignedInt**|Rückgabecode, der den Erfolg oder das Scheitern der Methode angibt. Der Hexadezimalwert muss in einen **UnsignedInt** -Wert konvertiert werden.|Nein|  
|**WarningCode**|**UnsignedInt**|Rückgabecode, der eine Warnbedingung angibt. Der Hexadezimalwert muss in einen **UnsignedInt** -Wert konvertiert werden.|Ja|  
|**Beschreibung**|**String**|Fehler- oder Warnungstext und Beschreibung, die durch die Komponente zurückgegeben werden, die den Fehler erzeugt hat.|Ja|  
|**Quelle**|**String**|Name der Komponente, die den Fehler oder die Warnung generiert hat.|Ja|  
|**HelpFile**|**String**|Pfad oder URL zur Hilfedatei oder dem Thema, das den Fehler oder die Warnung beschreibt.|Ja|  
  
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
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt die **Nachrichten** -Eigenschaft in der **Stamm** -Element für einen Befehl aus, wenn nach Ausführung des Befehls die folgenden Situationen auftreten:  
  
-   Die Methode selber schlug nicht fehl, aber nach erfolgreicher Ausführung des Methodenaufrufs trat ein Fehler auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ein.  
  
-   Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz gibt eine Warnung zurück, wenn der Befehl erfolgreich ist.  
  
 Die **Messages** -Eigenschaft folgt allen Eigenschaften, die im **root** -Element enthalten sind, und kann ein oder mehr **Message** -Elemente enthalten. Jedes **Message** -Element kann entweder ein einzelnes **error** - oder ein **warning** -Element enthalten, das entweder Fehler oder Warnungen beschreibt, die beim angegebenen Befehl aufgetreten sind.  
  
 Weitere Informationen zu Fehlern und Warnungen, die in befinden die **Nachrichten** -Eigenschaft finden Sie unter [Messages-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).  
  
### <a name="handling-errors-during-serialization"></a>Behandeln von Fehlern während der Serialisierung  
 Wenn ein Fehler auftritt, nachdem die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz bereits mit der Serialisierung der Ausgabe eines erfolgreich ausgeführten Befehls begonnen hat, gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ein [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) -Element an einem anderen Namespace als dem Punkt des Fehlers zurück. Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz schließt dann alle geöffneten Elemente, sodass das an den Client gesendete XML-Dokument gültig ist. Die Instanz gibt darüber hinaus ein **Messages** -Element zurück, das eine Beschreibung des Fehlers enthält.  
  
##  <a name="handling_inline_errors_and_warnings"></a> Behandeln von Inlinefehlern und-Warnungen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt ein Inlineschema zurück **Fehler** oder **Warnung** für einen Befehl aus, wenn die XMLA-Methode selbst keine Fehler aufgetreten, aber speziell für ein Datenelement in den Ergebnissen, die von der Methode zurückgegebene Fehler auf der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Instanz nach der XMLA-Methodenaufruf erfolgreich war.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gibt Inline- **Fehler** und **Warnung** Elementen, wenn Sie Probleme im Zusammenhang mit einer Zelle oder anderen Daten, die sich innerhalb einer **Stamm** Element mit der [ MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) Datentyp auftreten, hierzu können Sicherheits- oder Formatierungsfehler einer Zelle. In diesen Fällen gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ein **erroder** oder **Warning** -Element in der **Cell** oder **Row** element that contains the erroder oder Warning, respectively.  
  
 Das folgende Beispiel veranschaulicht ein Resultset, das einen Fehler in dem Rowset enthält, das von der **Execute** -Methode über den Befehl [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) zurückgegeben wurde.  
  
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
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
