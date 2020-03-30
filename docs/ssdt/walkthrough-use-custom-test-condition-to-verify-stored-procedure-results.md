---
title: Benutzerdefinierte Testbedingung zur Überprüfung der Ergebnisse einer gespeicherten Prozedur
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 4c33b494-a85e-4dd2-97b6-c88ee858a99c
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 60160fe3f36d61364b8bf4385fa53b744f9a3475
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79286594"
---
# <a name="walkthrough-using-a-custom-test-condition-to-verify-the-results-of-a-stored-procedure"></a>Exemplarische Vorgehensweise: Verwenden einer benutzerdefinierten Testbedingung zur Überprüfung der Ergebnisse einer gespeicherten Prozedur

In dieser exemplarischen Vorgehensweise zu Funktionserweiterungen erstellen Sie eine Testbedingung und überprüfen deren Funktionsfähigkeit, indem Sie einen SQL Server-Komponententest erstellen. In diesem Verfahren wird ein Klassenbibliotheksprojekt für die Testbedingung erstellt und die Testbedingung signiert und installiert. Wenn Sie bereits eine Testbedingung haben, die aktualisiert werden soll, lesen Sie [Gewusst wie: Durchführen eines Upgrades für eine benutzerdefinierte Visual Studio 2010-Testbedingung von einem älteren Release auf SQL Server Data Tools](../ssdt/how-to-upgrade-visual-studio-2010-custom-test-condition-to-ssdt.md).  
  
In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einer Testbedingung  
  
-   Signieren der Assembly mit einem starken Namen  
  
-   Hinzufügen der erforderlichen Verweise zum Projekt  
  
-   Erstellen einer Testbedingung  
  
-   Installieren der neuen Testbedingung  
  
-   Testen der neuen Testbedingung  
  
Für die Durchführung dieser exemplarischen Vorgehensweise müssen Sie Visual Studio 2010 oder Visual Studio 2012 mit der neuesten Version von SQL Server Data Tools verwenden. Weitere Informationen finden Sie unter [Installieren von SQL Server Data Tools](../ssdt/install-sql-server-data-tools.md).  
  
## <a name="creating-a-custom-test-condition"></a>Erstellen einer benutzerdefinierten Testbedingung  
Zunächst erstellen Sie eine Klassenbibliothek.  
  
1.  Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **Projekttypen** auf „Visual C\#“.  
  
3.  Wählen Sie unter **Vorlagen** den Eintrag **Klassenbibliothek** aus.  
  
4.  Geben Sie im Textfeld **Name** den Namen **ColumnCountCondition** ein, und klicken Sie dann auf **OK**.  
  
Als Nächstes signieren Sie das Projekt.  
  
1.  Klicken Sie im Menü **Projekt** auf **ColumnCountCondition-Eigenschaften**.  
  
2.  Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.  
  
3.  Klicken Sie im Feld **Schlüsseldatei mit starkem Namen wählen** auf **\<Neu...>** .  
  
    Das Dialogfeld **Schlüssel mit starkem Namen erstellen** wird geöffnet.  
  
4.  Geben Sie im Feld **Schlüsseldateiname** die Zeichenfolge **SampleKey** ein.  
  
5.  Geben Sie das Kennwort ein, bestätigen Sie es, und klicken Sie dann auf **OK**. Wenn Sie die Projektmappe erstellen, wird die Schlüsseldatei zum Signieren der Assembly verwendet.  
  
6.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
7.  Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.  
  
Im nächsten Schritt fügen Sie dem Projekt die erforderlichen Verweise hinzu.  
  
1.  Wählen Sie im **Projektmappen-Explorer** das Projekt **ColumnCountCondition** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**, um das Dialogfeld **Verweis hinzufügen** anzuzeigen.  
  
3.  Wählen Sie die Registerkarte **.NET** aus.  
  
4.  Suchen Sie in der Spalte **Komponentenname** die Komponente **System.ComponentModel.Composition**, und wählen Sie sie aus. Klicken Sie auf **OK**, nachdem Sie die Komponente ausgewählt haben.  
  
5.  Fügen Sie die erforderlichen Assemblyverweise hinzu. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie auf **Durchsuchen**, und navigieren Sie zum Ordner „C:\Programme (x86)\\Microsoft SQL Server\110\DAC\Bin“. Wählen Sie „Microsoft.Data.Tools.Schema.Sql.dll“ aus, klicken Sie auf „Hinzufügen“, und klicken Sie dann auf „OK“.  
  
6.  Klicken Sie im Menü **Projekt** auf **Projekt entladen**.  
  
