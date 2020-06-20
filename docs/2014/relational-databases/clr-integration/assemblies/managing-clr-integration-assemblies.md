---
title: Verwalten von CLR-Integrationsassemblys Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: f9acc56d72d2ed994f497676813e45ef0a914431
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953780"
---
# <a name="managing-clr-integration-assemblies"></a>Verwalten von CLR-Integrationsassemblys
  Verwalteter Code wird kompiliert und dann in Einheiten bereitgestellt, die Assembly genannt werden. Eine Assembly wird als DLL oder ausführbare Datei (EXE) gepackt. Während eine ausführbare Datei auch alleine ausgeführt werden kann, muss eine DLL in einer vorhandenen Anwendung gehostet werden. Verwaltete DLL-Assemblys können in geladen und von gehostet werden [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Datenbank, die die Create Assembly-Anweisung verwendet, bevor Sie in den Prozess geladen und verwendet werden kann. Assemblys können auch von einer neueren Version aus mithilfe der ALTER ASSEMBLY-Anweisung aktualisiert oder aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der DROP ASSEMBLY-Anweisung entfernt werden.  
  
 Assemblyinformationen werden in der Tabelle `sys.assembly_files` in der Datenbank gespeichert, in der die Assembly installiert wurde. Die Tabelle `sys.assembly_files` enthält die folgenden Spalten.  
  
|Column|Beschreibung|  
|------------|-----------------|  
|assembly_id|Der für die Assembly definierte Bezeichner. Diese Nummer wird allen Objekten mit Bezug auf dieselbe Assembly zugewiesen.|  
|Name|Der Name des Objekts.|  
|file_id|Eine Nummer, die die einzelnen Objekte identifiziert, wobei das erste Objekt, das einer angegebenen `assembly_id` zugeordnet ist, den Wert 1 erhält. Wenn mehrere Objekte derselben `assembly_id` zugeordnet werden, wird jeder nachfolgende `file_id`-Wert um 1 erhöht.|  
|Inhalt|Die Hexadezimaldarstellung der Assembly oder Datei.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen von Assemblys](creating-an-assembly.md)  
 Erläutert das Erstellen der Assemblys SAFE, EXTERNAL_ACCESS und UNSAFE CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Ändern einer Assembly](altering-an-assembly.md)  
 Beschreibt das Aktualisieren von CLR-Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Löschen von Assemblys](dropping-an-assembly.md)  
 Erläutert das Löschen von CLR-Assemblys aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit der CLR-Integration](../security/clr-integration-security.md)   
 [CLR-Integration und Codezugriffssicherheit](../security/clr-integration-code-access-security.md)  
  
  
