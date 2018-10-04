---
title: 'GenerateDatabaseRightsScript-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e322ca0ed99c5c5b84c764cf0d89e2f365b6ed31
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221290"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserverconfigurationsetting"></a>GenerateDatabaseRightsScript-Methode (WMI: MSReportServer_ConfigurationSetting)
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
 *UserName*  
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
  
## <a name="remarks"></a>Hinweise  
 Wenn *DatabaseName* leer ist, wird *IsRemote* ignoriert und der Wert aus der Konfigurationsdatei des Berichtsservers als Datenbankname verwendet.  
  
 Wenn *IsWindowsUser* nastaven NA hodnotu `true`, *Benutzername* muss im Format \<Domäne >\\< Benutzername\>.  
  
 Wenn *IsWindowsUser* nastaven NA hodnotu `true`, das generierte Skript gewährt Anmelderechte für den Benutzer für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Festlegen der Berichtsserver-Datenbank als Standarddatenbank und gewährt der **RSExec** -Rolle auf der Berichtsserver-Datenbank, die temporäre Berichtsserver-Datenbank, die master-Datenbank und die MSDB-Systemdatenbank.  
  
 Wenn *IsWindowsUser* nastaven NA hodnotu `true`, die Methode akzeptiert die standardmäßige Windows-SIDs als Eingabe. Wird eine standardmäßige Windows-SID oder ein Dienstkontoname bereitgestellt, wird diese bzw. dieser in eine Benutzernamen-Zeichenfolge übersetzt. Falls es sich bei der Datenbank um eine lokale Datenbank handelt, wird das Konto in die richtige lokalisierte Darstellung des Kontos übersetzt. Bei einer Remotedatenbank wird das Konto als das Konto des Computers dargestellt.  
  
 In der folgenden Tabelle sind Konten, die übersetzt werden, und ihre Remotedarstellung aufgeführt.  
  
|Konto/SID, das bzw. die übersetzt wird|Allgemeiner Name|Remotename|  
|---------------------------------------|-----------------|-----------------|  
|(S-1-5-18)|Lokales System|\<Domäne>\\<Computername\>$|  
|.\LocalSystem|Lokales System|\<Domäne>\\<Computername\>$|  
|ComputerName\LocalSystem|Lokales System|\<Domäne>\\<Computername\>$|  
|LocalSystem|Lokales System|\<Domäne>\\<Computername\>$|  
|(S-1-5-20)|Netzwerkdienst|\<Domäne>\\<Computername\>$|  
|NT AUTHORITY\NetworkService|Netzwerkdienst|\<Domäne>\\<Computername\>$|  
|(S-1-5-19)|Lokaler Dienst|Fehler – siehe unten.|  
|NT AUTHORITY\LocalService|Lokaler Dienst|Fehler – siehe unten.|  
  
 Wenn Sie unter [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]ein integriertes Konto verwenden und es sich bei der Berichtsserver-Datenbank um eine Remotedatenbank handelt, wird ein Fehler zurückgegeben.  
  
 Wenn die `LocalService` integriertes Konto angegeben ist, und der Berichtsserver-Datenbank auf einem Remotecomputer befindet, wird ein Fehler zurückgegeben.  
  
 Wenn *IsWindowsUser* auf true festgelegt ist und der in *UserName* bereitgestellte Wert übersetzt werden muss, bestimmt der WMI-Anbieter, ob sich die Berichtsserver-Datenbank auf demselben Computer oder auf einem Remotecomputer befindet. Um zu bestimmen, ob es sich um eine lokale Installation handelt, wertet der WMI-Anbieter die DatabaseServerName-Eigenschaft anhand der folgenden Werteliste aus. Wenn eine Übereinstimmung gefunden wird, handelt es sich um eine lokale Datenbank. Andernfalls ist es eine Remotedatenbank. Beim Vergleich wird die Groß- und Kleinschreibung nicht berücksichtigt.  
  
|Wert von "DatabaseServerName"|Beispiel|  
|---------------------------------|-------------|  
|“.”||  
|"(local)"||  
|"LOCAL"||  
|localhost||  
|\<Computername>|testlab14|  
|\<ComputerFQDN>|example.redmond.microsoft.com|  
|\<IP-Adresse>|180.012.345,678|  
  
 Wenn *IsWindowsUser* nastaven NA hodnotu `true`, der WMI-Anbieter ruft LookupAccountName auf, um die SID für das Konto abzurufen und anschließend ruft er LookupAccountSID zum Abrufen des Namens für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Skript. Hierdurch wird sichergestellt, dass der verwendete Kontoname die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Überprüfung erfolgreich durchläuft.  
  
 Beim *IsWindowsUser* nastaven NA hodnotu `false`, wird das generierte Skript gewährt die **RSExec** -Rolle auf der Berichtsserver-Datenbank, die temporäre Berichtsserver-Datenbank und die MSDB-Datenbank.  
  
 Wenn *IsWindowsUser* nastaven NA hodnotu `false`, der SQL Server-Benutzer muss bereits vorhanden sein, auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für das Skript erfolgreich ausgeführt.  
  
 Wenn für den Berichtsserver keine Berichtsserver-Datenbank angegeben ist, wird bei einem Aufruf von GrantRightsToDatabaseUser ein Fehler zurückgegeben.  
  
 Das generierte Skript unterstützt [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
