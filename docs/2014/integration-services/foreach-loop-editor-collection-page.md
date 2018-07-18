---
title: Foreach-Schleifen-Editor (Seite Auflistung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.collection.f1
ms.assetid: 95a19dde-61ca-4d9b-aa3d-131fa4264296
caps.latest.revision: 62
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d10057943aa872c919171227f072f6b2836eba4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318880"
---
# <a name="foreach-loop-editor-collection-page"></a>Foreach-Schleifen-Editor (Seite Auflistung)
  Verwenden Sie die Seite **Auflistung** des Dialogfelds **Foreach-Schleifen-Editor**, um den Enumeratortyp anzugeben und den Enumerator zu konfigurieren.  
  
 Weitere Informationen für Foreach-Schleifencontainer und wie diese zu konfigurieren sind, finden Sie unter [Foreach-Schleifencontainer](control-flow/foreach-loop-container.md) und [Konfigurieren eines Foreach-Schleifencontainers](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Enumerator**  
 Wählen Sie den Enumeratortyp aus der Liste aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**Foreach-Datei-Enumerator**|Zählt Dateien auf. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-Dateienumerator**die dynamischen Optionen angezeigt.|  
|**Foreach-Element-Enumerator**|Zählt Werte in einem Element auf. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-Elementenumerator**die dynamischen Optionen angezeigt.|  
|**Foreach-ADO-Enumerator**|Zählt Tabellen oder Zeilen in Tabellen auf. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-ADO-Enumerator**die dynamischen Optionen angezeigt.|  
|**Enumerator für Foreach-ADO.NET-Schemarowset**|Zählt ein Schema auf. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-ADO-Enumerator**die dynamischen Optionen angezeigt.|  
|**Foreach-Enumerator für Daten aus Variable**|Zählt den Wert in einer Variable auf. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-Enumerator für Daten aus Variable**die dynamischen Optionen angezeigt.|  
|**Foreach-NodeList-Enumerator**|Zählt Knoten in einem XML-Dokument auf. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-NodeList-Enumerator**die dynamischen Optionen angezeigt.|  
|**Foreach-SMO-Enumerator**|Zählt ein SMO-Objekt auf. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-SMO-Enumerator**die dynamischen Optionen angezeigt.|  
|**Foreach-Azure-Blob-Enumerator**|Auflisten von Blob-Dateien am angegebenen Blob-Speicherort. Wenn Sie diesen Wert auswählen, werden die dynamischen Optionen im Abschnitt **Foreach-Azure-Blob-Enumerator**angezeigt.|  
|**Foreach-ADLS-Datei-Enumerator**|Auflisten von Dateien, die Azure Data Lake Store mit Filtern. Wenn Sie diesen Wert auswählen, werden im Abschnitt **Foreach-ADLS-Datei-Enumerator** die dynamischen Optionen angezeigt.|
  
 **Ausdrücke**  
 Klicken Sie auf die Option **Ausdrücke** , oder erweitern Sie diese, um die Liste der vorhandenen Eigenschaftsausdrücke anzuzeigen. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, um einer Enumeratoreigenschaft einen Eigenschaftsausdruck hinzuzufügen, oder um einen vorhandenen Eigenschaftsausdruck zu bearbeiten und auszuwerten.  
  
 **Verwandte Themen:** [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md), [Eigenschaftsausdrucks-Editor](expressions/property-expressions-editor.md), [Ausdrucks-Generator](expressions/expression-builder.md)  
  
## <a name="enumerator-dynamic-options"></a>Enumerator (dynamische Optionen)  
  
### <a name="enumerator--foreach-file-enumerator"></a>Enumerator = Foreach-Dateienumerator  
 Mithilfe des Foreach-Dateienumerators können Dateien in einem Ordner aufgezählt werden. Wenn die Foreach-Schleife z. B. einen Task SQL ausführen enthält, können Sie mithilfe des Foreach-Dateienumerators Dateien aufzählen, die vom Task SQL ausführen ausgeführte SQL-Anweisungen enthalten. Der Enumerator kann so konfiguriert werden, dass Unterordner in der Aufzählung berücksichtigt werden.  
  
 Der Inhalt der Ordner und Unterordner, die der Foreach-Dateienumerator aufzählt, ändert sich möglicherweise beim Durchlaufen der Schleife, da externe Prozesse oder Tasks in der Schleife beim Durchlaufen der Schleife Dateien hinzufügen, umbenennen oder löschen. Dies kann zu unerwarteten Ergebnissen führen:  
  
-   Wenn Dateien gelöscht werden, bearbeitet ein Task in der Foreach-Schleife möglicherweise einen anderen Satz Dateien als den, der von nachfolgenden Tasks bearbeitet wird.  
  
-   Wenn Dateien umbenannt werden und ein externer Prozess Dateien automatisch hinzufügt, um die umbenannten Dateien zu ersetzen, wird derselbe Dateiinhalt möglicherweise zweimal von der Foreach-Schleife bearbeitet.  
  
-   Wenn Dateien hinzugefügt werden, kann es sich als schwierig erweisen, die von der Foreach-Schleife bearbeiteten Dateien zu erkennen.  
  
 **Ordner**  
 Gibt den Pfad für den Stammordner für die Aufzählung an.  
  
 **Durchsuchen**  
 Mit dieser Option können Sie den Stammordner suchen.  
  
 **Dateien**  
 Geben Sie die aufzuzählenden Dateien an.  
  
> [!NOTE]  
>  Sie können Platzhalterzeichen (*) verwenden, um die in der Sammlung zu berücksichtigenden Dateien anzugeben. Um Dateien einzubeziehen, deren Name „abc“ enthält, verwenden Sie beispielsweise den folgenden Filter: \*abc\*.  
>   
>  Wenn Sie eine Dateierweiterung angeben, gibt der Enumerator auch Dateien mit derselben Erweiterung mit angehängten zusätzlichen Zeichen zurück. (Dieses Verhalten entspricht dem Verhalten des **dir**-Befehls im Betriebssystem, mit dem 8.3-Dateinamen auf Abwärtskompatibilität überprüft werden.) Dieses Verhalten des Enumerators könnte unerwartete Ergebnisse verursachen. Angenommen, Sie möchten nur Excel 2003-Dateien auflisten und geben "*.xls" an. Der Enumerator gibt in diesem Fall auch Excel 2007-Dateien zurück, da diese Dateien die Erweiterung, ".xlsx", haben.  
>   
>  Sie können einen Ausdruck verwenden, um die in eine Sammlung einzubeziehenden Dateien anzugeben. Erweitern Sie dazu **Ausdrücke** auf der Seite **Sammlung** , wählen Sie die **FileSpec** -Eigenschaft aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungspunkten (…), um den Eigenschaftsausdruck hinzuzufügen. Weitere Informationen zum dynamischen Auswählen angegebener Dateien finden Sie unter [SSIS – Dynamisches Einstellen von File Mask : FileSpec](http://go.microsoft.com/fwlink/?LinkId=238154)  
  
 **Vollqualifiziert**  
 Wählen Sie diese Option aus, um den vollqualifizierten Pfad von Dateinamen abzurufen. Wenn in der Dateioption Platzhalterzeichen angegeben wurden, stimmen die zurückgegebenen vollqualifizierten Pfade mit dem Filter überein.  
  
 **Nur Name**  
 Wählen Sie diese Option aus, um nur die Dateinamen abzurufen. Wenn in der Dateioption Platzhalterzeichen angegeben wurden, stimmen die zurückgegebenen Dateinamen mit dem Filter überein.  
  
 **Name und Erweiterung**  
 Wählen Sie diese Option aus, um die Dateinamen und die Dateinamenerweiterungen abzurufen. Wenn in der Dateioption Platzhalterzeichen angegeben wurden, stimmen die zurückgegebenen Dateinamen und Dateierweiterungen mit dem Filter überein.  
  
 **Unterordner durchsuchen**  
 Wählen Sie diese Option aus, wenn die Unterordner in der Aufzählung berücksichtigt werden sollen.  
  
### <a name="enumerator--foreach-item-enumerator"></a>Enumerator = Foreach-Elementenumerator  
 Mithilfe des Foreach Item-Numerators können Elemente in einer Auflistung aufgezählt werden. Sie definieren die Elemente in der Auflistung, indem Sie Spalten und Spaltenwerte angeben. Ein Element wird durch die Spalten in einer Zeile definiert. Ein Element, das die von einem Task Prozess ausführen ausgeführten ausführbaren Dateien sowie das vom Task verwendete Arbeitsverzeichnis angibt, verfügt über zwei Spalten. Eine Spalte listet die Namen der ausführbaren Dateien auf und eine andere das Arbeitsverzeichnis. Die Anzahl von Zeilen bestimmt, wie oft die Schleife wiederholt wird. Wenn die Tabelle 10 Zeilen aufweist, wird die Schleife 10-mal wiederholt.  
  
 Um die Eigenschaften des Task Prozess ausführen zu aktualisieren, ordnen Sie Elementspalten mithilfe des Spaltenindex Variablen zu. Die erste im Enumeratorelement definierte Spalte verfügt über den Indexwert 0, die zweite über den Wert 1 usw. Die Variablenwerte werden bei jeder Wiederholung der Schleife aktualisiert. Die Eigenschaften `Executable` und `WorkingDirectory` des Tasks Prozess ausführen können dann mithilfe von Eigenschaftsausdrücken, die diese Variablen verwenden, aktualisiert werden.  
  
 **Definieren Sie die Elemente für die ForEach-Elementauflistung**  
 Geben Sie einen Wert für jede Spalte in der Tabelle an.  
  
> [!NOTE]  
>  Nachdem Sie die Werte in Zeilenspalten eingegeben haben, wird der Tabelle automatisch eine neue Zeile hinzugefügt.  
  
> [!NOTE]  
>  Wenn die angegebenen Werte nicht mit dem Spaltendatentyp kompatibel sind, wird der Text rot angezeigt.  
  
 **Datentyp der Spalte**  
 Führt den Datentyp der aktiven Spalte auf.  
  
 **Entfernen**  
 Wählen Sie ein Element aus, und klicken Sie anschließend auf **Entfernen** , um es aus der Liste zu entfernen.  
  
 **Spalten**  
 Klicken Sie auf diese Option, um den Datentyp der Spalten im Element zu konfigurieren.  
  
 **Verwandte Themen:** [ForEach-Elementspalten (Dialogfeld, Referenz zur Benutzeroberfläche)](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)  
  
### <a name="enumerator--foreach-ado-enumerator"></a>Enumerator = Foreach-ADO-Enumerator  
 Mithilfe des Foreach-ADO-Enumerators werden Zeilen oder Tabellen in einem in einer Variablen gespeicherten ADO- oder ADO.NET-Objekt aufgezählt. Wenn die Foreach-Schleife z. B. einen Skripttask enthält, mit dem ein Dataset in eine Variable geschrieben wird, können Sie mithilfe des Foreach-ADO-Enumerators die Zeilen im Dataset aufzählen. Wenn die Variable ein ADO.NET-Dataset enthält, kann der Enumerator zum Aufzählen von Zeilen in mehreren Tabellen oder zum Aufzählen von Tabellen konfiguriert werden.  
  
 **ADO-Objektquellvariable**  
 Wählen Sie eine benutzerdefinierte Variable aus der Liste aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen.  
  
> [!NOTE]  
>  Die Variable muss den Datentyp Objekt besitzen, andernfalls tritt ein Fehler auf.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md)  
  
 **Zeilen in der ersten Tabelle**  
 Wählen Sie diese Option aus, um nur Zeilen in der ersten Tabelle aufzuzählen.  
  
 **Zeilen in allen Tabellen (nur ADO.NET-Dataset)**  
 Wählen Sie diese Option aus, um Zeilen in allen Tabellen aufzuzählen. Diese Option ist nur verfügbar, wenn die aufzuzählenden Objekte alle Mitglieder desselben ADO.NET-Datasets sind.  
  
 **Alle Tabellen (nur ADO.NET-Dataset)**  
 Wählen Sie diese Option aus, um nur Tabellen aufzuzählen.  
  
### <a name="enumerator--foreach-adonet-schema-rowset-enumerator"></a>Enumerator = Enumerator für Foreach-ADO.NET-Schemarowset  
 Mithilfe des Enumerators für Foreach ADO.NET-Schemarowset kann ein Schema für eine angegebene Datenquelle aufgezählt werden. Wenn die Foreach-Schleife z. B. einen Task SQL ausführen enthält, können Sie mit dem Enumerator für Foreach ADO.NET-Schemarowset Schemas aufzählen (beispielsweise die Spalten in der **AdventureWorks** -Datenbank) und mit dem Task SQL ausführen Schemaberechtigungen abrufen.  
  
 **Verbindung**  
 Wählen Sie einen ADO.NET-Verbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen ADO.NET-Verbindungs-Manager zu erstellen.  
  
> [!IMPORTANT]  
>  Der ADO.NET-Verbindungs-Manager muss einen .NET-Anbieter für OLE DB verwenden. Wenn Sie eine Verbindung mit SQL Server herstellen, ist der empfohlene Anbieter der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client, der im Dialogfeld **Verbindungs-Manager** im Abschnitt **.Net-Anbieter für OleDb** aufgeführt ist.  
  
 **Verwandte Themen:** [ADO Connection Manager](connection-manager/ado-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)  
  
 **Schema**  
 Wählen Sie das aufzuzählende Schema aus.  
  
 **Einschränkungen festlegen**  
 Legen Sie die Einschränkungen fest, die auf das angegebene Schema angewendet werden sollen.  
  
 **Verwandte Themen:** [Schemaeinschränkungen (Dialogfeld)](../../2014/integration-services/schema-restrictions-dialog-box.md)  
  
### <a name="enumerator--foreach-from-variable-enumerator"></a>Enumerator = Foreach-Enumerator für Daten aus Variable  
 Mithilfe des Foreach-Enumerators für Daten aus Variable werden aufzählbare Objekte in einer angegebenen Variable aufgezählt. Wenn die Foreach-Schleife z. B. einen Task SQL ausführen enthält, der eine Abfrage ausführt und das Ergebnis in einer Variable speichert, können Sie den Foreach-Enumerator für Daten aus Variable zum Aufzählen der Abfrageergebnisse verwenden.  
  
 **Variable**  
 Wählen Sie in der Liste eine Variable aus, oder klicken Sie auf \<**Neue Variable…**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md)  
  
### <a name="enumerator--foreach-nodelist-enumerator"></a>Enumerator = Foreach-NodeList-Enumerator  
 Mithilfe des Foreach-Nodelist-Enumerators wird der XML-Knotensatz, der das Ergebnis der Anwendung eines XPath-Ausdrucks auf eine XML-Datei ist, aufgezählt. Wenn die Foreach-Schleife einen Skripttask enthält, können Sie mit dem Foreach-NodeList-Enumerator einen Wert, der den Kriterien des XPath-Ausdrucks entspricht, von der XML-Datei an den Skripttask übergeben.  
  
 Der XPath-Ausdruck, der auf die XML-Datei angewendet wird, ist der in der OuterXPathString-Eigenschaft gespeicherte äußere XPath-Vorgang. Wenn der XPath-Enumerationstyp, um festgelegt ist `ElementCollection`, kann anwenden, der Foreach-NodeList-Enumerator einen inneren XPath-Ausdruck, in der InnerXPathString-Eigenschaft, um eine Auflistung von Elementen gespeichert.  
  
 Weitere Informationen zum Arbeiten mit XML-Dokumenten und Daten finden Sie unter "[XML im .NET Framework](http://go.microsoft.com/fwlink/?LinkId=56214)" in der MSDN Library.  
  
 **DocumentSourceType**  
 Wählen Sie den Quelltyp des XML-Dokuments aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**Direct input**|Legen Sie als Quelle ein XML-Dokument fest.|  
|**File connection**|Wählen Sie eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legen Sie als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 **DocumentSource**  
 Wenn für **DocumentSourceType** die Option **Direkteingabe** festgelegt ist, geben Sie den XML-Code an, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (…), um mithilfe des Dialogfelds **Dokumentquellen-Editor** XML bereitzustellen.  
  
 Wenn **DocumentSourceType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **DocumentSourceType** auf **Variable** festgelegt ist, wählen Sie eine vorhandene Variable aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **EnumerationType**  
 Wählen Sie einen Enumerationstyp aus der Liste aus. Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar.  
  
|value|Description|  
|-----------|-----------------|  
|**Navigator**|Die Aufzählung erfolgt mithilfe eines XPathNavigators.|  
|**Node**|Zählt Knoten auf, die durch einen XPath-Vorgang zurückgegeben wurden.|  
|**NodeText**|Zählt Textknoten auf, die durch einen XPath-Vorgang zurückgegeben wurden.|  
|`ElementCollection`|Zählt Elementknoten auf, die durch einen XPath-Vorgang zurückgegeben wurden.|  
  
 **OuterXPathStringSourceType**  
 Wählen Sie den Quelltyp der XPath-Zeichenfolge aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**Direct input**|Legen Sie als Quelle ein XML-Dokument fest.|  
|**File connection**|Wählen Sie eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legen Sie als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 `OuterXPathString`  
 Wenn **OuterXPathStringSourceType** auf **Direkteingabe** festgelegt ist, geben Sie die XPath-Zeichenfolge an.  
  
 Wenn **OuterXPathStringSourceType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **OuterXPathStringSourceType** auf **Variable** festgelegt ist, wählen Sie eine vorhandene Variable aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
 **InnerElementType**  
 Wenn **EnumerationType** nastaven NA hodnotu `ElementCollection`, wählen Sie den Typ des inneren Elements in der Liste.  
  
 **InnerXPathStringSourceType**  
 Wählen Sie den Quelltyp der inneren XPath-Zeichenfolge aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**Direct input**|Legen Sie als Quelle ein XML-Dokument fest.|  
|**File connection**|Wählen Sie eine Datei aus, die das XML-Dokument enthält.|  
|**Variable**|Legen Sie als Quelle eine Variable fest, die das XML-Dokument enthält.|  
  
 `InnerXPathString`  
 Wenn **InnerXPathStringSourceType** auf **Direkteingabe** festgelegt ist, geben Sie die XPath-Zeichenfolge an.  
  
 Wenn **InnerXPathStringSourceType** auf **Dateiverbindung** festgelegt ist, wählen Sie einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Wenn **InnerXPathStringSourceType** auf **Variable** festgelegt ist, wählen Sie eine vorhandene Variable aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md).  
  
