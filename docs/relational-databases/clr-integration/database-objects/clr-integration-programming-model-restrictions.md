---
title: Einschränkungen des CLR-Integrationsprogrammmodells | Microsoft Docs
description: SQL Server führt Codeprüfungen für verwaltete Datenbankobjekte durch, wenn sie zum ersten Mal mit CREATE ASSEMBLY und zur Laufzeit registriert werden.
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
ms.openlocfilehash: 83b73909cf1844796640a83910ee609eadd7dba4
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488533"
---
# <a name="clr-integration-programming-model-restrictions"></a>Beschränkungen des Programmiermodells für die CLR-Integration
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Wenn Sie eine verwaltete gespeicherte Prozedur oder ein anderes verwaltetes Datenbankobjekt erstellen, müssen bestimmte Codeprüfungen durchgeführt werden, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] diesem ausgeführt werden müssen. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]führt Überprüfungen der verwalteten Codeassembly durch, wenn sie zum ersten Mal in der Datenbank registriert wird, mit der **CREATE ASSEMBLY-Anweisung** und auch zur Laufzeit. Der verwaltete Code wird außerdem zur Laufzeit überprüft, da in einer Assembly Codepfade vorhanden sein können, die zur Laufzeit eigentlich nicht erreicht werden.  Dadurch wird Flexibilität für die Registrierung von Assemblys von Drittanbietern geschaffen, sodass eine Assembly nicht blockiert wird, wenn ein "Unsafe"-Code vorliegt, der in einer Clientumgebung ausgeführt werden soll, jedoch nie in der gehosteten CLR ausgeführt wird. Die Anforderungen, die der verwaltete Code erfüllen muss, hängen davon ab, ob die Assembly als **SAFE**, **EXTERNAL_ACCESS**oder **UNSAFE**registriert ist, **SAFE** ist die strengste und werden unten aufgeführt.  
  
 Neben den Einschränkungen, die für verwaltete Codeassemblys gelten, werden außerdem Sicherheitsberechtigungen für Code erteilt. Die CLR (Common Language Runtime) unterstützt ein Sicherheitsmodell, das als Codezugriffssicherheit für verwalteten Code bezeichnet wird. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. **SAFE**-, **EXTERNAL_ACCESS-** und **UNSAFE-Assemblys** verfügen über unterschiedliche CAS-Berechtigungen. Weitere Informationen finden Sie unter [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY-Überprüfungen  
 Wenn die **CREATE ASSEMBLY-Anweisung** ausgeführt wird, werden die folgenden Prüfungen für jede Sicherheitsstufe durchgeführt.  Wenn eine Überprüfung fehlschlägt, schlägt **CREATE ASSEMBLY** mit einer Fehlermeldung fehl.  
  
### <a name="global-any-security-level"></a>Global (eine beliebige Sicherheitsebene)  
 Alle Assemblys, auf die verwiesen wird, müssen ein oder mehrere der folgenden Kriterien erfüllen:  
  
-   Die Assembly ist bereits in der Datenbank registriert.  
  
-   Die Assembly ist eine der unterstützten Assemblys. Weitere Informationen finden Sie unter [Unterstützte .NET Framework-Bibliotheken](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Sie verwenden CREATE ASSEMBLY_\<FROM-Standort>,_ und alle Assemblys, auf die verwiesen wird, und ihre Abhängigkeiten sind in **CREATE ASSEMBLY FROM** * \<speicherort>* verfügbar.  
  
-   Sie verwenden **CREATE ASSEMBLY FROM**_\<bytes ...>,_ und alle Verweise werden über durch Leerzeichen getrennte Bytes angegeben.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Alle **EXTERNAL_ACCESS** Assemblys müssen die folgenden Kriterien erfüllen:  
  
-   Statische Felder werden nicht verwendet, um Informationen zu speichern. Schreibgeschützte statische Felder sind zulässig.  
  
-   Der PEVerify-Test wird bestanden. Das PEVerify-Tool (peverify.exe), das überprüft, ob der MSIL-Code und die zugeordneten Metadaten den Anforderungen an die Typsicherheit entsprechen, wird mit .NET Framework SDK zur Verfügung gestellt.  
  
-   Die Synchronisierung, z. B. mit der **SynchronizationAttribute-Klasse,** wird nicht verwendet.  
  
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
  
-   Alle **EXTERNAL_ACCESS** Montagebedingungen werden überprüft.  
  
## <a name="runtime-checks"></a>Laufzeitprüfungen  
 Zur Laufzeit wird die Codeassembly auf die folgenden Bedingungen überprüft. Wird eine dieser Bedingungen erkannt, darf der verwaltete Code nicht ausgeführt werden und es wird eine Ausnahme ausgelöst.  
  
### <a name="unsafe"></a>UNSAFE  
 Das explizite Laden einer Assembly durch Aufrufen der **System.Reflection.Assembly.Load()-Methode** aus einem Bytearray oder implizit durch die Verwendung von **Reflection.Emit** namespace ist nicht zulässig.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Alle **UNSAFE-Bedingungen** werden überprüft.  
  
 Alle Typen und Methoden, die mit den folgenden Hostschutzattributwerten in der unterstützten Assemblyliste als Anmerkungen versehen sind, sind nicht zulässig.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Weitere Informationen zu HPAs und einer Liste nicht zulässiger Typen und Member in den unterstützten Assemblys finden Sie unter [Hostprotection Attributes and CLR Integration Programming](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Alle **EXTERNAL_ACCESS** Bedingungen werden überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte .NET Framework-Bibliotheken](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [CLR-Integrationscodezugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Host Protection-Attribute und CLR-Integrationsprogrammierung](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Erstellen von Assemblys](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
