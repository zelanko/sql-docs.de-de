---
title: Aufbauen von sicheren Verbindungen in ADOMD.NET | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- connections [ADOMD.NET]
- security [ADOMD.NET]
ms.assetid: b084d447-1456-45a4-8e0e-746c07d7d6fd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b77fefaad8ac573e526412f1c81be3969743a3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178210"
---
# <a name="establishing-secure-connections-in-adomdnet"></a>Aufbauen von sicheren Verbindungen in ADOMD.NET
  Wenn Sie eine Verbindung in ADOMD.NET verwenden, ist die für die Verbindung verwendete Sicherheitsmethode von dem Wert der `ProtectionLevel`-Eigenschaft der Verbindungszeichenfolge abhängig, die beim Aufruf der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A>-Methode der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> verwendet wird.  
  
 Die `ProtectionLevel`-Eigenschaft stellt vier Sicherheitsebenen bereit: nicht authentifiziert, authentifiziert, signiert und verschlüsselt. In der folgenden Tabelle werden diese verschiedenen Sicherheitsstufen beschrieben.  
  
> [!NOTE]  
>  Wenn Sie Datenbankverbindungspooling verwenden, ist die Datenbank nicht in der Lage, Sicherheit zu verwalten. Das liegt daran, dass für Datenbankverbindungspooling Verbindungszeichenfolgen identisch sein müssen, um Verbindungen zu einem Pool zusammenzufassen. Deshalb müssen Sie Sicherheit an anderer Stelle verwalten.  
  
|Sicherheitsebene|ProtectionLevel-Wert|  
|--------------------|---------------------------|  
|*nicht authentifizierte Verbindung*<br /> Eine nicht authentifizierte Verbindung nimmt keine Form der Authentifizierung vor. Diese Art der Verbindung stellt die am häufigsten unterstützte, aber am wenigsten sichere Verbindungsart, dar.|`None`|  
|*authentifizierte Verbindung*<br /> Eine authentifizierte Verbindung authentifiziert den Benutzer, der die Verbindung herstellt, sichert jedoch keine weitere Kommunikation. Diese Art der Verbindung ist sinnvoll, da Sie die Identität des Benutzers oder der Anwendung feststellen können, der oder die eine Verbindung mit der analytischen Datenquelle herstellt.|`Connect`|  
|*signierte Verbindung*<br /> Eine signierte Verbindung authentifiziert den Benutzer, der die Verbindung anfordert, und stellt anschließend sicher, dass die Übertragungen nicht verändert werden. Diese Art von Verbindung ist nützlich, wenn die Echtheit der übertragenen Daten überprüft werden muss. Eine signierte Verbindung verhindert jedoch nur, dass der Inhalt des Datenpakets geändert wird. Der Inhalt kann unterwegs noch immer angezeigt werden. **Hinweis:** eine signierte Verbindung wird nur unterstützt, von der XML for Analysis-Anbieter, die vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|`Pkt Integrity` oder `PktIntegrity`|  
|*verschlüsselte Verbindung*<br /> Eine verschlüsselte Verbindung ist der von ADOMD.NET verwendete Standardverbindungstyp. Diese Verbindungsart authentifiziert den Benutzer, der die Verbindung anfordert, und verschlüsselt außerdem die übertragenen Daten. Eine verschlüsselte Verbindung ist die sicherste Verbindungsart, die von ADOMD.NET erstellt werden kann. Der Inhalt des Datenpakets kann nicht angezeigt oder geändert werden, sodass die Daten während der Übertragung geschützt sind. **Hinweis:** eine verschlüsselte Verbindung wird nur unterstützt, von der XML for Analysis-Anbieter, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|`Pkt Privacy` oder `PktPrivacy`|  
  
 Es sind jedoch nicht alle Sicherheitsebenen für alle Arten von Verbindungen verfügbar:  
  
-   Eine TCP-Verbindung kann alle der vier Sicherheitsebenen verwenden. Tatsächlich stellt eine zusammen mit der integrierten Sicherheit von Windows verwendete TCP-Verbindung die sicherste Methode der Verbindung mit einer analytischen Datenquelle dar.  
  
