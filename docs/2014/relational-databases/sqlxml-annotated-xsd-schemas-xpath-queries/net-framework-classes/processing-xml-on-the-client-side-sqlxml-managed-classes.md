---
title: Verarbeitung von XML auf dem Client (verwaltete SQLXML Klassen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 242e06d72b7a1773235e51c7211b2526af6d4608
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201100"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a>Clientseitige Verarbeitung von XML (Verwaltete Klassen in SQLXML)
  Dieses Beispiel veranschaulicht die Verwendung der ClientSideXml-Eigenschaft. Die Anwendung führt eine gespeicherte Prozedur auf dem Server aus. Das Ergebnis der gespeicherten Prozedur (ein Rowset mit zwei Spalten) wird auf der Clientseite verarbeitet und ein XML-Dokument produziert.  
  
 Die folgenden GetContacts gespeicherte Prozedur gibt **FirstName** und **"LastName"** von Mitarbeitern in der Person.Contact-Tabelle in der AdventureWorks-Datenbank.  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 Diese C#-Anwendung führt die gespeicherte Prozedur und gibt die FOR XML AUTO-Option bei der Angabe des CommandText-Werts. In der Anwendung die ClientSideXml-Eigenschaft des SqlXmlCommand-Objekt festgelegt ist auf "true". Auf diese Weise können Sie bereits bestehende gespeicherte Prozeduren ausführen, die ein Rowset zurückgeben und auf dem Client eine XML-Transformation auf das Rowset anwenden.  
  
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
  
  
