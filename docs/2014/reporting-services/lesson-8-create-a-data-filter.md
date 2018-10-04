---
title: 'Lektion 8: Erstellen eines Datenfilters | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d5004ad7cb8283be11d7e89f96ee46bd29ccccd6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48189920"
---
# <a name="lesson-8-create-a-data-filter"></a>Lektion 8: Erstellen eines Datenfilters
  Nachdem Sie im übergeordneten Bericht eine Drillthroughaktion hinzugefügt haben, erstellen Sie im nächsten Schritt einen Datenfilter für die Datentabelle, die Sie für den untergeordneten Bericht definiert haben.  
  
 Sie können für den Drillthroughbericht einen tabellenbasierten Filter **oder** einen Abfragefilter erstellen. Diese Lektion enthält Anweisungen zum Erstellen beider Filtertypen.  
  
## <a name="table-based-filter"></a>Tabellenbasierter Filter  
 Führen Sie folgende Aufgaben aus, um einen tabellenbasierten Filter zu implementieren.  
  
-   Fügen Sie der Tablix im untergeordneten Bericht einen Filterausdruck hinzu.  
  
-   Erstellen Sie eine Funktion, mit der ungefilterte Daten aus der `PurchaseOrderDetail`-Tabelle ausgewählt werden.  
  
-   Fügen Sie einen Ereignishandler hinzu, durch den die `PurchaseOrderDetail`-DataTable an den untergeordneten Bericht gebunden wird.  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a>So fügen Sie der Tablix im untergeordneten Bericht einen Filterausdruck hinzu  
  
1.  Öffnen Sie den untergeordneten Bericht.  
  
2.  Wählen Sie in der Tablix eine Spaltenüberschrift aus, mit der rechten Maustaste in der grauen Zelle, die oberhalb der Spaltenüberschrift angezeigt wird, und klicken Sie dann auf **Tablix-Eigenschaften**.  
  
3.  Klicken Sie auf die Seite **Filter** und dann auf **Hinzufügen**.  
  
4.  In der **Ausdruck** abgelegt wird, klicken Sie `ProductID` aus der Dropdown-Liste. Dies ist die Spalte, auf die Sie den Filter anwenden.  
  
5.  Klicken Sie auf den Gleichheitsoperator (**=**)-Operator in der **Operator** Dropdown-Liste.  
  
6.  Klicken Sie auf die Schaltfläche "Ausdruck" neben der **Wert** auf **Parameter** in die **Kategorie** Bereich, und doppelklicken Sie dann auf `productid` in die  **Werte** Bereich. Das Feld **Ausdruck festlegen für: Wert** sollte jetzt einen mit **=Parameters!productid.Value**vergleichbaren Ausdruck enthalten.  
  
7.  Klicken Sie im Dialogfeld **Tablix-Eigenschaften** auf **OK** und ein zweites Mal auf **OK** .  
  
8.  Speichern Sie die RDLC-Datei.  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a>So erstellen Sie eine Funktion, durch die ungefilterte Daten aus der PurchaseOrderDetail-Tabelle ausgewählt werden  
  
1.  Erweitern Sie im Projektmappen-Explorer Default.aspx, und doppelklicken Sie dann auf Default.aspx.cs.  
  
