---
title: Einfache Microsoft OLE DB-Anbieter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- simple provider [ADO]
- providers [ADO], OLE DB simple provider
- OLE DB simple provider [ADO]
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bc17df7bad00205803b33cb4af17cb3c6ddaac56
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701285"
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Microsoft OLE DB Simple-Anbieter (Übersicht)
Der Microsoft OLE DB Simple Anbieter (OSP) ermöglicht ADO auf Daten zugreifen, für die ein Anbieter geschrieben wurde mithilfe, der [OLE DB Simple Anbieter (OSP) Toolkit](https://msdn.microsoft.com/6e7b7931-9e4a-4151-ae51-672abd3f84a6). Einfache Anbieter dienen zum Zugreifen auf Datenquellen, die nur grundlegende OLE DB-Unterstützung, z. B. in-Memory-Arrays oder XML-Dokumenten erfordern.

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen
 Legen Sie zum Verbinden mit dem OLE DB Simple-Anbieter-DLL der *Anbieter* Argument für die ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft:

```vb
MSDAOSP
```

 Dieser Wert kann auch festlegen oder Lesen Sie mithilfe der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft.

 Sie können auf einfache Anbieter verbinden, die mithilfe der registrierten Anbietername, der bestimmt, indem die Anbieterwriter als vollständige OLE DB-Anbieter registriert wurden.

## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge
 Eine typische Verbindungszeichenfolge für diesen Anbieter ist:

```vb
"Provider=MSDAOSP;Data Source=serverName"
```

 Die Zeichenfolge, die dieser Schlüsselwörter besteht aus:

|Schlüsselwort|Description|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB-Anbieter für SQL Server an.|
|**Data Source**|Gibt den Namen eines Servers.|

## <a name="xml-document-example"></a>Beispiel für XML-Dokument
 Der OLE DB Simple-Anbieter (OSP) in MDAC 2.7 oder höher und Windows Data Access Components (Windows DAC) wurde verbessert, um Unterstützung für das Öffnen von hierarchischen ADO **Recordsets** für den beliebigen XML-Dateien. Diese XML-Dateien können das ADO-XML-Persistenz-Schema enthalten, aber es ist nicht erforderlich. Dies wurde durch das Verbinden des OSPS, implementiert die **"Msxml2.dll"** daher **"Msxml2.dll"** oder höher ist erforderlich.

 Die **portfolio.xml** Datei im folgenden Beispiel enthält die folgende Struktur:

```console
Portfolio
   Stock
      Shares
      Symbol
      Price
      Info
         Company Name
         WebSite
```

 Das XML-DSO verwendet integrierte Heuristiken, um die Knoten in einer XML-Struktur zu Kapiteln in einer hierarchischen konvertieren **Recordset**.

 Verwenden diese integrierte Heuristiken, wird die XML-Struktur in eine zwei-Ebenen-hierarchische konvertiert **Recordset** im folgenden Format:

```console
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 Beachten Sie, dass die Portfolio und Info-Tags nicht, in der hierarchischen dargestellt werden **Recordset**. Eine Erläuterung, wie das XML-DSO XML-Strukturen in hierarchisch konvertiert **Recordsets**, finden Sie unter den folgenden Regeln. Die Spalte $Text wird im folgenden Abschnitt erläutert.

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>Regeln für das Zuweisen von XML-Elemente und Attribute, Spalten und Zeilen
 Das XML-DSO folgt ein Verfahren zum Zuweisen von Elementen und Attribute zu Zeilen und Spalten in datengebundene Anwendungen. XML wird als eine Struktur mit einem Tag modelliert, die die gesamte Hierarchie enthält. Beispielsweise kann eine XML-Beschreibung eines Buchs Kapitel Tags, Abbildung und Tags für Abschnitte enthalten. Auf der höchsten Ebene wäre die Buch-Tag, mit dem die Unterelemente Kapitel, Abbildung und Abschnitt. Wenn das XML-DSO-XML-Elemente in Zeilen und Spalten zugeordnet wird, werden die Unterelemente, kein Element der obersten Ebene, konvertiert.

 Das XML-DSO greift auf dieses Verfahren für die Konvertierung die untergeordneten Elemente:

-   Jedes Unterelement und Attribut entspricht einer Spalte in einigen **Recordset** in der Hierarchie.

-   Der Name der Spalte ist identisch mit den Namen des Unterelements oder Attributs, es sei denn, das übergeordnete Element ein Attribut als auch ein Unterelement mit demselben Namen in diesem Fall ein "!" auf den Namen des Unterelements Spalte vorangestellt ist.

-   Jede Spalte ist entweder ein *einfache* Spalte, die Skalare Werte (in der Regel Zeichenfolgen) enthält oder ein **Recordset** Spalte mit untergeordneten **Recordsets**.

-   Spalten, die Attributen entsprechen, sind stets einfach.

-   Spalten, die Unterelemente sind **Recordset** Spalten zurück, wenn das Unterelement hat seine eigenen untergeordneten Elemente oder Attribute (oder beides) oder des Unterelements übergeordnetes Element, mehr als eine Instanz des Unterelements als untergeordnetes Element besitzt. Andernfalls ist die Spalte einfach.

-   Wenn mehrere Instanzen von einem Unterelement (unter verschiedenen übergeordneten Elementen) vorhanden sind, wird die Spalte ist eine **Recordset** Spalte Wenn *alle* Instanzen beinhalten ein **Recordset** Spalte, dessen Spalte ist einfach nur, wenn *alle* Instanzen beinhalten eine einfache Spalte.

-   Alle **Recordsets** eine zusätzliche Spalte mit dem Namen $Text.

 Der Code, der erforderlich ist, zum Erstellen einer **Recordset** lautet wie folgt:

```vb
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "https://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  Der Pfad der Datendatei kann angegeben werden, mithilfe von vier verschiedene Benennungskonventionen.

```vb
'HTTP://
adoRS.Open "https://WebServer/VRoot/portfolio.xml", adoConn
'FILE://
adoRS.Open "file:/// C:\\Directory\\portfolio.xml", adoConn
'UNC Path
adoRS.Open "\\ComputerName\ShareName\portfolio.xml", adoConn
'Full DOS Path
adoRS.Open "C:\Directory\portfolio.xml", adoConn
```

 Sobald die **Recordset** geöffnet wurde, den übliche ADO **Recordset** Navigationsbefehle können verwendet werden.

 **Durch Recordsets** generiert, durch das OSP weisen einige Einschränkungen auf:

-   Clientcursor (**AdUseClient**) werden nicht unterstützt.

-   Hierarchische **Recordsets** erstellt für den beliebigen XML nicht beibehalten werden mithilfe von **Recordset.Save**.

-   **Durch Recordsets** mit das OSP erstellt sind schreibgeschützt.

-   Die XMLDSO Fügt eine zusätzliche Spalte mit Daten ($Text) auf die einzelnen **Recordset** in der Hierarchie.

 Weitere Informationen zu OLE DB Simple-Anbieter, finden Sie unter [Erstellen eines einfachen Anbieters](https://msdn.microsoft.com/b31a6cba-58ae-4ee8-9039-700973d354d6).

## <a name="code-example"></a>Codebeispiel
 Die folgende Visual Basic-Code wird veranschaulicht, öffnen eine beliebige XML-Datei, erstellen eine hierarchische **Recordset**, und Schreiben jeden Datensatz der einzelnen rekursiv **Recordset** zum Debug-Fenster.

 Hier ist eine einfache XML-Datei, die Aktienkurse enthält. Der folgende Code verwendet diese Datei zum Erstellen von hierarchischen einer zwei Ebenen **Recordset**.

```xml
<portfolio>
   <stock>
      <shares>100</shares>
      <symbol>MSFT</symbol>
      <price>$70.00</price>
      <info>
         <companyname>Microsoft Corporation</companyname>
         <website>https://www.microsoft.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>AAPL</symbol>
      <price>$107.00</price>
      <info>
         <companyname>Apple Computer, Inc.</companyname>
         <website>https://www.apple.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>DELL</symbol>
      <price>$50.00</price>
      <info>
         <companyname>Dell Corporation</companyname>
         <website>https://www.dell.com</website>
      </info>
    </stock>
    <stock>
       <shares>100</shares>
       <symbol>INTC</symbol>
       <price>$115.00</price>
       <info>
          <companyname>Intel Corporation</companyname>
          <website>https://www.intel.com</website>
       </info>
   </stock>
</portfolio>
```

 Es folgen zwei Visual Basic-Sub-Prozeduren. Die erste erstellt die **Recordset** und übergibt es an der *WalkHier* sub-Prozedur, die rekursiv in der Hierarchie führt, Schreiben jedes **Feld** in jedem Datensatz in den einzelnen **Recordset** zum Debug-Fenster.

```vb
Private Sub BrowseHierRecordset()
' Add ADO 2.7 or later to Project/References
' No need to add MSXML2, ADO just passes the ProgID through to the OSP.

    Dim adoConn As ADODB.Connection
    Dim adoRS As ADODB.Recordset
    Dim adoChildRS As ADODB.Recordset

    Set adoConn = New ADODB.Connection
    Set adoRS = New ADODB.Recordset
    Set adoChildRS = ADODB.Recordset

    adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
    adoRS.Open "https://bwillett3/Kowalski/portfolio.xml", adoConn

    Dim iLevel As Integer
    iLevel = 0
    WalkHier iLevel, adoRS

End Sub

Sub WalkHier(ByVal iLevel As Integer, ByVal adoRS As ADODB.Recordset)
    iLevel = iLevel + 1
    PriorLevel = iLevel
    While Not adoRS.EOF
        For ndx = 0 To adoRS.Fields.Count - 1
            If adoRS.Fields(ndx).Name <> "$Text" Then
                If adoRS.Fields(ndx).Type = adChapter Then
                    Set adoChildRS = adoRS.Fields(ndx).Value
                    WalkHier iLevel, adoChildRS
                Else
                    Debug.Print iLevel & ": adoRS.Fields(" & ndx & _
                       ") = " & adoRS.Fields(ndx).Name & " = " & _
                       adoRS.Fields(ndx).Value
                End If
            End If
        Next ndx
        adoRS.MoveNext
    Wend
    iLevel = PriorLevel
End Sub
```
