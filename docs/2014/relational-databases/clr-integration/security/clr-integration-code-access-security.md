---
title: CLR-Integration Code Zugriffssicherheit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
author: rothja
ms.author: jroth
ms.openlocfilehash: 75b283da2760b39349351802a83caae04e546c06
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953446"
---
# <a name="clr-integration-code-access-security"></a>CLR-Integration und Codezugriffssicherheit
  Der Common Language Runtime (CLR) unterstützt ein Sicherheitsmodell namens Code Zugriffssicherheit für verwalteten Code. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. Weitere Informationen finden Sie im Abschnitt "Codezugriffsicherheit" im .NET Framework Software Development Kit.  
  
 Die Sicherheitsrichtlinie, die die Berechtigungen für Assemblys bestimmt, wird an drei verschiedenen Stellen definiert:  
  
-   Computerrichtlinie: Diese Richtlinie gilt für den gesamten verwalteten Code auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert ist.  
  
-   Benutzerrichtlinie: Diese Richtlinie ist für verwalteten Code gültig, der von einem Prozess gehostet wird. , Wenn der- [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienst ausgeführt wird.  
  
-   Hostrichtlinie: Diese Richtlinie wird vom Host der CLR (in diesem Fall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) eingerichtet, die für den verwalteten Code gültig ist, der auf diesem Host ausgeführt wird.  
  
 Der von der CLR unterstützte Codezugriffs-Sicherheitsmechanismus basiert auf der Annahme, dass die Laufzeit sowohl vollständig vertrauenswürdigen als auch teilweise vertrauenswürdigen Code hosten kann. Die durch die CLR-Code Zugriffssicherheit geschützten Ressourcen werden in der Regel von verwalteten Anwendungs Programmierschnittstellen umschließt, die die entsprechende Berechtigung vorausgehen, bevor Sie den Zugriff auf die Ressource gewähren. Die demandfor-Berechtigung wird nur dann erfüllt, wenn alle Aufrufer (auf Assemblyebene) in der Aufruf Listen über die entsprechende Ressourcen Berechtigung verfügen.  
  
 Durch den Satz von Code Zugriffs Sicherheits Berechtigungen, die verwalteten Code bei der Ausführung von gewährt werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , wird ein Berechtigungs Satz für eine Assembly erteilt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die in geladen wird. der endgültige Satz von Berechtigungen, der für Benutzercode erteilt wurde, kann durch die Richtlinien auf Benutzer-und Computer Ebene weiter eingeschränkt werden.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Berechtigungssätze auf SQL Server Host-Richtlinienebene  
 Die Menge der Codezugriffsberechtigungen, die Assemblys von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Hostrichtlinienebene gewährt wird, wird von dem Berechtigungssatz bestimmt, der beim Erstellen der Assembly angegeben wurde. Es gibt drei Berechtigungs Sätze: `SAFE` , `EXTERNAL_ACCESS` und `UNSAFE` (angegeben mit der **PERMISSION_SET** -Option von[Create Assembly &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Sie ist nicht für die Standardanwendungsdomäne bestimmt, die gültig ist, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Instanz der CLR erstellt.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fixedpolicy für Systemassemblys und die benutzerdefinierte Richtlinie für Benutzerassemblys.  
  
 Die feste Richtlinie für CLR-Assemblys und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Systemassemblys verleiht ihnen volle Vertrauenswürdigkeit.  
  
 Der benutzerdefinierte Teil der Hostrichtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basiert darauf, dass der Assemblybesitzer einen von drei Berechtigungsbuckets für jede Assembly angibt. Weitere Informationen über die unten aufgeführten Sicherheitsberechtigungen finden Sie unter .NET Framework SDK.  
  
### <a name="safe"></a>SAFE  
 Nur interne Berechnungen und lokaler Datenzugriff sind zulässig. `SAFE` ist der restriktivste Berechtigungssatz. Code, der von einer Assembly mit `SAFE`-Berechtigungen ausgeführt wird, hat keinen Zugriff auf externe Systemressourcen wie Dateien, das Netzwerk, Umgebungsvariablen oder die Registrierung.  
  
 `SAFE`-Assemblys verfügen über folgende Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|`SecurityPermission`|`Execution:` Berechtigung zur Ausführung von verwaltetem Code.|  
|`SqlClientPermission`|`Context connection = true`, `context connection = yes`: Es kann nur die Kontextverbindung verwendet werden, und die Verbindungszeichenfolge kann nur den Wert "context connection=true" oder "context connection=yes" angeben.<br /><br /> **AllowBlankPassword = false:**  Leere Kenn Wörter sind nicht zulässig.|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS Assemblys verfügen über dieselben Berechtigungen wie Assemblys `SAFE` , mit der zusätzlichen Fähigkeit, auf externe Systemressourcen wie z. b. Dateien, Netzwerke, Umgebungsvariablen und die Registrierung zuzugreifen.  
  
 `EXTERNAL_ACCESS`-Assemblys verfügen außerdem über folgende Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|`DistributedTransactionPermission`|`Unrestricted:`Verteilte Transaktionen sind zulässig.|  
|`DNSPermission`|`Unrestricted:`Berechtigung zum Anfordern von Informationen von Domänen Namen Servern.|  
|`EnvironmentPermission`|`Unrestricted:` Der vollständige Zugriff auf System- und Benutzerumgebungsvariablen ist zulässig.|  
|`EventLogPermission`|`Administer:` Folgende Aktionen sind zulässig: Erstellen einer Ereignisquelle, Lesen vorhandener Protokolle, Löschen von Ereignisquellen oder -protokollen, Reagieren auf Einträge, Löschen eines Ereignisprotokolls, Überwachen von Ereignissen und Zugreifen auf eine Auflistung sämtlicher Ereignisprotokolle.|  
|`FileIOPermission`|`Unrestricted:` Der vollständige Zugriff auf Dateien und Ordner ist zulässig.|  
|`KeyContainerPermission`|`Unrestricted:` Der vollständige Zugriff auf Schlüsselcontainer ist zulässig.|  
|`NetworkInformationPermission`|`Access:` Die Pingausführung ist zulässig.|  
|`RegistryPermission`|Lässt Leseberechtigungen für `HKEY_CLASSES_ROOT`, `HKEY_LOCAL_MACHINE`, `HKEY_CURRENT_USER`, `HKEY_CURRENT_CONFIG` und `HKEY_USERS.` zu.|  
|`SecurityPermission`|`Assertion:` Die Fähigkeit zu bestätigen, dass alle Aufrufer dieses Codes über die erforderliche Berechtigung für den Vorgang verfügen.<br /><br /> `ControlPrincipal:` Die Fähigkeit zum Verändern des Hauptobjekts.<br /><br /> `Execution:` Berechtigung zur Ausführung von verwaltetem Code.<br /><br /> `SerializationFormatter:` Die Fähigkeit zum Bereitstellen von Serialisierungsdiensten.|  
|**Smtpberechtigung**|`Access:` Ausgehende Verbindungen an den Anschluss 25 des SMTP-Hosts werden zugelassen.|  
|`SocketPermission`|`Connect:` Ausgehende Verbindungen (alle Ports, alle Protokolle) auf einer Transportadresse werden zugelassen.|  
|`SqlClientPermission`|`Unrestricted:`Der vollständige Zugriff auf die Datenquelle ist zulässig.|  
|`StorePermission`|`Unrestricted:` Der vollständige Zugriff auf X.509-Zertifikatspeicher ist zulässig.|  
|`WebPermission`|`Connect:` Ausgehende Verbindungen an Webressourcen werden zugelassen.|  
  
### <a name="unsafe"></a>UNSAFE  
 Unsicher ermöglicht Assemblys den uneingeschränkten Zugriff auf Ressourcen innerhalb und außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Code, der innerhalb einer `UNSAFE`-Assembly ausgeführt wird, kann außerdem nicht verwalteten Code aufrufen.  
  
 `UNSAFE`-Assemblys erhalten `FullTrust`.  
  
> [!IMPORTANT]  
>  `SAFE` ist die empfohlene Berechtigungseinstellung für Assemblys, die Berechnungs- und Datenverwaltungstasks ausführen, ohne auf Ressourcen außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen. `EXTERNAL_ACCESS`Assemblys werden standardmäßig als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienst Konto ausgeführt, und die Ausführungs Berechtigung `EXTERNAL_ACCESS` sollte nur für Anmeldungen erteilt werden, die als Dienst Konto vertrauenswürdig eingestuft werden. Aus Sicht der Sicherheit sind die `EXTERNAL_ACCESS`-Assembly und die `UNSAFE`-Assembly identisch. `EXTERNAL_ACCESS`-Assemblys bieten gegenüber `UNSAFE`-Assemblys jedoch ein Mehr an Zuverlässigkeit und Stabilität. `UNSAFE`Durch die Angabe von kann der Code in der Assembly ungültige Vorgänge für die ausführen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Weitere Informationen zum Erstellen von CLR-Assemblys in finden Sie unter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Managing CLR Integration](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)Assemblys.  
  
## <a name="accessing-external-resources"></a>Zugreifen auf externe Ressourcen  
 Wenn ein benutzerdefinierter Typ (UDT), eine gespeicherte Prozedur oder eine andere Konstruktassembly mit dem `SAFE`-Berechtigungssatz registriert wird, kann der verwaltete Code, der in dem Konstrukt ausgeführt wird, nicht auf externe Ressourcen zugreifen. Wenn jedoch entweder der `EXTERNAL_ACCESS`-Berechtigungssatz oder der `UNSAFE`-Berechtigungssatz angegeben wird und der verwaltete Code versucht, auf externe Ressourcen zuzugreifen, wendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] folgende Regeln an:  
  
|Wenn|Then|  
|--------|----------|  
|Der Ausführungskontext entspricht einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldung.|Versuche, auf externe Ressourcen zuzugreifen, werden verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung, und der Ausführungskontext ist der ursprüngliche Aufrufer.|Der Zugriff auf die externe Ressource erfolgt im Sicherheitskontext des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienstkontos.|  
|Bei dem Aufrufer handelt es sich nicht um den ursprünglichen Aufrufer.|Der Zugriff wird verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungs Kontext entspricht einer Windows-Anmeldung, und der Ausführungs Kontext ist der ursprüngliche Aufrufer, und für den Aufrufer wurde ein Identitätswechsel durchgeführt.|Für den Zugriff wird anstelle des Dienstkontos der Sicherheitskontext des Aufrufers verwendet.|  
  
## <a name="permission-set-summary"></a>Zusammenfassung des Berechtigungssatzes  
 Das folgende Diagramm fasst die Einschränkungen und Berechtigungen zusammen, die den Berechtigungssätzen `SAFE`, `EXTERNAL_ACCESS` und `UNSAFE` erteilt werden.  
  
|||||  
|-|-|-|-|  
||`SAFE`|`EXTERNAL_ACCESS`|`UNSAFE`|  
|`Code Access Security Permissions`|Nur ausführen|Ausführen + Zugriff auf externe Ressourcen|Uneingeschränkt (einschließlich P/Invoke)|  
|`Programming model restrictions`|Ja|Ja|Keine Einschränkungen|  
|`Verifiability requirement`|Ja|Ja|Nein|  
|`Local data access`|Ja|Ja|Ja|  
|`Ability to call native code`|Nein|Nein |Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit der CLR-Integration](clr-integration-security.md)   
 [Host Schutz Attribute und Programmierung der CLR-Integration](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Einschränkungen für das Programmiermodell von CLR-Integration](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Gehostete CLR-Umgebung](../clr-integration-architecture-clr-hosted-environment.md)  
  
  
