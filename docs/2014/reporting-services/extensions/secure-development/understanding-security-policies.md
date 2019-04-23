---
title: Grundlegendes zu Sicherheitsrichtlinien| Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services], security policies
- Execution permission set
- custom assemblies [Reporting Services], security
- permission sets [Reporting Services]
- expressions [Reporting Services], security
- evidence [Reporting Services]
- FullTrust permission set
- security policies [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: a9bf043a-139a-4929-9a58-244815323df0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb69c4b064329b53f9ab3efef62f0d1c54b897a9
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60155849"
---
# <a name="understanding-security-policies"></a>Grundlegendes zu Sicherheitsrichtlinien
  Jeder Code, der von einem Berichtsserver ausgeführt wird, muss Teil einer bestimmten Codezugriff-Sicherheitsrichtlinie sein. Diese Sicherheitsrichtlinien bestehen aus Codegruppen, die einem Satz von benannten Berechtigungen Beweise zuordnen. Häufig sind Codegruppen einem benannten Berechtigungssatz zugeordnet, der die zulässigen Berechtigungen für Code in dieser Gruppe angibt. Die Laufzeit bestimmt anhand von Beweisen, die von einem vertrauenswürdigen Host oder dem Ladeprogramm bereitgestellt werden, zu welchen Codegruppen der Code gehört und welche Berechtigungen ihm daher zuzuweisen sind. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verwendet diese von der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Common Language Runtime (CLR) definierte Sicherheitsrichtlinienarchitektur. In den nachfolgenden Abschnitten werden die verschiedenen Codetypen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sowie die damit verknüpften Richtlinienregeln aufgeführt.  
  
## <a name="report-server-assemblies"></a>Berichtsserverassemblys  
 Berichtsserverassemblys sind Assemblys mit Code, der zu [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] gehört. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] wurde mit verwalteten Codeassemblys geschrieben. Alle diese Assemblys verfügen über starke Namen (sind digital signiert). Die Codegruppen für diese Assemblys werden mit **StrongNameMembershipCondition** definiert, die Beweise auf der Grundlage des öffentlichen Schlüssels für den starken Namen der Assembly bereitstellen. Der Codegruppe werden die **FullTrust**-Berechtigungen gewährt.  
  
## <a name="report-server-extensions-rendering-data-delivery-and-security"></a>Berichtsservererweiterungen (Rendering, Daten, Übermittlung und Sicherheit)  
 Berichtsservererweiterungen sind benutzerdefinierte Erweiterungen für Daten, Übermittlung, Rendering und Sicherheit, die Sie selbst oder Drittanbieter zur Erweiterung der Funktionen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] erstellen. Sie müssen diesen Erweiterungen oder dem Assemblycode in den Richtlinienkonfigurationsdateien, die mit der zu erweiternden [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Komponente verknüpft sind, **FullTrust** gewähren. Erweiterungen, die im Lieferumfang von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthalten sind, sind mit dem öffentlichen Schlüssel des Berichtsservers signiert und erhalten den **FullTrust**-Berechtigungssatz.  
  
> [!IMPORTANT]  
>  Sie müssen die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Richtlinienkonfigurationsdateien ändern, um **FullTrust** für Erweiterungen von Drittanbietern zu gewähren. Wenn Sie den benutzerdefinierten Erweiterungen keine Codegruppe mit **FullTrust** hinzufügen, können sie nicht vom Berichtsserver verwendet werden.  
  
 Weitere Informationen zu den Richtlinienkonfigurationsdateien in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] finden Sie unter [Using Reporting Services Security Policy Files (Verwenden von Reporting Services-Sicherheitsrichtliniendateien)](using-reporting-services-security-policy-files.md).  
  
## <a name="expressions-used-in-reports"></a>In Berichten verwendete Ausdrücke  
 Berichtsausdrücke sind Inlinecodeausdrücke oder benutzerdefinierte Methoden im **Code**-Element einer Berichtsdefinitions-Sprachdatei. In den Richtliniendateien ist bereits eine Codegruppe definiert, die diesen Ausdrücken die standardmäßig festgelegte Berechtigung **Execution** gewährt. Die Codegruppe sieht wie folgt aus:  
  
