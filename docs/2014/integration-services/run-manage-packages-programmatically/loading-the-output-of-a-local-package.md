---
title: Laden der Ausgabe eines lokalen Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9919db21f87b5b178d8893b55f0db93f9a48f23e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422787"
---
# <a name="loading-the-output-of-a-local-package"></a>Laden der Ausgabe eines lokalen Pakets
  Clientanwendungen können die Ausgabe von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketen lesen, wenn diese mithilfe von [!INCLUDE[vstecado](../../includes/vstecado-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zielen oder mithilfe der Klassen im **System.IO**-Namespace in Flatfilezielen gespeichert wird. Eine Clientanwendung kann jedoch die Ausgabe eines Pakets auch direkt aus dem Arbeitsspeicher lesen, ohne dass hierfür ein Zwischenschritt zur persistenten Speicherung der Daten erforderlich ist. Der Schlüssel für diese Lösung ist der- `Microsoft.SqlServer.Dts.DtsClient` Namespace, der spezialisierte Implementierungen der `IDbConnection` -, `IDbCommand` -und **IDbDataParameter** -Schnittstellen aus dem **System. Data** -Namespace enthält. Die Assembly „Microsoft.SqlServer.Dts.DtsClient.dll“ wird standardmäßig im Verzeichnis **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn** installiert.

> [!NOTE]
>  Für die in diesem Artikel beschriebene Vorgehensweise müssen die DelayValidation-Eigenschaft des Datenflusstasks und alle übergeordneten Objekte auf den Standardwert **FALSE** festgelegt werden.

## <a name="description"></a>BESCHREIBUNG
 In dieser Prozedur wird veranschaulicht, wie eine Clientanwendung in verwaltetem Code entwickelt wird, die die Ausgabe eines Pakets mit einem DataReader-Ziel direkt aus dem Arbeitsspeicher lädt. Die hier zusammengefassten Schritte werden in dem folgenden Codebeispiel veranschaulicht.

#### <a name="to-load-data-package-output-into-a-client-application"></a>So laden Sie Datenpaketausgabe in eine Clientanwendung

1.  Konfigurieren Sie in dem Paket ein DataReader-Ziel so, dass die Ausgabe empfangen wird, die in die Clientanwendung gelesen werden soll. Geben Sie dem DataReader-Ziel einen aussagekräftigen Namen, da Sie diesen Namen später in der Clientanwendung verwenden werden. Notieren Sie sich den Namen des DataReader-Ziels.

2.  Legen Sie im Entwicklungsprojekt einen Verweis auf den- `Microsoft.SqlServer.Dts.DtsClient` Namespace fest, indem Sie die Assembly **Microsoft.SqlServer.Dts.DtsClient.dll**suchen. Diese Assembly wird standardmäßig im Verzeichnis **C:\Programme\Microsoft SQL Server\100\DTS\Binn** installiert. Importieren Sie den Namespace mithilfe der c#- `Using` Anweisung oder der-Anweisung in Ihren Code [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` .

3.  Erstellen Sie in Ihrem Code ein Objekt vom Typ `DtsClient.DtsConnection` mit einer Verbindungs Zeichenfolge, die die Befehlszeilenparameter enthält, die für **dtexec.exe** zum Ausführen des Pakets erforderlich sind. Weitere Informationen finden Sie [hier](../packages/dtexec-utility.md). Öffnen Sie dann die Verbindung mit dieser Verbindungszeichenfolge. Sie können auch das **dtexecui**-Hilfsprogramm verwenden, um die erforderliche Verbindungszeichenfolge visuell zu erstellen.

    > [!NOTE]
    >  Im Beispielcode wird das Laden des Pakets aus dem Dateisystem mithilfe der `/FILE <path and filename>`-Syntax veranschaulicht. Sie können das Paket jedoch auch aus der MSDB-Datenbank mithilfe der `/SQL <package name>`-Syntax oder aus dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket mithilfe der `/DTS \<folder name>\<package name>`-Syntax laden.

4.  Erstellen Sie ein Objekt vom Typ `DtsClient.DtsCommand`, das die zuvor erstellte `DtsConnection` verwendet und die `CommandText`-Eigenschaft auf den Namen des DataReader-Ziels in dem Paket festlegt. Rufen Sie dann die `ExecuteReader`-Methode des Befehlsobjekts auf, um die Paketergebnisse in ein neues DataReader-Ziel zu laden.

5.  Optional können Sie die Ausgabe des Pakets indirekt parametrisieren, indem Sie die Auflistung von `DtsDataParameter`-Objekten im `DtsCommand`-Objekt verwenden, um Werte an die in dem Paket definierten Variablen zu übergeben. Innerhalb des Pakets können Sie diese Variablen als Abfrageparameter oder in Ausdrücken verwenden, um die an das DataReader-Ziel zurückgegebenen Ergebnisse zu beeinflussen. Sie müssen diese Variablen im Paket im **DtsClient** -Namespace definieren, bevor Sie Sie mit dem- `DtsDataParameter` Objekt aus einer Client Anwendung verwenden können. (Möglicherweise müssen Sie im Fenster **Variablen** auf die Symbolleisten Schaltfläche **Variablen Spalten auswählen** klicken, um die Spalte **Namespace** anzuzeigen.) Lassen Sie in Ihrem Client Code, wenn Sie der-Auflistung der einen hinzufügen `DtsDataParameter` `Parameters` `DtsCommand` , den DtsClient-Namespace Verweis aus dem Variablennamen weglassen. Beispiel:

    ```
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));
    ```

6.  Rufen Sie die `Read`-Methode des DataReader so oft wie benötigt wiederholt auf, um die Zeilen der Ausgabedaten zu durchlaufen. Verwenden Sie die Daten, oder speichern Sie die Daten zur späteren Verwendung in der Clientanwendung.

    > [!IMPORTANT]
    >  Die `Read`-Methode dieser Implementierung des DataReader gibt, nachdem die letzte Zeile der Daten gelesen wurde, `true` noch ein weiteres Mal zurück. Daher ist es schwierig, den normalen Code zu verwenden, der den DataReader durchläuft, während von `Read``true` zurückgegeben wird. Wenn der Code versucht, den DataReader oder die Verbindung nach dem Lesen der erwarteten Anzahl von Reihen zu schließen, ohne einen weiteren finalen Aufruf der `Read`-Methode durchzuführen, gibt der Code eine nicht behandelte Ausnahme aus. Wenn der Code jedoch versucht, die Daten bei dieser letzten Iteration durch eine Schleife zu lesen und von `Read` immer noch `true` zurückgegeben wird, die letzte Zeile jedoch übergeben wurde, gibt der Code eine nicht behandelte `ApplicationException` mit der folgenden Meldung aus: "Das SSIS-IDataReader-Objekt liegt hinter dem Ende des Resultsets." Dieses Verhalten unterscheidet sich von dem anderer DataReader-Implementierungen. Wenn Sie daher eine Schleife verwenden, um die Zeilen in dem DataReader zu lesen, und von `Read` wird `true` zurückgegeben, müssen Sie den Code so schreiben, dass diese erwartete `ApplicationException` beim letzten erfolgreichen Aufruf der `Read`-Methode abgefangen, getestet und verworfen wird. Sie können auch, wenn Sie die Anzahl von erwarteten Zeilen im Voraus wissen, die Zeilen verarbeiten und dann die `Read`-Methode ein letztes Mal aufrufen, bevor Sie den DataReader und die Verbindung schließen.

7.  Rufen Sie die `Dispose`-Methode des `DtsCommand`-Objekts auf. Dies ist besonders wichtig, wenn Sie `DtsDataParameter`-Objekte verwendet haben.

8.  Schließen Sie den DataReader und die Verbindungsobjekte.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird ein Paket ausgeführt, das einen einzelnen Aggregatwert berechnet und den Wert in einem DataReader-Ziel speichert. Dieser Wert wird dann vom DataReader gelesen und in einem Textfeld in einem Windows Form angezeigt.

 Beim Laden der Ausgabe eines Pakets in einer Clientanwendung müssen keine Parameter verwendet werden. Wenn Sie keinen Parameter verwenden möchten, können Sie die Verwendung der Variablen im **DtsClient** -Namespace weglassen und den Code weglassen, der das- `DtsDataParameter` Objekt verwendet.

#### <a name="to-create-the-test-package"></a>So erstellen Sie das Testpaket

1.  Erstellen Sie ein neues [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket. Im Beispielcode wird "DtsClientWParamPkg.dtsx" als Name des Pakets verwendet.

2.  Fügen Sie eine Variable der Typzeichenfolge im DtsClient-Namespace hinzu. Der Beispielscode verwendet "Country" als den Namen der Variablen. (Möglicherweise müssen Sie im Fenster **Variablen** auf **Variablenspalten auswählen** auf der Symbolleiste klicken, um die Spalte **Namespace** anzuzeigen.)

3.  Fügen Sie einen OLE DB-Verbindungs-Manager hinzu, der eine Verbindung zu der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Beispieldatenbank herstellt.

4.  Fügen Sie dem Paket einen Datenflusstask hinzu, und wechseln Sie zur Datenfluss-Entwurfsoberfläche.

5.  Fügen Sie dem Datenfluss eine OLE DB-Quelle hinzu, und konfigurieren Sie sie so, dass der zuvor erstellte OLE DB-Verbindungs-Manager verwendet werden kann, den Sie vorher erstellt haben. Fügen Sie auch den folgenden SQL-Befehl hinzu:

    ```
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?
    ```

6.  Klicken Sie auf, und ordnen Sie `Parameters` im Dialogfeld **Abfrage Parameter festlegen** den einzelnen Eingabeparameter in der Abfrage, Parameter0, der DtsClient:: Country-Variablen zu.

7.  Fügen Sie dem Datenfluss eine Transformation für das Aggregieren hinzu, und verbinden Sie die Ausgabe der OLE DB-Quelle mit der Transformation. Öffnen Sie den Transformations-Editor für Aggregieren, und konfigurieren Sie ihn so, dass er einen "count all"-Vorgang für alle Eingabe Spalten (*) ausführt und den aggregierten Wert mit dem Alias CustomerCount ausgibt.

8.  Fügen Sie dem Datenfluss ein DatenReader-Ziel hinzu, und verbinden Sie die Ausgabe der Transformation für das Aggregieren mit dem DataReader-Ziel. Im Beispielcode wird "DataReaderDest" als Name des DataReader verwendet. Wählen Sie die einzelne verfügbare Eingabespalte, CustomerCount, für das Ziel aus.

9. Speichern Sie das Paket. Die anschließend erstellte Testanwendung führt das Paket aus und ruft seine Ausgabe direkt vom Arbeitsspeicher ab.

#### <a name="to-create-the-test-application"></a>So erstellen Sie die Testanwendung

1.  Erstellen Sie eine neue Windows Forms-Anwendung.

2.  Fügen Sie einen Verweis auf den- `Microsoft.SqlServer.Dts.DtsClient` Namespace hinzu, indem Sie die Assembly mit demselben Namen in **%ProgramFiles%\Microsoft SQL server\100\dz\binn**suchen.

3.  Kopieren Sie den folgenden Beispielcode, und fügen Sie ihn in das Codemodul für das Formular ein.

4.  Ändern Sie den Wert der `dtexecArgs` Variablen nach Bedarf, damit Sie die Befehlszeilenparameter enthält, die für **dtexec.exe** zum Ausführen des Pakets erforderlich sind. Im Beispielcode wird das Paket aus dem Dateisystem geladen.

5.  Ändern Sie den Wert der `dataReaderName` Variablen nach Bedarf, damit Sie den Namen des DataReader-Ziels im Paket enthält.

6.  Setzen Sie eine Schaltfläche und ein Textfeld in das Formular. Im Beispielcode `btnRun` wird als Name der Schaltfläche und `txtResults` als Name des Textfelds verwendet.

7.  Führen Sie die Anwendung aus, und klicken Sie auf die Schaltfläche. Nach einer kurzen Pause während der Ausführung des Pakets sollte der von dem Paket berechnete Aggregatwert (die Anzahl von Kunden in Kanada) im Textfeld auf dem Formular angezeigt werden.

### <a name="sample-code"></a>Beispielcode

```vb
Imports System.Data
Imports Microsoft.SqlServer.Dts.DtsClient

Public Class Form1

  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click

    Dim dtexecArgs As String
    Dim dataReaderName As String
    Dim countryName As String

    Dim dtsConnection As DtsConnection
    Dim dtsCommand As DtsCommand
    Dim dtsDataReader As IDataReader
    Dim dtsParameter As DtsDataParameter

    Windows.Forms.Cursor.Current = Cursors.WaitCursor

    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""
    dataReaderName = "DataReaderDest"
    countryName = "Canada"

    dtsConnection = New DtsConnection()
    With dtsConnection
      .ConnectionString = dtexecArgs
      .Open()
    End With

    dtsCommand = New DtsCommand(dtsConnection)
    dtsCommand.CommandText = dataReaderName

    dtsParameter = New DtsDataParameter("Country", DbType.String)
    dtsParameter.Direction = ParameterDirection.Input
    dtsCommand.Parameters.Add(dtsParameter)

    dtsParameter.Value = countryName

    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)

    With dtsDataReader
      .Read()
      txtResults.Text = .GetInt32(0).ToString("N0")
    End With

    'After reaching the end of data rows,
    ' call the Read method one more time.
    Try
      dtsDataReader.Read()
    Catch ex As Exception
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception on final call to Read method", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    ' The following method is a best practice, and is
    '  required when using DtsDataParameter objects.
    dtsCommand.Dispose()

    Try
      dtsDataReader.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing DataReader", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Try
      dtsConnection.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing connection", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Windows.Forms.Cursor.Current = Cursors.Default

  End Sub

End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Data;
using Microsoft.SqlServer.Dts.DtsClient;

namespace DtsClientWParamCS
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);
    }

    private void btnRun_Click(object sender, EventArgs e)
    {
      string dtexecArgs;
      string dataReaderName;
      string countryName;

      DtsConnection dtsConnection;
      DtsCommand dtsCommand;
      IDataReader dtsDataReader;
      DtsDataParameter dtsParameter;

      Cursor.Current = Cursors.WaitCursor;

      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";
      dataReaderName = "DataReaderDest";
      countryName = "Canada";

      dtsConnection = new DtsConnection();
      {
        dtsConnection.ConnectionString = dtexecArgs;
        dtsConnection.Open();
      }

      dtsCommand = new DtsCommand(dtsConnection);
      dtsCommand.CommandText = dataReaderName;

      dtsParameter = new DtsDataParameter("Country", DbType.String);
      dtsParameter.Direction = ParameterDirection.Input;
      dtsCommand.Parameters.Add(dtsParameter);

      dtsParameter.Value = countryName;

      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);

      {
        dtsDataReader.Read();
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");
      }

      //After reaching the end of data rows,
      // call the Read method one more time.
      try
      {
        dtsDataReader.Read();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      // The following method is a best practice, and is
      //  required when using DtsDataParameter objects.
      dtsCommand.Dispose();

      try
      {
        dtsDataReader.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      try
      {
        dtsConnection.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      Cursor.Current = Cursors.Default;

    }
  }
}
```

![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

## <a name="see-also"></a>Weitere Informationen
 Grundlegendes zu [den Unterschieden zwischen der lokalen und der Remote Ausführung von](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) [Laden und Ausführen eines lokalen Pakets](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) Programm [Gesteuertes Laden und Ausführen eines Remote Pakets](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)


