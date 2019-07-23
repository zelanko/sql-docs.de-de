---
title: Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/29/2019
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a194338a41e64e18076ad37a4f895180a7d9e448
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956816"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel enthält Informationen zum Entwickeln von Java-Anwendungen für die Verwendung der Azure Active Directory Authentifizierungsfunktion mit dem Microsoft JDBC-Treiber für SQL Server.

Sie können die Azure Active Directory-Authentifizierung (AAD) verwenden, bei der es sich um einen Mechanismus zum Herstellen einer Verbindung mit Azure SQL-Datenbank V12 mit Identitäten in Azure Active Directory handelt. Verwenden Sie AAD-Authentifizierung zur zentralen Verwaltung von Identitäten von Datenbankbenutzern und als Alternative zur SQL Server-Authentifizierung. Mit dem JDBC-Treiber können Sie Ihre Azure Active Directory Anmelde Informationen in der JDBC-Verbindungs Zeichenfolge angeben, um eine Verbindung mit Azure SQL-Datenbank herzustellen. Weitere Informationen zum Konfigurieren Azure Active Directory Authentifizierung finden Sie [unter Herstellen einer Verbindung mit SQL-Datenbank mithilfe Azure Active Directory-Authentifizierung](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Verbindungs Eigenschaften zur Unterstützung Azure Active Directory Authentifizierung im Microsoft JDBC-Treiber für SQL Server sind:
*   **Authentifizierung**: Verwenden Sie diese Eigenschaft an, dass die SQL-Authentifizierung-Methode, die für die Verbindung verwendet. Folgende Werte sind möglich: 
    * **ActiveDirectoryMSI**
        * Unterstützt seit Version Version **7.2**von `authentication=ActiveDirectoryMSI` Driver, kann verwendet werden, um eine Verbindung mit einer Azure SQL-Datenbank/Data Warehouse aus einer Azure-Ressource herzustellen, in der die "Identitäts Unterstützung" aktiviert ist. Optional kann **msiclientid** in den Verbindungs-/DataSource-Eigenschaften zusammen mit diesem Authentifizierungsmodus angegeben werden, der die Client-ID einer verwaltete Dienstidentität enthalten muss, die zum Abrufen des **Access** Token zum Einrichten verwendet werden soll. die Verbindung.
    * **ActiveDirectoryIntegrated**
        * Unterstützt seit der **Treiber Version**6.0 `authentication=ActiveDirectoryIntegrated` , kann zum Herstellen einer Verbindung mit einer Azure SQL-Datenbank/Data Warehouse mithilfe integrierter Authentifizierung verwendet werden. Um diesen Authentifizierungsmodus zu verwenden, müssen Sie einen Verbund der lokalen Active Directory-Verbunddienste (AD FS) (AD FS) mit Azure Active Directory in der Cloud einrichten. Nach der Einrichtung können Sie eine Verbindung herstellen, indem Sie entweder die native Bibliothek "sqljdbc_auth. dll" dem Pfad der Anwendungsklasse unter Windows-Betriebssystem hinzufügen oder ein Kerberos-Ticket für die plattformübergreifende Authentifizierungs Unterstützung einrichten. Sie können auf Azure SQL-Datenbank/DW zugreifen, ohne zur Eingabe von Anmelde Informationen aufgefordert zu werden, wenn Sie bei einem in eine Domäne eingebundenen Computer angemeldet sind.
    * **ActiveDirectoryPassword**
        * Unterstützt seit Version **6.0**von Driver `authentication=ActiveDirectoryPassword` , kann zum Herstellen einer Verbindung mit einer Azure SQL-Datenbank/Data Warehouse mithilfe eines Azure AD Prinzipal namens und Kennworts verwendet werden.
    * **SqlPassword**
        * Verwenden `authentication=SqlPassword` Sie, um eine Verbindung mit einem SQL Server mithilfe der Eigenschaften Benutzername, Benutzer und Kennwort herzustellen
    * **NotSpecified**
        * Verwenden `authentication=NotSpecified` Sie den Standardwert, oder belassen Sie ihn als Standardwert, wenn keine dieser Authentifizierungsmethoden benötigt wird.

*   **accesstoken**: Verwenden Sie diese Verbindungs Eigenschaft, um eine Verbindung mit einer SQL-Datenbank mithilfe eines Zugriffs Tokens herzustellen. Access Token kann nur mit dem properties-Parameter der getConnection ()-Methode in der DriverManager-Klasse festgelegt werden. Sie kann nicht in der Verbindungs-URL verwendet werden.  

Weitere Informationen finden Sie unter der Eigenschaft Authentifizierung auf der Seite [Festlegen der Verbindungs Eigenschaften](../../connect/jdbc/setting-the-connection-properties.md) .  


## <a name="client-setup-requirements"></a>Client Setup Anforderungen
Für die **activedirectorymsi** -Authentifizierung müssen die folgenden Komponenten auf dem Client Computer installiert sein:
* Java 8 oder höher
* Microsoft JDBC Driver 7,2 (oder höher) für SQL Server
* Die Client Umgebung muss eine Azure-Ressource sein, und die Funktion "Identitäts Funktion" muss aktiviert sein.
* Ein eigenständiger Datenbankbenutzer, der die vom System zugewiesene verwaltete Identität oder vom Benutzer zugewiesene verwaltete Identität ihrer Azure-Ressource darstellt, muss in der Zieldatenbank vorhanden sein und über die CONNECT-Berechtigung verfügen.

Bei anderen Authentifizierungs Modi müssen die folgenden Komponenten auf dem Client Computer installiert sein:
* Java 7 oder höher
* Microsoft JDBC Driver 6,0 (oder höher) für SQL Server
* Wenn Sie den Zugriffs Token-basierten Authentifizierungsmodus verwenden, benötigen Sie [Azure-ActiveDirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) und seine Abhängigkeiten, um die Beispiele in diesem Artikel auszuführen. Weitere Informationen finden Sie im Abschnitt **Herstellen einer Verbindung mit dem Zugriffs Token** .
* Wenn Sie den Authentifizierungsmodus **activedirectorypassword** verwenden, benötigen Sie [Azure-ActiveDirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) und seine Abhängigkeiten. Weitere Informationen finden Sie im Abschnitt **Herstellen einer Verbindung mithilfe des activedirectorypassword-Authentifizierungsmodus** .
* Wenn Sie den **activedirectoriyintegrated** -Modus verwenden, benötigen Sie Azure-ActiveDirectory-Library-for-Java und seine Abhängigkeiten. Weitere Informationen finden Sie im Abschnitt **Herstellen einer Verbindung mithilfe des activedirectoryintegrated-Authentifizierungsmodus** .

## <a name="connecting-using-activedirectorymsi-authentication-mode"></a>Herstellen einer Verbindung mithilfe des activedirectorymsi-Authentifizierungsmodus
Im folgenden Beispiel wird veranschaulicht, wie der Modus `authentication=ActiveDirectoryMSI` verwendet wird. Führen Sie dieses Beispiel aus einer Azure-Ressource, e, einem virtuellen Azure-Computer, einem App Service oder einem Funktionen-App aus, der mit Azure Active Directory im Verbund ist.

Ersetzen Sie den Server-/Datenbanknamen durch Ihren Server-/Datenbanknamen in den folgenden Zeilen, bevor Sie das Beispiel ausführen:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
//Optional
ds.setMsiClientId("94de34e9-8e8c-470a-96df-08110924b814"); // Replace with Client ID of User-Assigned MSI to be used
```

Im folgenden Beispiel wird der activedirectorymsi-Authentifizierungsmodus verwendet:

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AAD_MSI {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryMSI");
        // Optional
        ds.setMsiClientId("94de34e9-8e8c-470a-96df-08110924b814"); // Replace with Client ID of User-Assigned MSI to be used

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```

Wenn Sie dieses Beispiel auf einem virtuellen Azure-Computer ausführen, wird ein Zugriffs Token von der vom _System zugewiesenen verwalteten Identität_ oder vom _Benutzer zugewiesenen verwalteten Identität_ abgerufen (wenn **msiclientid** angegeben ist) und eine Verbindung mithilfe des abgerufenen Zugriffs hergestellt. toben. Wenn eine Verbindung hergestellt wird, sollte die folgende Meldung angezeigt werden:

```bash
You have successfully logged on as: <your MSI username>
```

## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Herstellen einer Verbindung mithilfe des activedirectoryintegrated-Authentifizierungsmodus
Mit Version 6,4 bietet der Microsoft JDBC-Treiber Unterstützung für die activedirectoryintegrated-Authentifizierung mithilfe eines Kerberos-Tickets auf mehreren Plattformen (Windows, Linux und macOS).
Weitere Informationen finden Sie unter [Festlegen des Kerberos-Tickets unter Windows, Linux und Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) . Alternativ kann unter Windows auch sqljdbc_auth. dll für die activedirectoryintegrated-Authentifizierung mit dem JDBC-Treiber verwendet werden.

> [!NOTE]
>  Wenn Sie eine ältere Version des Treibers verwenden, überprüfen Sie diesen [Link](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) auf die jeweiligen Abhängigkeiten, die zur Verwendung dieses Authentifizierungsmodus erforderlich sind. 

Im folgenden Beispiel wird veranschaulicht, wie der Modus `authentication=ActiveDirectoryIntegrated` verwendet wird. Führen Sie dieses Beispiel auf einem mit einer Domäne verbundenen Computer aus, der mit Azure Active Directory verbunden ist. Ein eigenständiger Datenbankbenutzer, der den Azure AD Prinzipal oder eine der Gruppen darstellt, zu denen Sie gehören, muss in der Datenbank vorhanden sein und über die CONNECT-Berechtigung verfügen. 

Bevor Sie das Beispiel erstellen und ausführen, müssen Sie auf dem Client Computer (auf dem Sie das Beispiel ausführen möchten) die [Bibliothek Azure-ActiveDirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) und ihre Abhängigkeiten herunterladen und in den Java-buildpfad einschließen.

Ersetzen Sie den Server-/Datenbanknamen durch Ihren Server-/Datenbanknamen in den folgenden Zeilen, bevor Sie das Beispiel ausführen:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

Im folgenden Beispiel wird der activedirectoryintegrated-Authentifizierungsmodus verwendet:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADIntegrated {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```

Wenn Sie dieses Beispiel auf einem Client Computer ausführen, wird automatisch ein Kerberos-Ticket verwendet, und es ist kein Kennwort erforderlich. Wenn eine Verbindung hergestellt wird, sollte die folgende Meldung angezeigt werden:

```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Festlegen des Kerberos-Tickets unter Windows, Linux und Mac

Sie müssen ein Kerberos-Ticket einrichten, mit dem der aktuelle Benutzer mit einem Windows-Domänen Konto verknüpft wird. Unten finden Sie eine Zusammenfassung der wichtigsten Schritte.

#### <a name="windows"></a>Windows
JDK ist in `kinit`verfügbar, mit dem Sie ein TGT von Schlüsselverteilungscenter (KDC) auf einem in die Domäne eingebundener Computer erhalten können, der mit Azure Active Directory verbunden ist.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Schritt 1: Ticket Abruf für Ticket Abruf
- **Ausführen unter**: Windows
- **Aktion**:
  - Verwenden Sie den `kinit username@DOMAIN.COMPANY.COM` Befehl, um ein TGT von KDC zu erhalten, und Sie werden aufgefordert, Ihr Domänen Kennwort einzugeben.
  - Verwenden `klist` Sie, um die verfügbaren Tickets anzuzeigen. Wenn kinit erfolgreich war, sollte ein Ticket von krbtgt/Domain. Company. com @ Domain.Company.com angezeigt werden.

> [!NOTE]
>  Möglicherweise müssen Sie eine `.ini` `-Djava.security.krb5.conf` Datei angeben, in der Ihre Anwendung KDC finden soll.

#### <a name="linux-and-mac"></a>Linux und Mac

##### <a name="requirements"></a>Anforderungen
Zugriff auf einen in die Domäne eingebundenen Windows-Computer, um den Kerberos-Domänen Controller abzufragen.

##### <a name="step-1-find-kerberos-kdc"></a>Schritt 1: Suchen von Kerberos-KDC
- **Führen Sie auf**: Windows-Befehlszeile
- **Aktion**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (wobei "Domain.Company.com" dem Namen Ihrer Domäne zugeordnet ist)
- **Beispielausgabe**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **Zu** extra hier gende Informationen Der DC-Name, in diesem Fall`co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Schritt 2: Konfigurieren von KDC in krb5. conf
- **Ausführen unter**: Linux/Mac
- **Aktion**: Bearbeiten Sie die/etc/krb5.conf in einem Editor Ihrer Wahl. Konfigurieren Sie die folgenden Schlüssel
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Speichern Sie dann die Datei krb5. conf, und beenden Sie

> [!NOTE]
>  Die Domäne muss in allen Obergrenzen vorliegen.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Schritt 3: Testen des Ticket Abruf Tickets
- **Ausführen unter**: Linux/Mac
- **Aktion**:
  - Verwenden Sie den `kinit username@DOMAIN.COMPANY.COM` Befehl, um ein TGT von KDC zu erhalten, und Sie werden aufgefordert, Ihr Domänen Kennwort einzugeben.
  - Verwenden `klist` Sie, um die verfügbaren Tickets anzuzeigen. Wenn kinit erfolgreich war, sollte ein Ticket von krbtgt/Domain. Company. com @ Domain.Company.com angezeigt werden.

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Herstellen einer Verbindung mithilfe des activedirectorypassword-Authentifizierungsmodus
Im folgenden Beispiel wird veranschaulicht, wie der Modus `authentication=ActiveDirectoryPassword` verwendet wird.

Vor dem Aufbau und der Ausführung des Beispiels:
1.  Laden Sie auf dem Client Computer (auf dem Sie das Beispiel ausführen möchten) die [Bibliothek Azure-ActiveDirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) und deren Abhängigkeiten herunter, und fügen Sie Sie in den Java-buildpfad ein.
2.  Suchen Sie nach den folgenden Codezeilen, und ersetzen Sie den Server-/Datenbanknamen durch Ihren Server-/Datenbanknamen.
    ```java
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Suchen Sie nach den folgenden Codezeilen, und ersetzen Sie Benutzername durch den Namen des Aad-Benutzers, mit dem Sie eine Verbindung herstellen möchten.
    ```java
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

Im folgenden Beispiel wird der activedirectorypassword-Authentifizierungsmodus verwendet:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADUserPassword {
    
    public static void main(String[] args) throws Exception{
        
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        
        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
Wenn eine Verbindung hergestellt wird, sollte die folgende Meldung als Ausgabe angezeigt werden:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Eine eigenständige Benutzerdatenbank muss vorhanden sein, und ein eigenständiger Datenbankbenutzer, der den angegebenen Azure AD Benutzer oder eine der Gruppen darstellt, der angegebene Azure AD Benutzer gehört, muss in der Datenbank vorhanden sein und muss über die CONNECT-Berechtigung verfügen (außer Azure Active Directory Server Administrator oder-Gruppe)

## <a name="connecting-using-access-token"></a>Herstellen einer Verbindung über das Zugriffs Token
Anwendungen/Dienste können ein Zugriffs Token aus dem Azure Active Directory abrufen und verwenden, um eine Verbindung mit Azure SQL-Datenbank/Data Warehouse herzustellen.

> [!NOTE] 
> **Access** Token kann nur mit dem properties-Parameter der getConnection ()-Methode in der DriverManager-Klasse festgelegt werden. Sie kann nicht in der Verbindungs Zeichenfolge verwendet werden.

Das folgende Beispiel enthält eine einfache Java-Anwendung, die eine Verbindung mit Azure SQL-Datenbank/Data Warehouse mithilfe der Zugriffs Token-basierten Authentifizierung herstellt. Bevor Sie das Beispiel entwickeln und ausführen, führen Sie die folgenden Schritte aus:
1.  Erstellen Sie ein Anwendungs Konto in Azure Active Directory für Ihren Dienst.
    1. Melden Sie sich beim Azure-Portal an.
    2. Klicken Sie im linken Navigationsbereich auf Azure Active Directory.
    3. Klicken Sie auf die Registerkarte "App-Registrierungen".
    4. Klicken Sie in der Schublade auf "Registrierung neuer Anwendungen".
    5. Geben Sie meinerentest als anzeigen Amen für die Anwendung ein, und wählen Sie "Web-App/API" aus.
    6. Wir benötigen keine Anmelde-URL. Geben Sie einfach nichts an https://mytokentest: "".
    7. Klicken Sie unten auf "erstellen".
    9. Klicken Sie im Azure-Portal noch auf die Registerkarte "Einstellungen" der Anwendung, und öffnen Sie die Registerkarte "Eigenschaften".
    10. Suchen Sie den Wert "Anwendungs-ID" (auch als Client-ID bezeichnet), und kopieren Sie ihn, da Sie ihn später beim Konfigurieren Ihrer Anwendung benötigen (z. b. 1846943b-ad04-4808-aa13-4702d908b5c1). Siehe folgende Momentaufnahme.
    11. Erstellen Sie im Abschnitt "Keys" einen Schlüssel, indem Sie das Feld "Name" ausfüllen, die Dauer des Schlüssels auswählen und die Konfiguration speichern (lassen Sie das Feld "Wert" leer). Nach dem Speichern sollte das Wertfeld automatisch ausgefüllt werden. Kopieren Sie den generierten Wert. Dies ist der geheime Clientschlüssel.
    12. Klicken Sie im linken Bereich auf Azure Active Directory. Suchen Sie unter "App-Registrierungen" die Registerkarte "Endpunkte". Kopieren Sie die URL unter "Oath 2,0 Token Endpoint", dies ist Ihre STS-URL.
    
    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Melden Sie sich bei der Benutzerdatenbank Ihres Azure-SQL Server als Azure Active Directory Administrator an, und stellen Sie mithilfe eines T-SQL-Befehls einen eigenständigen Datenbankbenutzer für den Anwendungs Prinzipal bereit. Weitere Informationen zum Erstellen eines Azure Active Directory Administrators und eines eigenständigen Daten Bank Benutzers finden [Sie unter Herstellen einer Verbindung mit SQL-Datenbank oder SQL Data Warehouse mithilfe Azure Active Directory-Authentifizierung](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/) .

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  Laden Sie auf dem Client Computer (auf dem Sie das Beispiel ausführen möchten) die Bibliothek [Azure-ActiveDirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) und deren Abhängigkeiten herunter, und fügen Sie Sie in den Java-buildpfad ein. Beachten Sie, dass Azure-ActiveDirectory-Library-for-Java nur zum Ausführen dieses spezifischen Beispiels benötigt wird. Im Beispiel werden die APIs aus dieser Bibliothek verwendet, um das Zugriffs Token aus Azure Aad abzurufen. Wenn Sie bereits über ein Zugriffs Token verfügen, können Sie diesen Schritt überspringen. Beachten Sie, dass Sie auch den Abschnitt aus dem Beispiel entfernen müssen, mit dem das Zugriffs Token abgerufen wird.

Ersetzen Sie im folgenden Beispiel die STS-URL, die Client-ID, den geheimen Client Schlüssel, den Server-und Datenbanknamen durch ihre Werte.

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD.
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;

public class AADTokenBased {

    public static void main(String[] args) throws Exception {

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "1846943b-ad04-4808-aa13-4702d908b5c1"; // Replace with your client ID.
        String clientSecret = "..."; // Replace with your client secret.

        AuthenticationContext context = new AuthenticationContext(stsurl, false, Executors.newFixedThreadPool(1));
        ClientCredential cred = new ClientCredential(clientId, clientSecret);

        Future<AuthenticationResult> future = context.acquireToken(spn, cred, null);
        String accessToken = future.get().getAccessToken();

        System.out.println("Access Token: " + accessToken);

        // Connect with the access token.
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name.
        ds.setDatabaseName("demo"); // Replace with your database name.
        ds.setAccessToken(accessToken);

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
``` 

Wenn die Verbindung erfolgreich hergestellt wurde, sollte die folgende Meldung als Ausgabe angezeigt werden:

```bash
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
