---
title: Microsoft OLE DB Simple-Anbieter | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e36648fe42024502316d65e3cf27412b907ffc2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761598"
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Übersicht über den Microsoft OLE DB Simple-Anbieter
Der Microsoft OLE DB Simple Provider (OSP) ermöglicht ADO den Zugriff auf alle Daten, für die ein Anbieter mithilfe des [OSP-Toolkits (OLE DB Simple Provider)](https://msdn.microsoft.com/6e7b7931-9e4a-4151-ae51-672abd3f84a6)geschrieben wurde. Einfache Anbieter sind für den Zugriff auf Datenquellen vorgesehen, die nur grundlegende OLE DB Unterstützung benötigen, wie z. b. in-Memory-Arrays oder XML-Dokumente.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Legen Sie das *Provider* -Argument auf die [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft fest, um eine Verbindung mit der OLE DB Simple-Anbieter-DLL herzustellen:

```vb
MSDAOSP
```

 Dieser Wert kann auch mit der [Provider](../../../ado/reference/ado-api/provider-property-ado.md) -Eigenschaft festgelegt oder gelesen werden.

 Sie können eine Verbindung mit einfachen Anbietern herstellen, die als voll OLE DB Anbieter registriert wurden, indem Sie den Namen des registrierten Anbieters verwenden, der vom Anbieter-Writer festgelegt wurde.

## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet:

```vb
"Provider=MSDAOSP;Data Source=serverName"
```

 Die Zeichenfolge besteht aus folgenden Schlüsselwörtern:

|Stichwort|Beschreibung|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB Anbieter für SQL Server an.|
|**Data Source**|Gibt den Namen eines Servers an.|

## <a name="xml-document-example"></a>Beispiel für XML-Dokument
 Der OLE DB Simple Provider (OSP) in MDAC 2,7 oder höher und Windows Data Access Components (Windows DAC) wurde verbessert, um das Öffnen von hierarchischen ADO- **Recordsets** über beliebige XML-Dateien zu unterstützen. Diese XML-Dateien enthalten möglicherweise das ADO-XML-persistenzschema, sind jedoch nicht erforderlich. Dies wurde durch Verbinden des OSP mit der **MSXML2. dll implementiert.** Daher ist **MSXML2. dll** oder höher erforderlich.

 Die im folgenden Beispiel verwendete Datei **Portfolio. XML** enthält die folgende Struktur:

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

 Der XML-DSO verwendet integrierte Heuristik, um die Knoten in einer XML-Struktur in Kapitel in einem hierarchischen **Recordset**zu konvertieren.

 Mithilfe dieser integrierten Heuristik wird die XML-Struktur in ein hierarchisches **Recordset** mit zwei Ebenen der folgenden Form konvertiert:

```console
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 Beachten Sie, dass die Portfolio-und Info-Tags nicht im hierarchischen **Recordset**dargestellt werden. Eine Erläuterung dazu, wie XML-Strukturen XML-Strukturen in hierarchische **Recordsets**konvertiert, finden Sie in den folgenden Regeln. Die $Text-Spalte wird im folgenden Abschnitt erläutert.

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>Regeln zum Zuweisen von XML-Elementen und-Attributen zu Spalten und Zeilen
 Der XML-DSO befolgt eine Prozedur zum Zuweisen von Elementen und Attributen zu Spalten und Zeilen in Daten gebundenen Anwendungen. XML wird als Struktur mit einem Tag modelliert, das die gesamte Hierarchie enthält. Eine XML-Beschreibung eines Buchs könnte z. b. Kapitel Tags, Figur-Tags und Abschnitts Tags enthalten. Auf der höchsten Ebene ist das Book-Tag, das die unter Elemente Kapitel, Abbildung und Abschnitt enthält. Wenn das XML-DSO XML-Elemente Zeilen und Spalten zuordnet, werden die unter Elemente, nicht das Element der obersten Ebene, konvertiert.

 Der XML-DSO verwendet dieses Verfahren zum umrechnen der unter Elemente:

-   Jedes Unterelement und Attribut entsprechen einer Spalte in einem **Recordset** in der Hierarchie.

-   Der Name der Spalte entspricht dem Namen des untergeordneten Elements oder des Attributs, es sei denn, das übergeordnete Element verfügt über ein Attribut und ein untergeordnetes Element desselben Namens. in diesem Fall wird dem Spaltennamen des untergeordneten Elements ein "!" vorangestellt.

-   Jede Spalte ist entweder eine *einfache* Spalte, die skalare Werte (in der Regel Zeichen folgen) oder eine **Recordsetspalte** enthält, die untergeordnete **Recordsets**enthält.

-   Spalten, die den Attributen entsprechen, sind immer einfach.

-   Bei Spalten, die den unter Elementen entsprechen, handelt es sich um **Recordsetspalten** , wenn entweder das Unterelement über eigene unter Elemente oder Attribute (oder beides) verfügt oder das übergeordnete Element des unter Elements mehr als eine Instanz des untergeordneten Elements als untergeordnetes Element aufweist. Andernfalls ist die Spalte einfach.

-   Wenn mehrere Instanzen eines untergeordneten Elements (unter verschiedenen übergeordneten Elementen) vorhanden sind, handelt es *sich bei der* Spalte um eine **Recordsetspalte** , wenn eine der Instanzen eine **Recordsetspalte** impliziert. die Spalte ist nur dann einfach, wenn *alle* Instanzen eine einfache Spalte implizieren.

-   Alle **Recordsets** haben eine zusätzliche Spalte mit dem Namen $Text.

 Der Code, der zum Erstellen eines **Recordsets** erforderlich ist, lautet wie folgt:

```vb
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "https://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  Der Pfad der Datendatei kann mithilfe von vier verschiedenen Benennungs Konventionen angegeben werden.

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

 Sobald das **Recordset** geöffnet wurde, können die üblichen ADO- **Recordset** -Navigations Befehle verwendet werden.

 Die vom OSP generierten **Recordsets weisen** einige Einschränkungen auf:

-   Clientcursorn (**adUseClient**) werden nicht unterstützt.

-   Hierarchische **Recordsets** , die über beliebiges XML erstellt wurden, können nicht mit **Recordset. Save persistent gespeichert**werden

-   Mit dem OSP erstellte **Recordsets** sind schreibgeschützt.

-   Der Xmldso fügt jedem **Recordset** in der Hierarchie eine zusätzliche Spalte mit Daten ($Text) hinzu.

 Weitere Informationen zum OLE DB einfachen Anbieter finden Sie unter [Building a Simple Provider](https://msdn.microsoft.com/b31a6cba-58ae-4ee8-9039-700973d354d6).

## <a name="code-example"></a>Codebeispiel
 Der folgende Visual Basic Code veranschaulicht das Öffnen einer beliebigen XML-Datei, das Erstellen eines hierarchischen **Recordsets**und das rekursiv schreiben jedes Datensatzes jedes **Recordsets** in das Debugfenster.

 Im folgenden finden Sie eine einfache XML-Datei mit Aktien Anführungszeichen. Der folgende Code verwendet diese Datei, um ein hierarchisches **Recordset**mit zwei Ebenen zu erstellen.

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

 Im folgenden sind zwei Visual Basic unter Prozeduren beschrieben. Der erste erstellt das **Recordset** und übergibt es an die *Exemplarische Vorgehensweise, die die* Hierarchie rekursiv durchläuft, wobei jedes **Feld** in jedem Datensatz in jedem **Recordset** in das Debugfenster geschrieben wird.

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
