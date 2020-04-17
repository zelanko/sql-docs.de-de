---
title: CLR-Integrationscodezugriffssicherheit | Microsoft Docs
description: Für die SQL Server CLR-Integration unterstützt CLR die Codezugriffssicherheit für verwalteten Code, bei der Berechtigungen für Assemblys basierend auf der Codeidentität erteilt werden.
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
ms.openlocfilehash: 912db3acb6f6dc21952e99da31a1484a9745ed0b
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488310"
---
# <a name="clr-integration-code-access-security"></a>CLR-Integration und Codezugriffssicherheit
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Common Language Runtime (CLR) unterstützt ein Sicherheitsmodell namens Codezugriffssicherheit für verwalteten Code. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. Weitere Informationen finden Sie im Abschnitt "Codezugriffsicherheit" im .NET Framework Software Development Kit.  
  
 Die Sicherheitsrichtlinie, die die Berechtigungen für Assemblys bestimmt, wird an drei verschiedenen Stellen definiert:  
  
-   Computerrichtlinie: Diese Richtlinie gilt für den gesamten verwalteten Code auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert ist.  
  
-   Benutzerrichtlinie: Diese Richtlinie ist für verwalteten Code gültig, der von einem Prozess gehostet wird. Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gilt die Benutzerrichtlinie für das Windows-Konto, unter dem der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienst ausgeführt wird.  
  
