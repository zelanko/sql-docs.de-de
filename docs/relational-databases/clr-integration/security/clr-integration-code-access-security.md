---
title: CLR-Integration Code Zugriffssicherheit | Microsoft-Dokumentation
description: Bei SQL Server CLR-Integration unterstützt CLR die Code Zugriffssicherheit für verwalteten Code, wobei Berechtigungen für Assemblys basierend auf der Code Identität gewährt werden.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
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
ms.openlocfilehash: 2f28692cd1a5c3f60e823d6071244ae822fc557a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759044"
---
# <a name="clr-integration-code-access-security"></a>CLR-Integration und Codezugriffssicherheit
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Der Common Language Runtime (CLR) unterstützt ein Sicherheitsmodell namens Code Zugriffssicherheit für verwalteten Code. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. Weitere Informationen finden Sie im Abschnitt "Codezugriffsicherheit" im .NET Framework Software Development Kit.  
  
 Die Sicherheitsrichtlinie, die die Berechtigungen für Assemblys bestimmt, wird an drei verschiedenen Stellen definiert:  
  
-   Computerrichtlinie: Diese Richtlinie gilt für den gesamten verwalteten Code auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert ist.  
  
-   Benutzerrichtlinie: Diese Richtlinie ist für verwalteten Code gültig, der von einem Prozess gehostet wird. Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gilt die Benutzerrichtlinie für das Windows-Konto, unter dem der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienst ausgeführt wird.  
  
