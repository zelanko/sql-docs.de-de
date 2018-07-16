---
title: Verwalten von CLR-Integrationsassemblys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
caps.latest.revision: 56
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ab48a77c21b3ae288f18b166241b1021a7ee6766
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352517"
---
# <a name="managing-clr-integration-assemblies"></a>Verwalten von CLR-Integrationsassemblys
  Verwalteter Code wird kompiliert und dann in Einheiten bereitgestellt, die Assembly genannt werden. Eine Assembly wird als DLL oder ausführbare Datei (EXE) gepackt. Während eine ausführbare Datei auch alleine ausgeführt werden kann, muss eine DLL in einer vorhandenen Anwendung gehostet werden. Verwaltete DLL-Assemblys in geladen werden können, und von gehosteten [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Datenbank mit der CREATE ASSEMBLY-Anweisung aus, bevor er in den Prozess geladen und verwendet werden kann. Assemblys können auch von einer neueren Version aus mithilfe der ALTER ASSEMBLY-Anweisung aktualisiert oder aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der DROP ASSEMBLY-Anweisung entfernt werden.  
  
 Assemblyinformationen werden in der Tabelle `sys.assembly_files` in der Datenbank gespeichert, in der die Assembly installiert wurde. Die Tabelle `sys.assembly_files` enthält die folgenden Spalten.  
  
|Spalte|Description|  
|------------|-----------------|  
|assembly_id|Der für die Assembly definierte Bezeichner. Diese Nummer wird allen Objekten mit Bezug auf dieselbe Assembly zugewiesen.|  
|NAME|Der Name des Objekts.|  
|file_id|Eine Nummer, die die einzelnen Objekte identifiziert, wobei das erste Objekt, das einer angegebenen `assembly_id` zugeordnet ist, den Wert 1 erhält. Wenn mehrere Objekte derselben `assembly_id` zugeordnet werden, wird jeder nachfolgende `file_id`-Wert um 1 erhöht.|  
|content|Die Hexadezimaldarstellung der Assembly oder Datei.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen von Assemblys](creating-an-assembly.md)  
 Erläutert das Erstellen der Assemblys SAFE, EXTERNAL_ACCESS und UNSAFE CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Ändern einer Assembly](altering-an-assembly.md)  
 Beschreibt das Aktualisieren von CLR-Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Löschen von Assemblys](dropping-an-assembly.md)  
 Erläutert das Löschen von CLR-Assemblys aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../security/clr-integration-security.md)   
 [CLR-Integration und Codezugriffssicherheit](../security/clr-integration-code-access-security.md)  
  
  
