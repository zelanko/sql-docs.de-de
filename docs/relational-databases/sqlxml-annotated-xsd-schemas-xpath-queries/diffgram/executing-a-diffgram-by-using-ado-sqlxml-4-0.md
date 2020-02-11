---
title: Ausführen eines DiffGram mithilfe von ADO (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b7ca55bdea021127d73bcef8bb2e695a5fe45123
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75246654"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a>Ausführen eines DiffGram-Objekts mit ADO (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Diese [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic-Anwendung verwendet ADO, um eine Verbindung mit einer Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herzustellen, und führt dann ein DiffGram-Objekt aus. In dieser Anwendung werden das DiffGram-Objekt und das XSD-Schema in einer Datei gespeichert. Die Anwendung lädt das DiffGram-Objekt aus der angegebenen Datei. Sie können jedes der DiffGrams (und des zugehörigen XSD-Schemas) verwenden, das unter [DiffGram-Beispiele](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md)beschrieben wird.  
  
 Das ist der Ablauf bei der Beispielanwendung:  
  
-   Das **conn** -Objekt (**ADODB. Verbindung**) stellt eine Verbindung mit einer laufenden Instanz von SQL Server auf einem bestimmten Server her.  
  
-   Das **cmd** -Objekt (**ADODB. Command**) wird auf der eingerichteten Verbindung ausgeführt.  
  
-   Der Befehlsdialekt wird auf DBGUID_MSSQLXML festgelegt.  
  
-   Das DiffGram-Objekt wird aus einer Datei in den Befehlsdaten Strom (**straumin**) kopiert.  
  
-   Der Ausgabestream des Befehls wird auf das Objekt " **straumout** " (**ADODB) festgelegt. Stream**), um alle zurückgegebenen Daten zu empfangen.  
  
-   Wenn Sie den SQLOLEDB-Anbieter verwenden, wird die Microsoft SQLXML-Funktionalität standardmäßig von Sqlxmlx.dll bereitgestellt. Wenn Sie Sqlxml4. dll mit dem SQLOLEDB-Anbieter verwenden möchten, muss die **SQLXML-Version** -Eigenschaft im SQLOLEDB-Anbieter **Verbindungs** Objekt auf **SQLXML. 4.0** festgelegt werden.  
  
-   Der Befehl (DiffGram) wird ausgeführt.  
  
 Der folgende Code stellt die Beispielanwendung dar.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen.  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a>So testen Sie das DiffGram-Objekt  
  
1.  Kopieren Sie in einen Ordner auf Ihrem Computer eines der Diffgrams und das entsprechende XSD-Schema aus einem der Beispiele in [DiffGram-Beispielen](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
2.  Öffnen Sie Visual Basic, und erstellen Sie ein Standard-EXE-Projekt.  
  
3.  Fügen Sie dem Projekt die folgenden Verweise hinzu:  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  Klicken Sie in der Toolbox auf **CommandButton**, und zeichnen Sie dann eine Schaltfläche im Formular.  
  
5.  Doppelklicken Sie auf die Schaltfläche, um den Code zu bearbeiten, und fügen Sie den Anwendungscode aus dem Dokument hinzu.  
  
6.  Bearbeiten Sie den Code, um das DiffGram-Objekt und die XSD-Dateinamen anzugeben. Bearbeiten Sie außerdem die Verbindungszeichenfolge nach Bedarf.  
  
7.  Führen Sie die Anwendung aus. Das Ergebnis der Ausführung hängt davon ab, was für ein DiffGram-Objekt Sie ausführen.  