### <a name="enumerator--foreach-smo-enumerator"></a>Enumerator = Foreach-SMO-Enumerator  
 Mithilfe des Foreach-SMO-Enumerators werden SQL Server Management Object (SMO)-Objekte aufgezählt. Wenn die Foreach-Schleife z. B. einen Task SQL ausführen enthält, können Sie den Foreach-SMO-Enumerator zum Aufzählen der Tabellen in der **AdventureWorks** -Datenbank und Ausführen von Abfragen, mit denen die Anzahl von Zeilen pro Tabelle ermittelt wird, verwenden.  
  
 **Verbindung**  
 Wählen Sie einen vorhandenen ADO.NET-Verbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung…**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 Verwandte Themen: [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)  
  
 **Aufzählen**  
 Geben Sie das aufzuzählende SMO-Objekt an.  
  
 **Durchsuchen**  
 Wählen Sie die SMO-Enumeration aus.  
  
 **Verwandte Themen:** [SMO-Enumeration auswählen (Dialogfeld)](../../2014/integration-services/select-smo-enumeration-dialog-box.md)  
  
### <a name="enumerator--foreach-azure-blob-enumerator"></a>Enumerator = Foreach-Azure-Blob-Enumerator  
 Der  **Azure-Blob-Enumerator**ermöglicht einem SSIS-Paket das Aufzählen von Blob-Dateien an angegebenen Blob-Speicherort. Der Name von aufgezählten Blob-Dateien kann in einer Variablen gespeichert und in Aufgaben innerhalb des Foreach-Schleifencontainers verwendet werden.  
  
 **Azure Storage-Verbindungs-Manager**  
 Wählen Sie einen vorhandenen Azure Storage-Verbindungs-Manager aus, oder erstellen Sie einen neuen, der auf ein Azure Storage-Konto verweist.  
  
 Verwandte Themen: [Azure Storage Connection Manager](connection-manager/azure-storage-connection-manager.md).  
  
 **Blob-Containername**  
 Geben Sie den Namen des Blob-Containers an, der die aufzuzählenden Blob-Dateien enthält.  
  
 **Blob-Verzeichnis**  
 Geben Sie das Blob-Verzeichnis an, das die aufzuzählenden Blob-Dateien enthält. Das Blob-Verzeichnis ist eine virtuelle hierarchische Struktur.  
  
 **Blob-Namensfilter**  
 Geben Sie einen Namensfilter zum Auflisten von Dateien mit einem bestimmten Namensmuster an. Beispiel: „MeinArbeitsblatt*.xls\* “ schließt „MeinArbeitsblatt001.xls“ und „MeinArbeitsblattABC.xlsx“ ein.  
  
 **Blob-Zeitbereichsfilter „von/bis“**  
 Geben Sie einen Filter für den Zeitbereich an. Dateien, die nach **TimeRangeFrom** und vor **TimeRangeTo** geändert wurden, werden aufgezählt.  
