---
title: Verarbeiten von XML auf der Client Seite (SQLXML)
description: Erfahren Sie, wie Sie XML auf Clientseite mithilfe der ClientSideXML-Eigenschaft des SqlXmlCommand-Objekts in den verwalteten SQLXML-Klassen verarbeiten.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 42f55477c59b85945ccb1f0b776f9ab8ac2125b3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97430923"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a>Clientseitige Verarbeitung von XML (Verwaltete Klassen in SQLXML)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  In diesem Beispiel wird die Verwendung der ClientSideXML-Eigenschaft veranschaulicht. Die Anwendung führt eine gespeicherte Prozedur auf dem Server aus. Das Ergebnis der gespeicherten Prozedur (ein Rowset mit zwei Spalten) wird auf der Clientseite verarbeitet und ein XML-Dokument produziert.  
  
 Mit der folgenden gespeicherten Prozedur GetContacts werden **FirstName** und **LastName** von Mitarbeitern in der Person. Contact-Tabelle der AdventureWorks-Datenbank zurückgegeben.  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 Diese c#-Anwendung führt die gespeicherte Prozedur aus und gibt die for XML Auto-Option in der Angabe des CommandText-Werts an. In der Anwendung ist die ClientSideXML-Eigenschaft des SqlXmlCommand-Objekts auf "true" festgelegt. Auf diese Weise können Sie bereits bestehende gespeicherte Prozeduren ausführen, die ein Rowset zurückgeben und auf dem Client eine XML-Transformation auf das Rowset anwenden.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
    static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
 Um das Beispiel zu testen, muss auf dem Computer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installiert sein.  
  
### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Erstellen Sie die gespeicherte Prozedur.  
  
2.  Speichern Sie den in diesem Beispiel bereitgestellten C#-Code (DocSample.cs) in einem Ordner. Bearbeiten Sie den Code, um entsprechende Anmelde- und Kennwortinformationen anzugeben.  
  
3.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DocSample.exe) erstellt.  
  
4.  Führen Sie DocSample.exe an der Eingabeaufforderung aus.  

