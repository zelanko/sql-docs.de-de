---
title: 'GenerateDatabaseRightsScript-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 575eab878e0ef9b4357c09a0a3deedf143c237b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098483"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a>GenerateDatabaseRightsScript-Methode (WMI: MSReportServer_ConfigurationSetting)
  Generiert ein SQL-Skript, das verwendet werden kann, um einem Benutzer Berechtigungen für die Berichtsserver-Datenbank sowie für andere Datenbanken zu gewähren, die für das Ausführen eines Berichtsservers erforderlich sind. Es wird erwartet, dass der Aufrufer eine Verbindung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankserver herstellt und das Skript ausführt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *User*  
 Der Benutzername oder die Windows-Sicherheits-ID (SID) des Benutzers, dem durch das Skript Berechtigungen erteilt werden.  
  
 *DatabaseName*  
 Der Name der Datenbank, für die dem Benutzer durch das Skript Zugriff gewährt wird.  
  
 *IsRemote*  
 Ein boolescher Wert, der angibt, ob es sich vom Berichtsserver aus gesehen um eine Remotedatenbank handelt.  
  
 *IsWindowsUser*  
 Ein boolescher Wert, der angibt, ob der angegebene Benutzername für einen Windows-Benutzer oder einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzer steht.  
  
 *Skript*  
 [out] Eine Zeichenfolge, die das generierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Skript enthält  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn *DatabaseName* leer ist, wird *IsRemote* ignoriert und der Wert aus der Konfigurationsdatei des Berichtsservers als Datenbankname verwendet.  
  
 Wenn *IsWindowsUser* auf `true`festgelegt ist, muss der *Benutzername* im \<Format Domäne \\><\>Benutzername sein.  
  
 Wenn *IsWindowsUser* auf `true`festgelegt ist, werden dem Benutzer durch das generierte Skript Anmelde Berechtigungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erteilt, wobei die Berichts Server-Datenbank als Standarddatenbank festgelegt und die **RSExec** -Rolle für die Berichts Server-Datenbank, die temporäre Berichts Server-Datenbank, die Master-Datenbank und die msdb-Systemdatenbank erteilt wird.  
  
 Wenn *IsWindowsUser* auf `true`festgelegt ist, akzeptiert die Methode standardmäßige Windows-SIDs als Eingabe. Wird eine standardmäßige Windows-SID oder ein Dienstkontoname bereitgestellt, wird diese bzw. dieser in eine Benutzernamen-Zeichenfolge übersetzt. Falls es sich bei der Datenbank um eine lokale Datenbank handelt, wird das Konto in die richtige lokalisierte Darstellung des Kontos übersetzt. Bei einer Remotedatenbank wird das Konto als das Konto des Computers dargestellt.  
  
 In der folgenden Tabelle sind Konten, die übersetzt werden, und ihre Remotedarstellung aufgeführt.  
  
|Konto/SID, das bzw. die übersetzt wird|Allgemeiner Name|Remotename|  
|---------------------------------------|-----------------|-----------------|  
|(S-1-5-18)|Lokales System|
  \<Domäne>\\<Computername\>$|  
|.\LocalSystem|Lokales System|
  \<Domäne>\\<Computername\>$|  
|ComputerName\LocalSystem|Lokales System|
  \<Domäne>\\<Computername\>$|  
|LocalSystem|Lokales System|
  \<Domäne>\\<Computername\>$|  
|(S-1-5-20)|Netzwerkdienst|
  \<Domäne>\\<Computername\>$|  
|NT AUTHORITY\NetworkService|Netzwerkdienst|
  \<Domäne>\\<Computername\>$|  
|(S-1-5-19)|Lokaler Dienst|Fehler – siehe unten.|  
|NT AUTHORITY\LocalService|Lokaler Dienst|Fehler – siehe unten.|  
  
 Wenn Sie unter [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]ein integriertes Konto verwenden und es sich bei der Berichtsserver-Datenbank um eine Remotedatenbank handelt, wird ein Fehler zurückgegeben.  
  
 Falls das integrierte `LocalService`-Konto angegeben wird und es sich bei der Berichtsserver-Datenbank um eine Remotedatenbank handelt, wird ein Fehler zurückgegeben.  
  
 Wenn *IsWindowsUser* auf true festgelegt ist und der in *UserName* bereitgestellte Wert übersetzt werden muss, bestimmt der WMI-Anbieter, ob sich die Berichtsserver-Datenbank auf demselben Computer oder auf einem Remotecomputer befindet. Um zu bestimmen, ob es sich um eine lokale Installation handelt, wertet der WMI-Anbieter die DatabaseServerName-Eigenschaft anhand der folgenden Werteliste aus. Wenn eine Übereinstimmung gefunden wird, handelt es sich um eine lokale Datenbank. Andernfalls ist es eine Remotedatenbank. Bei dem Vergleich wird Groß- und Kleinschreibung nicht unterschieden.  
  
|Wert von "DatabaseServerName"|Beispiel|  
|---------------------------------|-------------|  
|"."||  
|„(local)“||  
|„LOCAL“||  
|localhost||  
|\<MachineName->|testlab14|  
|
  \<ComputerFQDN>|example.redmond.microsoft.com|  
|\<IPAddress->|180.012.345,678|  
  
 Wenn *IsWindowsUser* auf `true`festgelegt ist, ruft der WMI-Anbieter LookupAccountName auf, um die sid für das Konto zu erhalten, und ruft dann LookupAccountSid auf, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um den Namen zu erhalten, der in das Skript eingefügt werden soll. Hierdurch wird sichergestellt, dass der verwendete Kontoname die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Überprüfung erfolgreich durchläuft.  
  
 Wenn *IsWindowsUser* auf `false`festgelegt ist, gewährt das generierte Skript die **RSExec** -Rolle für die Berichts Server-Datenbank, die temporäre Berichts Server-Datenbank und die msdb-Datenbank.  
  
 Wenn *IsWindowsUser* auf `false`festgelegt ist, muss der SQL Server Benutzer bereits im vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sein, damit das Skript erfolgreich ausgeführt werden kann.  
  
 Wenn für den Berichtsserver keine Berichtsserver-Datenbank angegeben ist, wird bei einem Aufruf von GrantRightsToDatabaseUser ein Fehler zurückgegeben.  
  
 Das generierte Skript unterstützt [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
