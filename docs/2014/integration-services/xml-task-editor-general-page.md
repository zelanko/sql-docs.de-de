---
title: Editor für den XML-Task (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.general.f1
helpviewer_keywords:
- XML Task Editor
ms.assetid: b9622c48-3243-4408-a1de-9ba20e32ff70
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aa0f92cc3275810b73d1dbe661a1f8473c7234df
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054279"
---
# <a name="xml-task-editor-general-page"></a>Editor für den XML-Task (Seite Allgemein)
  Auf der Seite **Allgemein** des Dialogfelds **Editor für den XML-Task** können Sie den Vorgangstyp angeben und den Vorgang konfigurieren.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [XML Task](control-flow/xml-task.md). Weitere Informationen zum Arbeiten mit XML-Dokumenten und Daten finden Sie unter "[XML im .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in der MSDN Library.  
  
## <a name="static-options"></a>Statische Optionen  
 **OperationType**  
 Wählen Sie den Vorgangstyp aus der Liste aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Überprüfen**|Überprüft das XML-Dokument mithilfe eines DTD-(Document Type Definition-) bzw. XSD-(XML Schema Definition-)Schemas. Nach Auswahl dieser Option werden die dynamischen Optionen im Bereich **Validate**angezeigt.|  
|**XSLT**|Führt XSL-Transformationen in XML-Dokumenten aus. Nach Auswahl dieser Option werden die dynamischen Optionen im Bereich **XSLT**angezeigt.|  
|**XPath**|Führt XPath-Abfragen und -Auswertungen aus. Nach Auswahl dieser Option werden die dynamischen Optionen im Bereich **XPATH**angezeigt.|  
|**Merge** (Zusammenführen)|Führt zwei XML-Dokumente zusammen. Nach Auswahl dieser Option werden die dynamischen Optionen im Bereich **Merge**angezeigt.|  
|**Diff**|Vergleicht zwei XML-Dokumente miteinander. Nach Auswahl dieser Option werden die dynamischen Optionen im Bereich **Diff**angezeigt.|  
|**Patch**|Erstellt auf der Grundlage der Ausgabe des Vergleichsvorgangs ein neues Dokument. Nach Auswahl dieser Option werden die dynamischen Optionen im Bereich **Patch**angezeigt.|  
  
 **SourceType**  
 Hiermit wählen Sie den Quelltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **Quelle**  
 Wenn **Quelle** auf **Direkteingabe** festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann mithilfe des Dialogfelds **Dokumentquellen-Editor** den XML-Code bereit.  
  
 Wenn **Quelle** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **Quelle** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus, oder klicken Sie ** \<auf neue Variable... >** , um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
## <a name="operationtype-dynamic-options"></a>OperationType (dynamische Optionen)  
  
### <a name="operationtype--validate"></a>OperationType = Validate  
 Geben Sie Optionen für den Validate-Vorgang an.  
  
 **SaveOperationResult**  
 Geben Sie an, ob die Ausgabe des Validate-Vorgangs vom XML-Task gespeichert werden soll.  
  
 **OverwriteDestination**  
 Geben Sie an, ob die Zieldatei oder -variable überschrieben werden soll.  
  
 **Ziel**  
 Wählen Sie einen vorhandenen Dateiverbindungs-Manager \<aus, oder klicken Sie auf **neue Verbindung.**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 **DestinationType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **ValidationType**  
 Wählen Sie den Überprüfungstyp aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**DTD**|Verwenden Sie eine Dokumenttypdefinition (DTD).|  
|**XSD**|Verwenden Sie eine XML-Schemadefinition (XSD). Nach Auswahl dieser Option werden die dynamischen Optionen im Bereich **ValidationType**angezeigt.|  
  
 **FailOnValidationFail**  
 Geben Sie an, ob der Vorgang fehlschlägt, wenn bei der Dokumentüberprüfung ein Fehler auftritt.  
  
 **ValidationDetails**  
 Bietet eine umfassende Fehlerausgabe, wenn der Wert dieser Eigenschaft auf „true“ festgelegt ist. Weitere Informationen finden Sie unter [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md).  
  
### <a name="validationtype-dynamic-options"></a>ValidationType (dynamische Optionen)  
  
#### <a name="validationtype--xsd"></a>ValidationType = XSD  
 **SecondOperandType**  
 Wählen Sie den Quelltyp des zweiten XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperand**  
 Wenn **SecondOperandType** auf **Direkteingabe** festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann über das Dialogfeld **Quellen-Editor** den XML-Code bereit.  
  
 Wenn **SecondOperandType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **XPathStringSourceType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
### <a name="operationtype--xslt"></a>OperationType = XSLT  
 Geben Sie Optionen für den XSLT-Vorgang an.  
  
 **SaveOperationResult**  
 Geben Sie an, ob die Ausgabe des XSLT-Vorgangs vom XML-Task gespeichert werden soll.  
  
 **OverwriteDestination**  
 Geben Sie an, ob die Zieldatei oder -variable überschrieben werden soll.  
  
 **Ziel**  
 Wenn **DestinationType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **destinationType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperandType**  
 Wählen Sie den Quelltyp des zweiten XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperand**  
 Wenn **SecondOperandType** auf **Direkteingabe** festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann über das Dialogfeld **Quellen-Editor** den XML-Code bereit.  
  
 Wenn **SecondOperandType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **XPathStringSourceType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
### <a name="operationtype--xpath"></a>OperationType = XPATH  
 Geben Sie Optionen für den XPath-Vorgang an.  
  
 **SaveOperationResult**  
 Geben Sie an, ob die Ausgabe des XPath-Vorgangs vom XML-Task gespeichert werden soll.  
  
 **OverwriteDestination**  
 Geben Sie an, ob die Zieldatei oder -variable überschrieben werden soll.  
  
 **Ziel**  
 Wenn **DestinationType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **destinationType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperandType**  
 Wählen Sie den Quelltyp des zweiten XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperand**  
 Wenn **SecondOperandType** auf **Direkteingabe** festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann über das Dialogfeld **Quellen-Editor** den XML-Code bereit.  
  
 Wenn **SecondOperandType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **XPathStringSourceType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **PutResultInOneNode**  
 Geben Sie an, ob das Ergebnis in einen einzelnen Knoten geschrieben werden soll.  
  
 **XPathOperation**  
 Wählen Sie den XPath-Ergebnistyp aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Bewertung**|Gibt die Ergebnisse einer XPath-Funktion zurück.|  
|**Node list**|Gibt die ausgewählten Knoten als XML-Fragment zurück.|  
|**Werte**|Gibt den inneren Textwert aller ausgewählten Knoten als verkettete Zeichenfolge zurück.|  
  
### <a name="operationtype--merge"></a>OperationType = Merge  
 Geben Sie Optionen für den Merge-Vorgang an.  
  
 **XPathStringSourceType**  
 Hiermit wählen Sie den Quelltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **XPathStringSource**  
 Wenn **XPathStringSourceType** auf **Direkteingabe** festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann mithilfe des Dialogfelds **Dokumentquellen-Editor** den XML-Code bereit.  
  
 Wenn **XPathStringSourceType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **XPathStringSourceType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen**: [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
 Wenn Sie eine XPath-Anweisung zur Identifizierung des Mergespeicherorts im Quelldokument verwenden, wird erwartet, dass diese Anweisung einen einzelnen Knoten zurückgibt. Wenn die Anweisung mehrere Knoten zurückgibt, wird nur der erste Knoten verwendet. Der Inhalt des zweiten Dokuments wird unter dem ersten Knoten zusammengeführt, den die XPath-Abfrage zurückgibt.  
  
 **SaveOperationResult**  
 Geben Sie an, ob die Ausgabe des Merge-Vorgangs vom XML-Task gespeichert werden soll.  
  
 **OverwriteDestination**  
 Geben Sie an, ob die Zieldatei oder -variable überschrieben werden soll.  
  
 **Ziel**  
 Wenn **DestinationType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **destinationType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperandType**  
 Wählen Sie den Zieltyp des zweiten XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperand**  
 Wenn **SecondOperandType** auf **Direkteingabe**festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann über das Dialogfeld **Dokumentquellen-Editor** den XML-Code bereit.  
  
 Wenn **SecondOperandType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **SecondOperandType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen**: [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
### <a name="operationtype--diff"></a>OperationType = Diff  
 Geben Sie Optionen für den Vergleichsvorgang an.  
  
 **DiffAlgorithm**  
 Wählen Sie den Vergleichsalgorithmus aus, der beim Vergleich von Dokumenten verwendet werden soll. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Auto**|Wenn Sie diese Option auswählen, wird vom XML-Task bestimmt, ob der schnelle oder der genaue Algorithmus verwendet wird.|  
|**Schnell**|Wenn diese Option ausgewählt ist, wird ein schneller, aber weniger genauer Vergleichsalgorithmus verwendet.|  
|**Precise**|Wenn diese Option ausgewählt ist, wird genauer Vergleichsalgorithmus verwendet.|  
  
 **Diff Options**  
 Legen Sie die Vergleichsoptionen fest, die auf den Vergleichsvorgang angewendet werden sollen. Die Optionen sind in der folgenden Tabelle aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**IgnoreXMLDeclaration**|Geben Sie an, ob XML-Deklaration verglichen werden soll.|  
|**IgnoreDTD**|Geben Sie an, ob die Dokumenttypdefinition (DTD) ignoriert werden soll.|  
|**IgnoreWhiteSpaces**|Geben Sie an, ob Unterschiede hinsichtlich der Menge an Leerzeichen beim Vergleichen von Dokumenten ignoriert werden sollen.|  
|**IgnoreNamespaces**|Geben Sie an, ob der Namespace-URI (Uniform Resource Identifier) eines Elements und seine Attributnamen verglichen werden sollen.<br /><br /> Hinweis: Wenn diese Option auf `True` festgelegt ist, werden zwei Elemente, die denselben lokalen Namen, aber unterschiedliche Namespaces haben, als identisch betrachtet.|  
|**IgnoreProcessingInstructions**|Geben Sie an, ob Verarbeitungsanweisungen verglichen werden sollen.|  
|**IgnoreOrderOfChildElements**|Geben Sie an, ob die Reihenfolge untergeordneter Elemente verglichen werden soll.<br /><br /> Hinweis: Wenn diese Option auf `True` festgelegt ist, werden untergeordnete Elemente, die sich innerhalb einer Liste gleichgeordneter Elemente lediglich durch ihre Position unterscheiden, als identisch betrachtet.|  
|**IgnoreComments**|Geben Sie an, ob Kommentarknoten verglichen werden sollen.|  
|**IgnorePrefixes**|Geben Sie an, ob die Präfixe der Element- und Attributnamen verglichen werden sollen.<br /><br /> Hinweis: Wenn diese Option auf `True` festgelegt ist, werden zwei Elemente, die denselben lokalen Namen, aber unterschiedliche Namespace-URIs und -Präfixe haben, als identisch betrachtet.|  
  
 **FailOnDifference**  
 Geben Sie an, ob der Task fehlschlagen soll, wenn beim Vergleichsvorgang ein Fehler auftritt.  
  
 **SaveDiffGram**  
 Geben Sie an, ob das Vergleichsergebnis in einem DiffGram-Dokument gespeichert werden soll.  
  
 **SaveOperationResult**  
 Geben Sie an, ob die Ausgabe des Vergleichsvorgangs vom XML-Task gespeichert werden soll.  
  
 **OverwriteDestination**  
 Geben Sie an, ob die Zieldatei oder -variable überschrieben werden soll.  
  
 **Ziel**  
 Wenn **DestinationType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **destinationType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperandType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperand**  
 Wenn **SecondOperandType** auf **Direkteingabe**festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann über das Dialogfeld **Dokumentquellen-Editor** den XML-Code bereit.  
  
 Wenn **SecondOperandType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **SecondOperandType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen**: [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
### <a name="operationtype--patch"></a>OperationType = Patch  
 Geben Sie Optionen für den Patch-Vorgang an.  
  
 **SaveOperationResult**  
 Geben Sie an, ob die Ausgabe des Patch-Vorgangs vom XML-Task gespeichert werden soll.  
  
 **OverwriteDestination**  
 Geben Sie an, ob die Zieldatei oder -variable überschrieben werden soll.  
  
 **Ziel**  
 Wenn **DestinationType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **destinationType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:**[Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **DestinationType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperandType**  
 Wählen Sie den Zieltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legt ein XML-Dokument als Quelle fest.|  
|**File connection**|Wählt eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legt als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **SecondOperand**  
 Wenn **SecondOperandType** auf **Direkteingabe**festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, und stellen Sie dann über das Dialogfeld **Dokumentquellen-Editor** den XML-Code bereit.  
  
 Wenn **SecondOperandType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **SecondOperandType** auf **Variable**festgelegt ist, wählen Sie eine vorhandene Variable aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen**: [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  