### <a name="enumerator--foreach-adls-file-enumerator"></a>Enumerator = Foreach-ADLS-Datei-Enumerator  
Die **ADLS-Dateienumerator** ermöglicht einem SSIS-Paket zum Aufzählen von Dateien, die Azure Data Lake Store mit Filtern. Der Schrägstrich (`/`) – mit Präfix vollständiger Pfad der aufgelisteten Dateien in einer Variablen gespeichert und in Aufgaben innerhalb des Foreach-Schleifencontainers verwendet werden kann.
  
**AzureDataLakeConnection**  
Gibt einen Azure Data Lake-Verbindungs-Manager an oder erstellt einen neuen, der auf ein ADLS-Konto verweist.   
  
**AzureDataLakeDirectory**  
Gibt das ADLS-Verzeichnis zu suchen.
  
**FileNamePattern**  
Gibt einen Dateinamensfilter an. Nur Dateien, deren Name mit dem angegebenen Muster übereinstimmt, werden aufgezählt werden. Die Platzhalterzeichen `*` und `?` werden unterstützt. 
  
**SearchRecursively**  
Gibt an, ob im angegebenen Verzeichnis rekursiv gesucht werden soll.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Blogeintrag [SSIS – Foreach NodeList-Enumerator](http://go.microsoft.com/fwlink/?LinkId=220671)auf  auf bidn.combidn.com.  
  
-   Blogeintrag [SSIS–Dynamically set File Mask : FileSpec](http://go.microsoft.com/fwlink/?LinkId=238154)auf beyondrelational.com.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Foreach-Schleifen-Editor &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Foreach-Schleifen-Editor &#40;Seite Variablenzuordnungen&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [For-Schleifencontainer](control-flow/for-loop-container.md)  
  
  
