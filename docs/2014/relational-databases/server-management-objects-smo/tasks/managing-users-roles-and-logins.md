---
title: Verwalten von Benutzern, Rollen und Anmeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 36119391ebd552e1b3553e94ba3fcf0634887560
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134580"
---
# <a name="managing-users-roles-and-logins"></a>Verwalten von Benutzern, Rollen und Anmeldungen
  In SMO werden Anmeldungen durch das <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekt dargestellt. Wenn die Anmeldung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vorhanden ist, kann sie zu einer Serverrolle hinzugefügt werden. Die Serverrolle wird dargestellt, durch die <xref:Microsoft.SqlServer.Management.Smo.ServerRole> Objekt. Die Datenbankrolle wird durch das <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>-Objekt und die Anwendungsrolle durch das <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole>-Objekt dargestellt.  
  
 Der Serverebene zugeordnete Berechtigungen sind aufgeführt, als Eigenschaften der <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> Objekt. Berechtigungen können für einzelne Anmeldekonten gewährt, verweigert oder aufgehoben werden.  
  
 Jede <xref:Microsoft.SqlServer.Management.Smo.Database> Objekt verfügt über eine <xref:Microsoft.SqlServer.Management.Smo.UserCollection> -Objekt, das alle Benutzer in der Datenbank angibt. Jeder Benutzer wird einer Anmeldung zugeordnet. Eine Anmeldung kann Benutzern in mehr als einer Datenbank zugeordnet werden. Die <xref:Microsoft.SqlServer.Management.Smo.Login> des Objekts <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> Methode kann verwendet werden, um alle Benutzer in allen Datenbanken aufzulisten, die der Anmeldung zugeordnet sind. Alternativ legt die <xref:Microsoft.SqlServer.Management.Smo.User>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekts die Anmeldung fest, die dem Benutzer zugeordnet ist.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbanken verfügen auch über Rollen, die einen Satz von Berechtigungen auf Datenbankebene festlegen, mit die einen Benutzer bestimmte Tasks durchführen können. Im Gegensatz zu Serverrollen sind Datenbankrollen variabel. Sie können erstellt, geändert und gelöscht werden. Einer Datenbankrolle können für die Massenverwaltung Berechtigungen und Benutzer zugeordnet werden.  
  
## <a name="example"></a>Beispiel  
 Für das folgende Codebeispiel müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="enumerating-logins-and-associated-users-in-visual-basic"></a>Auflisten von Anmeldungen und zugeordneten Benutzern in Visual Basic  
 Jeder Benutzer in einer Datenbank ist einer Anmeldung zugeordnet. Die Anmeldung kann Benutzern in mehreren Datenbanken zugeordnet werden. Das Codebeispiel zeigt, wie die <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekts aufgerufen wird, um alle Datenbankbenutzer aufzulisten, die der Anmeldung zugeordnet sind. Das Beispiel erstellt eine Anmeldung und einen Benutzer in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank stellen Sie sicher, dass Zuordnungsinformationen vorliegen, die aufgelistet werden.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLogins1](SMO How to#SMO_VBLogins1)]  -->  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>Auflisten von Anmeldungen und zugeordneten Benutzern in Visual C#  
 Jeder Benutzer in einer Datenbank ist einer Anmeldung zugeordnet. Die Anmeldung kann Benutzern in mehreren Datenbanken zugeordnet werden. Das Codebeispiel zeigt, wie die <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekts aufgerufen wird, um alle Datenbankbenutzer aufzulisten, die der Anmeldung zugeordnet sind. Das Beispiel erstellt eine Anmeldung und einen Benutzer in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank stellen Sie sicher, dass Zuordnungsinformationen vorliegen, die aufgelistet werden.  
  
```  
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a>Auflisten von Anmeldungen und zugeordneten Benutzern in PowerShell  
 Jeder Benutzer in einer Datenbank ist einer Anmeldung zugeordnet. Die Anmeldung kann Benutzern in mehreren Datenbanken zugeordnet werden. Das Codebeispiel zeigt, wie die <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekts aufgerufen wird, um alle Datenbankbenutzer aufzulisten, die der Anmeldung zugeordnet sind. Das Beispiel erstellt eine Anmeldung und einen Benutzer in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank stellen Sie sicher, dass Zuordnungsinformationen vorliegen, die aufgelistet werden.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database oject  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }  
  
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a>Verwalten von Rollen und Benutzern  
 Im folgenden Beispiel wird die Verwaltung von Rollen und Benutzern gezeigt. Im ersten Beispiel wird C#, im zweiten Beispiel Visual Basic verwendet. Die folgenden Codebeispiele erfordern einen Verweis auf folgende Assemblys:  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```  
  
 Das ist die Visual Basic-Version:  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' Creating Logins  
      Dim login As New Login(svr, "Login1")  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim login2 As New Login(svr, "Login2")  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@1")  
  
      ' Creating Users in the database for the logins created  
      Dim user1 As New User(db, "User1")  
      user1.Login = "Login1"  
      user1.Create()  
  
      Dim user2 As New User(db, "User2")  
      user2.Login = "Login2"  
      user2.Create()  
  
      ' Creating database permission Sets  
      Dim dbPermSet As New DatabasePermissionSet(DatabasePermission.AlterAnySchema)  
      dbPermSet.Add(DatabasePermission.AlterAnyUser)  
  
      Dim dbPermSet2 As New DatabasePermissionSet(DatabasePermission.CreateType)  
      dbPermSet2.Add(DatabasePermission.CreateSchema)  
      dbPermSet2.Add(DatabasePermission.CreateTable)  
  
      ' Creating Database roles  
      Dim role1 As New DatabaseRole(db, "Role1")  
      role1.Create()  
  
      Dim role2 As New DatabaseRole(db, "Role2")  
      role2.Create()  
  
      ' Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name)  
      db.Grant(dbPermSet2, role2.Name)  
  
      ' Adding members (Users / Roles) to Role  
      role1.AddMember("User1")  
  
      role2.AddMember("User2")  
  
      ' Role1 becomes a member of Role2  
      role2.AddMember("Role1")  
  
      ' Enumerating through explicit permissions granted to Role1  
      ' enumerates all database permissions for the Grantee  
      Dim dbPermsRole1 As DatabasePermissionInfo() = db.EnumDatabasePermissions("Role1")  
      For Each dbp As DatabasePermissionInfo In dbPermsRole1  
         Console.WriteLine(dbp.Grantee + " has " & dbp.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
   End Sub  
End Class  
```  
  
  