```  
<CodeGroup  
   class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="Execution"  
   Name="Report_Expressions_Default_Permissions"  
   Description="This code group grants default permissions for code in report expressions and Code element. ">  
    <IMembershipCondition  
       class="StrongNameMembershipCondition"  
       version="1"  
       PublicKeyBlob="002400..."  
    />  
</CodeGroup>  
```  
  
 Die Berechtigung **Execution** lässt zu, dass Code ausgeführt werden kann, wobei jedoch keine geschützten Ressourcen verwendet werden können. Alle in einem Bericht gefundenen Ausdrücke werden in einer Assembly kompiliert ("Ausdruckshostassembly"), die als Teil des kompilierten Berichts gespeichert wird. Beim Ausführen des Berichts lädt der Berichtsserver die Ausdruckshostassembly und führt Aufrufe für diese Assembly zum Ausführen von Berechtigungen durch. Ausdruckshostassemblys werden mit einem bestimmten Schlüssel signiert, der zum Definieren der Codegruppe für alle Ausdruckshosts verwendet wird.  
  
 Berichtsausdrücke beziehen sich auf Berichtsobjekt-Modellauflistungen (Felder, Parameter usw.) und führen einfache Aufgaben wie arithmetische und Zeichenfolgenoperationen aus. Code, der diese einfachen Vorgänge ausführt, erfordert nur die Berechtigung **Execution**. Standardmäßig wird benutzerdefinierten Methoden im **Code**-Element und benutzerdefinierten Assemblys in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] die Berechtigung **Execution** gewährt. Daher muss bei den meisten Ausdrücken die aktuelle Konfiguration nicht in den Sicherheitsrichtliniendateien geändert werden. Um Ausdruckshostassemblys weitere Berechtigungen gewähren zu können, muss ein Administrator die Riechlinienkonfigurationsdateien des Berichtsservers und des Berichts-Designers anpassen sowie die Berichtsausdruck-Codegruppe ändern. Da es sich um eine globale Einsstellung handelt, wirkt sich eine Änderung der Standardberechtigungen für den Ausdruckshost auf alle Berichte aus. Aus diesem Grund wird empfohlen, jeglichen Code, der zusätzliche Sicherheit erfordert, in einer benutzerdefinierten Assembly zu speichern. Nur dieser Assembly werden die benötigten Berechtigungen gewährt.  
  
> [!IMPORTANT]  
>  Code, der externe Assemblys oder geschützte Ressourcen aufruft, muss zur Verwendung in Berichten in eine benutzerdefinierte Assembly einbezogen werden. Auf diese Weise können Sie die vom Code angeforderten und durchgesetzten Berechtigungen besser steuern. Es sollten keine Aufrufe von sicheren Methoden im **Code**-Element erfolgen. Hierzu müssen Sie dem Berichtsausdruckshost **FullTrust** sowie dem gesamten benutzerdefinierten Code Vollzugriff auf die CLR gewähren.  
  
> [!CAUTION]  
>  Gewähren Sie der Codegruppe für einen Berichtsausdruckshost keine **FullTrust**-Berechtigung. Ansonsten können alle Berichtsausdrücke geschützte Systemaufrufe ausführen.  
  
## <a name="custom-assemblies-referenced-in-reports"></a>In Berichten referenzierte benutzerdefinierte Assemblys  
 Einige Berichtsausdrücke können Codeassemblys von Drittanbietern aufrufen, die in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] auch als benutzerdefinierte Assemblys bezeichnet werden. Der Berichtsserver erwartet, dass diese Assemblys mindestens über die Berechtigung **Execution** in den Richtlinienkonfigurationsdateien verfügen. Standardmäßig gewähren die im Lieferumfang von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthaltenen Richtliniendateien allen Assemblys beginnend mit der Zone „Arbeitsplatz“ die Berechtigung **Execution**. Sie können benutzerdefinierten Assemblys nach Bedarf zusätzliche Berechtigungen gewähren.  
  
 In einigen Fällen müssen Sie einen Vorgang ausführen, der bestimmte Codeberechtigungen in einem Berichtsausdruck erfordert. In der Regel bedeutet dies, dass ein Berichtsausdruck einen Aufruf einer sicheren CLR-Bibliotheksmethode (z. B. einer Methode, die auf Dateien oder die Systemregistrierung zugreift) durchführen muss. In der Dokumentation zu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] werden die Codeberechtigungen beschrieben, die zum Durchführen dieses sicheren Aufrufs notwendig sind. Um den Aufruf ausführen zu können, müssen dem aufrufenden Code diese speziellen, sicheren Berechtigungen gewährt werden. Wenn Sie den Aufruf von einem Berichtsausdruck oder dem **Code**-Element aus durchführen, müssen der Ausdruckshostassembly die entsprechenden Berechtigungen gewährt werden. Nachdem Sie dem Ausdruckshost jedoch die Berechtigung gewährt haben, gilt diese spezielle Berechtigung für jeglichen Code, der in einem Ausdruck eines beliebigen Berichts ausgeführt wird. Es ist sicher, diesen Aufruf von einer benutzerdefinierten Assembly auszuführen und dieser benutzerdefinierten Assembly die speziellen Berechtigungen zuzuweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Code Access Security in Reporting Services (Codezugriffssicherheit in Reporting Services)](code-access-security-in-reporting-services.md)   
 [Sichere Entwicklung (Reporting Services)](secure-development-reporting-services.md)  
  
  