-   Eine HTTP-Verbindung kann nur eine authentifizierte Verbindung sein. Daher muss die `ProtectionLevel`-Eigenschaft auf `Connect` festgelegt werden.  
  
-   Eine HTTPS-Verbindung kann nur eine verschlüsselte Verbindung sein. Daher muss die `ProtectionLevel`-Eigenschaft auf `Pkt Privacy` oder `PktPrivacy` festgelegt werden.  
  
## <a name="securing-tcp-connections"></a>Sichern von TCP-Verbindungen  
 Für eine TCP-Verbindung unterstützt die `ProtectionLevel`-Eigenschaft alle vier Sicherheitsebenen, wie in der folgenden Tabelle dargestellt.  
  
|ProtectionLevel-Wert|Verwendung mit TCP-Verbindung?|Ergebnisse|  
|---------------------------|------------------------------|-------------|  
|`None`|Benutzerkontensteuerung|Gibt eine nicht authentifizierte Verbindung an.<br /><br /> Vom Anbieter wird ein TCP-Datenstrom angefordert, es wird jedoch für den Benutzer, der den Datenstrom anfordert, keinerlei Authentifizierung ausgeführt.|  
|`Connect`|Benutzerkontensteuerung|Gibt eine authentifizierte Verbindung an.<br /><br /> Vom Anbieter wird ein TCP-Datenstrom angefordert, und klicken Sie dann der Sicherheitskontext des Benutzers, der den Datenstrom anfordert, wird bei dem Server authentifiziert wird:<br /><br /> – Wenn die Authentifizierung erfolgreich ist, ist keine weitere Aktion ausgeführt.<br />– Wenn die Authentifizierung fehlschlägt, die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> Objekt trennt die Verbindung das mehrdimensionale Datenquelle und eine Ausnahme ausgelöst.<br /><br /> Nachdem die Authentifizierung erfolgreich gewesen ist oder fehlschlägt, wird der Sicherheitskontext, der verwendet wird, um die Verbindung zu authentifizieren, freigegeben.|  
|`Pkt Integrity` oder `PktIntegrity`|Benutzerkontensteuerung|Gibt eine signierte Verbindung an.<br /><br /> Vom Anbieter wird ein TCP-Datenstrom angefordert, und klicken Sie dann der Sicherheitskontext des Benutzers, der den Datenstrom anfordert, wird bei dem Server authentifiziert wird:<br /><br /> – Wenn die Authentifizierung erfolgreich ist, die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> Objekt schließt den bestehenden TCP-Datenstrom und öffnet einen signierten TCP-Datenstrom, um alle Anforderungen zu verarbeiten. Alle Anforderungen von Daten und Metadaten werden mithilfe des Sicherheitskontexts authentifiziert, der zum Öffnen der Verbindung verwendet wurde. Zudem wird jedes Paket digital signiert, um sicherzustellen, dass die Nutzlast des TCP-Pakets nicht auf irgendeine Weise geändert wurde.<br />– Wenn die Authentifizierung fehlschlägt, die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> Objekt trennt die Verbindung das mehrdimensionale Datenquelle und eine Ausnahme ausgelöst.|  
|`Pkt Privacy` oder `PktPrivacy`|Benutzerkontensteuerung|Gibt eine verschlüsselte Verbindung an. **Hinweis:** Sie können auch eine verschlüsselte Verbindung angeben, indem Sie nicht Festlegen der `ProtectionLevel` Eigenschaft in der Verbindungszeichenfolge. <br /><br /> Vom Anbieter wird ein TCP-Datenstrom angefordert, und der Sicherheitskontext des Benutzers, der den Datenstrom anfordert, wird bei dem Server authentifiziert.<br /><br /> – Wenn die Authentifizierung erfolgreich ist, die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> Objekt schließt den bestehenden TCP-Datenstrom und öffnet einen verschlüsselten TCP-Datenstrom, der alle Anforderungen zu verarbeiten. Alle Anforderungen von Daten und Metadaten werden mithilfe des Sicherheitskontexts authentifiziert, der zum Öffnen der Verbindung verwendet wurde. Außerdem wird die Nutzlast eines jeden TCP-Pakets mit der höchsten Verschlüsselungsmethode verschlüsselt, die sowohl von dem Anbieter als auch von der multidimensionalen Datenquelle unterstützt wird.<br />– Wenn die Authentifizierung fehlschlägt, die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> Objekt trennt die Verbindung das mehrdimensionale Datenquelle und eine Ausnahme ausgelöst.|  
  
