---
title: Grundlegendes zu XA-Transaktionen
description: Der Microsoft JDBC-Treiber für SQL Server unterstützt optional verteilte Transaktionen für die Java-Plattform und Enterprise Edition/JDBC 2.0.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 574e326f-0520-4003-bdf1-62d92c3db457
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ff48d23727c8dd48048293dd34127b6acbb3f005
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293998"
---
# <a name="understanding-xa-transactions"></a>Grundlegendes zu XA-Transaktionen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt optional verteilte Transaktionen für die Java-Plattform, Enterprise Edition/JDBC 2.0. JDBC-Verbindungen von der Klasse [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) können Bestandteil normaler verteilter Transaktionsverarbeitungsumgebungen wie Anwendungsserver für die Java-Plattform, Enterprise Edition (Java EE) sein.  

In diesem Artikel steht XA für erweiterte Architektur.

> [!WARNING]  
> Der Microsoft JDBC-Treiber 4.2 (und höher) für SQL enthält neue Timeoutoptionen für die vorhandene Funktion für den automatischen Rollback nicht vorbereiteter Transaktionen. Ausführliche Informationen finden Sie weiter unten in diesem Artikel unter [Konfigurieren von serverseitigen Timeouteinstellungen für den automatischen Rollback nicht vorbereiteter Transaktionen](../../connect/jdbc/understanding-xa-transactions.md#BKMK_ServerSide).  

## <a name="remarks"></a>Bemerkungen

Für die Implementierung verteilter Transaktionen stehen die folgenden Klassen zur Verfügung:  
  
| Klasse                                              | Implementiert                      | BESCHREIBUNG                                       |
| -------------------------------------------------- | ------------------------------- | ------------------------------------------------- |
| com.microsoft.sqlserver.jdbc.SQLServerXADataSource | javax.sql.XADataSource          | Das Klassenfactory für verteilte Verbindungen.    |
| com.microsoft.sqlserver.jdbc.SQLServerXAResource   | javax.transaction.xa.XAResource | Der Ressourcenadapter für den Transaktions-Manager. |
  
> [!NOTE]  
> Verbindungen für verteilte XA-Transaktionen verwenden standardmäßig die Isolationsstufe "Lesen mit Commit".  
  
## <a name="guidelines-and-limitations-when-using-xa-transactions"></a>Richtlinien und Einschränkungen für die Verwendung von XA-Transaktionen  

Die folgenden zusätzlichen Richtlinien gelten für eng verkoppelte Transaktionen:  

- Wenn Sie XA-Transaktionen zusammen mit MS DTC (Microsoft Distributed Transaction Coordinator) verwenden, stellen Sie möglicherweise fest, dass die aktuelle Version von MS DTC eng verkoppeltes XA-Verzweigungsverhalten nicht unterstützt. MS DTC verfügt beispielsweise über eine 1:1-Zuordnung zwischen einer Transaktions-ID für eine XA-Verzweigung (XID) und einer MS DTC-Transaktions-ID, und die von lose verbundenen XA-Verzweigungen ausgeführten Aktionen sind voneinander isoliert.  
  
- MS DTC unterstützt auch eng verknüpfte XA-Branches, bei denen mehrere XA-Branches mit der gleichen globalen Transaktions-IDs (GTRID) einer einzelnen MS DTC-Transaktions-ID zugewiesen werden. Durch diese Unterstützung können mehrere eng verkoppelte XA-Verzweigungen die jeweiligen Änderungen im Ressourcen-Manager anzeigen, beispielsweise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
- Das Flag [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) ermöglicht, dass die Anwendungen die eng verkoppelten XA-Transaktionen verwenden können, die verschiedene XA-Verzweigungstransaktions-IDs (BQUAL) aufweisen, jedoch über dieselbe globale Transaktions-ID (GTRID) und Format-ID (FormatID) verfügen. Damit Sie dieses Feature verwenden können, müssen Sie [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) für den flags-Parameter der XAResource.start-Methode festlegen:
  
    ```java
    xaRes.start(xid, SQLServerXAResource.SSTRANSTIGHTLYCPLD);  
    ```  
  
## <a name="configuration-instructions"></a>Konfigurationsanweisungen

Die folgenden Schritte sind erforderlich, wenn Sie XA-Datenquellen zusammen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden möchten.  

> [!NOTE]  
> Die JDBC-Komponenten für verteilte Transaktionen sind im Verzeichnis "xa" der JDBC-Treiberinstallation enthalten. Zu diesen Komponenten zählen die Dateien "xa_install.sql" und "sqljdbc_xa.dll". Wenn Sie auf verschiedenen Clients verschiedene Versionen des JDBC-Treibers installiert haben, empfiehlt sich die Verwendung der aktuellen sqljdbc_xa.dll-Datei auf dem Server.  

> [!NOTE]  
> Ab SQL Server 2019 CTP 2.0 (Public Preview) sind die verteilten JDBC-XA-Transaktionskomponenten in der SQL Server-Engine enthalten. Außerdem können diese mithilfe einer gespeicherten Systemprozedur aktiviert oder deaktiviert werden.
> Führen Sie die folgende gespeicherte Prozedur aus, um die erforderlichen Komponenten zum Durchführen von verteilten XA-Transaktionen mit dem JDBC-Treiber zu aktivieren.
>
> EXEC sp_sqljdbc_xa_install
>
> Führen Sie die folgende gespeicherte Prozedur aus, um die zuvor installierten Komponenten zu deaktivieren.
>
> EXEC sp_sqljdbc_xa_uninstall

### <a name="running-the-ms-dtc-service"></a>Ausführen des MS DTC-Diensts

Der MS DTC-Dienst muss im Service Manager als **Automatisch** markiert werden, damit er beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensts ausgeführt wird. Führen Sie die folgenden Schritte aus, um MS DTC für XA-Transaktionen zu aktivieren:  
  
Unter Windows Vista und höher:  
  
1. Klicken Sie auf **Start**, geben Sie im Feld **Suche starten** den Namen **dcomcnfg** ein, und drücken Sie dann die EINGABETASTE, um **Komponentendienste** zu öffnen. Sie können auch im Feld **Suche starten** auch den Pfad %windir%\system32\comexp.msc eingeben, um **Komponentendienste** zu öffnen.  
  
2. Erweitern Sie Komponentendienste, Computer, Arbeitsplatz und dann Distributed Transaction Coordinator.  
  
3. Klicken Sie mit der rechten Maustaste auf **Lokaler DTC**, und wählen Sie anschließend **Eigenschaften** aus.  
  
4. Klicken Sie im Dialogfeld **Eigenschaften von Lokaler DTC** auf die Registerkarte **Sicherheit**.  
  
5. Aktivieren Sie das Kontrollkästchen **XA-Transaktionen ermöglichen**, und klicken Sie anschließend auf **OK**. Daraufhin wird der MS DTC-Dienst neu gestartet.
  
6. Klicken Sie erneut auf **OK**, um das Dialogfeld **Eigenschaften** zu schließen, und schließen Sie anschließend **Komponentendienste**.  
  
7. Beenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und starten Sie diesen erneut, damit die MS DTC-Änderungen synchronisiert werden.  

### <a name="configuring-the-jdbc-distributed-transaction-components"></a>Konfigurieren der JDBC-Komponenten für verteilte Transaktionen  

Führen Sie die folgenden Schritte aus, um die Komponenten des JDBC-Treibers für verteilte Transaktionen zu konfigurieren:  
  
1. Kopieren Sie die neue Datei „sqljdbc_xa.dll“ aus dem Installationsverzeichnis des JDBC-Treibers auf allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computern, die an verteilten Transaktionen teilnehmen, in das Verzeichnis „Binn“.  
  
    > [!NOTE]  
    > Wenn Sie XA-Transaktionen mit einem 32-Bit-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden, verwenden Sie die Datei „sqljdbc_xa.dll“ im Ordner „x86“, auch wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem x64-Prozessor installiert ist. Wenn Sie XA-Transaktionen mit einem 64-Bit-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem x64-Prozessor verwenden, verwenden Sie die Datei „sqljdbc_xa.dll“ im Ordner „x64“.  
  
2. Führen Sie auf allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanzen, die an verteilten Transaktionen teilnehmen, das Datenbankskript „xa_install.sql“ aus. Mit diesem Skript werden die erweiterten gespeicherten Prozeduren installiert, die von sqljdbc_xa.dll aufgerufen werden. Diese erweiterten gespeicherten Prozeduren implementieren die Unterstützung für verteilte Transaktionen und XA für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. Sie müssen dieses Skript als Administrator der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz ausführen.  
  
3. Um einem bestimmten Benutzer die Berechtigungen für die Teilnahme an verteilten Transaktionen mit dem JDBC-Treiber zu gewähren, fügen Sie den Benutzer der Rolle "SqlJDBCXAUser" hinzu.  
  
Sie können auf jeder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz nur eine Version der Assembly „sqljdbc_xa.dll“ gleichzeitig konfigurieren. Anwendungen müssen möglicherweise unterschiedliche Versionen des JDBC-Treibers verwenden, um mithilfe der XA-Verbindung eine Verbindung mit der gleichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herzustellen. In diesem Fall muss die Datei „sqljdbc_xa.dll“, die Teil des neuesten JDBC-Treibers ist, auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz installiert werden.  
  
Sie können die derzeit auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz installierte Version von „sqljdbc_xa.dll“ auf drei Arten überprüfen:
  
1. Öffnen Sie das Verzeichnis „LOG“ des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computers, der an verteilten Transaktionen teilnehmen soll. Wählen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datei „ERRORLOG“ aus, und öffnen Sie diese. Suchen Sie in der Datei "ERRORLOG" nach "Version ... von 'SQLJDBC_XA.dll' wird verwendet".  
  
2. Öffnen Sie das Verzeichnis „Binn“ des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computers, der an verteilten Transaktionen teilnehmen soll. Wählen Sie die Assembly „sqljdbc_xa.dll“ aus.

    - Unter Windows Vista oder höher: Klicken Sie mit der rechten Maustaste auf „sqljdbc_xa.dll“, und wählen Sie dann „Eigenschaften“ aus. Klicken Sie dann auf die Registerkarte **Details**. Im Feld **Dateiversion** wird die Version von „sqljdbc_xa.dll“ angezeigt, die derzeit auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz installiert ist.  
  
3. Legen Sie die Protokollfunktion wie im Codebeispiel im nächsten Abschnitt fest. Suchen Sie in der Ausgabeprotokolldatei nach "Server-XA-DLL-Version ...".  

### <a name="configuring-server-side-timeout-settings-for-automatic-rollback-of-unprepared-transactions"></a><a name="BKMK_ServerSide"></a>Konfigurieren von serverseitigen Timeouteinstellungen für den automatischen Rollback nicht vorbereiteter Transaktionen  

> [!WARNING]  
> Diese serverseitige Option wurde im Microsoft JDBC-Treiber 4.2 (und höher) für SQL Server neu eingeführt. Um das aktualisierte Verhalten zu verwenden, stellen Sie sicher, dass sqljdbc_xa.dll auf dem Server aktualisiert wurde. Weitere Informationen zum Festlegen von clientseitigen Timeouts finden Sie unter [XAResource.setTransactionTimeout()](https://docs.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html).  

Das Timeoutverhalten von verteilten Transaktionen wird mithilfe von zwei Registrierungseinstellungen (DWORD-Werten) gesteuert:  
  
- **XADefaultTimeout** (in Sekunden): Der zu verwendende Standardwert für das Zeitlimit, wenn der Benutzer kein Zeitlimit angibt Die Standardeinstellung ist 0.  
  
- **XAMaxTimeout** (in Sekunden): Der Höchstwert, den Benutzer für das Zeitlimit festlegen können Die Standardeinstellung ist 0.  
  
Diese Einstellungen sind für die jeweilige SQL Server-Instanz spezifisch und sollten unter diesem Registrierungsschlüssel erstellt werden:  

```bash
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL<version>.<instance_name>\XATimeout  
```

> [!NOTE]  
> Für 32-Bit-Installationen von SQL Server, die auf 64-Bit-Computern ausgeführt werden, sollten die Registrierungseinstellungen unter diesem Schlüssel erstellt werden: `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Microsoft SQL Server\MSSQL<version>.<instance_name>\XATimeout`
  
Ein Timeoutwert wird für jede Transaktion bei deren Start festgelegt, und es erfolgt ein Rollback der Transaktion durch SQL Server, wenn der Timeout abläuft. Das Timeout wird auf der Grundlage dieser Registrierungseinstellungen und der Angaben des Benutzers in „XAResource.setTransactionTimeout()“ festgelegt. Hier einige Beispiele zur Interpretation dieser Timeoutwerte:  
  
- `XADefaultTimeout = 0`, `XAMaxTimeout = 0`
  
     Bedeutet, dass kein Standardtimeout verwendet wird, und kein maximales Timeout für Clients durchgesetzt wird. In diesem Fall tritt ein Timeout für Transaktionen nur dann auf, wenn der Client ein Timeout mithilfe von XAResource.setTransactionTimeout festlegt.  
  
- `XADefaultTimeout = 60`, `XAMaxTimeout = 0`
  
     Bedeutet, dass alle Transaktionen ein Timeout von 60 Sekunden aufweisen, wenn vom Client kein Timeout festgelegt wird. Wenn der Client ein Timeout angibt, wird dieser Timeoutwert verwendet. Es wird kein maximaler Wert für das Timeout durchgesetzt.  
  
- `XADefaultTimeout = 30`, `XAMaxTimeout = 60`
  
     Bedeutet, dass alle Transaktionen ein Timeout von 30 Sekunden aufweisen, wenn vom Client kein Timeout festgelegt wird. Wenn der Client ein Timeout angibt, wird das Timeout des Clients verwendet, sofern es weniger als 60 Sekunden (den Maximalwert) beträgt.  
  
- `XADefaultTimeout = 0`, `XAMaxTimeout = 30`
  
     Bedeutet, dass alle Transaktionen ein Timeout von 30 Sekunden (den Maximalwert) aufweisen, wenn vom Client kein Timeout festgelegt wird. Wenn der Client ein Timeout angibt, wird das Timeout des Clients verwendet, sofern es weniger als 30 Sekunden (den Maximalwert) beträgt.  
  
### <a name="upgrading-sqljdbc_xadll"></a>Aktualisieren von "sqljdbc_xa.dll"

Wenn Sie eine neue Version des JDBC-Treibers installieren, sollten Sie auch sqljdbc_xa.dll aus der neuen Version verwenden, um sqljdbc_xa.dll auf dem Server zu aktualisieren.  
  
> [!IMPORTANT]  
> Sie sollten das Upgrade der Datei „sqljdbc_xa.dll“ im Rahmen einer Wartung oder zu einem Zeitpunkt ausführen, zu dem keine MS DTC-Transaktionen in Bearbeitung sind.
  
1. Entladen Sie „sqljdbc_xa.dll“ mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehl **DBCC sqljdbc_xa (FREE)** .  
  
2. Kopieren Sie die neue Datei „sqljdbc_xa.dll“ aus dem Installationsverzeichnis des JDBC-Treibers auf allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computern, die an verteilten Transaktionen teilnehmen, in das Verzeichnis „Binn“.  
  
    Die neue DLL wird geladen, wenn eine erweiterte Prozedur in sqljdbc_xa.dll aufgerufen wird. Sie müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht neu starten, um die neuen Definitionen zu laden.  
  
### <a name="configuring-the-user-defined-roles"></a>Konfigurieren der benutzerdefinierten Rollen

Um einem bestimmten Benutzer die Berechtigungen für die Teilnahme an verteilten Transaktionen mit dem JDBC-Treiber zu gewähren, fügen Sie den Benutzer der Rolle "SqlJDBCXAUser" hinzu. Mit dem folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code können Sie z.B. der Rolle „SqlJDBCXAUser“ einen Benutzer mit dem Namen „shelby“ (Benutzer mit dem Namen „shelby“, der die normale SQL-Anmeldung verwendet) hinzufügen:  

```sql
USE master  
GO  
EXEC sp_grantdbaccess 'shelby', 'shelby'  
GO  
EXEC sp_addrolemember [SqlJDBCXAUser], 'shelby'  
```

Benutzerdefinierte SQL-Rollen werden jeweils für eine Datenbank definiert. Wenn Sie aus Sicherheitsgründen eigene Rollen erstellen möchten, müssen Sie die Rolle in jeder Datenbank definieren und die Benutzer den jeweiligen Datenbanken hinzufügen. Die Rolle "SqlJDBCXAUser" ist ausschließlich in der Masterdatenbank definiert, da damit Zugriff auf die erweiterten gespeicherten SQL JDBC-Prozeduren gewährt wird, die sich in der Masterdatenbank befinden. Sie müssen den einzelnen Benutzern zuerst Zugriff auf die Masterdatenbank und dann auf die Rolle "SqlJDBCXAUser" gewähren. Dazu müssen Sie bei der Masterdatenbank angemeldet sein.  

## <a name="example"></a>Beispiel  

```java
import java.net.Inet4Address;
import java.sql.*;
import java.util.Random;
import javax.sql.XAConnection;
import javax.transaction.xa.*;
import com.microsoft.sqlserver.jdbc.*;


public class testXA {

    public static void main(String[] args) throws Exception {

        // Create variables for the connection string.
        String prefix = "jdbc:sqlserver://";
        String serverName = "localhost";
        int portNumber = 1433;
        String databaseName = "AdventureWorks";
        String user = "UserName";
        String password = "*****";

        String connectionUrl = prefix + serverName + ":" + portNumber + ";databaseName=" + databaseName + ";user="
                + user + ";password=" + password;

        Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement()) {
            stmt.executeUpdate("CREATE TABLE XAMin (f1 int, f2 varchar(max))");

        }
        // Create the XA data source and XA ready connection.
        SQLServerXADataSource ds = new SQLServerXADataSource();
        ds.setUser(user);
        ds.setPassword(password);
        ds.setServerName(serverName);
        ds.setPortNumber(portNumber);
        ds.setDatabaseName(databaseName);

        XAConnection xaCon = ds.getXAConnection();
        try (Connection con = xaCon.getConnection()) {

            // Get a unique Xid object for testing.
            XAResource xaRes = null;
            Xid xid = null;
            xid = XidImpl.getUniqueXid(1);

            // Get the XAResource object and set the timeout value.
            xaRes = xaCon.getXAResource();
            xaRes.setTransactionTimeout(0);

            // Perform the XA transaction.
            System.out.println("Write -> xid = " + xid.toString());
            xaRes.start(xid, XAResource.TMNOFLAGS);
            PreparedStatement pstmt = con.prepareStatement("INSERT INTO XAMin (f1,f2) VALUES (?, ?)");
            pstmt.setInt(1, 1);
            pstmt.setString(2, xid.toString());
            pstmt.executeUpdate();

            // Commit the transaction.
            xaRes.end(xid, XAResource.TMSUCCESS);
            xaRes.commit(xid, true);
        }
        xaCon.close();

        // Open a new connection and read back the record to verify that it worked.
        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT * FROM XAMin")) {
            rs.next();
            System.out.println("Read -> xid = " + rs.getString(2));
            stmt.executeUpdate("DROP TABLE XAMin");
        }
    }
}


class XidImpl implements Xid {

    public int formatId;
    public byte[] gtrid;
    public byte[] bqual;

    public byte[] getGlobalTransactionId() {
        return gtrid;
    }

    public byte[] getBranchQualifier() {
        return bqual;
    }

    public int getFormatId() {
        return formatId;
    }

    XidImpl(int formatId, byte[] gtrid, byte[] bqual) {
        this.formatId = formatId;
        this.gtrid = gtrid;
        this.bqual = bqual;
    }

    public String toString() {
        int hexVal;
        StringBuffer sb = new StringBuffer(512);
        sb.append("formatId=" + formatId);
        sb.append(" gtrid(" + gtrid.length + ")={0x");
        for (int i = 0; i < gtrid.length; i++) {
            hexVal = gtrid[i] & 0xFF;
            if (hexVal < 0x10)
                sb.append("0" + Integer.toHexString(gtrid[i] & 0xFF));
            else
                sb.append(Integer.toHexString(gtrid[i] & 0xFF));
        }
        sb.append("} bqual(" + bqual.length + ")={0x");
        for (int i = 0; i < bqual.length; i++) {
            hexVal = bqual[i] & 0xFF;
            if (hexVal < 0x10)
                sb.append("0" + Integer.toHexString(bqual[i] & 0xFF));
            else
                sb.append(Integer.toHexString(bqual[i] & 0xFF));
        }
        sb.append("}");
        return sb.toString();
    }

    // Returns a globally unique transaction id.
    static byte[] localIP = null;
    static int txnUniqueID = 0;

    static Xid getUniqueXid(int tid) {

        Random rnd = new Random(System.currentTimeMillis());
        txnUniqueID++;
        int txnUID = txnUniqueID;
        int tidID = tid;
        int randID = rnd.nextInt();
        byte[] gtrid = new byte[64];
        byte[] bqual = new byte[64];
        if (null == localIP) {
            try {
                localIP = Inet4Address.getLocalHost().getAddress();
            } catch (Exception ex) {
                localIP = new byte[] {0x01, 0x02, 0x03, 0x04};
            }
        }
        System.arraycopy(localIP, 0, gtrid, 0, 4);
        System.arraycopy(localIP, 0, bqual, 0, 4);

        // Bytes 4 -> 7 - unique transaction id.
        // Bytes 8 ->11 - thread id.
        // Bytes 12->15 - random number generated by using seed from current time in milliseconds.
        for (int i = 0; i <= 3; i++) {
            gtrid[i + 4] = (byte) (txnUID % 0x100);
            bqual[i + 4] = (byte) (txnUID % 0x100);
            txnUID >>= 8;
            gtrid[i + 8] = (byte) (tidID % 0x100);
            bqual[i + 8] = (byte) (tidID % 0x100);
            tidID >>= 8;
            gtrid[i + 12] = (byte) (randID % 0x100);
            bqual[i + 12] = (byte) (randID % 0x100);
            randID >>= 8;
        }
        return new XidImpl(0x1234, gtrid, bqual);
    }
}

```

## <a name="see-also"></a>Weitere Informationen  

[Ausführen von Transaktionen mit dem JDBC-Treiber](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
