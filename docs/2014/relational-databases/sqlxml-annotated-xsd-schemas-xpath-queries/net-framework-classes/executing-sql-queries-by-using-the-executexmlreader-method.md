---
title: Ausführen von SQL-Abfragen mithilfe der ExecuteXmlReader-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteXmlReader method
- SQL queries [SQLXML]
ms.assetid: f106a4c5-8d6e-40c0-bf1f-11e121afcb01
author: rothja
ms.author: jroth
ms.openlocfilehash: 49189e6bacd9151cd21f8c7ebfed3df63b4eb92e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062890"
---
# <a name="executing-sql-queries-by-using-the-executexmlreader-method"></a>Ausführen von SQL-Abfragen mithilfe der 'ExecuteXMLReader'-Methode
  Anstatt die executedestream-Methode zu verwenden, können Sie die ExecuteXmlReader-Methode des SqlXmlCommand-Objekts verwenden, um Befehle auszuführen. Diese Methode gibt ein XmlReader-Objekt zurück, das für die weitere Verarbeitung des Ergebnisses verwendet werden kann (in diesem Beispiel werden die Element-oder Attributnamen und die Werte gedruckt).  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml;  
   class Test  
   {  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks2012;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         SqlXmlParameter p;  
         XmlReader Reader;  
         XmlTextWriter tw;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "select FirstName, LastName from Person.Person where LastName = ? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         Reader = cmd.ExecuteXmlReader();  
            tw = new XmlTextWriter(Console.Out);  
         Reader.MoveToContent();  
         tw.WriteNode(Reader, false);  
         tw.Flush();  
         tw.Close();  
         Reader.Close();  
  
         return 0;  
      }  
  
      static int Main(string[] args)  
      {  
         testParams();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Stellen Sie sicher, dass [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework auf dem Computer installiert ist.  
  
2.  Speichern Sie den in diesem Thema bereitgestellten C#-Code (&lt;legacyBold&gt;DocSample.cs&lt;/legacyBold&gt;) in einem Ordner.  
  
3.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DocSample.exe) erstellt.  
  
4.  Führen Sie DocSample.exe an der Eingabeaufforderung aus.  
  
  
