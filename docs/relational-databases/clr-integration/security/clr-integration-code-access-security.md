---
title: Codezugriffssicherheit für CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
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
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 87b58d73233cf586ec631e43ad17cb9232d59f8f
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37357662"
---
# <a name="clr-integration-code-access-security"></a>CLR-Integration und Codezugriffssicherheit
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die common Language Runtime (CLR) unterstützt ein Sicherheitsmodell namens Codezugriffssicherheit für verwalteten Code. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. Weitere Informationen finden Sie im Abschnitt "Codezugriffsicherheit" im .NET Framework Software Development Kit.  
  
 Die Sicherheitsrichtlinie, die die Berechtigungen für Assemblys bestimmt, wird an drei verschiedenen Stellen definiert:  
  
-   Computerrichtlinie: Diese Richtlinie gilt für den gesamten verwalteten Code auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert ist.  
  
-   Benutzerrichtlinie: Diese Richtlinie ist für verwalteten Code gültig, der von einem Prozess gehostet wird. Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gilt die Benutzerrichtlinie für das Windows-Konto, unter dem der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienst ausgeführt wird.  
  
-   Hostrichtlinie: Diese Richtlinie wird vom Host der CLR (in diesem Fall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) eingerichtet, die für den verwalteten Code gültig ist, der auf diesem Host ausgeführt wird.  
  
 Der von der CLR unterstützte Codezugriffs-Sicherheitsmechanismus basiert auf der Annahme, dass die Laufzeit sowohl vollständig vertrauenswürdigen als auch teilweise vertrauenswürdigen Code hosten kann. Die durch die CLR-Codezugriffssicherheit geschützten Ressourcen sind in der Regel von verwalteten Anwendungsprogrammierschnittstellen umschlossen, die die entsprechende Berechtigung vor dem Zugriff auf die Ressource erforderlich ist. Die Anforderung der Berechtigung ist nur dann erfüllt, wenn alle aufrufenden Prozesse (auf Assemblyebene) in der Aufrufliste über die entsprechende Ressourcenberechtigung verfügen.  
  
 Die Menge der Codezugriffsberechtigungen, die verwaltetem Code gewährt werden, wenn dieser innerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, ist die Schnittmenge der Berechtigungen, die auf den drei oben genannten Richtlinienebenen erteilt werden. Auch wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einer in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] geladenen Assembly einen Berechtigungssatz gewährt, kann der schließlich für Benutzercode gewährte Berechtigungssatz durch die Richtlinien auf Computer- und Benutzerebenen weiter eingeschränkt sein.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Berechtigungssätze auf SQL Server Host-Richtlinienebene  
 Die Menge der Codezugriffsberechtigungen, die Assemblys von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Hostrichtlinienebene gewährt wird, wird von dem Berechtigungssatz bestimmt, der beim Erstellen der Assembly angegeben wurde. Es gibt drei Berechtigungssätze: **sicher**, **EXTERNAL_ACCESS** und **UNSAFE** (angegeben mit der **PERMISSION_SET** Option [ Erstellen der ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt für die gehostete CLR eine Sicherheitsrichtlinie auf Hostebene bereit; diese Richtlinie stellt eine zusätzliche Richtlinienebene unterhalb der zwei Richtlinienebenen dar, die immer gültig sind. Die Richtlinie wird für jede Anwendungsdomäne festgelegt, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]erstellt wird. Sie ist nicht für die Standardanwendungsdomäne bestimmt, die gültig ist, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Instanz der CLR erstellt.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Richtlinie auf Hostebene ist eine Kombination der festen Richtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für Systemassemblys und der benutzerdefinierten Richtlinie für Benutzerassemblys.  
  
 Die feste Richtlinie für CLR-Assemblys und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Systemassemblys verleiht ihnen volle Vertrauenswürdigkeit.  
  
 Der benutzerdefinierte Teil der Hostrichtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basiert darauf, dass der Assemblybesitzer einen von drei Berechtigungsbuckets für jede Assembly angibt. Weitere Informationen über die unten aufgeführten Sicherheitsberechtigungen finden Sie unter .NET Framework SDK.  
  
### <a name="safe"></a>SAFE  
 Nur interne Berechnungen und lokaler Datenzugriff sind zulässig. **Sichere** ist der restriktivste Berechtigungssatz. Code, der ausgeführt wird, indem Sie eine Assembly mit **sicher** Berechtigungen können nicht auf externe Systemressourcen wie Dateien, das Netzwerk, Umgebungsvariablen oder die Registrierung zugreifen.  
  
 **Sichere** Assemblys verfügen über folgende Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|**SecurityPermission**|**Ausführung:** Berechtigung zum Ausführen von verwalteten Codes.|  
|**SqlClientPermission**|**Kontextverbindung = True**, **kontextverbindung = Yes**: nur die kontextverbindung verwendet werden kann und die Verbindungszeichenfolge nur Sie den Wert geben kann "kontextverbindung = True" oder "kontextverbindung = Yes".<br /><br /> **AllowBlankPassword = False:** leere Kennwörter sind nicht zulässig.|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS-Assemblys über die gleichen Berechtigungen wie **sicher** Assemblys, mit der zusätzlichen Fähigkeit, auf externe Systemressourcen wie Dateien, Netzwerke, Webdienste, Umgebungsvariablen und die Registrierung zugreifen.  
  
 **EXTERNAL_ACCESS** Assemblys verfügen außerdem über folgende Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**Unrestricted:** verteilte Transaktionen sind zulässig.|  
|**DNSPermission**|**Unrestricted:** über die Berechtigung zum Anfordern von Informationen von DNS-Servern.|  
|**EnvironmentPermission**|**Unrestricted:** vollständigen Zugriff auf System- und Benutzerumgebungsvariablen ist zulässig.|  
|**EventLogPermission**|**Verwalten:** die folgenden Aktionen sind zulässig: Erstellen einer Ereignisquelle, lesen vorhandener Protokolle, Löschen von Ereignisquellen oder-Protokolle, reagieren auf Einträge, Löschen eines Ereignisprotokolls, Überwachen von Ereignissen und Zugreifen auf eine Auflistung sämtlicher Ereignisprotokolle.|  
|**FileIOPermission**|**Unrestricted:** vollen Zugriff auf Dateien und Ordner zulässig ist.|  
|**KeyContainerPermission**|**Unrestricted:** vollständigen Zugriff auf Schlüsselcontainer ist zulässig.|  
|**NetworkInformationPermission**|**Zugriff:** Ping ist zulässig.|  
|**RegistryPermission**|Lässt Leseberechtigungen für **HKEY_CLASSES_ROOT**, **HKEY_LOCAL_MACHINE**, **HKEY_CURRENT_USER**, **HKEY_CURRENT_CONFIG**, und  **HKEY_USERS.**|  
|**SecurityPermission**|**-Assertion:** Fähigkeit zu bestätigen, dass alle Aufrufer dieses Codes über die erforderliche Berechtigung für den Vorgang verfügen.<br /><br /> **ControlPrincipal:** können Sie das principal-Objekt zu ändern.<br /><br /> **Ausführung:** Berechtigung zum Ausführen von verwalteten Codes.<br /><br /> **SerializationFormatter:** Möglichkeit zum Bereitstellen von Serialisierungsdiensten.|  
|**SmtpPermission**|**Zugriff:** ausgehende Verbindungen mit dem SMTP-Host-Port 25 zugelassen werden.|  
|**SocketPermission**|**Eine Verbindung herstellen:** ausgehende Verbindungen (alle Ports, alle Protokolle) auf einer Transportadresse werden zugelassen.|  
|**SqlClientPermission**|**Unrestricted:** vollständigen Zugriff auf die Datenquelle ist zulässig.|  
|**StorePermission**|**Unrestricted:** vollen Zugriff auf x. 509-Zertifikat wird der Speicher ist zulässig.|  
|**WebPermission**|**Eine Verbindung herstellen:** ausgehende Verbindungen an Webressourcen werden zugelassen.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE ermöglicht Assemblys den uneingeschränkten Zugriff auf Ressourcen innerhalb und außerhalb [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Code ausführen, die innerhalb einer **UNSAFE** Assembly kann auch nicht verwalteten Code aufrufen.  
  
 **Unsichere** Assemblys erhalten **FullTrust**.  
  
> [!IMPORTANT]  
>  **Sichere** ist die empfohlene berechtigungseinstellung für Assemblys, die berechnungs- und Verwaltungsaufgaben ausführen, ohne den Zugriff auf Ressourcen außerhalb [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **EXTERNAL_ACCESS** wird empfohlen, Assemblys, die Zugriff auf Ressourcen außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **EXTERNAL_ACCESS** Assemblys werden standardmäßig ausgeführt, als die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkonto. Es ist möglich, dass **EXTERNAL_ACCESS** Code für die Authentifizierung von Windows-Sicherheitskontext des Aufrufers explizit annehmen. Aufgrund der standardmäßigen Ausführung als die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienstkonto und die Berechtigung zum Ausführen von **EXTERNAL_ACCESS** sollten nur vertrauenswürdigen Logins, führen Sie als Dienstkonto erteilt werden. Aus Gründen der Sicherheit **EXTERNAL_ACCESS** und **UNSAFE** Assemblys identisch sind. Allerdings **EXTERNAL_ACCESS** Assemblys bieten Zuverlässigkeit und Stabilität, die nicht in **UNSAFE** Assemblys. Angeben von **UNSAFE** kann der Code in der Assembly unzulässige Operationen gegen Ausführen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Prozessbereich und potenzielle Gefährdung der Stabilität und Skalierbarkeit von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Weitere Informationen zum Erstellen von CLR-Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], finden Sie unter [Verwalten von CLR-Integrationsassemblys](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Zugreifen auf externe Ressourcen  
 Wenn Sie einen benutzerdefinierten Typ (UDT), gespeicherte Prozedur oder andere Art von Konstruktassembly mit registriert ist die **sicher** Berechtigungssatz, dann ist verwalteter Code ausgeführt wird, im Konstrukt kann nicht auf externe Ressourcen zuzugreifen. Aber wenn entweder die **EXTERNAL_ACCESS** oder **UNSAFE** Berechtigungen angegeben werden, und verwalteter Code versucht, den Zugriff auf externe Ressourcen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die folgenden Regeln angewendet:  
  
|Wenn|Then|  
|--------|----------|  
|Der Ausführungskontext entspricht einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldung.|Versuche, auf externe Ressourcen zuzugreifen, werden verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung, und der Ausführungskontext ist der ursprüngliche Aufrufer.|Der Zugriff auf die externe Ressource erfolgt im Sicherheitskontext des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienstkontos.|  
|Bei dem Aufrufer handelt es sich nicht um den ursprünglichen Aufrufer.|Der Zugriff wird verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung und der Ausführungskontext ist der ursprüngliche Aufrufer und der Aufrufer verfügt über dessen Identität angenommen wurde.|Für den Zugriff wird anstelle des Dienstkontos der Sicherheitskontext des Aufrufers verwendet.|  
  
## <a name="permission-set-summary"></a>Zusammenfassung des Berechtigungssatzes  
 Das folgende Diagramm fasst die Einschränkungen und Berechtigungen für die **sicher**, **EXTERNAL_ACCESS**, und **UNSAFE** Berechtigungssätze.  
  
|||||  
|-|-|-|-|  
||**SAFE**|**EXTERNAL_ACCESS**|**UNSICHERE**|  
|**Berechtigungen für die Codezugriffssicherheit**|Nur ausführen|Ausführen + Zugriff auf externe Ressourcen|Uneingeschränkt (einschließlich P/Invoke)|  
|**Einschränkungen des Programmiermodells**|ja|ja|Keine Einschränkungen|  
|**Überprüfbarkeit erforderlich**|ja|ja|nein|  
|**Zugriffe auf lokale Daten**|ja|ja|ja|  
|**Möglichkeit zum Aufrufen von nativem code**|nein|nein|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Hostschutzattribute und Programmierung der CLR-Integration](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR-Integration Einschränkungen des Programmiermodells](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Gehostete CLR-Umgebung](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