7.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **<project name>.csproj bearbeiten** aus.  
  
8.  Fügen Sie nach dem Import von **Microsoft.CSharp.targets** folgende Import-Anweisung hinzu:  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' == ''" />  
  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' != ''" />  
    ```  
  
9. Speichern Sie die Datei, und schließen Sie sie. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Projekt erneut laden** aus.  
  
    Die erforderlichen Verweise werden unter dem Knoten **Verweise** des Projekts im **Projektmappen-Explorer** angezeigt.  
  
## <a name="creating-the-resultsetcolumncountcondition-class"></a>Erstellen der ResultSetColumnCountCondition-Klasse  
Benennen Sie jetzt **Class1** in **ResultSetColumnCountCondition**, und leiten Sie sie von [testcondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx) ab. Die Klasse **ResultSetColumnCountCondition** ist eine einfache Testbedingung, mit der die Anzahl der im Resultset zurückgegebenen Spalten überprüft wird. Mit dieser Bedingung können Sie sicherstellen, dass der Vertrag für eine gespeicherte Prozedur richtig ist.  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf „Class1.cs“, klicken Sie auf **Umbenennen**, und geben Sie **ResultSetColumnCountCondition.cs** ein.  
  
2.  Klicken Sie auf **Ja**, um zu bestätigen, dass alle Verweise in „Class1“ umbenannt werden sollen.  
  
3.  Öffnen Sie die Datei **ResultSetColumnCountCondition.cs**, und fügen Sie der Datei die folgenden using-Anweisungen hinzu:  
  
    ```  
    using System;  
    using System.ComponentModel;  
    using System.Data;  
    using System.Data.Common;  
    using Microsoft.Data.Tools.Schema.Sql.UnitTesting;  
    using Microsoft.Data.Tools.Schema.Sql.UnitTesting.Conditions;  
  
    namespace ColumnCountCondition {  
        public class ResultSetColumnCountCondition  
    ```  
  
4.  Leiten Sie die Klasse von [testcondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx) ab:  
  
    ```  
    public class ResultSetColumnCountCondition : TestCondition  
    ```  
  
5.  Fügen Sie [ExportTestConditionAttribute](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.exporttestconditionattribute(v=vs.103).aspx) hinzu. Weitere Informationen zu UnitTesting.Conditions.ExportTestConditionAttribute finden Sie unter [Gewusst wie: Erstellen von Testbedingungen für den SQL Server Komponententest-Designer](../ssdt/how-to-create-test-conditions-for-the-sql-server-unit-test-designer.md).  
  
    ```  
    [ExportTestCondition("ResultSet Column Count", typeof(ResultSetColumnCountCondition))]  
        public class ResultSetColumnCountCondition : TestCondition  
    ```  
  
6.  Erstellen Sie die Membervariablen und den Konstruktor:  
  
    ```  
            private int _resultSet;  
            private int _count;  
            private int _batch;  
  
            public ResultSetColumnCountCondition() {  
                _resultSet = 1;  
                _count = 0;  
                _batch = 1;  
            }  
    ```  
  
7.  Überschreiben Sie die **Assert**-Methode. Die Methode enthält Argumente für **IDbConnection**, d.h. die Verbindung mit der Datenbank, sowie **SqlExecutionResult**. In der Methode wird **DataSchemaException** für die Fehlerbehandlung verwendet:  
  
    ```  
           //method you need to override  
            //to perform the condition verification  
            public override void Assert(DbConnection validationConnection, SqlExecutionResult[] results)  
            {  
                //call base for parameter validation  
                base.Assert(validationConnection, results);  
  
                //verify batch exists  
                if (results.Length < _batch)  
                    throw new DataException(String.Format("Batch {0} does not exist", _batch));  
  
                SqlExecutionResult result = results[_batch - 1];  
  
                //verify resultset exists  
                if (result.DataSet.Tables.Count < ResultSet)  
                    throw new DataException(String.Format("ResultSet {0} does not exist", ResultSet));  
  
                DataTable table = result.DataSet.Tables[ResultSet - 1];  
  
                //actual condition verification  
                //verify resultset column count matches expected  
                if (table.Columns.Count != Count)  
                    throw new DataException(String.Format(  
                        "ResultSet {0}: {1} columns did not match the {2} columns expected",  
                        ResultSet, table.Columns.Count, Count));  
            }  
  
    Add the following method, which overrides the ToString method:  
    C#  
            //this method is called to provide the string shown in the  
            //test conditions panel grid describing what the condition tests  
            public override string ToString()  
            {  
                return String.Format(  
                    "Condition fails if ResultSet {0} does not contain {1} columns",  
                    ResultSet, Count);  
            }  
    ```  
  
8.  Fügen Sie die folgenden Eigenschaften für Testbedingungen hinzu, indem Sie die Attribute **CategoryAttribute**, **DisplayNameAttribute**, und **DescriptionAttribute** verwenden:  
  
    ```  
            //below are the test condition properties  
            //that are exposed to the user in the property browser  
            #region Properties  
  
            //property specifying the resultset for which  
            //you want to check the column count  
            [Category("Test Condition")]  
            [DisplayName("ResultSet")]  
            [Description("ResultSet Number")]  
            public int ResultSet  
            {  
                get { return _resultSet; }  
  
                set  
                {  
                    //basic validation  
                    if (value < 1)  
                        throw new ArgumentException("ResultSet cannot be less than 1");  
  
                    _resultSet = value;  
                }  
            }  
  
            //property specifying  
            //expected column count  
            [Category("Test Condition")]  
            [DisplayName("Count")]  
            [Description("Column Count")]  
            public int Count  
            {  
                get { return _count; }  
  
                set  
                {  
                    //basic validation  
                    if (value < 0)  
                        throw new ArgumentException("Count cannot be less than 0");  
  
                    _count = value;  
                }  
            }  
             #endregion  
    ```  
  
Die fertige Codeauflistung lautet:  
  
```  
using System;  
using System.ComponentModel;  
using System.Data;  
using System.Data.Common;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting.Conditions;  
  
namespace ColumnCountCondition  
{  
  
    [ExportTestCondition("ResultSet Column Count", typeof(ResultSetColumnCountCondition))]  
    public class ResultSetColumnCountCondition : TestCondition  
    {  
        private int _resultSet;  
        private int _count;  
        private int _batch;  
  
        public ResultSetColumnCountCondition()  
        {  
            _resultSet = 1;  
            _count = 0;  
            _batch = 1;  
        }  
  
        //method you need to override  
        //to perform the condition verification  
        public override void Assert(DbConnection validationConnection, SqlExecutionResult[] results)  
        {  
            //call base for parameter validation  
            base.Assert(validationConnection, results);  
  
            //verify batch exists  
            if (results.Length < _batch)  
                throw new DataException(String.Format("Batch {0} does not exist", _batch));  
  
            SqlExecutionResult result = results[_batch - 1];  
  
            //verify resultset exists  
            if (result.DataSet.Tables.Count < ResultSet)  
                throw new DataException(String.Format("ResultSet {0} does not exist", ResultSet));  
  
            DataTable table = result.DataSet.Tables[ResultSet - 1];  
  
            //actual condition verification  
            //verify resultset column count matches expected  
            if (table.Columns.Count != Count)  
                throw new DataException(String.Format(  
                    "ResultSet {0}: {1} columns did not match the {2} columns expected",  
                    ResultSet, table.Columns.Count, Count));  
        }  
  
        //this method is called to provide the string shown in the  
        //test conditions panel grid describing what the condition tests  
        public override string ToString()  
        {  
            return String.Format(  
                "Condition fails if ResultSet {0} does not contain {1} columns",  
                ResultSet, Count);  
        }  
  
        //below are the test condition properties  
        //that are exposed to the user in the property browser  
        #region Properties  
  
        //property specifying the resultset for which  
        //you want to check the column count  
        [Category("Test Condition")]  
        [DisplayName("ResultSet")]  
        [Description("ResultSet Number")]  
        public int ResultSet  
        {  
            get { return _resultSet; }  
  
            set  
            {  
                //basic validation  
                if (value < 1)  
                    throw new ArgumentException("ResultSet cannot be less than 1");  
  
                _resultSet = value;  
            }  
        }  
  
        //property specifying  
        //expected column count  
        [Category("Test Condition")]  
        [DisplayName("Count")]  
        [Description("Column Count")]  
        public int Count  
        {  
            get { return _count; }  
  
            set  
            {  
                //basic validation  
                if (value < 0)  
                    throw new ArgumentException("Count cannot be less than 0");  
  
                _count = value;  
            }  
        }  
  
        #endregion  
    }  
}  
  
```  
  
Als Nächstes wird das Projekt erstellt.  
  
## <a name="compiling-the-project-and-installing-your-test-condition"></a><a name="xxx"></a>Kompilieren des Projekts und Installieren der Testbedingung  
Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.  
  
Im nächsten Schritt kopieren Sie die Assemblyinformationen in das Verzeichnis „Extensions“. Beim Start von Visual Studio werden alle Erweiterungen im Ordner „%Programme%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions“ und in dessen Unterverzeichnissen identifiziert und für die Verwendung zur Verfügung gestellt:  
  
Kopieren Sie die Assemblydatei **ColumnCountCondition.dll** aus dem Ausgabeverzeichnis in das Verzeichnis „%Programme%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions“.  
  
Der Pfad Ihrer kompilierten DLL-Datei lautet standardmäßig „*IhrProjektmappenpfad*\\*IhrProjektpfad*\bin\Debug“ oder „*IhrProjektmappenpfad*\\*IhrProjektpfad*\bin\Release“.  
  
Als Nächstes starten Sie eine neue Visual Studio-Sitzung und erstellen ein Datenbankprojekt. So starten Sie eine neue Visual Studio-Sitzung und erstellen ein Datenbankprojekt  
  
1.  Starten Sie eine zweite Visual Studio-Sitzung.  
  
2.  Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.  
  
3.  Wählen Sie im Dialogfeld **Neues Projekt** in der Liste installierter Vorlagen den Knoten **SQL Server** aus.  
  
4.  Klicken Sie im Detailbereich auf **SQL Server-Datenbankprojekt**.  
  
5.  Geben Sie im Textfeld **Name** den Namen **SampleConditionDB** ein, und klicken Sie dann auf **OK**.  
  
Jetzt muss ein Komponententest erstellt werden. So erstellen Sie einen SQL Server-Komponententest in einer neuen Testklasse  
  
1.  Klicken Sie im Menü **Test** auf **Neuer Test**, um das Dialogfeld **Neuen Test hinzufügen** aufzurufen.  
  
    Sie können auch den **Projektmappen-Explorer** öffnen, mit der rechten Maustaste auf ein Testprojekt klicken, auf **Hinzufügen** zeigen und dann auf **Neuer Test** klicken.  
  
2.  Klicken Sie in der Vorlagenliste auf **SQL Server-Komponententest**.  
  
3.  Geben Sie unter **Testname** Folgendes ein: **SampleUnitTest**.  
  
4.  Klicken Sie unter **Zu Testprojekt hinzufügen** auf **Neues Visual C\#-Testprojekt erstellen**. Klicken Sie dann auf **OK**, um das Dialogfeld **Neues Testprojekt** anzuzeigen.  
  
5.  Geben Sie als Projektnamen **SampleUnitTest** ein.  
  
6.  Klicken Sie auf **Abbrechen**, um den Komponententest zu erstellen, ohne dass das Testprojekt für die Verwendung einer Datenbankverbindung konfiguriert wird. Der leere Test wird im SQL Server-Komponententest-Designer angezeigt. Dem Testprojekt wird eine Visual C\#-Quellcodedatei hinzugefügt.  
  
    Weitere Informationen zum Erstellen und Konfigurieren von Datenbankkomponententests mit Datenbankverbindungen finden Sie unter [Gewusst wie: Erstellen eines leeren SQL Server-Komponententests](../ssdt/how-to-create-an-empty-sql-server-unit-test.md).  
  
7.  Klicken Sie auf **Klicken Sie zum Erstellen hierauf**, um die Erstellung des Komponententests abzuschließen. Die neue Testbedingung wird im SQL Server-Projekt angezeigt.  
  
> [!NOTE]  
> Zur Verwendung der benutzerdefinierten Testbedingung mit vorhandenen Komponententestprojekten muss mindestens eine neue SQL Server-Komponententestklasse erstellt werden. Der erforderliche Verweis auf die Testbedingungsassembly wird dem Testprojekt während der Erstellung der Testklasse hinzugefügt.  
  
So zeigen Sie die neue Testbedingung an  
  
1.  Klicken Sie im **SQL Server-Komponententest-Designer** unter **Testbedingungen** unter der Spalte **Name** auf den Test „inconclusiveCondition1“.  
  
2.  Klicken Sie auf die Symbolleistenschaltfläche **Testbedingung löschen**, um den Test „inconclusiveCondition1“ zu entfernen.  
  
3.  Klicken Sie auf das Dropdownmenü **Testbedingungen**, und wählen Sie **ResultSet-Spaltenanzahl** aus.  
  
4.  Klicken Sie auf die Symbolleistenschaltfläche **Testbedingung hinzufügen**, um die benutzerdefinierte Testbedingung hinzuzufügen.  
  
5.  Konfigurieren Sie im Fenster **Eigenschaften** die Eigenschaften „Count“, „Enabled“ und „ResultSet“.  
  
    Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Testbedingungen zu SQL Server-Komponententests](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Benutzerdefinierte Testbedingungen für SQL Server-Komponententests](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
  
