---
title: Übersicht über benutzerdefinierte Attribute für CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8df7881dd5f38935628cb6653d57763a8846e60f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62781105"
---
# <a name="overview-of-clr-integration-custom-attributes"></a>Übersicht über benutzerdefinierte Attribute der CLR-Integration 
  Die CLR-Komponente (Common Language Runtime) von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ermöglicht den Einsatz beschreibender Schlüsselwörter, so genannter Attribute. Diese Attribute stellen weitere Informationen für viele Elemente bereit, z. B. Methoden und Klassen. Die Attribute werden mit den Metadaten des Objekts in der Assembly gespeichert. Mit Attributen kann Code für andere Entwicklungstools beschrieben oder das Laufzeitverhalten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beeinflusst werden.  
  
 Wenn Sie eine CLR-Routine bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registrieren, leitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Satz von Eigenschaften zu der Routine ab. Diese Routineneigenschaften bestimmen die Fähigkeiten der Routine, darunter auch, ob die Routine indiziert werden kann. Durch Festlegen von `DataAccess` für die `DataAccessKind.Read`-Eigenschaft können Sie beispielsweise innerhalb einer CLR-Funktion auf Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Benutzertabellen zugreifen. Das folgende Beispiel zeigt einen einfachen Fall, in dem die `DataAccess` -Eigenschaftensatz auf Daten aus einer Benutzertabelle zu erleichtern **table1**.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 Für [!INCLUDE[tsql](../../includes/tsql-md.md)]-Routinen leitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Routineneigenschaften direkt aus der Routinendefinition ab. Für CLR-Routinen analysiert der Server den Routinentext nicht, um diese Eigenschaften abzuleiten. Stattdessen können Sie benutzerdefinierte Attribute für Klassen und Klassenmember verwenden, die in einer [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Sprache implementiert wurden.  
  
 Die für CLR-Routinen benötigten benutzerdefinierten Attribute, benutzerdefinierte Typen und Aggregate werden im `Microsoft.SqlServer.Server`-Namespace definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierte Attribute für CLR-Routinen](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  