-   Hostrichtlinie: Diese Richtlinie wird vom Host der CLR (in diesem Fall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) eingerichtet, die für den verwalteten Code gültig ist, der auf diesem Host ausgeführt wird.  
  
 Der von der CLR unterstützte Codezugriffs-Sicherheitsmechanismus basiert auf der Annahme, dass die Laufzeit sowohl vollständig vertrauenswürdigen als auch teilweise vertrauenswürdigen Code hosten kann. Die durch die CLR-Codezugriffssicherheit geschützten Ressourcen sind üblicherweise von verwalteten Schnittstellen für die Anwendungsprogrammierung (Application Programming Interfaces oder API) umgeben, für die die entsprechenden Berechtigungen erforderlich sind, bevor der Zugriff auf die Ressource zugelassen wird. Die Anforderung der Berechtigung ist nur dann erfüllt, wenn alle aufrufenden Prozesse (auf Assemblyebene) in der Aufrufliste über die entsprechende Ressourcenberechtigung verfügen.  
  
 Die Menge der Codezugriffsberechtigungen, die verwaltetem Code gewährt werden, wenn dieser innerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, ist die Schnittmenge der Berechtigungen, die auf den drei oben genannten Richtlinienebenen erteilt werden. Auch wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einer in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] geladenen Assembly einen Berechtigungssatz gewährt, kann der schließlich für Benutzercode gewährte Berechtigungssatz durch die Richtlinien auf Computer- und Benutzerebenen weiter eingeschränkt sein.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Berechtigungssätze auf SQL Server Host-Richtlinienebene  
 Die Menge der Codezugriffsberechtigungen, die Assemblys von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Hostrichtlinienebene gewährt wird, wird von dem Berechtigungssatz bestimmt, der beim Erstellen der Assembly angegeben wurde. Es gibt drei Berechtigungs Sätze: **Safe**, **EXTERNAL_ACCESS** und **unsicher** (angegeben mit der **PERMISSION_SET** -Option von [Create Assembly &#40;Transact-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt für die gehostete CLR eine Sicherheitsrichtlinie auf Hostebene bereit; diese Richtlinie stellt eine zusätzliche Richtlinienebene unterhalb der zwei Richtlinienebenen dar, die immer gültig sind. Die Richtlinie wird für jede Anwendungsdomäne festgelegt, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]erstellt wird. Sie ist nicht für die Standardanwendungsdomäne bestimmt, die gültig ist, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Instanz der CLR erstellt.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Richtlinie auf Hostebene ist eine Kombination der festen Richtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für Systemassemblys und der benutzerdefinierten Richtlinie für Benutzerassemblys.  
  
 Die feste Richtlinie für CLR-Assemblys und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Systemassemblys verleiht ihnen volle Vertrauenswürdigkeit.  
  
 Der benutzerdefinierte Teil der Hostrichtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basiert darauf, dass der Assemblybesitzer einen von drei Berechtigungsbuckets für jede Assembly angibt. Weitere Informationen über die unten aufgeführten Sicherheitsberechtigungen finden Sie unter .NET Framework SDK.  
  
### <a name="safe"></a>SAFE  
 Nur interne Berechnungen und lokaler Datenzugriff sind zulässig. **Safe** ist der restriktivste Berechtigungs Satz. Code, der von einer Assembly mit **sicheren** Berechtigungen ausgeführt wird, kann nicht auf externe Systemressourcen wie z. b. Dateien, das Netzwerk, Umgebungsvariablen oder die Registrierung zugreifen.  
  
 **Sichere** Assemblys verfügen über die folgenden Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|**SecurityPermission**|**Ausführung:** Berechtigung zum Ausführen von verwaltetem Code.|  
|**SqlClientPermission**|**Kontext Verbindung = true**, **Kontext Verbindung = ja**: nur die Kontext Verbindung kann verwendet werden, und in der Verbindungs Zeichenfolge kann nur der Wert "context connection = true" oder "context connection = yes" angegeben werden.<br /><br /> **AllowBlankPassword = false:**  Leere Kenn Wörter sind nicht zulässig.|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS Assemblys verfügen über die gleichen Berechtigungen wie **sichere** Assemblys, mit der zusätzlichen Fähigkeit, auf externe Systemressourcen wie z. b. Dateien, Netzwerke, Umgebungsvariablen und die Registrierung zuzugreifen.  
  
 **EXTERNAL_ACCESS** Assemblys verfügen auch über die folgenden Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**Uneingeschränkt:** Verteilte Transaktionen sind zulässig.|  
|**DnsPermission**|**Uneingeschränkt:** Berechtigung zum Anfordern von Informationen von Domänen Namen Servern.|  
|**Umgebungs Berechtigung**|**Uneingeschränkt:** Vollzugriff auf System-und Benutzer Umgebungsvariablen ist zulässig.|  
|**EventLogPermission**|**Verwalten:** Folgende Aktionen sind zulässig: Erstellen einer Ereignis Quelle, lesen vorhandener Protokolle, Löschen von Ereignis Quellen oder Protokollen, reagieren auf Einträge, Löschen eines Ereignis Protokolls, lauschen auf Ereignisse und Zugreifen auf eine Auflistung aller Ereignisprotokolle.|  
|**FileIOPermission**|**Uneingeschränkt:** Der vollständige Zugriff auf Dateien und Ordner ist zulässig.|  
|**Keycontainerberechtigung**|**Uneingeschränkt:** Vollzugriff auf Schlüssel Container ist zulässig.|  
|**NetworkInformationPermission**|**Zugriff:** Pingen ist zulässig.|  
|**RegistryPermission**|Ermöglicht das Lesen von Rechten für **HKEY_CLASSES_ROOT**, **HKEY_LOCAL_MACHINE**, **HKEY_CURRENT_USER**, **HKEY_CURRENT_CONFIG**und **HKEY_USERS.**|  
|**SecurityPermission**|Assert **:** Die Möglichkeit, zu bestätigen, dass alle Aufrufer dieses Codes über die erforderliche Berechtigung für den Vorgang verfügen.<br /><br /> **ControlPrincipal:** Die Fähigkeit zum Bearbeiten des Prinzipal Objekts.<br /><br /> **Ausführung:** Berechtigung zum Ausführen von verwaltetem Code.<br /><br /> **SerializationFormatter:** Die Möglichkeit, Serialisierungsdienste bereitzustellen.|  
|**Smtpberechtigung**|**Zugriff:** Ausgehende Verbindungen mit dem SMTP-hostport 25 sind zulässig.|  
|**SocketPermission**|**Verbinden:** Ausgehende Verbindungen (alle Ports, alle Protokolle) für eine Transport Adresse sind zulässig.|  
|**SqlClientPermission**|**Uneingeschränkt:** Der vollständige Zugriff auf die Datenquelle ist zulässig.|  
|**Storeberechtigung**|**Uneingeschränkt:** Vollzugriff auf X. 509-Zertifikat Speicher ist zulässig.|  
|**WebPermission**|**Verbinden:** Ausgehende Verbindungen mit Webressourcen sind zulässig.|  
  
### <a name="unsafe"></a>UNSAFE  
 Unsicher ermöglicht Assemblys den uneingeschränkten Zugriff auf Ressourcen innerhalb und außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Code, der aus einer **unsicheren** Assembly heraus ausgeführt wird, kann auch nicht verwalteten Code aufgerufen werden.  
  
 **Unsichere** Assemblys erhalten **FullTrust**.  
  
> [!IMPORTANT]  
>  **Safe** ist die empfohlene Berechtigungseinstellung für Assemblys, die Berechnungs-und Daten Verwaltungs Tasks ausführen, ohne auf Ressourcen außerhalb von zuzugreifen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . **EXTERNAL_ACCESS** wird für Assemblys empfohlen, die auf Ressourcen außerhalb von zugreifen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . **EXTERNAL_ACCESS** Assemblys werden standardmäßig als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienst Konto ausgeführt. **EXTERNAL_ACCESS** Code kann die Identität des Sicherheits Kontexts der Windows-Authentifizierung des Aufrufers explizit annehmen. Da standardmäßig als Dienst Konto ausgeführt wird [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , sollte die Berechtigung zum Ausführen von **EXTERNAL_ACCESS** nur Anmeldungen erteilt werden, die vertrauenswürdig sind, als Dienst Konto ausgeführt zu werden. Aus Sicht der Sicherheit sind **EXTERNAL_ACCESS** und **unsichere** Assemblys identisch. Allerdings bieten **EXTERNAL_ACCESS** Assemblys verschiedene Zuverlässigkeits-und Stabilitäts Schutzmaßnahmen, die sich nicht in **unsicheren** Assemblys befinden Durch die Angabe von **unsicher** kann der Code in der Assembly unzulässige Vorgänge für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Prozessbereich durchführen und somit die Stabilität und Skalierbarkeit von beeinträchtigen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Weitere Informationen zum Erstellen von CLR-Assemblys in finden Sie unter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Managing CLR Integration](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)Assemblys.  
  
## <a name="accessing-external-resources"></a>Zugreifen auf externe Ressourcen  
 Wenn ein benutzerdefinierter Typ (User-Defined Type, UDT), eine gespeicherte Prozedur oder eine andere Art von konstruktionsassembly mit dem **Safe** -Berechtigungs Satz registriert ist, kann verwalteter Code, der im Konstrukt ausgeführt wird, nicht auf externe Ressourcen zugreifen. Wenn jedoch entweder der **EXTERNAL_ACCESS** oder **unsichere** Berechtigungs Sätze angegeben werden und verwalteter Code versucht, auf externe Ressourcen zuzugreifen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wendet die folgenden Regeln an:  
  
|Wenn|Then|  
|--------|----------|  
|Der Ausführungskontext entspricht einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldung.|Versuche, auf externe Ressourcen zuzugreifen, werden verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung, und der Ausführungskontext ist der ursprüngliche Aufrufer.|Der Zugriff auf die externe Ressource erfolgt im Sicherheitskontext des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienstkontos.|  
|Bei dem Aufrufer handelt es sich nicht um den ursprünglichen Aufrufer.|Der Zugriff wird verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungs Kontext entspricht einer Windows-Anmeldung, und der Ausführungs Kontext ist der ursprüngliche Aufrufer, und für den Aufrufer wurde ein Identitätswechsel durchgeführt.|Für den Zugriff wird anstelle des Dienstkontos der Sicherheitskontext des Aufrufers verwendet.|  
  
## <a name="permission-set-summary"></a>Zusammenfassung des Berechtigungssatzes  
 Im folgenden Diagramm werden die Einschränkungen und Berechtigungen zusammengefasst, die den Berechtigungs Sätzen **Safe**, **EXTERNAL_ACCESS**und **unsichere** erteilt wurden.  
  
|||||  
|-|-|-|-|  
||**SAFE**|**EXTERNAL_ACCESS**|**Unsicher**|  
|**Berechtigungen für die Code Zugriffssicherheit**|Nur ausführen|Ausführen + Zugriff auf externe Ressourcen|Uneingeschränkt (einschließlich P/Invoke)|  
|**Beschränkungen des Programmiermodells**|Ja|Ja|Keine Einschränkungen|  
|**Überprüfbarkeit erforderlich**|Ja|Ja|Nein|  
|**Lokaler Datenzugriff**|Ja|Ja|Ja|  
|**Aufrufbarkeit von systemeigenem Code**|Nein|Nein |Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit der CLR-Integration](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Host Schutz Attribute und Programmierung der CLR-Integration](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Einschränkungen für das Programmiermodell von CLR-Integration](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Gehostete CLR-Umgebung](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
