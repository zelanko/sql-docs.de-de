---
title: Verwenden benutzerdefinierter Assemblys mit Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e79f48f4e4a2eb5fbc83c353461709658caf2509
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63265656"
---
# <a name="using-custom-assemblies-with-reports"></a>Verwenden benutzerdefinierter Assemblys mit Berichten
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] können Sie benutzerdefinierten Code für Werte, Formate und Formatierungen von Berichtselementen schreiben. Beispielsweise können Sie mit benutzerdefiniertem Code Währungen entsprechend einem Gebietsschema formatieren, bestimmte Werte mit speziellen Formatierungen belegen oder andere Geschäftsregeln anwenden, die in Ihrem Unternehmen praktiziert werden. Eine Möglichkeit, diesen Code in Berichte einzufügen, besteht in der Erstellung einer benutzerdefinierten Codeassembly unter Verwendung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], auf die Ihre Berichtsdefinitionsdateien verweisen können. Der Server ruft die Funktionen in Ihren benutzerdefinierten Assemblys auf, wenn ein Bericht ausgeführt wird. Mithilfe von benutzerdefinierten Assemblys können spezielle Funktionen abgerufen werden, die Sie in den Berichten verwenden möchten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Referencing Assemblies in an RDL File (Verweisen auf Assemblys in einer RDL-Datei)](referencing-assemblies-in-an-rdl-file.md)  
 Beschreibt, wie in einer Sprachdatei der Berichtsdefinition auf die benutzerdefinierten Assemblys verwiesen wird.  
  
 [Bereitstellen einer benutzerdefinierten Assembly](deploying-a-custom-assembly.md)  
 Beschreibt den Einsatz einer benutzerdefinierten Assembly im Berichtsserver und im Berichts-Manager.  
  
 [Using Strong-Named Custom Assemblies (Verwenden von benutzerdefinierten Assemblys mit starken Namen)](using-strong-named-custom-assemblies.md)  
 Beschreibt die Verwendung benutzerdefinierter Assemblys zusammen mit starken Namen.  
  
 [Asserting Permissions in Custom Assemblies (Berechtigungserteilung in benutzerdefinierten Assemblys)](asserting-permissions-in-custom-assemblies.md)  
 Beschreibt, wie benutzerdefinierte Assemblys mit beschränkten und speziellen Berechtigungen eingesetzt werden und wie diese Berechtigungen im Code erteilt werden.  
  
 [Accessing Custom Assemblies Through Expressions (Zugriff auf benutzerdefinierte Assemblys über Ausdrücke)](accessing-custom-assemblies-through-expressions.md)  
 Beschreibt, wie benutzerdefinierte Assemblymethoden als Berichtsausdrücke in den Berichtsdefinitionen aufgerufen werden.  
  
 [Initializing Custom Assembly Objects (Initialisieren von Objekten benutzerdefinierter Assemblys)](initializing-custom-assembly-objects.md)  
 Beschreibt, wie Werte für benutzerdefinierte Assemblyobjekte initialisiert werden, die von einem Bericht aufgerufen werden.  
  
 [Vorgehensweise: Debuggen von benutzerdefinierten Assemblys](how-to-debug-custom-assemblies.md)  
 Beschreibt das Debuggen von benutzerdefiniertem Assemblycode.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsdefinitionssprache (SSRS)](../reports/report-definition-language-ssrs.md)  
  
  
