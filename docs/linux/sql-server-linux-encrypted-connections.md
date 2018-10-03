---
title: Verschlüsseln von Verbindungen zu SQLServer unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt Verschlüsseln von Verbindungen zu SQL Server unter Linux.
author: vin-yu
ms.date: 01/30/2018
ms.author: vinsonyu
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
helpviewer_keywords:
- Linux, encrypted connections
ms.openlocfilehash: 46795611f8bb3554491dbdd400d383a59a540b5c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766590"
---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Verschlüsseln von Verbindungen zu SQLServer unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux können Transport Layer Security (TLS) zum Verschlüsseln von Daten, die über ein Netzwerk zwischen einer Clientanwendung und einer Instanz von übertragen werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt die gleichen TLS-Protokolle unter Windows und Linux: TLS 1.2, 1.1 und 1.0. Die Schritte zum Konfigurieren von TLS sind jedoch spezifisch für das Betriebssystem auf dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgeführt wird.  

## <a name="requirements-for-certificates"></a>Anforderungen für Zertifikate 
Bevor Sie beginnen, müssen Sie sicherstellen, dass Ihre Zertifikate die folgenden Voraussetzungen erfüllen:
- Die aktuelle Systemzeit muss nach der gültig von-Eigenschaft des Zertifikats und vor der gültig bis-Eigenschaft des Zertifikats liegen.
- Das Zertifikat muss für die Serverauthentifizierung vorgesehen sein. Dies erfordert die Enhanced Key Usage-Eigenschaft des Zertifikats, das Serverauthentifizierung (1.3.6.1.5.5.7.3.1) angeben.
- Das Zertifikat muss mit der Option KeySpec AT_KEYEXCHANGE erstellt werden. Das Zertifikat des Key Usage-Eigenschaft (KEY_USAGE) enthält in der Regel auch Schlüsselverschlüsselung (CERT_KEY_ENCIPHERMENT_KEY_USAGE).
- Dass der allgemeine Name (CN) den Hostnamen oder den vollqualifizierten Domänennamen (FQDN) des Servercomputers übereinstimmt, muss die Eigenschaft Subject des Zertifikats angeben. Hinweis: Platzhalterzertifikate werden unterstützt.

## <a name="configuring-the-openssl-libraries-for-use-optional"></a>Konfigurieren die OpenSSL-Bibliotheken für die Verwendung (Optional)
Können Sie symbolische Verknüpfungen erstellen die `/opt/mssql/lib/` Verzeichnis, das dem verweisen auf `libcrypto.so` und `libssl.so` Bibliotheken für die Verschlüsselung verwendet werden soll. Dies ist nützlich, wenn Sie SQL Server verwenden eine bestimmte Version von OpenSSL anstelle der Standardeinstellung, die vom System bereitgestellten erzwingen möchten. Wenn diese symbolischen Verknüpfungen nicht vorhanden sind, wird SQL Server die konfiguriert standardmäßig OpenSSL-Bibliotheken auf dem System geladen.

Diese symbolischen Verknüpfungen heißen `libcrypto.so` und `libssl.so` und platziert Sie in der `/opt/mssql/lib/` Verzeichnis.

## <a name="overview"></a>Übersicht
TLS wird zum Verschlüsseln von Verbindungen von einer Clientanwendung verwendet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Wenn ordnungsgemäß konfiguriert ist, bietet TLS sowohl Datenschutz und Integrität der Daten für die Kommunikation zwischen dem Client und dem Server.  TLS-Verbindungen können es sich entweder um Client initiiert oder Server initiierten sein. 

## <a name="client-initiated-encryption"></a>Vom Client initiierten Verschlüsselung 
- **Zertifikat generieren** (/ CN sollte mit Ihrem SQL Server-Host des vollständig qualifizierten Domänennamen überein)

> [!NOTE]
> Für dieses Beispiel, dass wir ein selbstsigniertes Zertifikat verwenden sollte dies nicht für Produktionsszenarien verwendet werden. Sie sollten ZS-Zertifikate verwenden. 

        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Konfigurieren von SQLServer**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0 

