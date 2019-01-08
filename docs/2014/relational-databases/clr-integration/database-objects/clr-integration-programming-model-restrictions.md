---
title: Beschränkungen des Programmiermodells der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: a9b51e0fc192c94b32b4d496523dbf3c9216efd6
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52509897"
---
# <a name="clr-integration-programming-model-restrictions"></a>Beschränkungen des Programmiermodells für die CLR-Integration
  Wenn Sie eine verwaltete gespeicherte Prozedur oder anderes verwaltetes Datenbankobjekt erstellen, es gibt bestimmte codeprüfungen ausgeführt werden, indem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] führt Überprüfungen der verwalteten Codeassembly, wenn es zuerst in der Datenbank registriert wird mithilfe der `CREATE ASSEMBLY` -Anweisung, und auch zur Laufzeit. Der verwaltete Code wird außerdem zur Laufzeit überprüft, da in einer Assembly Codepfade vorhanden sein können, die zur Laufzeit eigentlich nicht erreicht werden.  Dadurch wird Flexibilität für die Registrierung von Assemblys von Drittanbietern geschaffen, sodass eine Assembly nicht blockiert wird, wenn ein "Unsafe"-Code vorliegt, der in einer Clientumgebung ausgeführt werden soll, jedoch nie in der gehosteten CLR ausgeführt wird. Die Anforderungen an, die der verwaltete Code erfüllen muss, hängen davon ab, ob die Assembly, als registriert wurde `SAFE`, `EXTERNAL_ACCESS`, oder `UNSAFE`, `SAFE` ist die strengste Anforderung, und sind unten aufgeführt.  
  
 Neben den Einschränkungen, die für verwaltete Codeassemblys gelten, werden außerdem Sicherheitsberechtigungen für Code erteilt. Die CLR (Common Language Runtime) unterstützt ein Sicherheitsmodell, das als Codezugriffssicherheit für verwalteten Code bezeichnet wird. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. `SAFE`-, `EXTERNAL_ACCESS`- und `UNSAFE`-Assemblys verfügen über andere CAS-Berechtigungen (Code Access Security). Weitere Informationen finden Sie unter [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY-Überprüfungen  
 Wenn die `CREATE ASSEMBLY`-Anweisung ausgeführt wird, werden die folgenden Überprüfungen für jede Sicherheitsebene vorgenommen.  Schlägt eine Überprüfung fehl, wird `CREATE ASSEMBLY` mit einer Fehlermeldung abgebrochen.  
  
### <a name="global-any-security-level"></a>Global (eine beliebige Sicherheitsebene)  
 Alle Assemblys, auf die verwiesen wird, müssen ein oder mehrere der folgenden Kriterien erfüllen:  
  
-   Die Assembly ist bereits in der Datenbank registriert.  
  
-   Die Assembly ist eine der unterstützten Assemblys. Weitere Informationen finden Sie unter [unterstützt .NET Framework-Bibliotheken](supported-net-framework-libraries.md).  
  
-   Verwenden Sie `CREATE ASSEMBLY FROM`  *\<Speicherort >,* und alle referenzierten Assemblys und deren Abhängigkeiten stehen im  *\<Speicherort >*.  
  
-   Verwenden Sie `CREATE ASSEMBLY FROM`  *\<Bytes... >,* und alle Verweise, durch Leerzeichen angegeben werden getrennte Bytes.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Alle `EXTERNAL_ACCESS`-Assemblys müssen die folgenden Kriterien erfüllen:  
  
-   Statische Felder werden nicht verwendet, um Informationen zu speichern. Schreibgeschützte statische Felder sind zulässig.  
  
-   Der PEVerify-Test wird bestanden. Das PEVerify-Tool (peverify.exe), das überprüft, ob der MSIL-Code und die zugeordneten Metadaten den Anforderungen an die Typsicherheit entsprechen, wird mit .NET Framework SDK zur Verfügung gestellt.  
  
-   Die Synchronisierung, z. B. mit der `SynchronizationAttribute`-Klasse, wird nicht verwendet.  
  
-   Finalizer-Methoden werden nicht verwendet.  
  
 Die folgenden benutzerdefinierten Attribute sind in `EXTERNAL_ACCESS`-Assemblys nicht zulässig:  
  
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
  
-   Alle `EXTERNAL_ACCESS`-Assemblybedingungen werden überprüft.  
  
## <a name="runtime-checks"></a>Überprüfungen zur Laufzeit  
 Zur Laufzeit wird die Codeassembly auf die folgenden Bedingungen überprüft. Wird eine dieser Bedingungen erkannt, darf der verwaltete Code nicht ausgeführt werden und es wird eine Ausnahme ausgelöst.  
  
### <a name="unsafe"></a>UNSAFE  
 Laden einer Assembly entweder explizit durch Aufrufen der `System.Reflection.Assembly.Load()` -Methode aus einem Bytearray oder implizit durch die Verwendung von `Reflection.Emit` Namespace-ist nicht zulässig.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Alle `UNSAFE`-Bedingungen werden überprüft.  
  
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
  
 Weitere Informationen über Hostschutzattribute und eine Liste der unzulässigen Typen und Member in den unterstützten Assemblys finden Sie unter [Hostschutzattribute und Programmieren von CLR-Integration](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Alle `EXTERNAL_ACCESS`-Bedingungen werden überprüft.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte .NET Framework-Bibliotheken](supported-net-framework-libraries.md)   
 [Codezugriffssicherheit für CLR-Integration](../security/clr-integration-code-access-security.md)   
 [Hostschutzattribute und Programmierung der CLR-Integration](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Erstellen von Assemblys](../assemblies/creating-an-assembly.md)  
  
  
