---
title: Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f699c97aee04bfe2c6f29789be6f34b673408e7
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52401153"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel enthält Informationen zum Entwickeln von Java-Anwendungen in die Azure Active Directory-Authentifizierung-Funktion mit dem Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server verwenden.

Sie können Azure Active Directory (AAD)-Authentifizierung, die ein Mechanismus zum Herstellen einer Verbindung mit Azure SQL-Datenbank v12 ist die Verwendung von Identitäten in Azure Active Directory. Verwenden Sie AAD-Authentifizierung zur zentralen Verwaltung von Identitäten von Datenbankbenutzern und als Alternative zur SQL Server-Authentifizierung. Der JDBC-Treiber können Sie Ihre Azure Active Directory-Anmeldeinformationen in der JDBC-Verbindungszeichenfolge zur Verbindung mit Azure SQL-Datenbank angeben. Informationen zum Konfigurieren von Azure Active Directory-Authentifizierung finden Sie unter [Herstellen einer Verbindung mit SQL-Datenbank mithilfe der Azure Active Directory Authentifizierung](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Zwei neue Verbindungseigenschaften wurden hinzugefügt, um Azure Active Directory-Authentifizierung zu unterstützen:
*   **Authentifizierung**: Verwenden Sie diese Eigenschaft an, dass die SQL-Authentifizierung-Methode, die für die Verbindung verwendet. Mögliche Werte sind: **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **"sqlpassword"**, und die standardmäßige **"NotSpecified"**.
    * Mit "Authentication = ActiveDirectoryIntegrated" für die Verbindung mit einer SQL-Datenbank mithilfe der integrierten Windows-Authentifizierung. Um diesen Authentifizierungsmodus zu verwenden, müssen Sie die lokalen Active Directory Federation Services (ADFS) mit AAD in der Cloud zu verbinden. Nachdem Sie dies sowie ein Kerberos-Ticket eingerichtet haben, können Sie Azure SQL-Datenbank zugreifen, ohne zur Eingabe von Anmeldeinformationen aufgefordert werden, wenn Sie eine Domäne eingebundenen Computer angemeldet sind. 
    * Mit "Authentication = ActiveDirectoryPassword" für die Verbindung mit einer SQL-Datenbank mithilfe einer Azure AD-Prinzipalnamen und das Kennwort.
    * Verwenden "Authentication = SqlPassword" zur Verbindung mit einem SQL Server mithilfe von Benutzername/Benutzer und Kennwort-Eigenschaften.
    * Mit "Authentifizierung" NotSpecified "=", oder lassen Sie sie als Standard aus, wenn keine dieser Authentifizierungsmethoden benötigt werden.

*   **AccessToken**: Diese Eigenschaft für die Verbindung mit einer SQL-Datenbank mithilfe eines Zugriffstokens verwenden. AccessToken kann nur festgelegt werden, verwenden den Eigenschaftenparameter der getConnection()-Methode in der DriverManager-Klasse. Es kann nicht in der Verbindungs-URL verwendet werden.  

Weitere Informationen finden Sie unter der Authentifizierungseigenschaft auf die [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md) Seite.  


## <a name="client-setup-requirements"></a>Installationsanforderungen für Clients
Stellen Sie sicher, dass die folgenden Komponenten auf dem Clientcomputer installiert sind:
* Java 7 oder höher
*   Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server
*   Wenn Sie den Zugriffsmodus für die tokenbasierte Authentifizierung verwenden, müssen Sie [Azure-Activedirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) und dessen Abhängigkeiten zum Ausführen der Beispiele in diesem Artikel. Weitere Informationen finden Sie unter **Verbindungsherstellung per Zugriffstoken** Abschnitt.
*   Wenn Sie den Authentifizierungsmodus "ActiveDirectoryPassword" verwenden, müssen Sie [Azure-Activedirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) und seine Abhängigkeiten. Weitere Informationen finden Sie unter **Herstellen einer Verbindung mit der Authentifizierungsmodus "ActiveDirectoryPassword"** Abschnitt.
*   Wenn Sie den ActiveDirectoryIntegrated-Modus verwenden, benötigen Sie Azure-Activedirectory-Library-for-Java und seine Abhängigkeiten. Weitere Informationen finden Sie unter **Herstellen einer Verbindung mit der Authentifizierungsmodus ActiveDirectoryIntegrated** Abschnitt.
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Herstellen einer Verbindung mit ActiveDirectoryIntegrated-Authentifizierungsmodus
 Mit Version 6.4 unterstützt Microsoft JDBC-Treiber für die ActiveDirectoryIntegrated-Authentifizierung, die mit einem Kerberos-Ticket auf mehreren Plattformen (Windows/Linux und Mac).
Weitere Informationen finden Sie unter [festgelegt Kerberos-Ticket für Windows, Linux und Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) Weitere Details. Alternativ kann auf Windows, "sqljdbc_auth.dll" auch für die Authentifizierung ActiveDirectoryIntegrated JDBC-Treiber verwendet werden.

> [!NOTE]
>  Wenn Sie eine ältere Version des Treibers verwenden, aktivieren Sie diese Option [Link](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) für die jeweiligen Abhängigkeiten, die erforderlich sind, um diesen Authentifizierungsmodus zu verwenden. 

Das folgende Beispiel zeigt, wie Sie mit "Authentication = ActiveDirectoryIntegrated" Modus. Führen Sie dieses Beispiel aus, auf eine Domäne eingebundenen Computer ein, der in Azure Active Directory verbunden ist. Die Benutzer einer eigenständigen Datenbank, die Ihrem Azure AD-Dienstprinzipal oder eine der Gruppen darstellt, Sie gehören, müssen in der Datenbank vorhanden sein und müssen über die CONNECT-Berechtigung verfügen. 

Vor dem Erstellen und das Beispiel, auf dem Clientcomputer ausführen (auf, die zum Ausführen des Beispiels werden sollen), Herunterladen der [Azure-Activedirectory-Library-for-Java-Bibliothek](https://github.com/AzureAD/azure-activedirectory-library-for-java) und seine Abhängigkeiten, und sie in der Java-Buildpfad einschließen

Ersetzen Sie den Namen für die Server-Datenbank durch den Namen Ihres Server-Datenbank in den folgenden Zeilen, bevor Sie das Beispiel ausführen:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

Im Beispiel ActiveDirectoryIntegrated Authentifizierungsmodus verwenden:
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
        ds.setHostNameInCertificate("*.database.windows.net");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
Ausführen des Beispiels auf einem Clientcomputer automatisch Ihr Kerberos-Ticket verwendet und ist kein Kennwort erforderlich. Wenn Sie eine Verbindung hergestellt ist, sollten Sie die folgende Meldung angezeigt:
```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Legen Sie die Kerberos-Ticket für Windows, Linux und Mac

Sie müssen ein Kerberos-Ticket verknüpfen Ihres aktuellen Benutzers zu einem Windows-Domänenkonto einrichten. Eine Zusammenfassung der wichtigsten Schritte ist unten enthalten.

#### <a name="windows"></a>Windows
Im Lieferumfang von JDK `kinit`, die Sie verwenden können, um ein TGT vom Schlüsselverteilungscenter (KDC) in einer Domäne erhalten eingebundenen Computer an, die in Azure Active Directory verbunden ist.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Schritt 1: Ticket-Granting-Ticket abrufen
- **Führen Sie auf**: Windows
- **Aktion**:
  - Verwenden Sie den Befehl `kinit username@DOMAIN.COMPANY.COM` um ein TGT vom KDC erhalten, dann werden Sie aufgefordert für das Domänenkennwort ein.
  - Verwendung `klist` zu den verfügbaren Tickets finden Sie unter. Wenn die Kinit erfolgreich war, sollte ein Ticket von krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM angezeigt werden.

> [!NOTE]
>  Müssen Sie möglicherweise angeben einer `.ini` -Datei mit `-Djava.security.krb5.conf` für Ihre Anwendung um KDC zu suchen.

#### <a name="linux-and-mac"></a>Linux und Mac

##### <a name="requirements"></a>Anforderungen
Zugriff auf ein Windows-Domäne eingebundenen Computer dem Kerberos-Domänencontroller abgefragt.

##### <a name="step-1-find-kerberos-kdc"></a>Schritt 1: Suchen von Kerberos-KDC
- **Führen Sie auf**: Windows-Befehlszeile
- **Aktion**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (wobei "DOMAIN.COMPANY.COM" ordnet in Ihrer Domäne-Namen)
- **Beispielausgabe**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **Informationen zum Extrahieren** der DC-Namen, in diesem Fall `co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Schritt 2: Konfigurieren der KDC in krb5.conf
- **Führen Sie auf**: Linux/Mac
- **Aktion**: Bearbeiten der /etc/krb5.conf in einem Editor Ihrer Wahl. Konfigurieren Sie die folgenden Schlüssel
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Speichern Sie die Datei krb5.conf, und beenden

> [!NOTE]
>  Domäne muss in Großbuchstaben.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Schritt 3: Testen das Ticket-Granting-Ticket abrufen
- **Führen Sie auf**: Linux/Mac
- **Aktion**:
  - Verwenden Sie den Befehl `kinit username@DOMAIN.COMPANY.COM` um ein TGT vom KDC erhalten, dann werden Sie aufgefordert für das Domänenkennwort ein.
  - Verwendung `klist` zu den verfügbaren Tickets finden Sie unter. Wenn die Kinit erfolgreich war, sollte ein Ticket von krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM angezeigt werden.

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Herstellen einer Verbindung mit der Authentifizierungsmodus "ActiveDirectoryPassword"
Das folgende Beispiel zeigt, wie Sie mit "Authentication = ActiveDirectoryPassword" Modus.

Vor dem Erstellen und Ausführen des Beispiels:
1.  Auf dem Clientcomputer (auf, die Sie das Beispiel ausführen möchten), Herunterladen der [Azure-Activedirectory-Library-for-Java-Bibliothek](https://github.com/AzureAD/azure-activedirectory-library-for-java) und seine Abhängigkeiten, und sie in der Java-Buildpfad einschließen
2.  Suchen Sie nach den folgenden Code ein, und Ersetzen Sie den Namen des Server-Datenbank durch den Namen Ihres Server-Datenbank.
    ```java
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Suchen Sie nach den folgenden Code aus, und Ersetzen Sie Benutzername, mit dem Namen der AAD-Benutzer, die, dem Sie als eine Verbindung herstellen möchten.
    ```java
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

Im Beispiel Authentifizierungsmodus "ActiveDirectoryPassword" verwenden:
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
        ds.setHostNameInCertificate("*.database.windows.net");
        
        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
Wenn die Verbindung hergestellt wurde, sollten Sie als Ausgabe die folgende Meldung angezeigt:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Eine Datenbank mit eigenständigen Benutzern muss vorhanden sein, und der Benutzer einer eigenständigen Datenbank, die die angegebene Azure AD-Benutzer oder eine der Gruppen der angegebenen Azure AD-Benutzer gehört, muss in der Datenbank vorhanden sein, und muss (mit Ausnahme von Azure Active Directory CONNECT-Berechtigung Serveradministrator oder Gruppe)

## <a name="connecting-using-access-token"></a>Verbindungsherstellung per Zugriffstoken
Anwendungen/Diensten können Abrufen eines Zugriffstokens aus Azure Active Directory und verwenden, die Verbindung mit SQL Azure-Datenbank herstellen.

> [!NOTE] 
> **AccessToken** kann nur mit den Eigenschaftenparameter der getConnection()-Methode in der DriverManager-Klasse festgelegt werden. Es kann nicht in der Verbindungszeichenfolge verwendet werden.

Das folgende Beispiel enthält eine einfache Java-Anwendung die Verbindung mit Azure SQL-Datenbank mithilfe von Access-Token-basierte Authentifizierung. Vor dem Erstellen und das Beispiel ausführen, führen Sie die folgenden Schritte aus:
1.  Erstellen Sie ein Anwendungskonto in Azure Active Directory, für den Dienst.
    1. Melden Sie sich beim Azure-Portal an.
    2. Klicken Sie auf Azure Active Directory auf, um im linken Navigationsbereich.
    3. Klicken Sie auf der Registerkarte "App-Registrierungen".
    4. Klicken Sie in der Detailansicht zu öffnen auf "Registrierung einer neuen Anwendung".
    5. Geben Sie einen Anzeigenamen für die Anwendung Mytokentest, wählen Sie "Web-App/API".
    6. Anmelde-URL benötigt nicht. Geben Sie nur etwas: "https://mytokentest".
    7. Klicken Sie auf "Erstellen", am unteren Rand.
    9. Klicken Sie im Azure-Portal, klicken Sie auf der Registerkarte "Einstellungen" Ihrer Anwendung, und öffnen Sie die Registerkarte "Eigenschaften".
    10. Suchen Sie den Wert "Anwendungs-ID" (auch bekannt als Client-ID), und kopieren Sie ihn, da Sie benötigen diesen später beim Konfigurieren Ihrer Anwendung (z. B. 1846943b-ad04-4808-aa13-4702d908b5c1). Finden Sie die folgende Momentaufnahme aus.
    11. Erstellen Sie einen Schlüssel im Abschnitt "Schlüssel" indem Sie in das Namensfeld ausfüllen, die Dauer des Schlüssels auswählen und Speichern der Konfiguration (lassen Sie das Feld "Wert" leer). Nach dem Speichern, muss das Feld "Wert" automatisch ausgefüllt, kopieren Sie den generierten Wert. Dies ist der geheime Clientschlüssel.
    12. Klicken Sie auf der linken Seitenleiste die auf Azure Active Directory. Finden Sie unter "App-Registrierungen" die Registerkarte "Endpunkte" ein. Kopieren Sie die URL unter "Oath-2.0-TOKENENDPUNKT", dies ist Ihre STS-URL.
    
    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Melden Sie sich mit Ihrem Azure SQL-Server-Benutzerdatenbank als Azure Active Directory-Administrator und Benutzer einer eigenständigen Datenbank mithilfe von T-SQL-Befehl bereitstellen für Ihre Anwendung, Dienstprinzipal an. Weitere Informationen finden Sie unter den [beim Verbinden mit SQL-Datenbank oder SQL Data Warehouse durch Verwenden von Azure Active Directory-Authentifizierung](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/) ausführliche Informationen zum Erstellen von Azure Active Directory-Administrator und Benutzer einer eigenständigen Datenbank.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  Auf dem Clientcomputer (auf, die Sie das Beispiel ausführen möchten), Herunterladen der [Azure-Activedirectory-Library-for-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) Bibliothek und ihre Abhängigkeiten, und sie in der Java-Buildpfad einschließen. Beachten Sie, dass die Azure-Activedirectory-Library-for-Java nur zum Ausführen von diesem speziellen Beispiel benötigt wird. Im Beispiel wird die APIs aus dieser Bibliothek, zum Abrufen von Zugriffstoken aus Azure AD. Wenn Sie bereits über ein Zugriffstoken verfügen, können Sie diesen Schritt überspringen. Beachten Sie, dass müssen Sie auch den Abschnitt im Beispiel zu entfernen, die Zugriffstoken abruft.

Ersetzen Sie den STS-URL, Client-ID, den geheimen Clientschlüssel, Server und Datenbank Namen im folgenden Beispiel durch Ihre Werte.

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
        ds.setHostNameInCertificate("*.database.windows.net");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {

            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
``` 

Wenn die Verbindung erfolgreich ist, sollten Sie als Ausgabe die folgende Meldung angezeigt:
```java
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