-   Hostrichtlinie: Diese Richtlinie wird vom Host der CLR (in diesem Fall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) eingerichtet, die für den verwalteten Code gültig ist, der auf diesem Host ausgeführt wird.  
  
 Der von der CLR unterstützte Codezugriffs-Sicherheitsmechanismus basiert auf der Annahme, dass die Laufzeit sowohl vollständig vertrauenswürdigen als auch teilweise vertrauenswürdigen Code hosten kann. Die durch die CLR-Codezugriffssicherheit geschützten Ressourcen sind üblicherweise von verwalteten Schnittstellen für die Anwendungsprogrammierung (Application Programming Interfaces oder API) umgeben, für die die entsprechenden Berechtigungen erforderlich sind, bevor der Zugriff auf die Ressource zugelassen wird. Die Anforderung der Berechtigung ist nur dann erfüllt, wenn alle aufrufenden Prozesse (auf Assemblyebene) in der Aufrufliste über die entsprechende Ressourcenberechtigung verfügen.  
  
 Die Menge der Codezugriffsberechtigungen, die verwaltetem Code gewährt werden, wenn dieser innerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, ist die Schnittmenge der Berechtigungen, die auf den drei oben genannten Richtlinienebenen erteilt werden. Auch wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einer in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] geladenen Assembly einen Berechtigungssatz gewährt, kann der schließlich für Benutzercode gewährte Berechtigungssatz durch die Richtlinien auf Computer- und Benutzerebenen weiter eingeschränkt sein.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Berechtigungssätze auf SQL Server Host-Richtlinienebene  
 Die Menge der Codezugriffsberechtigungen, die Assemblys von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Hostrichtlinienebene gewährt wird, wird von dem Berechtigungssatz bestimmt, der beim Erstellen der Assembly angegeben wurde. Es gibt drei Berechtigungssätze: **SAFE**, **EXTERNAL_ACCESS** und **UNSAFE** (mit der **PERMISSION_SET** Option von CREATE ASSEMBLY [&#40;Transact-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md)angegeben).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt für die gehostete CLR eine Sicherheitsrichtlinie auf Hostebene bereit; diese Richtlinie stellt eine zusätzliche Richtlinienebene unterhalb der zwei Richtlinienebenen dar, die immer gültig sind. Die Richtlinie wird für jede Anwendungsdomäne festgelegt, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]erstellt wird. Sie ist nicht für die Standardanwendungsdomäne bestimmt, die gültig ist, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Instanz der CLR erstellt.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Richtlinie auf Hostebene ist eine Kombination der festen Richtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für Systemassemblys und der benutzerdefinierten Richtlinie für Benutzerassemblys.  
  
 Die feste Richtlinie für CLR-Assemblys und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Systemassemblys verleiht ihnen volle Vertrauenswürdigkeit.  
  
 Der benutzerdefinierte Teil der Hostrichtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basiert darauf, dass der Assemblybesitzer einen von drei Berechtigungsbuckets für jede Assembly angibt. Weitere Informationen über die unten aufgeführten Sicherheitsberechtigungen finden Sie unter .NET Framework SDK.  
  
### <a name="safe"></a>SAFE  
 Nur interne Berechnungen und lokaler Datenzugriff sind zulässig. **SAFE** ist der restriktivste Berechtigungssatz. Code, der von einer Assembly mit **SAFE-Berechtigungen** ausgeführt wird, kann nicht auf externe Systemressourcen wie Dateien, das Netzwerk, Umgebungsvariablen oder die Registrierung zugreifen.  
  
 **SAFE-Assemblys** verfügen über die folgenden Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|**Securitypermission**|**Ausführung:** Berechtigung zum Ausführen von verwaltetem Code.|  
|**Sqlclientpermission**|**Context connection = true**, **context connection = yes**: Nur die context-connection kann verwendet werden und die Verbindungszeichenfolge kann nur einen Wert von "context connection=true" oder "context connection=yes" angeben.<br /><br /> **AllowBlankPassword = false:**  Leere Kennwörter sind nicht zulässig.|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS Assemblys haben **SAFE** dieselben Berechtigungen wie SAFE-Assemblys, mit der zusätzlichen Möglichkeit, auf externe Systemressourcen wie Dateien, Netzwerke, Umgebungsvariablen und die Registrierung zuzugreifen.  
  
 **EXTERNAL_ACCESS** Assemblys verfügen außerdem über die folgenden Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**Uneingeschränkt:** Verteilte Transaktionen sind zulässig.|  
|**Dnspermission**|**Uneingeschränkt:** Berechtigung zum Anfordern von Informationen von Domänennamenservern.|  
|**Environmentpermission**|**Uneingeschränkt:** Der vollständige Zugriff auf System- und Benutzerumgebungsvariablen ist zulässig.|  
|**EventLogPermission**|**Verwaltung:** Die folgenden Aktionen sind zulässig: Erstellen einer Ereignisquelle, Lesen vorhandener Protokolle, Löschen von Ereignisquellen oder -protokollen, Reagieren auf Einträge, Löschen eines Ereignisprotokolls, Abhören von Ereignissen und Zugriff auf eine Auflistung aller Ereignisprotokolle.|  
|**FileIOPermission**|**Uneingeschränkt:** Der volle Zugriff auf Dateien und Ordner ist zulässig.|  
|**Keycontainerpermission**|**Uneingeschränkt:** Der vollständige Zugriff auf Schlüsselcontainer ist zulässig.|  
|**NetworkInformationPermission**|**Zugang:** Pingen ist erlaubt.|  
|**Registrypermission**|Ermöglicht Leserechte für **HKEY_CLASSES_ROOT**, **HKEY_LOCAL_MACHINE**, **HKEY_CURRENT_USER**, **HKEY_CURRENT_CONFIG**und **HKEY_USERS.**|  
|**Securitypermission**|**Behauptung:** Die Möglichkeit zu behaupten, dass alle Aufrufer dieses Codes über die erforderliche Berechtigung für den Vorgang verfügen.<br /><br /> **ControlPrincipal:** Fähigkeit, das Hauptobjekt zu bearbeiten.<br /><br /> **Ausführung:** Berechtigung zum Ausführen von verwaltetem Code.<br /><br /> **SerialisierungS-Formatter:** Möglichkeit, Serialisierungsdienste bereitzustellen.|  
|**Smtppermission**|**Zugang:** Ausgehende Verbindungen mit SMTP-Hostport 25 sind zulässig.|  
|**Socketpermission**|**Verbinden:** Ausgehende Verbindungen (alle Ports, alle Protokolle) an einer Transportadresse sind zulässig.|  
|**Sqlclientpermission**|**Uneingeschränkt:** Der vollständige Zugriff auf die Datenquelle ist zulässig.|  
|**Storepermission**|**Uneingeschränkt:** Der volle Zugriff auf X.509-Zertifikatspeicher ist zulässig.|  
|**Webpermission**|**Verbinden:** Ausgehende Verbindungen zu Webressourcen sind zulässig.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE ermöglicht Assemblys uneingeschränkten Zugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Ressourcen, sowohl innerhalb als auch außerhalb . Code, der innerhalb einer **UNSAFE-Assembly** ausgeführt wird, kann auch nicht verwalteten Code aufrufen.  
  
 **UNSAFE-Assemblys** erhalten **FullTrust**.  
  
> [!IMPORTANT]  
>  **SAFE** ist die empfohlene Berechtigungseinstellung für Assemblys, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Berechnungs- und Datenverwaltungsaufgaben ausführen, ohne auf Ressourcen außerhalb zugreifen. **EXTERNAL_ACCESS** wird für Assemblys [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]empfohlen, die außerhalb von auf Ressourcen zugreifen. **EXTERNAL_ACCESS** Assemblys werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] standardmäßig als Dienstkonto ausgeführt. Es ist **möglich, dass EXTERNAL_ACCESS** Code explizit die Identität des Windows-Authentifizierungssicherheitskontexts des Aufrufers ausgibt. Da die Standardausführung standardmäßig [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Dienstkonto erfolgt, sollte die Berechtigung zum Ausführen **EXTERNAL_ACCESS** nur Für Anmeldungen erteilt werden, die als Dienstkonto ausgeführt werden sollen. Aus Sicherheitssicht sind **EXTERNAL_ACCESS-** und **UNSAFE-Assemblys** identisch. **EXTERNAL_ACCESS** Assemblys bieten jedoch verschiedene Zuverlässigkeits- und Robustheitsschutzvorrichtungen, die nicht in **UNSAFE-Assemblys** enthalten sind. Durch die Angabe von **UNSAFE** kann der Code [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Assembly illegale Vorgänge für den Prozessbereich ausführen und kann daher die Robustheit und Skalierbarkeit von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]beeinträchtigen. Weitere Informationen zum Erstellen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]CLR-Assemblys in finden Sie unter [Verwalten von CLR-Integrationsassemblys](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Zugreifen auf externe Ressourcen  
 Wenn ein benutzerdefinierter Typ (UDT), eine gespeicherte Prozedur oder **SAFE** ein anderer Bauaufbautyp mit dem SAFE-Berechtigungssatz registriert ist, kann verwalteter Code, der im Konstrukt ausgeführt wird, nicht auf externe Ressourcen zugreifen. Wenn jedoch entweder die **EXTERNAL_ACCESS-** oder **UNSAFE-Berechtigungssätze** angegeben werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und verwalteter Code versucht, auf externe Ressourcen zuzugreifen, gelten die folgenden Regeln:  
  
|Wenn|Then|  
|--------|----------|  
|Der Ausführungskontext entspricht einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldung.|Versuche, auf externe Ressourcen zuzugreifen, werden verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung, und der Ausführungskontext ist der ursprüngliche Aufrufer.|Der Zugriff auf die externe Ressource erfolgt im Sicherheitskontext des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienstkontos.|  
|Bei dem Aufrufer handelt es sich nicht um den ursprünglichen Aufrufer.|Der Zugriff wird verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung, und der Ausführungskontext ist der ursprüngliche Aufrufer, und der Aufrufer wurde imitiert.|Für den Zugriff wird anstelle des Dienstkontos der Sicherheitskontext des Aufrufers verwendet.|  
  
## <a name="permission-set-summary"></a>Zusammenfassung des Berechtigungssatzes  
 Das folgende Diagramm fasst die Einschränkungen und Berechtigungen zusammen, die den Berechtigungssätzen **SAFE**, **EXTERNAL_ACCESS**und **UNSAFE** gewährt wurden.  
  
|||||  
|-|-|-|-|  
||**SAFE**|**External_access**|**Unsichere**|  
|**Codezugriffssicherheitsberechtigungen**|Nur ausführen|Ausführen + Zugriff auf externe Ressourcen|Uneingeschränkt (einschließlich P/Invoke)|  
|**Beschränkungen des Programmiermodells**|Ja|Ja|Keine Beschränkungen|  
|**Überprüfbarkeit erforderlich**|Ja|Ja|Nein|  
|**Lokaler Datenzugriff**|Ja|Ja|Ja|  
|**Aufrufbarkeit von systemeigenem Code**|Nein|Nein |Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-Integrationssicherheit](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Host Protection-Attribute und CLR-Integrationsprogrammierung](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Einschränkungen des CLR-Integrationsprogrammierungsmodells](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Gehostete CLR-Umgebung](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