- **Registrieren des Zertifikats auf dem Client (Windows, Linux oder MacOS)**

    -   Wenn Sie mit der Zertifizierungsstelle signiertes Zertifikat arbeiten, müssen Sie das Zertifikat der Zertifizierungsstelle (Certificate Authority, CA) anstelle des Benutzerzertifikats auf den Clientcomputer kopieren. 
    -   Wenn Sie das selbstsignierte Zertifikat verwenden, kopieren Sie die PEM-Datei in die folgenden Ordner, die je nach Verteilung und führen Sie die Befehle, um sie zu aktivieren 
        - **Ubuntu**: Copy-Zertifikats in den ```/usr/share/ca-certificates/``` CRT-Erweiterung umbenennen Dpkg-Reconfigure ZS-Zertifikate verwenden, um es als System-CA-Zertifikat zu aktivieren. 
        - **RHEL**: Copy-Zertifikats in den ```/etc/pki/ca-trust/source/anchors/``` verwenden ```update-ca-trust``` als System-CA-Zertifikat aktivieren.
        - **SUSE**: Copy-Zertifikats in den ```/usr/share/pki/trust/anchors/``` verwenden ```update-ca-certificates``` als System-CA-Zertifikat aktivieren.
        - **Windows**: importieren die PEM-Datei als ein Zertifikat unter dem aktuellen Benutzer -> Vertrauenswürdige Stammzertifizierungsstellen-Zertifikate >.
        - **macOS**: 
           - Kopieren Sie das Zertifikat zu ```/usr/local/etc/openssl/certs```
           - Führen Sie den folgenden Befehl aus, um den Hashwert zu erhalten: ```/usr/local/Cellar/openssql/1.0.2l/openssql x509 -hash -in mssql.pem -noout```
           - Benennen Sie das Zertifikat in Wert ein. Beispiel: ```mv mssql.pem dc2dd900.0```. Stellen Sie sicher, dass dc2dd900.0 ```/usr/local/etc/openssl/certs```
    
-   **Exemplarische Verbindungszeichenfolgen** 

    - **[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]**   
  ![SSMS-Verbindungsdialogfeld](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "SSMS-Verbindungsdialogfeld")  
  
    - **SQLCMD** 

            sqlcmd  -S <sqlhostname> -N -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=True; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=Yes; TrustServerCertificate=no;" 
    - **JDBC** 
    
            "encrypt=true; trustServerCertificate=false;" 

## <a name="server-initiated-encryption"></a>Vom Server initiierte Verschlüsselung 

- **Zertifikat generieren** (/ CN sollte mit Ihren SQL Server-Host den vollqualifizierten Domänennamen überein)
        
        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Konfigurieren von SQLServer**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
        
-   **Exemplarische Verbindungszeichenfolgen** 

    - **SQLCMD**

            sqlcmd  -S <sqlhostname> -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=False; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=no; TrustServerCertificate=no;"  
    - **JDBC** 
    
            "encrypt=false; trustServerCertificate=false;" 
            
> [!NOTE]
> Legen Sie **TrustServerCertificate** auf "true", wenn der Client an Zertifizierungsstelle, um die Authentizität des Zertifikats überprüft keine Verbindung herstellen kann

## <a name="common-connection-errors"></a>Häufigen Verbindungsproblemen  

|Fehlermeldung |Fix |
|--- |--- |
|Die Zertifikatkette wurde von einer Zertifizierungsstelle ausgestellt, die nicht vertrauenswürdig ist.  |Dieser Fehler tritt auf, wenn Clients nicht zum Überprüfen der Signatur auf das von SQL Server während des TLS-Handshakes bereitgestellte Zertifikat können. Stellen Sie sicher, dass der Client vertraut wird entweder die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] direkt Zertifikat oder der Zertifizierungsstelle, die das SQL Server-Zertifikat signiert. |
|Der Zielprinzipalname ist falsch.  |Stellen Sie sicher, dass das Feld "Common Name" für SQL Server Zertifikat in der Clientverbindungszeichenfolge angegebene Servername entspricht. |  
|Eine vorhandene Verbindung wurde erzwungenermaßen vom Remotehost geschlossen. |Dieser Fehler kann auftreten, wenn der Client die TLS-Protokollversion, die erforderlich sind, von SQL Server nicht unterstützt. Z. B. wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für TLS 1.2 erfordern, stellen Sie sicher, dass Ihre Clients unterstützen auch das TLS 1.2-Protokoll konfiguriert ist. |
| | |   
