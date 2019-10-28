---
title: Einfügen eines Bilds aus einer Datei
description: Beschreibt das Arbeiten mit einem Bild aus einer Datei.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d8f7b561a6aba4539964d73dacfd9e45db2dd6aa
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452178"
---
# <a name="inserting-an-image-from-a-file"></a>Einfügen eines Bilds aus einer Datei

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Je nach Feldtyp in der Datenquelle können Sie eine Binary Large Object (BLOB) als Binär-oder Zeichendaten in eine Datenbank schreiben. BLOB ist ein allgemeiner Begriff, der sich auf die Datentypen `text`, `ntext` und `image` bezieht, die in der Regel Dokumente und Bilder enthalten.  
  
Um einen BLOB-Wert in die Datenbank zu schreiben, geben Sie die entsprechende INSERT- oder UPDATE-Anweisung aus, und übergeben Sie den BLOB-Wert als Eingabeparameter. Wenn Ihr BLOB als Text gespeichert wird, z. b. ein SQL Server `text` Feld, können Sie das BLOB als Zeichen folgen Parameter übergeben. Wenn das BLOB im Binärformat gespeichert wird, z. b. in einem SQL Server `image` Feld, können Sie ein Array vom Typ `byte` als binären Parameter übergeben.
  
## <a name="example"></a>Beispiel  
Im folgenden Codebeispiel werden der Employees-Tabelle in der Northwind-Datenbank Mitarbeiter Informationen hinzugefügt. Ein Foto des Mitarbeiters wird aus einer Datei gelesen und dem Photo-Feld in der Tabelle hinzugefügt, einem Bildfeld.  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Binäre Daten und Daten mit umfangreichen Werten in SQL Server](sql-server-binary-large-value-data.md)