2.  Erstellen Sie eine neue Funktion, die einen Parameter akzeptiert `productid`, vom Typ Integer und gibt eine `datatable` Objekt aus, und werden die folgenden Schritte ausgeführt.  
  
    1.  Erstellt eine Instanz des Datasets `DataSet2`, in Schritt2 erstellte [Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Herstellen einer Verbindung mit der SQL Server-Datenbank, um die in **Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht**definierte Abfrage auszuführen.  
  
    3.  Die Abfrage gibt ungefilterte Daten zurück.  
  
    4.  Füllen der DataSet-Instanz mit den ungefilterten Daten, indem die Abfrage ausgeführt wird.  
  
    5.  Zurückgeben der `PurchaseOrderDetail` DataTable.  
  
         Die Funktion sieht etwa wie folgt aus. (Sie dient nur zur Veranschaulichung. Sie können zum Abrufen der erforderlichen Daten für den untergeordneten Bericht ein beliebiges Muster verwenden.)  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a>So fügen Sie einen Ereignishandler hinzu, durch den die PurchaseOrderDetail-DataTable an den untergeordneten Bericht gebunden wird  
  
1.  Öffnen Sie Default.aspx.  
  
2.  Klicken Sie mit der rechten Maustaste auf das ReportViewer-Steuerelement, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie auf der Seite **Eigenschaften** auf das Symbol **Ereignisse** .  
  
4.  Doppelklicken Sie auf das Ereignis **Drillthrough** .  
  
     Dadurch wird dem Code ein mit folgendem Block vergleichbarer Ereignishandlerabschnitt hinzugefügt.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Vervollständigen Sie den Ereignishandler. Er sollte folgende Funktionen umfassen.  
  
    1.  Abrufen des Verweises des untergeordneten Berichtsobjekts aus dem *DrillthroughEventArgs* -Parameter.  
  
    2.  Rufen Sie die Funktion, `GetPurchaseOrderDetail`  
  
    3.  Binden der `PurchaseOrderDetail` DataTable mit dem Bericht die entsprechende Datenquelle.  
  
         Der vollständige Ereignishandlercode sollte dem folgenden ähnlich sein.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Speichern Sie die Datei.  
  
## <a name="query-filter"></a>Abfragefilter  
 Führen Sie folgende Aufgaben aus, um einen Abfragefilter zu implementieren.  
  
-   Erstellen Sie eine Funktion, die ausgewählt gefilterte Daten aus der `PurchaseOrderDetail` Tabelle.  
  
-   Fügen Sie einen Ereignishandler hinzu, durch den Parameterwerte abgerufen und die `PurchaseOrdeDetail`-DataTable an den untergeordneten Bericht gebunden wird.  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a>So erstellen Sie eine Funktion, durch die gefilterte Daten aus der PurchaseOrderDetail-Tabelle ausgewählt werden  
  
1.  Erweitern Sie im Projektmappen-Explorer Default.aspx, und doppelklicken Sie dann auf Default.aspx.cs.  
  
2.  Erstellen Sie eine neue Funktion, die einen Parameter akzeptiert `productid`, vom Typ Integer und gibt eine `datatable` Objekt und führt die folgenden.  
  
    1.  Erstellt eine Instanz des Datasets `DataSet2`, in Schritt2 erstellte [Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Herstellen einer Verbindung mit der SQL Server-Datenbank, um die in **Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht**definierte Abfrage auszuführen.  
  
    3.  Die Abfrage enthält den `productid`-Parameter, der gewährleistet, dass die zurückgegebenen Daten auf Grundlage der im übergeordneten Bericht ausgewählten `ProductID` gefiltert werden.  
  
    4.  Füllen der DataSet-Instanz mit den gefilterten Daten, indem die Abfrage ausgeführt wird.  
  
    5.  Zurückgeben der `PurchaseOrderDetail` DataTable.  
  
         Die Funktion sieht etwa wie folgt aus. (Sie dient nur zur Veranschaulichung. Sie können zum Abrufen der erforderlichen Daten für den untergeordneten Bericht ein beliebiges Muster verwenden.)  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a>So fügen Sie einen Ereignishandler hinzu, durch den Parameterwerte abgerufen und die PurchaseOrderDetail-DataTable an den untergeordneten Bericht gebunden wird  
  
1.  Öffnen Sie Default.aspx.  
  
2.  Klicken Sie auf der ReportViewer-Steuerelement, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie im Bereich **Eigenschaften** auf das Symbol **Ereignisse** .  
  
4.  Doppelklicken Sie auf das Ereignis **Drillthrough** .  
  
     Dadurch wird dem Code ein mit Folgendem vergleichbarer Ereignishandlerabschnitt hinzugefügt.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Vervollständigen Sie den Ereignishandler. Er sollte folgende Funktionen umfassen.  
  
    1.  Abrufen des Verweises des untergeordneten Berichtsobjekts aus dem *DrillthroughEventArgs* -Parameter.  
  
    2.  Abrufen der Parameterliste des untergeordneten Berichts aus dem abgerufenen untergeordneten Berichtsobjekt.  
  
    3.  Durchlaufen der Parameterauflistung und Abrufen des Werts für den Parameter `ProductID`aus dem übergeordneten Bericht übergebenen.  
  
    4.  Aufrufen der `GetPurchaseOrderDetail`-Funktion und Übergeben des Werts für den `ProductID`-Parameter.  
  
    5.  Binden der `PurchaseOrderDetail` DataTable mit dem Bericht die entsprechende Datenquelle.  
  
         Der vollständige Ereignishandlercode sollte dem folgenden ähnlich sein.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Speichern Sie die Datei.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben erfolgreich einen Datenfilter für die Datentabelle erstellt, die Sie für den untergeordneten Bericht definiert haben. Als Nächstes werden Sie die Websiteanwendung erstellen und ausführen.  
  
  
