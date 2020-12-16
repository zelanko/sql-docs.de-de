---
description: 'Tutorial: Entwickeln einer .NET Framework-Anwendung mithilfe von Always Encrypted mit Secure Enclaves'
title: 'Tutorial: Entwickeln einer .NET Framework-Anwendung mithilfe von Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15'
ms.openlocfilehash: 84ab8334a2a34552d0aa301d7fd92d04dd9ce214
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97463081"
---
# <a name="tutorial-develop-a-net-framework-application-using-always-encrypted-with-secure-enclaves"></a>Tutorial: Entwickeln einer .NET Framework-Anwendung mithilfe von Always Encrypted mit Secure Enclaves
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

In diesem Tutorial erfahren Sie, wie Sie eine einfache Anwendung entwickeln, die Datenbankabfragen ausgibt, die eine serverseitige Secure Enclave für [Always Encrypted mit Secure Enclaves](encryption/always-encrypted-enclaves.md) verwendet. 

## <a name="prerequisites"></a>Voraussetzungen
Dieses Tutorial ist die Fortsetzung von [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](./tutorial-getting-started-with-always-encrypted-enclaves.md). Schließen Sie dieses zunächst ab, bevor Sie mit den folgenden Schritten fortfahren.

Darüber hinaus benötigen Sie Visual Studio (Version 2019 wird empfohlen). Den Download finden Sie unter [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com). Auf Ihrem Anwendungsentwicklungscomputer muss .NET Framework 4.7.2 oder höher ausgeführt werden.

## <a name="step-1-set-up-your-visual-studio-project"></a>Schritt 1: Einrichten Ihres Visual Studio-Projekts

Damit Sie Always Encrypted mit Secure Enclaves in einer.NET Framework-Anwendung verwenden können, müssen Sie sicherstellen, dass Ihre Anwendung auf .NET Framework 4.7.2 basiert und mit dem [Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders-NuGet-Paket](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders) integriert ist. Wenn Sie Ihren Spaltenhauptschlüssel im Azure Key Vault speichern, müssen Sie Ihre Anwendung außerdem mit Version 2.2.0 oder höher des [Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider -NuGet-Pakets](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) integrieren. 

1. Öffnen Sie Visual Studio.

2. Erstellen Sie ein neues C\#-Konsolen-App-Projekt (.NET Framework).

3. Stellen Sie sicher, dass das Projekt mindestens auf .NET Framework 4.7.2 ausgerichtet ist. Klicken Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, wählen Sie „Eigenschaften“ aus und setzen Sie das Zielframework auf .NET Framework 4.7.2.

4. Installieren Sie das folgende NuGet-Paket, indem Sie zu **Tools** (Hauptmenü) > **NuGet-Paket-Manager** > **Paket-Manager-Konsole** gehen. Führen Sie den folgenden Code in der Paket-Manager-Konsole aus.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders -IncludePrerelease
   ```

5. Wenn Sie Azure Key Vault für die Speicherung Ihrer Spaltenhauptschlüssel verwenden, installieren Sie die folgenden NuGet-Pakete, indem Sie zu **Tools** (Hauptmenü) > **NuGet-Paket-Manager** > **Paket-Manager-Konsole** gehen. Führen Sie den folgenden Code in der Paket-Manager-Konsole aus.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider -IncludePrerelease -Version 2.2.0
   Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
   ```

7. Öffnen Sie die Datei „App.config“ für Ihr Projekt.

8. Suchen Sie nach dem Abschnitt \<configuration\>, und führen Sie die \<configSections\>-Abschnitte hinzu oder aktualisieren Sie diese.

   a. Wenn der Abschnitt \<configuration\> **nicht** den Abschnitt \<configSections\> enthält, fügen Sie den folgenden Inhalt direkt unter \<configuration\> hinzu.
   
      ```xml
      <configSections>
         <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
      </configSections>
      ```
   b. Wenn der Abschnitt \<configruation\> den Abschnitt \<configSections\> bereits enthält, fügen Sie die folgende Zeile in \<configSections\> hinzu:

   ```xml
   <section name="SqlColumnEncryptionEnclaveProviders"  type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data,  Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
   ```

9. Fügen Sie den folgenden Abschnitt unter \<configSections\> im Abschnitt „configuration“ hinzu, um einen Enclave-Anbieter festzulegen, der für die Bestätigung und Interaktion mit VBS-Enclaves verwendet werden soll:

   ```xml
   <SqlColumnEncryptionEnclaveProviders>
       <providers>
           <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
       </providers>
   </SqlColumnEncryptionEnclaveProviders>
   ```

Hier ist ein vollständiges Beispiel für eine app.config-Datei für eine einfache Konsolenanwendung.
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
    </providers>
  </SqlColumnEncryptionEnclaveProviders>
  <startup> 
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.2" />
  </startup>
</configuration>
```
## <a name="step-2-implement-your-application-logic"></a>Schritt 2: Implementieren Ihrer Anwendungslogik
Ihre Anwendung stellt eine Verbindung mit der **ContosoHR**-Datenbank aus dem [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](tutorial-getting-started-with-always-encrypted-enclaves.md) her und führt eine Abfrage aus, die das `LIKE`-Prädikat in der Spalte **SSN** sowie einen Bereichsvergleich in der Spalte **Salary** enthält.

1. Ersetzen Sie mit dem folgenden Code den Inhalt der Datei „Program.cs“ (wird von Visual Studio generiert). Aktualisieren Sie die Datenverbindungszeichenfolge mit Ihren Servernamen und die Enclave-Nachweis-URL für Ihre Umgebung. Sie können auch die Datenbankauthentifizierungseinstellungen aktualisieren.

    ```cs
    using System;
    using System.Data.SqlClient;
    using System.Data;

    namespace ConsoleApp1
    {
        class Program
        {
            static void Main(string[] args)
            {
    
                string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = http://hgs.bastion.local/Attestation; Integrated Security = true";

                using (SqlConnection connection = new SqlConnection(connectionString))
                {
                    connection.Open();

                    SqlCommand cmd = connection.CreateCommand();
                    cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [Salary] FROM [dbo].[Employees] WHERE [SSN] LIKE @SSNPattern AND [Salary] > @MinSalary;";

                    SqlParameter paramSSNPattern = cmd.CreateParameter();

                    paramSSNPattern.ParameterName = @"@SSNPattern";
                    paramSSNPattern.DbType = DbType.AnsiStringFixedLength;
                    paramSSNPattern.Direction = ParameterDirection.Input;
                    paramSSNPattern.Value = "%1111";
                    paramSSNPattern.Size = 11;

                    cmd.Parameters.Add(paramSSNPattern);

                    SqlParameter MinSalary = cmd.CreateParameter();

                    MinSalary.ParameterName = @"@MinSalary";
                    MinSalary.DbType = DbType.Currency;
                    MinSalary.Direction = ParameterDirection.Input;
                    MinSalary.Value = 900;

                    cmd.Parameters.Add(MinSalary);
                    cmd.ExecuteNonQuery();
    
                    SqlDataReader reader = cmd.ExecuteReader();
                    while (reader.Read())

                    {
                        Console.WriteLine(reader);
                        Console.WriteLine(reader[0] + ", " + reader[1] + ", " + reader[2] + ", " + reader[3]);
                    }   
                    Console.ReadKey();
                }
            }
        }
    }
    ```
2. Erstellen Sie die Anwendung, und führen Sie sie aus.  

## <a name="see-also"></a>Weitere Informationen
- [Verwenden von Always Encrypted mit dem .NET Framework-Datenanbieter für SQL Server](encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