### <a name="using-windows-integrated-security-for-the-connection"></a>Verwenden der integrierten Sicherheit von Windows für die Verbindung  
 Die integrierte Sicherheit von Windows ist die sicherste Möglichkeit, eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] herzustellen und zu sichern. Die integrierte Sicherheit von Windows zeigt während des Authentifizierungsprozesses keine Sicherheitsanmeldeinformationen wie Benutzername oder Kennwort an, stattdessen wird die Sicherheits-ID des zurzeit ausgeführten Prozesses verwendet, um die Identität zu ermitteln. Für die meisten Clientanwendungen stellt diese Sicherheits-ID die Identität des gerade angemeldeten Benutzers dar.  
  
 Um die integrierte Sicherheit von Windows zu verwenden, sind für die Verbindungszeichenfolge die folgenden Einstellungen erforderlich:  
  
-   Legen Sie diese Eigenschaft für die `Integrated Security`-Eigenschaft nicht fest, oder legen Sie die Eigenschaft auf `SSPI` fest.  
  
    > [!NOTE]  
    >  Die integrierte Sicherheit von Windows ist nur für TCP-Verbindungen verfügbar, da HTTP-Verbindungen die `Basic`-Einstellung für die `Integrated Security`-Eigenschaft verwenden müssen.  
  
-   Legen Sie diese Eigenschaft für die `ProtectionLevel`-Eigenschaft auf `Connect`, `Pkt Integrity` oder `Pkt Privacy` fest.  
  
## <a name="securing-http-connections"></a>Sichern von HTTP-Verbindungen  
 HTTPS und Secure Sockets Layer (SSL) kann verwendet werden, um die HTTP-Kommunikation mit einer analytischen Datenquelle extern zu sichern.  
  
 Da ein XMLA-Anbieter nur sicheres HTTP verwendet, muss eine HTTP-Verbindung in ADOMD.NET eine signierte Verbindung sein, wie in der folgenden Tabelle dargestellt.  
  
|ProtectionLevel-Wert|Verwendung mit HTTP oder HTTPS|  
|---------------------------|----------------------------|  
|`None`|nein|  
|`Connect`|HTTP|  
|`Pkt Integrity` oder `PktIntegrity`|nein|  
|`Pkt Privacy` oder `PktPrivacy`|HTTPS|  
  
### <a name="opening-a-secure-http-connection"></a>Öffnen einer sicheren HTTP-Verbindung  
 Das folgende Beispiel erläutert, wie ADOMD.NET verwendet wird, um eine HTTP-Verbindung für die `AdventureWorksAS` [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Beispieldatenbank zu öffnen:  
  
```vb  
Public Function GetAWEncryptedConnection( _  
    Optional ByVal serverName As String = "https:\\localhost\isapy\msmdpump.dll") _  
    As AdomdConnection  
  
    Dim strConnectionString As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' To establish an encrypted connection, set the   
        ' ProtectionLevel setting to PktPrivacy.  
        strConnectionString = "DataSource=" & serverName & ";" & _  
            "Catalog=AdventureWorksAS;" & _  
            "ProtectionLevel=PktPrivacy;"  
  
        ' Note that username and password are not supplied here.  
        ' The current security context is used for authentication  
        ' purposes.  
  
        objConnection.ConnectionString = strConnectionString  
        objConnection.Open()  
    Catch ex As Exception  
        objConnection = Nothing  
        Throw ex  
    Finally  
        ' Return the encrypted connection.  
        GetAWEncryptedConnection = objConnection  
    End Try  
End Function  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Aufbauen von Verbindungen in ADOMD.NET](connections-in-adomd-net.md)  
  
  
