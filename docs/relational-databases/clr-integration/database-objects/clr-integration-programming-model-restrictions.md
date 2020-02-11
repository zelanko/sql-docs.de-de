---
title: Einschränkungen für das CLR-Integrations Programmiermodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: c019b50f896109a699869d748d8eef20b57d6edb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70212365"
---
# <a name="clr-integration-programming-model-restrictions"></a>Beschränkungen des Programmiermodells für die CLR-Integration
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Wenn Sie eine verwaltete gespeicherte Prozedur oder ein anderes verwaltetes Datenbankobjekt entwickeln, werden bestimmte Code Überprüfungen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] durchgeführt, die berücksichtigt werden müssen. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]führt Überprüfungen der verwalteten Codeassembly aus, wenn Sie zum ersten Mal in der Datenbank registriert wird, mithilfe der **Create Assembly** -Anweisung und auch zur Laufzeit. Der verwaltete Code wird außerdem zur Laufzeit überprüft, da in einer Assembly Codepfade vorhanden sein können, die zur Laufzeit eigentlich nicht erreicht werden.  Dadurch wird Flexibilität für die Registrierung von Assemblys von Drittanbietern geschaffen, sodass eine Assembly nicht blockiert wird, wenn ein "Unsafe"-Code vorliegt, der in einer Clientumgebung ausgeführt werden soll, jedoch nie in der gehosteten CLR ausgeführt wird. Die Anforderungen, die der verwaltete Code erfüllen muss, hängen davon ab, ob die Assembly als **sicher**, **EXTERNAL_ACCESS**oder **unsicher**, **sicher, sicher** und im folgenden aufgeführt ist.  
  
 Neben den Einschränkungen, die für verwaltete Codeassemblys gelten, werden außerdem Sicherheitsberechtigungen für Code erteilt. Die CLR (Common Language Runtime) unterstützt ein Sicherheitsmodell, das als Codezugriffssicherheit für verwalteten Code bezeichnet wird. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. **Sichere**, **EXTERNAL_ACCESS**und **unsichere** Assemblys verfügen über unterschiedliche CAS-Berechtigungen. Weitere Informationen finden Sie unter [CLR-Integration Code Zugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY-Überprüfungen  
 Wenn die **Create Assembly** -Anweisung ausgeführt wird, werden die folgenden Überprüfungen für jede Sicherheitsstufe ausgeführt.  Wenn eine Überprüfung fehlschlägt, schlägt **Create Assembly** mit einer Fehlermeldung fehl.  
  
### <a name="global-any-security-level"></a>Global (eine beliebige Sicherheitsebene)  
 Alle Assemblys, auf die verwiesen wird, müssen ein oder mehrere der folgenden Kriterien erfüllen:  
  
-   Die Assembly ist bereits in der Datenbank registriert.  
  
-   Die Assembly ist eine der unterstützten Assemblys. Weitere Informationen finden Sie [unter Supported .NET Framework Libraries](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Sie verwenden **Create Assembly from**_\<Location>,_ und alle referenzierten Assemblys und ihre Abhängigkeiten sind an * \<Location>* verfügbar.  
  
-   Sie verwenden **Create Assembly from**_\<bytes... >,_ und alle Verweise werden mit durch Leerzeichen getrennten Bytes angegeben.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Alle **EXTERNAL_ACCESS** -Assemblys müssen die folgenden Kriterien erfüllen:  
  
-   Statische Felder werden nicht verwendet, um Informationen zu speichern. Schreibgeschützte statische Felder sind zulässig.  
  
-   Der PEVerify-Test wird bestanden. Das PEVerify-Tool (peverify.exe), das überprüft, ob der MSIL-Code und die zugeordneten Metadaten den Anforderungen an die Typsicherheit entsprechen, wird mit .NET Framework SDK zur Verfügung gestellt.  
  
-   Synchronisierungen, z. b. mit der **SynchronizationAttribute** -Klasse, werden nicht verwendet.  
  
-   Finalizer-Methoden werden nicht verwendet.  
  
 Die folgenden benutzerdefinierten Attribute sind in **EXTERNAL_ACCESS** Assemblys nicht zulässig:  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   Alle **EXTERNAL_ACCESS** Assemblybedingungen werden geprüft.  
  
## <a name="runtime-checks"></a>Laufzeitüberprüfungen  
 Zur Laufzeit wird die Codeassembly auf die folgenden Bedingungen überprüft. Wird eine dieser Bedingungen erkannt, darf der verwaltete Code nicht ausgeführt werden und es wird eine Ausnahme ausgelöst.  
  
### <a name="unsafe"></a>UNSAFE  
 Laden einer Assembly (explizit durch Aufrufen der **System. Reflection. Assembly. Load ()** -Methode aus einem Bytearray) oder implizit durch die Verwendung von **Reflection.** "Namespace ausgeben" ist nicht zulässig.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Alle **unsicheren** Bedingungen werden geprüft.  
  
 Alle Typen und Methoden, die mit den folgenden Hostschutzattributwerten in der unterstützten Assemblyliste als Anmerkungen versehen sind, sind nicht zulässig.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   Benutzeroberfläche  
  
 Weitere Informationen zu HPAs und eine Liste der unzulässigen Typen und Member in den unterstützten Assemblys finden Sie unter [Host Schutz Attribute und CLR-Integrations Programmierung](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Alle **EXTERNAL_ACCESS** Bedingungen werden geprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte .NET Framework-Bibliotheken](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [Code Zugriffssicherheit für die CLR-Integration](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Host Schutz Attribute und Programmierung der CLR-Integration](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Erstellen von Assemblys](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
