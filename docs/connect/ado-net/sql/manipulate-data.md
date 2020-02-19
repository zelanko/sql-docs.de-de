---
title: Bearbeiten von Daten
description: Beispiele für das Programmieren von MARS-Anwendungen.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 7855ef064061957cbc44dfcb4b075ebbd3893325
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247734"
---
# <a name="manipulating-data"></a>Bearbeiten von Daten

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Vor der Einführung von MARS (Multiple Active Result Sets, mehrere aktive Resultsets) mussten Entwickler entweder mehrere Verbindungen oder serverseitige Cursor verwenden, um bestimmte Szenarien aufzulösen. Bei der Verwendung mehrerer Verbindungen in einem Transaktionskontext waren darüber hinaus gebundene Verbindungen (mit **sp_getbindtoken** und **sp_bindsession**) erforderlich. In den folgenden Szenarien wird gezeigt, wie eine MARS-fähige Verbindung anstelle mehrerer Verbindungen verwendet wird.  
  
## <a name="using-multiple-commands-with-mars"></a>Verwenden mehrerer Befehle mit MARS  
Die folgende Konsolenanwendung veranschaulicht die Verwendung zweier <xref:Microsoft.Data.SqlClient.SqlDataReader>-Objekte mit zwei <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekten und einem einzelnen <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekt bei aktiviertem MARS.  
  
### <a name="example"></a>Beispiel  
Im Beispiel wird eine einzelne Verbindung mit der **AdventureWorks**-Datenbank geöffnet. Wenn Sie ein <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt verwenden, wird ein <xref:Microsoft.Data.SqlClient.SqlDataReader> erstellt. Bei Verwenden des Readers wird ein zweiter <xref:Microsoft.Data.SqlClient.SqlDataReader> geöffnet, wobei die Daten aus dem ersten <xref:Microsoft.Data.SqlClient.SqlDataReader> als Eingabe in die WHERE-Klausel für den zweiten Reader verwendet werden.  
  
> [!NOTE]
>  Im folgenden Beispiel wird die in SQL Server enthaltene **AdventureWorks**-Beispieldatenbank verwendet. Bei der im Beispielcode bereitgestellten Verbindungszeichenfolge wird davon ausgegangen, dass die Datenbank auf dem lokalen Computer installiert und verfügbar ist. Ändern Sie die Verbindungszeichenfolge nach Bedarf für Ihre Umgebung.  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a>Lesen und Aktualisieren von Daten mit MARS  
MARS ermöglicht die Verwendung einer Verbindung sowohl für Lese- als auch für DML-Vorgänge (Data Manipulation Language, Datenbearbeitungssprache) mit mehr als einem ausstehenden Vorgang. Dieses Feature macht eine Anwendung zur Behandlung von Fehlern im Zusammenhang mit der Verbindungsauslastung überflüssig. Darüber hinaus kann MARS die Verwendung serverseitiger Cursor ersetzen, die im Allgemeinen mehr Ressourcen benötigen. Da außerdem mehrere Vorgänge über eine einzelne Verbindung ausgeführt werden können, kann ein gemeinsamer Transaktionskontext verwendet werden. Dadurch ist die Verwendung der gespeicherten Systemprozeduren **sp_getbindtoken** und **sp_bindsession** nicht mehr erforderlich.  
  
### <a name="example"></a>Beispiel  
Die folgende Konsolenanwendung veranschaulicht die Verwendung zweier <xref:Microsoft.Data.SqlClient.SqlDataReader>-Objekte mit drei <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekten und einem einzelnen <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekt bei aktiviertem MARS. Das erste Befehlsobjekt ruft eine Liste von Anbietern ab, deren Bonitätsbewertung 5 ist. Das zweite Befehlsobjekt verwendet die von einem <xref:Microsoft.Data.SqlClient.SqlDataReader> bereitgestellte Anbieter-ID, um den zweiten <xref:Microsoft.Data.SqlClient.SqlDataReader> mit allen Produkten für den bestimmten Anbieter zu laden. Jeder Produktdatensatz wird vom zweiten <xref:Microsoft.Data.SqlClient.SqlDataReader> besucht. Es wird eine Berechnung ausgeführt, um den neuen Wert für **OnOrderQty** zu bestimmen. Anschließend wird mithilfe des dritten Befehlsobjekts die **ProductVendor**-Tabelle mit dem neuen Wert aktualisiert. Der gesamte Prozess findet innerhalb einer einzelnen Transaktion statt, für die am Ende ein Rollback erfolgt.  
  
> [!NOTE]
>  Im folgenden Beispiel wird die in SQL Server enthaltene **AdventureWorks**-Beispieldatenbank verwendet. Bei der im Beispielcode bereitgestellten Verbindungszeichenfolge wird davon ausgegangen, dass die Datenbank auf dem lokalen Computer installiert und verfügbar ist. Ändern Sie die Verbindungszeichenfolge nach Bedarf für Ihre Umgebung.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Mehrere aktive Resultsets (MARS)](multiple-active-result-sets-mars.md)
